---
title: "Blog 2"
date: 2025-10-04
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# **Lưu trữ trò chơi thế giới liên tục trên Máy chủ Amazon GameLift** 
Bởi Juho Jantunen | Ngày 18 Tháng 6 Năm 2025 | Trong các mục [Amazon DynamoDB](https://aws.amazon.com/blogs/gametech/category/database/amazon-dynamodb/), [Amazon GameLift](https://aws.amazon.com/blogs/gametech/category/game-development/amazon-gamelift/), [Amazon Simple Storage Service (S3)](https://aws.amazon.com/blogs/gametech/category/storage/amazon-simple-storage-services-s3/), [Cơ sở dữ liệu](https://aws.amazon.com/blogs/gametech/category/database/), [Phát triển trò chơi](https://aws.amazon.com/blogs/gametech/category/game-development/), [Trò chơi](https://aws.amazon.com/blogs/gametech/category/industries/games/), [Ngành công nghiệp](https://aws.amazon.com/blogs/gametech/category/industries/) | [Đường dẫn cố định](https://aws.amazon.com/blogs/gametech/host-persistent-world-games-on-amazon-gamelift-servers/)

Các trò chơi nhiều người chơi đã tiến hóa từ các trò chơi chỉ dựa trên phiên chơi (session-based) và các trò chơi trực tuyến nhiều người chơi truyền thống (MMOs) sang các trải nghiệm trực tuyến mới kết hợp các yếu tố liên tục (persistent) và dựa trên phiên chơi. Các trò chơi như Destiny 2 và Rust là những ví dụ điển hình. Trò chơi liên tục có thể là “hubs” hoặc “thế giới nhà” mà người chơi di chuyển và tương tác, sau đó tham gia vào các trải nghiệm dựa trên phiên chơi. Những trò chơi này cho phép người chơi tạo ra các thế giới liên tục mới và đăng nhập, đăng xuất tùy ý. Việc hỗ trợ làn sóng trải nghiệm nhiều người chơi mới này đòi hỏi công nghệ linh hoạt, cả về quản lý phiên chơi và lưu trữ dữ liệu thế giới trò chơi.

[Amazon GameLift Servers](https://aws.amazon.com/gamelift/) là một giải pháp được xây dựng chuyên dụng để lưu trữ các trò chơi nhiều người chơi thuộc nhiều thể loại trên quy mô toàn cầu. Dịch vụ này hỗ trợ nhiều trường hợp sử dụng, từ các trò chơi dựa trên phiên chơi truyền thống đến các loại trò chơi liên tục khác nhau. Việc giới thiệu hỗ trợ container cho Amazon GameLift Servers giúp đơn giản hóa các thách thức khi lưu trữ các trò chơi thế giới liên tục và trò chơi dựa trên phiên. Trò chơi thế giới liên tục có thể chạy các tiến trình container phụ bên cạnh mỗi máy chủ trò chơi để truy cập cơ sở dữ liệu cho dữ liệu liên tục. Bạn cũng có thể tách quản lý trạng thái thế giới thành nhiều tiến trình container có thể giao tiếp qua localhost. Khi cần truy cập các dịch vụ khác của AWS cho trò chơi, vai trò [AWS Identity and Access Management (IAM)](https://aws.amazon.com/iam/) của đội container được gán tự động cho mỗi container, cho phép bạn sử dụng [AWS SDK](https://builder.aws.com/build/tools) và  [AWS Command Line Interface (AWS CLI)](https://aws.amazon.com/cli/).

Trong bài viết này, chúng tôi sẽ hướng dẫn cách kết hợp lối chơi dựa trên phiên và dựa trên liên tục. Bài viết này bao gồm các bước sau:

* Quản lý vòng đời của các thế giới liên tục
* Quản lý phiên chơi của người chơi cho các thế giới liên tục
* Lưu trữ trạng thái của thế giới trò chơi
* Bắt đầu trò chơi dựa trên phiên từ trải nghiệm liên tục

### **Quản lý vòng đời của các thế giới liên tục**

Các thế giới liên tục khuyến khích bạn tạo các thế giới mới khi cần và cho phép người chơi tham gia và rời đi. Việc tạo thế giới có thể được kích hoạt bởi người chơi hoặc được quản lý tập trung bởi hệ thống quản trị của bạn. Bạn cũng cần định tuyến người chơi đến các thế giới này và quản lý các phiên của người chơi.

Bước đầu tiên là tải lên bản dựng máy chủ trò chơi của bạn dưới dạng tệp zip hoặc hình ảnh container, và tạo một đội tàu toàn cầu để lưu trữ trên Máy chủ Amazon GameLift. Khả năng đa vị trí cho phép bạn lưu trữ các thế giới trò chơi gần với người chơi của mình trên toàn cầu. Bộ công cụ [Containers Starter Kit](https://github.com/aws/amazon-gamelift-toolkit/tree/main/containers-starter-kit) là một cách nhanh chóng và dễ dàng để chạy bất kỳ bản dựng máy chủ trò chơi nào trên dịch vụ.

Để tạo các phiên bản thế giới trò chơi trên đội tàu, hãy sử dụng API CreateGameSession với AWS SDK. Khi gọi API, bạn truyền vị trí và bất kỳ siêu dữ liệu cụ thể nào của thế giới trò chơi mà bạn cần để tạo thế giới và nhận thông tin về thế giới phản hồi. Để có luồng dựa trên sự kiện nhiều hơn, bạn cũng có thể sử dụng hàng đợi [Amazon GameLift Servers Queue](https://docs.aws.amazon.com/gameliftservers/latest/developerguide/queues-creating.html), và đặt các phiên trò chơi trên đội thông qua hàng đợi.

Ví dụ yêu cầu CreateGameSession (sử dụng AWS CLI minh họa):

```bash
aws gamelift create-game-session \
  --fleet-id my-fleet-id \
  --location us-west-2 \
  --maximum-player-session-count 200 \
  --game-properties "Key=worldName,Value=MyWorld" "Key=mapToLoad,Value=HomeArena"
```

Phản hồi thành công sẽ như sau:

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

Sau đó, thông tin phiên trò chơi bạn nhận được phản hồi sẽ được lưu trữ trong cơ sở dữ liệu để tham khảo trong tương lai. Một tùy chọn lưu trữ dữ liệu là [Amazon DynamoDB](https://aws.amazon.com/dynamodb/), cho phép bạn lưu trữ dữ liệu khóa-giá trị ở quy mô lớn. Hình dưới đây minh họa một kiến ​​trúc mẫu để lưu trữ thông tin thế giới trò chơi. Việc tạo thế giới trò chơi có thể được kích hoạt bởi yêu cầu của người chơi (ví dụ: tạo một thế giới cố định để chơi cùng bạn bè) hoặc bởi một quy trình phụ trợ (ví dụ: cung cấp các thế giới cố định dựa trên cấu hình do nhà phát triển cung cấp).

![](/images/3-Translated-Blogs/3.2-Blog2/1.png) 

*Hình 1: Tạo phiên trò chơi (người chơi và phần phụ trợ khởi tạo).*

Khi thế giới trò chơi trở nên nhàn rỗi hoặc đạt đến thời gian tồn tại cố định, phiên trò chơi cơ bản thường bị chính quy trình máy chủ trò chơi chấm dứt. Máy chủ Amazon GameLift cho phép bạn lưu trữ quy trình máy chủ trò chơi trong thời gian bạn cần. Sau khi máy chủ trò chơi đã lưu trữ trạng thái và sẵn sàng chấm dứt, nó sẽ gọi phương thức ProcessEnding() của Amazon GameLift Server SDK để tự động xóa phiên trò chơi. Hạm đội ngay lập tức tạo một quy trình mới sẵn sàng để lưu trữ một thế giới khác. Bạn cũng có thể kích hoạt việc chấm dứt phiên trò chơi bên ngoài bằng API TerminateGameSession từ backend của trò chơi. Khi sử dụng tùy chọn chấm dứt nhẹ nhàng của API này, máy chủ trò chơi sẽ nhận được một lệnh gọi lại và có thể quản lý việc chấm dứt nhẹ nhàng.

### **Quản lý phiên chơi của người chơi cho các thế giới liên tục**

Người chơi thường có thể rời khỏi và tham gia các thế giới cố định theo thời gian. Bạn có thể chọn quản lý phiên người chơi trong phần phụ trợ của mình hoặc sử dụng các tính năng phiên người chơi của Máy chủ Amazon GameLift. Phiên người chơi được tạo bằng API CreatePlayerSession.

Sau đây là ví dụ về cách yêu cầu phiên người chơi với AWS CLI:

```bash
aws gamelift create-player-session \
  --game-session-id arn:aws:gamelift:us-west-2::gamesession/id \
  --player-id 12345
```

Sau khi phản hồi thành công, bạn sẽ nhận được thông tin kết nối có thể truyền lại cho máy khách trò chơi:

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

Sau đó, máy khách trò chơi có thể kết nối trực tiếp với phiên bằng IP/DnsName và Port. Thuộc tính PlayerSessionId có thể được sử dụng để xác thực danh tính người chơi trên máy chủ trò chơi và kích hoạt phiên người chơi. Hình bên dưới minh họa cách người chơi yêu cầu tham gia một thế giới cụ thể, với thông tin thế giới được truy vấn từ DynamoDB và phiên người chơi được tạo cho thế giới đó để cung cấp thông tin kết nối.

![](/images/3-Translated-Blogs/3.2-Blog2/2.png) 

*Hình 2: Tham gia vào thế giới trò chơi.*

Để theo dõi số lượng phiên người chơi hiện tại trong một thế giới, chẳng hạn như thông tin cập nhật về những người chơi đã rời đi, chúng tôi khuyên bạn nên cập nhật tập trung dữ liệu phiên trò chơi trong cơ sở dữ liệu của mình. Bạn có thể chạy một quy trình phụ trợ để liên tục cập nhật dữ liệu. API DescribeGameSessions có thể được sử dụng để lặp lại tất cả các phiên trò chơi. Nó truy xuất tối đa 100 phiên trò chơi cho mỗi yêu cầu, và bạn có thể lặp lại tất cả các phiên bằng cách sử dụng NextToken nhận được trong các phản hồi. Hình sau đây minh họa một ví dụ về cách triển khai này.

![](/images/3-Translated-Blogs/3.2-Blog2/3.png) 

*Hình 3: Cập nhật trạng thái hiện tại của thế giới trò chơi vào cơ sở dữ liệu của bạn.*

### **Duy trì trạng thái của thế giới trò chơi**

Thông thường, khi phiên đang chạy, trạng thái của thế giới trò chơi được lưu trữ trong bộ nhớ. Tuy nhiên, chúng tôi khuyên bạn nên định kỳ lưu trữ trạng thái thế giới vào kho dữ liệu ngoài vì nhiều lý do. Một lý do là để dọn dẹp các thế giới nhàn rỗi sau khi duy trì trạng thái của chúng, cho phép bạn khôi phục trạng thái khi người chơi tham gia lại. Nếu bạn lưu trữ các thế giới trò chơi có thời gian tồn tại nhiều tuần hoặc thậm chí nhiều tháng, thì bạn muốn có thể khôi phục trạng thái thế giới trong trường hợp tiến trình máy chủ trò chơi gặp sự cố hoặc khi thực hiện luân chuyển thế giới định kỳ để tránh sự cố rò rỉ bộ nhớ.

Sau đây là một số tùy chọn để lưu trữ trạng thái thế giới từ nhóm máy chủ trò chơi của bạn:

* Lưu trực tiếp tệp lưu thế giới (world save file) lên [Amazon S3](https://aws.amazon.com/s3/)
* Chạy cơ sở dữ liệu cục bộ trên đĩa và đồng bộ bản sao/dump của cơ sở dữ liệu lên Amazon S3
* Lưu dữ liệu thế giới dưới dạng dữ liệu khóa-giá trị (key-value) trong DynamoDB
* Triển khai một lớp API bảo mật để nhận dữ liệu thế giới và lưu vào cơ sở dữ liệu mà bạn lựa chọn

Trong các phần tiếp theo, chúng tôi sẽ đi chi tiết cho từng tùy chọn này.

#### **Lưu trực tiếp tệp lưu thế giới lên Amazon S3**

Máy chủ Amazon GameLift hỗ trợ việc gắn vai trò IAM vào các phiên bản hoặc vùng chứa [Amazon Elastic Compute Cloud (Amazon EC2](https://aws.amazon.com/ec2/)) trong nhóm của bạn. Bạn có thể gắn quyền cho vai trò này để truy cập các tài nguyên như Amazon S3. Việc truy cập các tài nguyên này có thể được thực hiện thông qua AWS SDK trực tiếp trên quy trình máy chủ trò chơi hoặc chạy một quy trình hoặc vùng chứa phụ trợ quản lý quyền truy cập.

Khi lưu trữ tệp lưu thế giới trực tiếp lên Amazon S3, bạn sẽ tạo tệp lưu trên máy chủ trò chơi và tải lên Amazon S3. Nếu bạn cần khôi phục trạng thái thế giới trên một quy trình máy chủ trò chơi khác sau này, bạn sẽ phải tải dữ liệu thế giới khi khởi chạy.

#### **Chạy cơ sở dữ liệu cục bộ trên đĩa và và đồng bộ hóa bản sao lưu cơ sở dữ liệu với Amazon S3**

Một cách tiếp cận khác là lưu trữ cơ sở dữ liệu cục bộ, thường là giải pháp cơ sở dữ liệu dựa trên SQL mà máy chủ trò chơi liên tục ghi các bản cập nhật thế giới. Sau đó, bạn có một tiến trình sidecar hoặc một container tạo các bản sao lưu cơ sở dữ liệu và tải lên Amazon S3 theo khoảng thời gian bạn chọn.

#### **Lưu dữ liệu thế giới dưới dạng ữ liệu khóa-giá trị (key-value) trong DynamoDB**

Một lựa chọn được đề xuất là lưu trữ trạng thái thế giới trực tiếp vào cơ sở dữ liệu, một lần nữa bằng cách sử dụng AWS SDK trên máy chủ trò chơi của bạn hoặc sử dụng một tiến trình sidecar hoặc container mà máy chủ trò chơi giao tiếp. Amazon DynamoDB là một lựa chọn tuyệt vời với khả năng mở rộng cao cho việc này.

Lợi ích của phương pháp này là bạn có một cơ sở dữ liệu khóa-giá trị có khả năng mở rộng cao được quản lý hoàn toàn và tất cả các thay đổi trạng thái thế giới đều được ghi lại gần như theo thời gian thực. Phương pháp này cũng cung cấp khả năng khôi phục trạng thái thế giới liền mạch. Nếu thiết kế trò chơi của bạn yêu cầu mọi hành động của người chơi phải được lưu trữ ngay lập tức, thì phương pháp này hoạt động tốt. Amazon Games New World là một ví dụ về một trò chơi sử dụng phương pháp này, xử lý khoảng 800.000 lần ghi mỗi 30 giây để lưu trữ trạng thái trò chơi. DynamoDB có giới hạn kích thước mục là 400 kB, vì vậy bạn thường cần chia dữ liệu thế giới thành nhiều mục.

#### **Sử dụng tiến trình phụ (sidecar) cho lưu trữ và cơ sở dữ liệu**

Máy chủ trò chơi thường là phiên bản không có giao diện (headless) của các bản dựng Unreal, Unity hoặc các công cụ trò chơi khác. Việc truy cập cơ sở dữ liệu hoặc dịch vụ lưu trữ trực tiếp từ máy chủ trò chơi là khả thi, nhưng việc phân chia trách nhiệm này cho một quy trình sidecar hoặc container mang lại một số lợi ích::

* Sử dụng AWS SDK trong ngôn ngữ phổ biến cho backend như Python hoặc Go.
* Không cần thêm phụ thuộc vào dự án máy chủ trò chơi của bạn.
* Phát triển và duy trì tích hợp cơ sở dữ liệu và lưu trữ độc lập với máy chủ trò chơi của bạn.
* Giảm tải các hoạt động I/O nặng từ tiến trình máy chủ trò chơi của bạn.

Đội container của Amazon GameLift Servers cho phép bạn định nghĩa container phụ mà máy chủ trò chơi có thể truy cập, ví dụ qua endpoint HTTPS trên localhost, như hình dưới đây:

*![](/images/3-Translated-Blogs/3.2-Blog2/4.png) *

*Hình 4: Sử dụng quy trình sidecar để lưu trữ dữ liệu thế giới.*

### **Bắt đầu chơi dựa trên phiên từ trải nghiệm liên tục**

Khi trải nghiệm liên tục được triển khai, chúng tôi có thể xem xét các yếu tố dựa trên phiên của trò chơi. Điều này có thể là việc người chơi tập hợp trong trung tâm của bạn và bắt đầu cuộc phiêu lưu PvE theo phiên, hoặc trải nghiệm PvP dựa trên ghép trận, tùy theo thiết kế trò chơi.

Dù trường hợp nào đi nữa, việc lưu trữ trò chơi theo phiên là tính năng gốc của Máy chủ Amazon GameLift. Trước tiên, bạn tải lên bản dựng máy chủ trò chơi của mình và thiết lập vị trí nào trên thế giới mà bạn muốn lưu trữ trò chơi. Sau đó, bạn có hai lựa chọn tùy thuộc vào trải nghiệm: trực tiếp tạo phiên cho một nhóm người chơi hoặc sử dụng tính năng ghép trận.

#### **Tạo phiên cho một nhóm người chơi**

Khi bạn đã biết nhóm người chơi mà bạn sẽ bắt đầu phiên cho họ (có thể họ được nhóm trong thế giới trung tâm của bạn), bạn có thể sử dụng Hàng đợi Máy chủ Amazon GameLift để yêu cầu sắp xếp phiên cho họ. Bạn có thể chuyển độ trễ của từng người chơi cho tất cả các vị trí bạn hỗ trợ hoặc cung cấp danh sách ưu tiên các vị trí để tổ chức phiên. Bạn cũng có thể xác định các thuộc tính của phiên trong yêu cầu sắp xếp. Quy trình máy chủ trò chơi sẽ nhận thông tin này và có thể sử dụng nó để tải bản đồ chính xác chẳng hạn.

Sau đây là ví dụ về yêu cầu sắp xếp phiên cho nhiều người chơi sử dụng AWS CLI:

```bash
aws gamelift start-game-session-placement \
  --game-session-queue-name my-game-session-queue \
  --placement-id "unique-id-1234" \
  --maximum-player-session-count 200 \
  --game-properties "Key=mapName,Value=DungeonRaid" "Key=difficulty,Value=hard" \
  --player-latencies "PlayerId=player1,RegionIdentifier=us-east-1,LatencyInMilliseconds=20" "PlayerId=player2,RegionIdentifier=us-east-1,LatencyInMilliseconds=30" \
  --desired-player-sessions "PlayerId=player1" "PlayerId=player2"
```

Hàng đợi (Queue) phát các sự kiện sắp xếp ([placement events](https://docs.aws.amazon.com/gamelift/latest/developerguide/queue-events.html)) mà phần mềm trò chơi của bạn có thể xử lý để truyền thông tin phiên cho người chơi.

#### **Sử dụng tính năng ghép cặp để nhóm người chơi**

Một lựa chọn khác là người chơi chọn trải nghiệm dựa trên phiên mà họ muốn tham gia, và hệ thống quản lý trò chơi sẽ tạo phiếu ghép cặp cho mỗi người chơi để tìm ra nhóm người chơi tối ưu. Tính năng ghép cặp tích hợp này sử dụng [Amazon GameLift Servers FlexMatch](https://docs.aws.amazon.com/gameliftservers/latest/flexmatchguide/match-intro.html), có thể có các quy tắc ghép cặp dựa trên độ trễ, đội, cũng như trình độ kỹ năng và các thuộc tính khác của người chơi. Nếu người chơi của bạn đã tạo nhóm trong trải nghiệm liên tục, họ có thể được ghép cặp với nhau để đảm bảo họ tham gia cùng một đội trong một phiên chung.

Sau đây là ví dụ về lệnh gọi API để bắt đầu một phiếu ghép cặp:

```bash
aws gamelift start-matchmaking \
  --configuration-name "MyMatchmakingConfig" \
  --players 'PlayerId=player123,LatencyInMs={us-west-2=45,us-east-1=120},PlayerAttributes={skill={N=29}}'
```

Đối với một nhóm người chơi được thành lập trước, bạn sẽ chuyển tất cả người chơi trong một cuộc gọi duy nhất để đảm bảo rằng họ tham gia cùng một đội trong một phiên chung:

```bash
aws gamelift start-matchmaking \
  --configuration-name "MyMatchmakingConfig" \
  --players 'PlayerId=player1,LatencyInMs={us-west-2=45,us-east-1=120},PlayerAttributes={skill={N=29}}' \
           'PlayerId=player2,LatencyInMs={us-west-2=50,us-east-1=125},PlayerAttributes={skill={N=39}}'
```

### **Kết luận**

Trong bài viết này, chúng tôi đã đề cập đến cách sử dụng Máy chủ Amazon GameLift để lưu trữ trò chơi thế giới liên tục trên toàn cầu. Chúng tôi cũng đã đề cập đến cách bạn có thể quản lý các phiên người chơi cho các thế giới liên tục. Hơn nữa, chúng tôi đã thảo luận về các phương pháp khác nhau để duy trì trạng thái thế giới và đi sâu hơn vào cách bạn có thể kết hợp trò chơi dựa trên phiên với trải nghiệm liên tục.

Các trò chơi nhiều người chơi hiện đại sử dụng nhiều chiến lược để quản lý cách người chơi được nhóm lại và cách họ được ánh xạ vào các phiên bản khác nhau của thế giới trò chơi và trò chơi dựa trên phiên. Máy chủ Amazon GameLift cung cấp các khả năng và API cho phép bạn xây dựng trải nghiệm độc đáo phù hợp với thiết kế trò chơi của mình. Hơn nữa, sức mạnh của sự đa dạng các dịch vụ trên AWS cho phép bạn mở rộng hiệu quả sang các phương pháp khác nhau để quản lý chức năng phụ trợ và duy trì trạng thái thế giới.

Hãy bắt đầu ngay hôm nay với Máy chủ Amazon GameLift để lưu trữ máy chủ trò chơi nhiều người chơi. [Liên hệ với đại diện AWS](https://pages.awscloud.com/Amazon-Game-Tech-Contact-Us.html) để tìm hiểu cách chúng tôi có thể giúp thúc đẩy doanh nghiệp của bạn.

### **Tham khảo thêm**

* [Lưu trữ trò chơi thế giới liên tục trên AWS.](https://aws.amazon.com/solutions/guidance/persistent-world-game-hosting-on-aws/?did=sl_card&trk=sl_card)
* [Lưu trữ nhiều người chơi nhanh hơn với các container trên Máy chủ Amazon GameLift.](https://aws.amazon.com/blogs/gametech/faster-multiplayer-hosting-with-containers-on-amazon-gamelift-servers/)
* [Amazon GameLift đạt 100 triệu người dùng kết nối đồng thời cho mỗi trò chơi.](https://aws.amazon.com/blogs/gametech/amazon-gamelift-achieves-100-million-concurrently-connected-users-per-game/)

|                                                 |                                                                                                                                                                                                                                                                                                                                           |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](/images/3-Translated-Blogs/3.2-Blog2/5.png) | **Juho Jantunen** Juho Jantunen là Kiến trúc sư Giải pháp Chính Toàn cầu của nhóm AWS for Games, chuyên về các giải pháp lưu trữ máy chủ và backend cho game. Anh có kinh nghiệm trong ngành công nghiệp game và công nghệ đám mây, đồng thời đã xây dựng và vận hành backend game trên AWS cho nhiều tựa game với hàng triệu người chơi. |