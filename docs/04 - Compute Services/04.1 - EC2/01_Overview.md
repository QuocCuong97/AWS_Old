# Amazon Elastic Compute Cloud (EC2)
## **1) Giới thiệu** <img src=https://i.imgur.com/flJD3wU.png width=15% align=right padding-left=8px>
- **Amazon Elastic Compute Cloud (EC2)** là dịch vụ cung cấp compute có thể thay đổi theo yêu cầu thực tế, giúp lập trình viên xây dựng các hệ thống chịu tải cao một cách dễ dàng hơn.
- Sử dụng **EC2** rất đơn giản, bạn có toàn quyền quản lý tài nguyên compute của mình. Thông qua dịch vụ **EC2** bạn được sử dụng môi trường compute đáng tin cậy của **Amazon**. Với **Amazon EC2**, thời gian để có và khởi động một máy chủ giảm xuống chỉ còn vài phút.
- **Amazon EC2** ra đời làm thay đổi mô hình tính tiền dịch vụ cho thuê máy chủ, giờ đây bạn chỉ cần trả tiền cho đúng lượng compute đã sử dụng trong thực tế.
- Một số thuật ngữ bạn sẽ hay gặp khi làm việc với **EC2** :
    - `Tag` : là tập `key-value` do bạn tự chọn, dùng để dán nhãn cho tài nguyên của **Amazon Web Services (AWS)** để giúp cho việc quản lý tài nguyên được dễ hơn. Ví dụ bạn gắn tag là `DEPARTMENT=FINANCE` cho một máy chủ **EC2**, để dánh dấu máy chủ này là dùng cho phòng tài chính, phân biệt với các máy chủ khác.
    - `Amazon Machine Image (AMI)` : là image của **Amazon EC2**, được lưu trữ trong dịch vụ lưu trữ **Amazon S3**. **AMI** chứa đầy đủ thông tin cần thiết để khởi tạo một máy chủ mới, máy chủ mới được sinh ra từ **AMI** được gọi là một **instance** của **AMI** đấy.
    - `Compute` : khả năng tạo compute của **Amazon** gần như là vô hạn, được tạo ra từ hàng ngàn máy chủ kết nối với nhau.
- Một số ưu điểm của **EC2**:
    - Cung cấp 19 loại **instance** với năng lực xử lý khác nhau để khách hàng lựa chọn.
    - Thời gian để tạo và khởi động **instance** rất ngắn, chỉ vài phút hoặc vài giây.
    - Khách hàng có thể thay đổi cấu hình theo nhu cầu thực tế.
    - Khách hàng chỉ cần trả tiền cho phần sử dụng thực tế của mình.
    - Khách hàng có thể sử dụng hệ điều hành Linux hoặc Windows.
    - Các máy chủ được triển khai ở nhiều vùng địa lý nên có độ tin cậy cao và giảm thiểu thiệt hại khi có sự cố.
## **2) Cách sử dụng Amazon EC2**
- Để sử dụng EC2 bạn chọn một máy ảo do Amazon tạo sẵn gọi là AMI, hoặc tự tạo AMI mới trong đó chứa sẵn ứng dụng, dữ liệu, thư viện và các cấu hình cần thiết. Bạn sử dụng AMI đó để tạo ra server instance nhân bản của máy chủ. Bạn có thể chạy nhiều loại instance từ một AMI, mỗi loại instance cung cấp năng lực xử lý và bộ nhớ khác nhau, lựa chọn loại phù hợp dựa trên nhu cầu thực tế :
    - Instance được tạo ra sẽ chạy liên tục cho đến khi bạn dừng, xóa hoặc bị lỗi. Khi bị lỗi bạn có thể tạo một instance mới từ cùng một AMI
    - Sau khi instance chạy bạn cần cấu hình mạng và an ninh cho nó
    - Chọn loại instance bạn muốn khởi động, xóa và theo dõi chúng số lượng instance không bị giới hạn, Amazon Web Services (AWS) cung cấp web server API và các công cụ để bạn dễ dàng quản lý chúng.
    - Bạn cũng cần quyết định cho chạy instance ở nhiều vùng hay không, có sử dụng IP tĩnh hay không..
    - Bạn chỉ cần phải trả tiền cho đúng lượng sử dụng thực tế.
### **2.1) Amazon Machine Images : AMIs**
- Là image do **Amazon** tạo sẵn dùng đẻ tạo server trên **EC2**, các **AMI** này có thể sử dụng **S3** để lưu trữ dữ liệu và các thông tin cần thiết cho nó.
### **2.2) Cách chạy một EC2 instance**

<p align=center><img src=https://i.imgur.com/8RSI6zf.png width=50%></p>

- Trước tiên bạn chọn **AMI** và chọn **Instance**, có thể chọn thêm **Availability Zone** nếu cần, sau đó chọn một số cấu hình như loại mạng **EC2 Classic** hoặc **VPC**, loại ổ lưu trữ, số lượng và kích thước ổ, loại ổ này có được sinh ra từ **S3 snapshots** hay không,...
### **2.3) EC2 Security Groups**
- Cho phép bạn kiểm soát những truy cập inboud đến máy ảo của bạn và outbound từ máy ảo của bạn ra bên ngoài. Nếu bạn chưa có **VPC** mặc định, bạn cần tạo ra một **VPC** và chạy các máy ảo của bạn trong **VPC** đó để sử dụng các tính năng cao cấp về mạng như private subnet, VPN connection,...

    <p align=center><img src=https://i.imgur.com/V9qXBuq.png width=50%></p>
    
## **3) Làm thế nào để lấy thông tin về một máy ảo EC2 từ chính máy ảo đó ?**
- **AWS** cung cấp tính năng cho phép lấy thông tin về một máy ảo từ chính máy ảo đó bằng URL : 
    ```
    http://169.254.169.254/latest/meta-data
    ```
- Thông tin trả về metadata của máy ảo bao gồm :

    <p align=center><img src=https://i.imgur.com/CfTT6wE.png width=50%></p>


    