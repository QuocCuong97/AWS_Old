# Các Service chính trong AWS

<p align=center><img src=https://i.imgur.com/3vciHF7.png width=50%></p>

### **Elastic Compute Cloud (EC2 - IaaS)**
- Là một dịch vụ Web cho phép bạn yêu cầu các máy ảo trong vòng một vài phút và dễ dàng thay đổi khả năng của bạn hoặc tải xuống dựa trên nhu cầu. Bạn chỉ cần phải trả chi phí cho khoảng thời gian mà bạn sử dụng. Nếu bạn muốn tăng khả năng tính toán bạn có thể nhanh chóng khởi tạo máy ảo và chấm dứt khi không sử dụng nữa.
### **Simple Storage Service (S3 - IaaS)**
- Dịch vụ cung cấp các giao diện dịch vụ Web, cho phép lưu trữ và phục hồi dữ liệu.
- Dữ liệu được cho ở bất kì loại nào và có thể lưu trữ và truy cập từ bất kỳ vị trí nào thông qua internet.
- Bạn có thể lưu trữ không giới hạn các đối tượng trong S3 với kích thước các đối tượng trong khoảng 1 byte đến 5Gb.
- Các lưu trữ có thể ở Mỹ hoặc Liên minh Châu Âu, bạn có thể chọn vị trí lưu trữ cho các đối tượng của bạn, khi bạn tạo ra Package, tương tự như khái niệm vủa thư mục trong hệ thống xử lý của bạn.
- Dữ liệu được đảm bảo lưu trữ an toàn bàng cách sử dụng cùng hạ tầng cơ sở lưu trữ Amazon, sử dụng sức mạnh của mình trên toàn thế giới, với một mạng lưới trang Web thương mại điện tử.
### **Elastic Block Storage (EBS - IaaS)**
- Cung cấp thiết bị lưu trữ dạng Block phục vụ cho EC2. Với những thiết bị này trong một số trường hợp có thể định dạng lại dưới dạng file System.
- EBS có thể hỗ trợ một số lượng lưu trữ có thể lên đến 1 Tb. Dung lượng lưu trữ có thể được nhân rộng và tránh việc mất mát theo từng phần. 
### **DynamoDB (SBD - PaaS)**
- Là dịch vụ quản lý độc quyền NoSQL database ra mắt vào năm 2012 hay còn gọi là Not only SQL database.
- Đây là một phần trong danh mục đầu tư của Amazon, được thiết kế để giái quyết các vấn đế vè conflict version. Dịch vụ này sẽ đồng bộ bền vững giữa các trung tâm dữ liệu khác nhau.
### **Simple Queue Service (SQS - SaaS)**
- Cung cấp khả năng truy cập đến hạ tầng kiến trúc thông điệp được đảm bảo bởi Amazon, bạn có thể gửi và nhận các thông điệp từ bất cứ nơi nào bằng cách sử dụng các yêu cầu http đơn giản, không cần cài đặt và cấu hình gì cả.
- Bạn có thể tạo ra số lượng không giới hạn các hàng đợi và gửi một lượng không giới hạn các tin nhắn, nơi mà chũng được lưu trữ bởi Amazon thông qua nhiều máy chủ và các trung tâm dữ liệu dể cung cấp khả năng dư thừa và đáng tin cậy bạn cần từ hệ thống nhắn tin, tin nhắn có thể lưu trữ tối đa 8Kb dưới dạng văn bản.