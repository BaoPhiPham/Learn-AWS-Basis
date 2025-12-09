---
title: "Blog 3"
date: 2025-10-04
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# **Xây dựng trải nghiệm AI Đàm thoại thời gian thực bằng Amazon Nova Sonic và LiveKit**

Sự phát triển nhanh chóng của công nghệ AI tạo sinh đã là chất xúc tác cho sự tăng trưởng năng suất kinh doanh, tạo ra những cơ hội mới cho hiệu quả cao hơn, trải nghiệm dịch vụ khách hàng được nâng cao và kết quả khách hàng thành công hơn. Những tiến bộ của AI tạo sinh hiện nay đang giúp các công nghệ hiện có đạt được tiềm năng đã hứa bấy lâu. Ví dụ, các ứng dụng ưu tiên giọng nói đã ngày càng phổ biến trong nhiều ngành công nghiệp trong nhiều năm qua — từ dịch vụ khách hàng đến giáo dục, đến trợ lý và tác nhân giọng nói cá nhân. Nhưng các phiên bản đầu tiên của công nghệ này gặp khó khăn trong việc diễn giải giọng nói của con người hoặc mô phỏng cuộc trò chuyện thực tế.c. Xây dựng AI giọng nói thời gian thực, tự nhiên, với độ trễ thấp vẫn là điều phức tạp, đặc biệt khi làm việc với cơ sở hạ tầng phát trực tuyến (streaming) và các mô hình nền tảng giọng nói (FMs).

Sự tiến bộ nhanh chóng của công nghệ AI hội thoại đã dẫn đến sự phát triển các mô hình mạnh mẽ, giải quyết những thách thức lịch sử của các ứng dụng ưu tiên giọng nói truyền thống. [Amazon Nova Sonic](https://aws.amazon.com/ai/generative-ai/nova/speech/)  là một FM chuyển đổi giọng nói thành giọng nói tiên tiến, được thiết kế để xây dựng các ứng dụng AI đàm thoại thời gian thực trên [Amazon Bedrock](https://aws.amazon.com/bedrock/). Mô hình này cung cấp hiệu suất giá cả hàng đầu ngành và độ trễ thấp. Kiến trúc Amazon Nova Sonic hợp nhất việc hiểu và tạo giọng nói thành một mô hình duy nhất, cho phép các cuộc hội thoại bằng giọng nói thực sự giống con người trong các ứng dụng AI.

Amazon Nova Sonic đáp ứng được sự đa dạng và phong phú của ngôn ngữ con người. Nó có thể hiểu giọng nói theo nhiều phong cách khác nhau và tạo giọng nói với nhiều giọng biểu cảm, bao gồm giọng nam và giọng nữ. Amazon Nova Sonic cũng có thể điều chỉnh nhấn nhá, ngữ điệu và phong cách của câu trả lời giọng nói được tạo để phù hợp với ngữ cảnh và nội dung của câu nói đầu vào. Ngoài ra, Amazon Nova Sonic hỗ trợ gọi hàm và nền tảng tri thức với dữ liệu doanh nghiệp sử dụng Retrieval-Augmented Generation (RAG). Để đơn giản hóa hơn nữa quá trình khai thác tối đa công nghệ này, Amazon Nova Sonic hiện được tích hợp với [LiveKit Agents](https://docs.livekit.io/agents/?utm_source=aws&utm_medium=blog&utm_campaign=nova_sonic_plugin), một nền tảng phổ biến giúp các nhà phát triển xây dựng các ứng dụng giao tiếp thời gian thực bằng âm thanh, video và dữ liệu. Sự tích hợp này cho phép các nhà phát triển xây dựng giao diện giọng nói hội thoại mà không cần quản lý các đường ống âm thanh hoặc giao thức tín hiệu (signaling) phức tạp. Trong bài viết này, chúng tôi giải thích cách hoạt động của sự tích hợp này, cách nó giải quyết các thách thức lịch sử của các ứng dụng ưu tiên giọng nói, và một số bước đầu tiên để bắt đầu sử dụng giải pháp này.

### **Tổng quan về giải pháp**

[LiveKit](https://livekit.io/?utm_source=aws&utm_medium=blog&utm_campaign=nova_sonic_plugin) là một nền tảng mã nguồn mở để xây dựng các ứng dụng AI bằng giọng nói, video và vật lý có thể nhìn, nghe, và nói. Được thiết kế như một giải pháp toàn diện, nó cung cấp SDK cho client trên web, mobile và hệ thống backend, máy chủ WebRTC cho truyền tải mạng độ trễ thấp, và các tính năng tích hợp như phát hiện lượt người dùng, cân bằng tải tác nhân, điện thoại, và tích hợp bên thứ ba. Các nhà phát triển có thể xây dựng các quy trình công việc tác nhân mạnh mẽ cho các ứng dụng thời gian thực mà không phải lo lắng về cơ sở hạ tầng cơ bản, dù là tự lưu trữ, triển khai trên AWS, hay chạy trên dịch vụ đám mây của LiveKit.

Xây dựng các ứng dụng AI ưu tiên giọng nói thời gian thực đòi hỏi quản lý hạ tầng phức tạp - từ ghi âm và phát trực tuyến (streaming) âm thanh đến tín hiệu (signaling), định tuyến (routing) và tối ưu hóa độ trễ - đặc biệt khi sử dụng các mô hình hai chiều như Amazon Nova Sonic. Để đơn giản hóa, chúng tôi tích hợp một [Nova Sonic plugin](https://docs.livekit.io/agents/models/realtime/plugins/nova-sonic/?utm_source=aws&utm_medium=blog&utm_campaign=nova_sonic_plugin) vào mô hình Agents của LiveKit, loại bỏ nhu cầu quản lý các đường ống (pipeline) hoặc lớp truyền tải tùy chỉnh. LiveKit xử lý việc định tuyến âm thanh thời gian thực và quản lý phiên, trong khi Nova Sonic cung cấp khả năng hiểu và tạo giọng nói. Các nhà phát triển được trang bị sẵn các tính năng như âm thanh song công đầy đủ, phát hiện hoạt động giọng nói và khử nhiễu, giúp họ có thể tập trung vào việc thiết kế trải nghiệm người dùng tuyệt vời cho các ứng dụng giọng nói AI của mình.

Video dưới đây minh họa Amazon Nova Sonic và LiveKit đang hoạt động. Bạn có thể tìm mã cho ví dụ này tại [LiveKit Examples GitHub repo](https://github.com/livekit-examples?utm_source=aws&utm_medium=blog&utm_campaign=nova_sonic_plugin).

![ml 19251](/images/3-Translated-Blogs/3.3-Blog3/1.png) 

Sơ đồ sau đây minh họa kiến ​​trúc giải pháp của Amazon Nova Sonic được triển khai dưới dạng tác nhân giọng nói trong khuôn khổ LiveKit trên AWS.

![](/images/3-Translated-Blogs/3.3-Blog3/2.png) 

### **Điều kiện tiên quyết**

Để triển khai giải pháp, ạn phải đáp ứng các điều kiện tiên quyết sau:

* Python phiên bản 3.12 trở lên
* Tài khoản AWS có quyền [quản lý danh tính và truy cập](https://aws.amazon.com/iam/) (IAM) phù hợp cho Amazon Bedrock
* [Quyền truy cập](https://docs.aws.amazon.com/bedrock/latest/userguide/model-access.html#:~:text=To%20request%20access%20to%20a,want%20to%20add%20access%20to.) Amazon Nova Sonic trên Amazon Bedrock
* Trình duyệt web (như Google Chrome hoặc Mozilla Firefox) có hỗ trợ WebRTC

### **Triển khai giải pháp**

Hoàn thành các bước sau để bắt đầu tương tác với Amazon Nova Sonic thông qua LiveKit:

1. Cài đặt các thiết bị phụ thuộc cần thiết:

```bash
brew install livekit livekit-cli
curl -LsSf https://astral.sh/uv/install.sh | sh
```

uv là một giải pháp thay thế nhanh chóng, dễ dàng cho pip, được sử dụng trong LiveKit Agents SDK (bạn cũng có thể chọn sử dụng pip).

2. Thiết lập môi trường ảo cục bộ mới:

```bash
uv init sonic_demo
cd sonic_demo
uv venv --python 3.12
uv add livekit-agents python-dotenv 'livekit-plugins-aws[realtime]'
```

3. Để chạy máy chủ LiveKit cục bộ, hãy mở một terminal mới (ví dụ: một tiến trình UNIX mới) và chạy lệnh sau:

```bash
livekit-server --dev
```

Bạn phải giữ máy chủ LiveKit chạy trong toàn bộ thời gian mà Amazon Nova Sonic agent đang chạy, vì nó chịu trách nhiệm ủy quyền dữ liệu giữa các bên.

4. Tạo mã thông báo truy cập bằng mã sau. Giá trị mặc định cho api-key và api-secret lần lượt là devkey và secret. Khi tạo mã thông báo truy cập để cấp quyền tham gia phòng LiveKit, bạn phải chỉ định tên phòng và danh tính người dùng.

```bash
lk token create \
  --api-key devkey --api-secret secret \
  --join --room my-first-room --identity user1 \
  --valid-for 24h
```

5. Tạo biến môi trường. Bạn phải chỉ định thông tin đăng nhập AWS:

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

6. Tạo tệp main.py:

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

7. Chạy tệp main.py:

```bash
uv run python main.py connect --room my-first-room
```

Bây giờ bạn đã sẵn sàng kết nối với giao diện người dùng của tác nhân (agents).

1. Truy cập <https://agents-playground.livekit.io/>.
2. Chọn **Manual**
3. Trong ô đầu tiên, nhập ws://localhost:7880
4. Trong trường văn bản thứ hai, nhập mã thông báo truy cập bạn đã tạo
5. Chọn **Connect**

Bây giờ bạn có thể giao tiếp với Amazon Nova Sonic theo thời gian thực.

Nếu bạn bị ngắt kết nối khỏi phòng LiveKit, bạn sẽ phải khởi động lại quy trình tác nhân (main.py) để giao tiếp lại với Amazon Nova Sonic.

### **Dọn dẹp**

Ví dụ này chạy cục bộ, nghĩa là không cần các bước gỡ bỏ (teardown) đặc biệt nào để dọn dẹp. Bạn chỉ cần thoát tiến trình tavc nhân (agent) và LiveKit server. Chi phí duy nhất phát sinh là chi phí thực hiện các cuộc gọi đến Amazon Bedrock để giao tiếp với Amazon Nova Sonic. Sau khi ngắt kết nối khỏi phòng LiveKit, bạn sẽ không còn phải trả phí nữa và không còn tài nguyên AWS nào được sử dụng nữa.

### **Kết luận**

Nhờ AI tạo sinh (generative AI), những lợi ích về chất lượng mà các ứng dụng giọng nói ưu tiên đã hứa hẹn từ lâu giờ đây có thể được hiện thực hóa. Bằng cách kết hợp Amazon Nova Sonic với khung Agents của LiveKit, các nhà phát triển có thể xây dựng các ứng dụng AI giọng nói ưu tiên theo thời gian thực với độ phức tạp thấp hơn và triển khai nhanh hơn. Việc tích hợp này giúp giảm nhu cầu về các pipeline âm thanh tùy chỉnh, nhờ đó các nhóm có thể tập trung vào việc xây dựng trải nghiệm đàm thoại hấp dẫn.

"Mục tiêu của chúng tôi với sự tích hợp này là đơn giản hóa việc phát triển các ứng dụng AI giọng nói," Russ d’Sa, CEO và đồng sáng lập LiveKit, cho biết. "Bằng cách kết hợp khung Agents của LiveKit với khả năng nhận diện giọng nói của Nova Sonic, chúng tôi giúp các nhà phát triển di chuyển nhanh hơn — không cần quản lý cơ sở hạ tầng cấp thấp, do đó họ có thể tập trung vào việc xây dựng ứng dụng của mình."

Để tìm hiểu thêm về Amazon Nova Sonic, hãy đọc Blog Tin tức AWS, trang sản phẩm Amazon Nova Sonic và Hướng dẫn sử dụng Amazon Nova Sonic. Để bắt đầu sử dụng Amazon Nova Sonic trên Amazon Bedrock, hãy truy cập bảng điều khiển Amazon Bedrock.

### **About the authors**

| ![](/images/3-Translated-Blogs/3.3-Blog3/3.png) | [Glen Ko](https://github.com/BumaldaOverTheWater94) là nhà phát triển AI tại AWS Bedrock, nơi ông tập trung vào việc thúc đẩy sự phổ biến của các công cụ AI nguồn mở và hỗ trợ đổi mới nguồn mở.                                                                                                               |
| ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](/images/3-Translated-Blogs/3.3-Blog3/4.png) | [Anuj Jauhari](https://www.linkedin.com/in/anuj-jauhari/) là Trưởng phòng Tiếp thị Sản phẩm tại Amazon Web Services, nơi ông giúp khách hàng nhận ra giá trị từ những đổi mới trong AI tạo sinh.                                                                                                                |
| ![](/images/3-Translated-Blogs/3.3-Blog3/5.png) | [Osman Ipek](https://www.linkedin.com/in/uyguripek/) là Kiến trúc sư Giải pháp trong nhóm AGI của Amazon, tập trung vào các mô hình nền tảng Nova. Anh hướng dẫn các nhóm đẩy nhanh quá trình phát triển thông qua các chiến lược triển khai AI thực tế, với chuyên môn sâu rộng về AI giọng nói, NLP và MLOps. |