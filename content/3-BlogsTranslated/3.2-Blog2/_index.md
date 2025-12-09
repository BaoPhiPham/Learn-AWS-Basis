---
title: "Blog 2"
date: 2025-10-04
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# **Host persistent world games on Amazon GameLift Servers** 

Multiplayer games have evolved from session-based games and traditional massively multiplayer online games (MMOs) to new online experiences that combine persistent and session-based elements. Games like Destiny 2 and Rust are prime examples. Persistent games can be “hubs” or “home worlds” that players travel to and interact with, and then join session-based experiences. These games allow players to create new persistent worlds and log in and out at will. Supporting this new wave of multiplayer experiences requires flexible technology, both in terms of session management and game world data storage.

[Amazon GameLift Servers](https://aws.amazon.com/gamelift/) is a purpose-built solution for hosting multiplayer games of all genres on a global scale. The service supports a wide range of use cases, from traditional session-based games to various types of persistent games. Introducing container support for Amazon GameLift Servers simplifies the challenges of hosting session-based and persistent world games. Persistent world games can run secondary container processes next to each game server to access a database for persistent data. You can also split world state management into multiple container processes that can communicate over localhost. When accessing other AWS services for your game, the container fleet [AWS Identity and Access Management (IAM)](https://aws.amazon.com/iam/) role is automatically assigned to each container, allowing you to use the [AWS SDK](https://builder.aws.com/build/tools) and  [AWS Command Line Interface (AWS CLI)](https://aws.amazon.com/cli/).

In this article, we will walk through how to combine session-based and persistent gameplay. This article covers the following steps:

* Managing the Lifecycle of Persistent Worlds
* Managing Player Sessions for Persistent Worlds
* Storing Game World State
* Starting a Session-Based Game from a Persistent Experience

### **Managing the Lifecycle of Persistent Worlds**

Persistent worlds encourage you to create new worlds as needed and allow players to join and leave. World creation can be triggered by players or managed centrally by your governance system. You also need to route players to these worlds and manage player sessions.

The first step is to upload your game server build as a zip file or container image, and create a global fleet to host on Amazon GameLift Server. Multi-location capabilities allow you to host game worlds close to your players around the globe. The [Containers Starter Kit](https://github.com/aws/amazon-gamelift-toolkit/tree/main/containers-starter-kit) is a quick and easy way to run any game server build on the service.

To create game world instances on a fleet, use the CreateGameSession API with the AWS SDK. When calling the API, you pass the location and any game world-specific metadata you need to create the world and receive information about the world in response. For a more event-based stream, you can also use the [Amazon GameLift Servers Queue](https://docs.aws.amazon.com/gameliftservers/latest/developerguide/queues-creating.html), and place game sessions on the fleet through the queue.

Example CreateGameSession request (using AWS CLI demonstration):

```bash
aws gamelift create-game-session \
  --fleet-id my-fleet-id \
  --location us-west-2 \
  --maximum-player-session-count 200 \
  --game-properties "Key=worldName,Value=MyWorld" "Key=mapToLoad,Value=HomeArena"
```

A successful response will look like this:

```json
{
  "GameSession": {
    "GameSessionId": "arn:aws:gamelift:us-west-2::gamesession/id",
    "FleetId": "my-fleet-id",
    "FleetArn": "arn:aws:gamelift:us-west-2:111122223333:my-fleet",
    "CreationTime": "2025-02-18T20:51:01.714000+00:00",
    "CurrentPlayerSessionCount": 0,
    "MaximumPlayerSessionCount": 200,
    "Status": "ACTIVATING",
    "GameProperties": [],
    "IpAddress": "11.222.3.444",
    "DnsName": "ec2-11-222-3-444.us-west-2.compute.amazonaws.com",
    "Port": 4195,
    "PlayerSessionCreationPolicy": "ACCEPT_ALL",
    "Location": "us-west-2",
    "GameProperties": [
      {
        "Key": "worldName",
        "Value": "MyWorld"
      },
      {
        "Key": "mapToLoad",
        "Value": "HomeArena"
      }
    ]
  }
}
```

The game session information you receive in response is then stored in a database for future reference. One option for storing data is [Amazon DynamoDB](https://aws.amazon.com/dynamodb/), which allows you to store key-value data at scale. The figure below illustrates a sample architecture for storing game world information. Game world creation can be triggered by a player request (e.g., creating a fixed world to play with friends) or by a backend process (e.g., serving fixed worlds based on developer-provided configuration).

![](/images/3-Translated-Blogs/3.2-Blog2/1.png) 

*Figure 1: Game session creation (player and backend initialization).*

When the game world becomes idle or reaches its fixed lifetime, the underlying game session is typically terminated by the game server process itself. Amazon GameLift Server allows you to host your game server process for as long as you need. Once the game server has stored state and is ready to terminate, it calls the Amazon GameLift Server SDK's ProcessEnding() method to automatically delete the game session. The fleet immediately creates a new process ready to host another world. You can also trigger the termination of a game session externally using the TerminateGameSession API from your game backend. When using the graceful termination option of this API, the game server receives a callback and can manage the graceful termination.

### **Managing Player Sessions for Persistent Worlds**

Players can often leave and join persistent worlds over time. You can choose to manage player sessions in your backend or use the player session features of Amazon GameLift Server. Player sessions are created using the CreatePlayerSession API.

Here's an example of how to request a player session with the AWS CLI:

```bash
aws gamelift create-player-session \
  --game-session-id arn:aws:gamelift:us-west-2::gamesession/id \
  --player-id 12345
```

After a successful response, you will receive connection information that can be passed back to the game client:

```json
{
  "PlayerSession": {
    "PlayerSessionId": "psess-abcd1234",
    "PlayerId": "12345",
    "GameSessionId": "arn:aws:gamelift:us-west-2::gamesession/id",
    "FleetId": "my-fleet-id",
    "FleetArn": "arn:aws:gamelift:us-west-2:111122223333:my-fleet",
    "CreationTime": "2025-02-18T20:54:54.304000+00:00",
    "Status": "RESERVED",
    "IpAddress": "11.222.3.444",
    "DnsName": "ec2-11-222-3-444.us-west-2.compute.amazonaws.com",
    "Port": 4195
  }
}
```

The game client can then connect directly to the session using the IP/DnsName and Port. The PlayerSessionId property can be used to authenticate the player's identity on the game server and activate the player session. The figure below illustrates how a player requests to join a specific world, with the world information being retrieved from DynamoDB and a player session being created for that world to provide connection information.

![](/images/3-Translated-Blogs/3.2-Blog2/2.png) 

*Figure 2: Joining a game world.*

To keep track of the current number of player sessions in a world, such as updates on players who have left, we recommend centrally updating the game session data in your database. You can run a backend process to continuously update the data. The DescribeGameSessions API can be used to iterate over all game sessions. It retrieves up to 100 game sessions per request, and you can iterate over all sessions using the NextToken received in the responses. The following figure illustrates an example of this implementation.

![](/images/3-Translated-Blogs/3.2-Blog2/3.png) 

*Figure 3: Updating the current state of the game world to your database.*

### **Pertaining the game world state**

Normally, while a session is running, the game world state is stored in memory. However, we recommend periodically storing the world state to an external data store for several reasons. One reason is to clean up idle worlds after persisting their state, allowing you to restore the state when the player rejoins. If you are storing game worlds that have a lifetime of weeks or even months, you want to be able to restore the world state in case the game server process crashes or when performing periodic world rotations to avoid memory leaks.

Here are some options for storing world state from your game server fleet:

* Save the world save file directly to [Amazon S3](https://aws.amazon.com/s3/)
* Run a local database on disk and sync a copy/dump of the database to Amazon S3
* Save the world data as key-value data in DynamoDB
* Implement a secure API layer to receive the world data and save it to a database of your choice

In the following sections, we will go into detail for each of these options.

#### **Save world save files directly to Amazon S3**

Amazon GameLift servers support attaching IAM roles to instances or containers [Amazon Elastic Compute Cloud (Amazon EC2](https://aws.amazon.com/ec2/)) in your fleet. You can assign permissions to this role to access resources such as Amazon S3. Accessing these resources can be done through the AWS SDK directly on the game server process, or by running a backend process or container that manages access.

When you store world save files directly to Amazon S3, you create the save file on the game server and upload it to Amazon S3. If you need to restore the world state on a different game server process later, you will have to load the world data at launch.

#### **Run a local database on disk and sync database backups to Amazon S3**

Another approach is to host a local database, typically a SQL-based database solution that the game server writes world updates to continuously. You then have a sidecar process or container create database backups and upload them to Amazon S3 at intervals of your choosing.

###**Save world data as key-value data in DynamoDB**

A recommended option is to store world state directly in a database, again using the AWS SDK on your game server or using a sidecar process or container that the game server talks to. Amazon DynamoDB is a great, highly scalable option for this.

The benefit of this approach is that you have a fully managed, highly scalable key-value database, and all world state changes are recorded in near real-time. This approach also provides seamless world state recovery. If your game design requires that every player action be stored immediately, this approach works well. Amazon Games New World is an example of a game that uses this approach, handling around 800,000 writes every 30 seconds to store game state. DynamoDB has a 400 kB item size limit, so you often need to split your world data into multiple items.

#### **Use a sidecar process for storage and databases**

Game servers are typically headless versions of Unreal, Unity, or other game engine builds. Accessing the database or storage service directly from the game server is possible, but splitting this responsibility to a sidecar process or container offers several benefits:

* Use the AWS SDK in a popular backend language like Python or Go.

* No additional dependencies on your game server project.

* Develop and maintain database and storage integrations independently of your game server.

* Offload heavy I/O operations from your game server process.

Amazon GameLift Servers container fleet allows you to define a secondary container that your game server can access, for example via an HTTPS endpoint on localhost, as shown below:

*![](/images/3-Translated-Blogs/3.2-Blog2/4.png) *

*Figure 4: Using a sidecar process to store world data.*

### **Starting session-based play from a persistent experience**

Once a persistent experience is deployed, we can consider session-based elements of the game. This could be players gathering in your hub and starting a session-based PvE adventure, or a matchmaking-based PvP experience, depending on the game design.

Either way, session-based game hosting is a native feature of Amazon GameLift Server. First, you upload your game server build and set up where in the world you want to host the game. You then have two options depending on your experience: create a session for a group of players directly or use matchmaking.

#### **Create a session for a group of players**

Once you know the group of players you will be starting a session for (they may be grouped in your hub world), you can use Amazon GameLift Server Queues to request a session to be placed on them. You can pass individual player latency for all locations you support or provide a priority list of locations to place the session. You can also specify session attributes in the placement request. The game server process will receive this information and can use it to load the correct map, for example.

Here is an example of a multiplayer session placement request using the AWS CLI:

```bash
aws gamelift start-game-session-placement \
  --game-session-queue-name my-game-session-queue \
  --placement-id "unique-id-1234" \
  --maximum-player-session-count 200 \
  --game-properties "Key=mapName,Value=DungeonRaid" "Key=difficulty,Value=hard" \
  --player-latencies "PlayerId=player1,RegionIdentifier=us-east-1,LatencyInMilliseconds=20" "PlayerId=player2,RegionIdentifier=us-east-1,LatencyInMilliseconds=30" \
  --desired-player-sessions "PlayerId=player1" "PlayerId=player2"
```

Queues emit placement events ([placement events](https://docs.aws.amazon.com/gamelift/latest/developerguide/queue-events.html)) that your game software can process to communicate session information to players.

#### **Use matchmaking to group players**

Another option is for players to select experiences based on the session they want to join, and the game management system will create matchmaking tickets for each player to find the optimal group of players. This built-in matchmaking uses [Amazon GameLift Servers FlexMatch](https://docs.aws.amazon.com/gameliftservers/latest/flexmatchguide/match-intro.html), which can have matchmaking rules based on latency, team, as well as player skill level and other attributes. If your players have created a team in a persistent experience, they can be matched up to ensure they are on the same team in a shared session.

Here is an example API call to initiate a matchmaking ticket:

```bash
aws gamelift start-matchmaking \
  --configuration-name "MyMatchmakingConfig" \
  --players 'PlayerId=player123,LatencyInMs={us-west-2=45,us-east-1=120},PlayerAttributes={skill={N=29}}'
```

For a pre-formed group of players, you would transfer all players in a single call to ensure that they join the same team in a common session:

```bash
aws gamelift start-matchmaking \
  --configuration-name "MyMatchmakingConfig" \
  --players 'PlayerId=player1,LatencyInMs={us-west-2=45,us-east-1=120},PlayerAttributes={skill={N=29}}' \
           'PlayerId=player2,LatencyInMs={us-west-2=50,us-east-1=125},PlayerAttributes={skill={N=39}}'
```

### **Conclusion**

In this article, we covered how to use Amazon GameLift Server to host a global persistent world game. We also covered how you can manage player sessions for persistent worlds. Furthermore, we discussed different methods for maintaining world state and delved into how you can combine session-based gaming with persistent experiences.

Modern multiplayer games use a variety of strategies to manage how players are grouped and how they are mapped to different versions of the game world and session-based gaming. Amazon GameLift Server provides capabilities and APIs that allow you to build unique experiences that fit your game design. Furthermore, the power of the diversity of services on AWS allows you to scale efficiently to different methods for managing backend functionality and maintaining world state.

Get started today with Amazon GameLift Servers to host your multiplayer game servers. [Contact an AWS representative](https://pages.awscloud.com/Amazon-Game-Tech-Contact-Us.html) to learn how we can help boost your business.

### **See also**

* [Persistent world game hosting on AWS.](https://aws.amazon.com/solutions/guidance/persistent-world-game-hosting-on-aws/?did=sl_card&trk=sl_card)
* [Faster multiplayer hosting with containers on Amazon GameLift Servers.](https://aws.amazon.com/blogs/gametech/faster-multiplayer-hosting-with-containers-on-amazon-gamelift-servers/)
* [Amazon GameLift achieves 100 million concurrently connected users per game.](https://aws.amazon.com/blogs/gametech/amazon-gamelift-achieves-100-million-concurrently-connected-users-per-game/)

|                                                 |                                                                                                                                                                                                                                                                                                                         |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](/images/3-Translated-Blogs/3.2-Blog2/5.png) | **Juho Jantunen** Juho Jantunen is a Global Principal Solutions Architect on the AWS for Games team, specializing in server hosting and backend solutions for games. He has experience in the gaming and cloud industries and has built and operated game backends on AWS for multiple titles with millions of players. |