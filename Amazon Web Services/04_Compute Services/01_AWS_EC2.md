# Amazon Elastic Compute Cloud : EC2
## **1) Giới thiệu** <img src=https://i.imgur.com/flJD3wU.png width=15% align=right padding-left=8px>
- Amazon Elastic Compute Cloud (EC2) là dịch vụ cung cấp năng lực tính tóan có thể thay đổi theo yêu cầu thực tế, giúp lập trình viên xây dựng các hệ thống chịu tải cao một cách dễ dàng hơn.
- Sử dụng EC2 rất đơn giản, bạn có toàn quyền quản lý tài nguyên tính toán của mình. Thông qua dịch vụ EC2 bạn được sử dụng môi trường tính toán đáng tin cậy của Amazon. Với Amazon EC2, thời gian để có và khởi động một máy chủ giảm xuống chỉ còn vài phút, do đó bạn có thể nhanh chóng tăng hay giảm nguồn lực tính toán khi nhu cầu thực tế thay đổi.
- Amazon EC2 ra đời làm thay đổi mô hình tính tiền dịch vụ cho thuê máy chủ, giờ đây bạn chỉ cần trả tiền cho đúng nguồn lực tính toán đã sử dụng trong thực tế. EC2 cung cấp cho các lập trình viên công cụ để xây dựng hệ thống có khả năng chịu lợi cao tránh được các lỗi thường gặp.
- Một số thuật ngữ bạn sẽ hay gặp khi làm việc với EC2 :
    - Tag : là tập key-value do bạn tự chọn, dùng để dán nhãn cho tài nguyên của Amazon Web Services (AWS) để giúp cho việc quản lý tài nguyên được dễ hơn. Ví dụ bạn gắn tag là DEPARTMENT=FINANCE  cho một máy chủ EC2, để dánh dấu máy chủ này là dùng cho phòng tài chính, phân biệt với các máy chủ khác.
    - Amazon Machine Image (AMI) : là máy ảo của Amazon EC2, được lưu trữ trong dịch vụ lưu trữ Amazon S3. AMI chứa đầy đủ thông tin cần thiết để khởi tạo một máy chủ mới, máy chủ mới được sinh ra từ AMI được gọi là một instance của AMI đấy.
    - Năng lực tính toán (Compute) : Năng lực tính toán của Amazon gần như là vô hạn, được tạo ra từ hàng ngàn máy chủ kết nối với nhau.
- Một số ưu điểm của EC2:
    - Cung cấp 19 loại instance với năng lực xử lý khác nhau để khách hàng lựa chọn.
    - Thời gian để tạo và khởi động instance rất ngắn, chỉ vài phút hoặc vài giây.
    - Khách hàng có thể thay đổi cấu hình theo nhu cầu thực tế.
    - Khách hàng chỉ cần trả tiền cho phần sử dụng thực tế của mình.
    - Khách hàng có thể sử dụng hệ điều hành Linux hoặc Windows.
    - Các máy chủ được triển khai ở nhiều vùng địa lý nên có độ tin cậy cao và giảm thiểu thiệt hại khi có sự cố.
## **2) Các loại Instance và gói dịch vụ của Amazon EC2**
- Amazon EC2 có nhiều loại instance để bạn lựa chọn cho phù hợp với nhu cầu. Mỗi loại instance cung cấp một loại năng lực tính toán ổn định cho khách hàng, tiền được tính theo thời gian sử dụng thực tế.
    - Standard Instance thế hệ đầu tiên có mã M1: là loại instance cân đối giữa năng lực tính toán và giá thành thấp. Nó phù hợp với đa số các loại ứng dụng
    - Standard Instance thế hệ thứ hai có mã M3: là loại instance tiêu chuẩn, có năng lực tính toán cao hơn M1. Nó phù hợp với ưng dụng yêu cầu nhiều Memory và CP như ưng dụng xử lý encoding hoặc hệ thống quản trị nội dung có lượng truy cập lớn.
    - High Memory instance : là instance cung cấp nhiều memory cao, phù hợp với các ứng dụng có throw/push cao như database
    - High CPU instance : là instance cung nhiều CPU, phù hợp với ứng dụng có nhu cầu tính toán cao

        <p align=center><img src=https://i.imgur.com/NBhSAct.png width=40%></p>

- Amazon đưa ra nhiều gói dịch vụ cho bạn lựa chọn để tiết kiệm chi phí tối đa:
    - On demand instances : bạn chỉ cần trả số tiền đúng bằng số giờ thực tế bạn sử dụng, không cần phải trả tiền đặt trước và không cần cam kết sử dụng lâu dài. Là gói bạn sẽ đăng ký máy chủ khi cần thiết và trả lại khi sử dụng xong
    - Reserved instances: là gói bạn cần trả trước một số tiền. Bù lại bạn sẽ được giảm giá đáng kể. Gói này phù hợp với các ứng dụng đang chạy ổn định lượng tải dự đoán được
    - Gói đấu giá ( Spot instances ) : Amazon luôn có các máy chủ nhàn rỗi, khách hàng sẽ đấu giá đẻ được sử dụng những máy chủ này. Mức giá thắng cuộc sẽ được quyết định tự động dựa trên mức giá đưa ra của các khách hàng và số lượng EC2 nhàn rỗi. Nếu mức giá bạn đưa ra lớn hơn mức giá thắng cuộc thì bạn sẽ được sử dụng máy chủ đó, nhưng đến khi mức giá của bạn thấp hơn mức giá thắng cuộc thì bạn sẽ bị thu hồi máy chủ đó.
- Vậy trong trường hợp nào thì nên sử dụng loại instance nào ?  Hãy xem ví dụ sau đây :

    <p align=center><img src=https://i.imgur.com/lZhuOrm.png width=50%></p>

    - Trên hình là đường cong thể hiện nhu cầu tài nguyên tính toán:
        - Dưới mức 3000 là thể hiện ứng dụng chạy ổn định, chúng ta nên dùng gói đặt trước.
        - Với trường hợp nhu cầu thay đổi nhiều thì nên sử dụng gói On Demand hoặc Spot.
## **3) Cách sử dụng Amazon EC2**
- Để sử dụng EC2 bạn chọn một máy ảo do Amazon tạo sẵn gọi là AMI, hoặc tự tạo AMI mới trong đó chứa sẵn ứng dụng, dữ liệu, thư viện và các cấu hình cần thiết. Bạn sử dụng AMI đó để tạo ra server instance nhân bản của máy chủ. Bạn có thể chạy nhiều loại instance từ một AMI, mỗi loại instance cung cấp năng lực xử lý và bộ nhớ khác nhau, lựa chọn loại phù hợp dựa trên nhu cầu thực tế :
    - Instance được tạo ra sẽ chạy liên tục cho đến khi bạn dừng, xóa hoặc bị lỗi. Khi bị lỗi bạn có thể tạo một instance mới từ cùng một AMI
    - Sau khi instance chạy bạn cần cấu hình mạng và an ninh cho nó
    - Chọn loại instance bạn muốn khởi động, xóa và theo dõi chúng số lượng instance không bị giới hạn, Amazon Web Services (AWS) cung cấp web server API và các công cụ để bạn dễ dàng quản lý chúng.
    - Bạn cũng cần quyết định cho chạy instance ở nhiều vùng hay không, có sử dụng IP tĩnh hay không..
    - Bạn chỉ cần phải trả tiền cho đúng lượng sử dụng thực tế.
### **3.1) Amazon Machine Images : AMIs**
- là máy ảo do Amazon tạo sẵn dùng đẻ tạo server trên EC2, các AMI này có thể sử dụng S3 để lưu trữ dữ liệu và các thông tin cần thiết cho nó.
### **3.2) Cách chạy một EC2 instance**

<p align=center><img src=https://i.imgur.com/8RSI6zf.png width=50%></p>

- Trước tiên bạn chọn AMI và chọn Instance, có thể chọn thêm Availability Zone nếu cần, sau đó chọn một số cấu hình như loại mạng EC2 Classic hoặc VPC, loại ổ lưu trữ, số lượng và kích thước ổ, loại ổ này có được sinh ra từ S3 snapshots hay không,...
### **3.3) EC2 Security Groups**
- Cho phép bạn kiểm soát những truy cập inboud đến máy ảo của bạn và outbound từ máy ảo của bạn ra bên ngoài. Nếu bạn chưa có VPC mặc định, bạn cần tạo ra một VPC và chạy các máy ảo của bạn trong VPC đó để sử dụng các tính năng cao cấp về mạng như private subnet, VPN connection,...

    <p align=center><img src=https://i.imgur.com/V9qXBuq.png width=50%></p>
    
## **4) Làm thế nào để lấy thông tin về một máy ảo EC2 từ chính máy ảo đó ?**
- AWS cung cấp tính năng cho phép lấy thông tin về một máy ảo từ chính máy ảo đó bằng Link URL : 
    ```
    http://169.254.169.254/latest/meta-data
    ```
- Thông tin trả về meta data của máy ảo bao gồm :

    <p align=center><img src=https://i.imgur.com/CfTT6wE.png width=50%></p>
