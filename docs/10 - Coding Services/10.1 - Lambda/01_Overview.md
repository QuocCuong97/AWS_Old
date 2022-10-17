# Tổng quan về Lambda
## **1) Giới thiệu** <img src=https://i.imgur.com/vbOzlJh.png width=20% align=right padding-left=18px>
- **AWS Lambda** (hay **Lambda**) là một dịch vụ điện toán phi máy chủ (***serverless***), dựa trên mô hình **FaaS** (*Function-as-a-service*). Khi sử dụng dịch vụ này, người dùng sẽ không cần quan tâm đến hạ tầng hệ thống bên dưới. **Lambda** sẽ thực thi các đoạn code do người dùng quy định khi được yêu cầu. Điều này giúp người dùng, đặc biệt là các lập trình viên (developer) sẽ có nhiều thời gian hơn để tập trung vào phát triển ứng dụng của mình.
- **AWS** free tới `1 triệu request/tháng` ~ `3.2 triệu giây xử lý` đối với **Lambda**
- Các ngôn ngữ được hỗ trợ :
    - NodeJS
    - Java
    - Python
    - C#
    - Ruby
    - Golang
    - PowerShell
- **Lambda** không phải một global service. Người dùng phải thay đổi region về nơi bạn muốn triển khai **Lambda** function
- **Lambda** chỉ thực hiện code chỉ khi cần thiết, và được mở rộng một cách tự động, từ một vài request đến hàng ngàn request/ giây. Với khả năng đó, có thể sử dụng **Lambda** dễ dàng để build dữ liệu cho các dịch vụ **AWS S3** và **Amazon DynamoDB**, luồng xử lý dữ liệu trong **Amazon Kinesis** hoặc tạo backend riêng mà **AWS** thực hiện có quy mô, năng suất và bảo mật.
- Một số tính năng quan trọng của **Lambda** :
    - **Lambda** dễ dàng scale cơ sở hạ tầng mà không cần bất kỳ cấu hình bổ sung nào. Dịch vụ này giúp các developer giảm công việc vận hành liên quan tới hạ tầng hệ thống.
    - Dịch vụ cung cấp nhiều tùy chọn như dịch vụ **Amazon S3**, **Amazon CloudWatch**, **Amazon DynamoDB**, **Amazon API Gateway**, **Amazon Kinesis**, **Amazon CodeCommit** và nhiều tùy chọn khác để trigger event.
    - Không yêu cầu chi phí trả trước (upfront). Chỉ trả tiền cho bộ nhớ được sử dụng bởi **lambda** function và chi phí tối thiểu cho số lượng request do đó **Lambda** khá tiết kiệm chi phí cho người dùng.
    - **Lambda** sử dụng **AWS IAM** để xác định tất cả các vai trò và chính sách bảo mật do đảm bảo tính bảo mật cho ứng dụng của người dùng.
    - **Lambda** cũng cung cấp khả năng chịu lỗi (fault tolerance) cho các services run code và function. Người dùng sẽ không cần lo về downtime của ứng dụng.
## **2) Một số ứng dụng thực tế của Lambda**
### **2.1) Xử lý tập tin**
- Một ví dụ cơ bản đó là việc xử lý hình ảnh tự động khi người dùng upload ảnh lên **S3** bucket. Trong đó, khi hình ảnh được upload bucket được chỉ định, người dùng sẽ tạo một task tự động trigger **Lambda** để chúng thực việc thay đổi độ phân giải của ảnh và lưu vào 1 bucket khác.

    <img src=https://i.imgur.com/nfv7Gtj.png>

### **2.2) Xử lý streaming data**
- Với những ứng dụng có traffic “khủng”, hệ thống thường sử dụng dịch vụ **Lambda** và **Amazon Kinesis Stream** để xử lý các dữ liệu streaming real-time để ứng dụng theo dõi các hoạt động (application activity tracking), hay các nghiên cứu các dữ liệu real-time khác nhau từ các nguồn data khác nhau như như Website clickstream, Payment transactions, Social media timeline, IT logs hay Location based tracking.

    <img src=https://i.imgur.com/3iT6Zaj.png>

### **2.3) Web Backend**
- **AWS Lambda** cũng có thể đóng vai trò là một backend dùng để xử lý các request từ phía frontend và có khả năng scale linh hoạt tùy theo số lượng request.

    <img src=https://i.imgur.com/LqpKCYT.png>

### **2.4) IoT Backend**
- Tương tự như việc xử lý streaming data, **Lambda** có thể được tích hợp với **Amazon Kinesis** để xử lý các thông tin được gửi từ các thiết bị IoT và thực hiện các công việc cần thiết.

    <img src=https://i.imgur.com/ZJs01Lx.png>

### **2.5) Mobile Backend**
- Người dùng có thể tích hợp **AWS Lambda** với **Amazon API Gateway** để làm backend xử lý các request từ các thiết bị di động một cách dễ dàng

    <img src=https://i.imgur.com/D4iEyAJ.png>

### **2.6) Cron job**
- Thay vì phải cài đặt và thiết lập cron job trên server, người dùng hoàn toàn có thể thực hiện điều này theo dạng serverless. Bạn có thể kết hợp **AWS Lambda** và **Amazon EventBridge** để tạo các cron job trên **AWS**.
## **3) Cách hoạt động của Lambda**
- Các thành phần chính trong **Lambda** :
    - **Lambda Function** : sau khi upload code hoàn chỉnh lên **Lambda**, khi đó gọi nó là function của **Lambda**, và **Lambda function** có quan hệ phụ thuộc với cấu hình cài đặt, nói cách khác, phải cài đặt trước tài nguyên cho function đó, và tất nhiên, cài đặt này có thể chỉnh sửa được.
    - **Event Source** : đưa ra các sự kiện, và một **Lambda function** tùy biến code theo những gì bạn viết và xử lý các sự kiện một cách tự động, mỗi thay đổi của **Event** sẽ kích hoạt **Lambda function** tương ứng của, có thể gọi **Lambda function** điều hướng đến HTPS hoặc sử dụng **AWS SDKs**.

        <p align=center><img src=https://i.imgur.com/wIwacjy.png></p>
- Tính toán tài nguyên cho hệ thống là con số ước lượng đưa ra mà function cần dùng. Chỉ cần tính toán về bộ nhớ, hệ thống sẽ tự tính toán ra CPU cho function.
- **VD :** nếu cấp phát `256MB` cho function của mình, thì CPU nhận được sẽ lớn gấp đôi trong trường hợp chỉ cấp phát `128MB` cho function đó.
- Chú ý :
    - **Lambda function** và **bucket** phải có cùng region. Ví dụ như: **bucket** ở region Tokyo thì **lambda function** cũng phải được config region là **Tokyo**.
    - Mỗi **Lambda function** chỉ chấp nhận một cặp suffix và Event
## **4) Ưu và nhược điểm của AWS Lambda**
- Ưu điểm :
    - Khả năng scale dựa theo số lượng request/invoke
    - Không cần phải quản lý hạ tầng bên dưới vì nó đã được quản lý bởi **AWS**
    - Chỉ phải trả phí dựa trên thời gian **Lambda** xử lý. Người dùng chỉ phải trả phí khi **Lambda** được trigger.
- Nhược điểm :
    - Thời gian xử lý tối đa là `300s` (`5m`)
    - Dung lượng ổ cứng tối đa có thể sử dụng là `512 MB`
    - Dung lượng memory giới hạn trong mức `128-10240 MB`
    - Không xử lý các request có dung lượng “body” lớn hơn `128KB`
    - Log chỉ được ghi vào **CloudWatch** của **AWS**
    - Đối với API, thời gian phản hồi sẽ chậm hơn đôi chút đối với những request đầu tiên vì “cold start” – thời điểm function trigger lần đầu tiên.
## **5) Công cụ phát triển cần thiết**
- **Visual Studio Code**
- Plugin **AWS Toolkit**