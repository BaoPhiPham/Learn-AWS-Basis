---
title: "Blog 3"
date: 2025-10-04
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# **Build real-time conversational AI experiences using Amazon Nova Sonic and LiveKit** 

The rapid growth of generative AI technology has been a catalyst for business productivity growth, creating new opportunities for greater efficiency, enhanced customer service experiences, and more successful customer outcomes. Advances in generative AI today are helping existing technologies achieve their long-promised potential. For example, voice-first applications have been increasingly prevalent across many industries over the years—from customer service to education to personal voice assistants and agents. But early versions of this technology struggled to interpret human speech or simulate real-life conversations.c. Building real-time, natural, low-latency voice AI remains complex, especially when working with streaming infrastructure and voice platform models (FMs).

The rapid advancement of conversational AI technology has led to the development of powerful models that address the historical challenges of traditional voice-first applications. [Amazon Nova Sonic](https://aws.amazon.com/ai/generative-ai/nova/speech/) is an advanced speech-to-speech FM designed for building real-time conversational AI applications on [Amazon Bedrock](https://aws.amazon.com/bedrock/). It offers industry-leading price performance and low latency. The Amazon Nova Sonic architecture unifies speech understanding and generation into a single model, enabling truly human-like voice conversations in AI applications.

Amazon Nova Sonic caters to the richness and variety of human language. It can understand speech in a variety of styles and generate speech with a variety of expressive accents, including male and female voices. Amazon Nova Sonic can also adjust the accent, intonation, and style of the generated voice response to match the context and content of the input. Additionally, Amazon Nova Sonic supports function invocation and knowledge base with enterprise data using Retrieval-Augmented Generation (RAG). To further simplify the process of getting the most out of this technology, Amazon Nova Sonic is now integrated with [LiveKit Agents](https://docs.livekit.io/agents/?utm_source=aws&utm_medium=blog&utm_campaign=nova_sonic_plugin), a popular platform that helps developers build real-time communication applications using audio, video, and data. This integration allows developers to build conversational voice interfaces without managing complex audio pipelines or signaling protocols. In this post, we explain how this integration works, how it addresses the historical challenges of voice-first applications, and some first steps to get started with this solution.

### **Solution Overview**

[LiveKit](https://livekit.io/?utm_source=aws&utm_medium=blog&utm_campaign=nova_sonic_plugin) is an open-source platform for building voice, video, and physical AI applications that can see, hear, and speak. Designed as a comprehensive solution, it provides SDKs for web, mobile, and backend clients, a WebRTC server for low-latency network transport, and built-in features like user turn detection, agent load balancing, telephony, and third-party integrations. Developers can build powerful agent workflows for real-time applications without worrying about the underlying infrastructure, whether self-hosted, deployed on AWS, or running on LiveKit's cloud service.

Building real-time, voice-first AI applications requires managing complex infrastructure—from audio recording and streaming to signaling, routing, and latency optimization—especially when using bidirectional models like Amazon Nova Sonic. To simplify, we integrate a [Nova Sonic plugin](https://docs.livekit.io/agents/models/realtime/plugins/nova-sonic/?utm_source=aws&utm_medium=blog&utm_campaign=nova_sonic_plugin) into LiveKit's Agents model, eliminating the need to manage custom pipelines or transport layers. LiveKit handles real-time audio routing and session management, while Nova Sonic provides speech understanding and generation. Developers are equipped with features like full-duplex audio, voice activity detection, and noise suppression, allowing them to focus on designing great user experiences for their AI voice applications.

The video below demonstrates Amazon Nova Sonic and LiveKit in action. You can find the code for this example in the [LiveKit Examples GitHub repo](https://github.com/livekit-examples?utm_source=aws&utm_medium=blog&utm_campaign=nova_sonic_plugin).

[![ml 19251](/images/3-Translated-Blogs/3.3-Blog3/1.png)](https://youtu.be/fuisgQIwXg4) 

The following diagram illustrates the solution architecture of Amazon Nova Sonic deployed as a voice agent within the LiveKit framework on AWS.

![](/images/3-Translated-Blogs/3.3-Blog3/2.png) 

### **Prerequisites**

To deploy the solution, you must meet the following prerequisites:

* Python version 3.12 or higher
* An AWS account with appropriate [identity and access management](https://aws.amazon.com/iam/) (IAM) permissions for Amazon Bedrock
* Amazon Nova Sonic on Amazon Bedrock [Access permissions](https://docs.aws.amazon.com/bedrock/latest/userguide/model-access.html#:~:text=To%20request%20access%20to%20a,want%20to%20add%20access%20to.)
* A web browser (such as Google Chrome or Mozilla Firefox) that supports WebRTC

### **Deploy the solution**

Complete the following steps to begin interacting with Amazon Nova Sonic via LiveKit:

1. Install the required dependencies:

```bash
brew install livekit livekit-cli
curl -LsSf https://astral.sh/uv/install.sh | sh
```

uv is a quick, easy alternative to pip, used in the LiveKit Agents SDK (you can also choose to use pip).

2. Set up a new local virtual environment:

```bash
uv init sonic_demo
cd sonic_demo
uv venv --python 3.12
uv add livekit-agents python-dotenv 'livekit-plugins-aws[realtime]'
```

3. To run the LiveKit server locally, open a new terminal (e.g., a new UNIX process) and run the following command:

```bash
livekit-server --dev
```

You must keep the LiveKit server running the entire time the Amazon Nova Sonic agent is running, as it is responsible for authorizing data between parties.

4. Generate an access token using the following code. The default values for api-key and api-secret are devkey and secret, respectively. When generating an access token to grant access to a LiveKit room, you must specify the room name and user identity.

```bash
lk token create \
  --api-key devkey --api-secret secret \
  --join --room my-first-room --identity user1 \
  --valid-for 24h
```

5. Create an environment variable. You must specify AWS credentials:

```bash
vim .env
```

```env
# contents of the .env file
AWS_ACCESS_KEY_ID=<aws access key id>
AWS_SECRET_ACCESS_KEY=<aws secret access key>

# if using a permanent identity (e.g. IAM user)
# then session token is optional
AWS_SESSION_TOKEN=<aws session token>

LIVEKIT_API_KEY=devkey
LIVEKIT_API_SECRET=secret
```

6. Create main.py file:

```python
from dotenv import load_dotenv
from livekit import agents
from livekit.agents import AgentSession, Agent, AutoSubscribe
from livekit.plugins.aws.experimental.realtime import RealtimeModel

load_dotenv()

async def entrypoint(ctx: agents.JobContext):
    # Connect to the LiveKit server
    await ctx.connect(auto_subscribe=AutoSubscribe.AUDIO_ONLY)

    # Initialize the Amazon Nova Sonic agent
    agent = Agent(instructions="You are a helpful voice AI assistant.")
    session = AgentSession(llm=RealtimeModel())

    # Start the session in the specified room
    await session.start(
        room=ctx.room,
        agent=agent,
    )

if __name__ == "__main__":
    agents.cli.run_app(agents.WorkerOptions(entrypoint_fnc=entrypoint))
```

7. Run the main.py file:

```bash
uv run python main.py connect --room my-first-room
```

Now you're ready to connect to the agents' UI.

1. Go to <https://agents-playground.livekit.io/>.

2. Select **Manual**
3. In the first box, enter ws://localhost:7880
4. In the second text field, enter the access token you generated
5. Select **Connect**

You can now communicate with Amazon Nova Sonic in real time.

If you get disconnected from the LiveKit room, you'll need to restart the agent process (main.py) to communicate with Amazon Nova Sonic again.

### **Cleanup**

This example runs locally, meaning there are no special teardown steps required to clean up. You just need to quit the agent process and the LiveKit server. The only cost incurred is the cost of making calls to Amazon Bedrock to communicate with Amazon Nova Sonic. Once disconnected from the LiveKit room, there are no further charges and no AWS resources are used.

### **Conclusion**

Generative AI makes the quality benefits long promised for voice-first applications possible. By combining Amazon Nova Sonic with LiveKit’s Agents framework, developers can build real-time, voice-first AI applications with less complexity and faster deployment. This integration reduces the need for custom audio pipelines, allowing teams to focus on building engaging conversational experiences.

“Our goal with this integration is to simplify the development of voice AI applications,” said Russ d’Sa, CEO and co-founder of LiveKit. “By combining LiveKit’s Agents framework with Nova Sonic’s speech recognition capabilities, we help developers move faster — without managing low-level infrastructure, so they can focus on building their applications.”

To learn more about Amazon Nova Sonic, read the AWS News Blog, the Amazon Nova Sonic product page, and the Amazon Nova Sonic User Guide. To get started using Amazon Nova Sonic on Amazon Bedrock, visit the Amazon Bedrock console.

### **About the authors**

| ![](/images/3-Translated-Blogs/3.3-Blog3/3.png) | [Glen Ko](https://github.com/BumaldaOverTheWater94) is an AI developer at AWS Bedrock, where he focuses on accelerating the proliferation of open source AI tools and supporting open source innovation.                                                                      |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](/images/3-Translated-Blogs/3.3-Blog3/4.png) | [Anuj Jauhari](https://www.linkedin.com/in/anuj-jauhari/) is Head of Product Marketing at Amazon Web Services, where he helps customers realize value from innovations in generative AI.                                                                                      |
| ![](/images/3-Translated-Blogs/3.3-Blog3/5.png) | [Osman Ipek](https://www.linkedin.com/in/uyguripek/) is a Solutions Architect on Amazon's AGI team, focusing on Nova platform models. He guides teams to accelerate development through practical AI deployment strategies, with deep expertise in speech AI, NLP, and MLOps. |