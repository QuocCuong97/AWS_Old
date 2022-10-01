# AWS Services
## **1) Tổng quan**
- **Amazon Web Services** cung cấp một tập hợp các dịch vụ như : phân tích, tính toán, lưu trữ, phân tích dữ liệu, ứng dụng và triển khai hệ thống trên cloud, để giúp cho các doanh nghiệp phát triển nhanh hơn, tiết kiệm chi phí vận hành cũng như nâng cao khả năng mở rộng hệ thống.
- Dịch vụ được chính thức đưa ra thị trường vào năm `2006`. Nhanh chóng đạt được mốc `180.000` lập trình viên đăng ký sử dụng vào T6/2017.
- Cùng với sự phát triển của **Cloud Computing**, trong những năm gần đây **AWS** đạt được mức tăng trưởng ấn tượng, và là nhà cung cấp **cloud computing** có doanh thu lớn nhất thể giúp hiện nay ước tính `3,8 tỷ USD` trong năm `2013`.
- Hiện tại **AWS** phục vụ hàng trăm, hàng ngàn khách hàng trên `190` quốc gia ở Bắc Mỹ, Trung Mỹ, Châu Âu, Trung Đông, châu Phi và châu Á Thái Bình Dương,..
## **2) AWS Core Infrastructure & Services**

<p align=center><img src=https://i.imgur.com/q1mCYh2.png width=60%></p>

- Khi nhìn vào tập hợp các services của **AWS**, chúng ta có thể thấy hầu như tất cả những gì cần thiết về mặt cơ sở hạ tầng trong một hệ thống trên data center truyền thống đều có thành phần tương ứng trên **AWS**.
## **3) AWS Platform**
<p align=center><img src=https://i.imgur.com/bQbxO57.png width=60%></p>

- **AWS** cung cấp dịch vụ đến hàng triệu khách hàng ở trên `190` nước trên thế giới, **AWS** vẫn đang mở rộng global infrastructure để cung cấp cho khách hàng khả năng tương tác dữ liệu nhanh hơn, lower latency, higher throughput, và đảm bảo khách hàng có thể lựa chọn đặt dữ liệu tại vùng họ muốn. Ở thời điểm tháng `4` năm `2015`, **AWS** có `11` **region**, hơn `28` **avabilty zone** và hơn `50` **edge location** trên toàn thế giới.
- Các dịch vụ cơ bản - ***Foundation Services*** - là tập hợp các dịch vụ nền tảng và tập trung vào 4 mảng chính : ***Điện toán ( Compute )*** , ***lưu trữ ( storage )*** , ***Networking*** và ***Cơ sở dữ liệu (Database).***
- Các dịch vụ ứng dụng - ***Application Services*** - là các dịch vụ ứng dụng, hệ sinh thái các services của **AWS** phục vụ cho các ứng dụng bao gồm các phần chính : ***truyền tải nội dung (Content Delivery)***, ***Networking***, ***Tìm kiếm ( Searching)***, ***điện toán phân tán (Distributed computing)***, ***Library*** and ***SDK***.
- Triển khai và quản lý - ***Deployment & Management*** - là tập hợp đầy đủ các dịch vụ cho việc triển khai và quản lý ứng dụng bao gồm các phần chính như giao diện web, triển khai và quản trị, định dạng và truy cập, điều khiển .
## **4) Các service chính trong AWS**

<p align=center><img src=https://i.imgur.com/3vciHF7.png width=50%></p>

### **Elastic Compute Cloud (EC2 - IaaS)**
- Là một dịch vụ Web cho phép bạn khởi tạo các máy ảo trong vòng một vài phút và dễ dàng thay đổi cấu hình của chúng dựa trên nhu cầu. Bạn chỉ cần phải trả chi phí cho khoảng thời gian mà bạn sử dụng.
### **Simple Storage Service (S3 - IaaS)**
- Dịch vụ cung cấp các giao diện dịch vụ Web, cho phép lưu trữ và phục hồi dữ liệu.
- Dữ liệu được cho ở bất kì loại nào và có thể lưu trữ và truy cập từ bất kỳ vị trí nào thông qua internet.
- Bạn có thể lưu trữ không giới hạn các **object** trong **S3** với kích thước các **object** trong khoảng `1 byte` đến `5Gb`.
- Các vị trí lưu trữ có thể ở Mỹ hoặc Liên minh Châu Âu, bạn có thể chọn vị trí lưu trữ cho các **object** của bạn, khi bạn tạo ra Package, tương tự như khái niệm của thư mục trong hệ thống xử lý của bạn.
- Dữ liệu được đảm bảo lưu trữ an toàn bàng cách sử dụng cùng hạ tầng cơ sở lưu trữ **Amazon**, sử dụng sức mạnh của mình trên toàn thế giới, với một mạng lưới trang Web thương mại điện tử rộng lớn.
### **Elastic Block Storage (EBS - IaaS)**
- Cung cấp thiết bị lưu trữ dạng **Block** phục vụ cho **EC2**. Với những thiết bị này trong một số trường hợp có thể định dạng lại dưới dạng file System.
- **EBS** có thể hỗ trợ một số lượng lưu trữ có thể lên đến `1 Tb`. Dung lượng lưu trữ có thể được nhân rộng và tránh việc mất mát theo từng phần. 
### **DynamoDB (SBD - PaaS)**
- Là dịch vụ quản lý độc quyền **NoSQL database** ra mắt vào năm 2012 hay còn gọi là ***Not only SQL database***.
- Đây là một phần trong danh mục đầu tư của **Amazon**, được thiết kế để giải quyết các vấn đế vè conflict version. Dịch vụ này sẽ đồng bộ bền vững giữa các trung tâm dữ liệu khác nhau.
### **Simple Queue Service (SQS - SaaS)**
- Cung cấp khả năng truy cập đến hạ tầng kiến trúc **Queue Message** được đảm bảo bởi **Amazon**, bạn có thể gửi và nhận các **message** từ bất cứ nơi nào bằng cách sử dụng các HTTP request đơn giản, không cần cài đặt và cấu hình gì cả.
- Bạn có thể tạo ra số lượng không giới hạn các **queue** và gửi một lượng không giới hạn các **message**, nơi mà chúng được lưu trữ bởi **Amazon** thông qua nhiều máy chủ và các trung tâm dữ liệu dể cung cấp khả năng ***High Availability*** và ***Reliability*** bạn cần từ hệ thống **message**, **message** có thể lưu trữ tối đa `8Kb` dưới dạng văn bản.