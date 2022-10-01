# Amazon Elastic Compute Cloud : EC2
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
## **2) Các loại Instance và gói dịch vụ của Amazon EC2**
- **Amazon EC2** có nhiều loại **instance** để bạn lựa chọn cho phù hợp với nhu cầu. Mỗi loại **instance** cung cấp một loại năng lực tính toán ổn định cho khách hàng, tiền được tính theo thời gian sử dụng thực tế.
    - **Standard Instance thế hệ đầu tiên có mã M1**: là loại **instance** cân đối giữa năng lực compute và giá thành thấp. Nó phù hợp với đa số các loại ứng dụng.
    - **Standard Instance thế hệ thứ hai có mã M3**: là loại **instance** tiêu chuẩn, có năng lực tính toán cao hơn **M1**. Nó phù hợp với ứng dụng yêu cầu nhiều Memory và CPU như ưng dụng xử lý encoding hoặc hệ thống quản trị nội dung có lượng truy cập lớn.
    - **High Memory instance** : là **instance** cung cấp nhiều memory cao, phù hợp với các ứng dụng có throw/push cao như database.
    - **High CPU instance** : là **instance** cung cấp nhiều CPU, phù hợp với ứng dụng có nhu cầu tính toán cao.

        <p align=center><img src=https://i.imgur.com/NBhSAct.png width=40%></p>

- **Amazon** đưa ra nhiều gói dịch vụ cho bạn lựa chọn để tiết kiệm chi phí tối đa:
    - **On demand instances** : bạn chỉ cần trả số tiền đúng bằng số giờ thực tế bạn sử dụng, không cần phải trả tiền đặt trước và không cần cam kết sử dụng lâu dài. Là gói bạn sẽ đăng ký máy chủ khi cần thiết và trả lại khi sử dụng xong.
    - **Reserved instances** : là gói bạn cần trả trước một số tiền. Bù lại bạn sẽ được giảm giá đáng kể. Gói này phù hợp với các ứng dụng đang chạy ổn định lượng tải dự đoán được
    - **Gói đấu giá ( Spot instances )** : **Amazon** luôn có các máy chủ nhàn rỗi, khách hàng sẽ đấu giá để được sử dụng những máy chủ này. Mức giá thắng cuộc sẽ được quyết định tự động dựa trên mức giá đưa ra của các khách hàng và số lượng **EC2** nhàn rỗi. Nếu mức giá bạn đưa ra lớn hơn mức giá thắng cuộc thì bạn sẽ được sử dụng máy chủ đó, nhưng đến khi mức giá của bạn thấp hơn mức giá thắng cuộc thì bạn sẽ bị thu hồi máy chủ đó.
- Vậy trong trường hợp nào thì nên sử dụng loại **instance** nào ? Hãy xem ví dụ sau đây :

    <p align=center><img src=https://i.imgur.com/lZhuOrm.png width=50%></p>

    - Trên hình là đường cong thể hiện nhu cầu tài nguyên tính toán:
        - Dưới mức `3000` là thể hiện ứng dụng chạy ổn định, chúng ta nên dùng gói **Reserved instances**.
        - Với trường hợp nhu cầu thay đổi nhiều thì nên sử dụng gói **On Demand** hoặc **Spot**.
## **3) Cách sử dụng Amazon EC2**
- Để sử dụng EC2 bạn chọn một máy ảo do Amazon tạo sẵn gọi là AMI, hoặc tự tạo AMI mới trong đó chứa sẵn ứng dụng, dữ liệu, thư viện và các cấu hình cần thiết. Bạn sử dụng AMI đó để tạo ra server instance nhân bản của máy chủ. Bạn có thể chạy nhiều loại instance từ một AMI, mỗi loại instance cung cấp năng lực xử lý và bộ nhớ khác nhau, lựa chọn loại phù hợp dựa trên nhu cầu thực tế :
    - Instance được tạo ra sẽ chạy liên tục cho đến khi bạn dừng, xóa hoặc bị lỗi. Khi bị lỗi bạn có thể tạo một instance mới từ cùng một AMI
    - Sau khi instance chạy bạn cần cấu hình mạng và an ninh cho nó
    - Chọn loại instance bạn muốn khởi động, xóa và theo dõi chúng số lượng instance không bị giới hạn, Amazon Web Services (AWS) cung cấp web server API và các công cụ để bạn dễ dàng quản lý chúng.
    - Bạn cũng cần quyết định cho chạy instance ở nhiều vùng hay không, có sử dụng IP tĩnh hay không..
    - Bạn chỉ cần phải trả tiền cho đúng lượng sử dụng thực tế.
### **3.1) Amazon Machine Images : AMIs**
- Là image do **Amazon** tạo sẵn dùng đẻ tạo server trên **EC2**, các **AMI** này có thể sử dụng **S3** để lưu trữ dữ liệu và các thông tin cần thiết cho nó.
### **3.2) Cách chạy một EC2 instance**

<p align=center><img src=https://i.imgur.com/8RSI6zf.png width=50%></p>

- Trước tiên bạn chọn **AMI** và chọn **Instance**, có thể chọn thêm **Availability Zone** nếu cần, sau đó chọn một số cấu hình như loại mạng **EC2 Classic** hoặc **VPC**, loại ổ lưu trữ, số lượng và kích thước ổ, loại ổ này có được sinh ra từ **S3 snapshots** hay không,...
### **3.3) EC2 Security Groups**
- Cho phép bạn kiểm soát những truy cập inboud đến máy ảo của bạn và outbound từ máy ảo của bạn ra bên ngoài. Nếu bạn chưa có **VPC** mặc định, bạn cần tạo ra một **VPC** và chạy các máy ảo của bạn trong **VPC** đó để sử dụng các tính năng cao cấp về mạng như private subnet, VPN connection,...

    <p align=center><img src=https://i.imgur.com/V9qXBuq.png width=50%></p>
    
## **4) Làm thế nào để lấy thông tin về một máy ảo EC2 từ chính máy ảo đó ?**
- **AWS** cung cấp tính năng cho phép lấy thông tin về một máy ảo từ chính máy ảo đó bằng URL : 
    ```
    http://169.254.169.254/latest/meta-data
    ```
- Thông tin trả về metadata của máy ảo bao gồm :

    <p align=center><img src=https://i.imgur.com/CfTT6wE.png width=50%></p>

## **4) Các thao tác tạo EC2 instance**
- **B1 :** Trên **AWS Management Console**, chọn **Launch a virtual machine** :

    <img src=https://i.imgur.com/K60Al5U.png>

- **B2 :** Tại **Step 1**, chọn **AMI** sẽ sử dụng cho instance :

    <img src=https://i.imgur.com/lVrqShg.png>

- **B3 :** Tại **Step 2**, chọn gói phần cứng cho instance -> ***Next: Configure Instance Details*** :

    <img src=https://i.imgur.com/psv4q3h.png>

- **B4 :** Tại **Step 3**, điền các thông tin cơ bản của instance bao gồm :
    - **Network** : chọn **VPC** muốn gán cho instance
    - **Subnet** : chọn **subnet** muốn gán cho instance
    - **Auto-assign Public IP** : chọn `Enable` để gán IP Public tự động cho instance
    - Sau khi chọn xong -> ***Next: Add Storage*** :

    <img src=https://i.imgur.com/cRWpWoV.png>

- **B5 :** Tại **Step 4**, chọn dung lượng disk và **Volume Type** muốn gán cho instance -> ***Next: Add Tags***:

    <img src=https://i.imgur.com/6L8V6Cw.png>

- **B6 :** Tại **Step 5**, thêm Tags cho instance (hoặc có thể bỏ qua) -> ***Next: Configure Security Group*** :

    <img src=https://i.imgur.com/SHby7sS.png>

- **B7 :** Tại **Step 6**, chọn **security group** muốn áp dụng cho instance -> ***Review and Launch*** :

    <img src=https://i.imgur.com/tLVBLnE.png>

- **B8 :** Tại **Step 7**, review lại toàn bộ cấu hình của instance -> ***Launch*** :

    <img src=https://i.imgur.com/juNWrcm.png>

- **B9 :** Chọn key sẽ sử dụng để access instance. Ở bước này, nếu chưa tạo key trước đó -> ***Create a new key pair*** -> Nhập tên key pair -> ***Download Key Pair*** -> ***Launch Instances*** :

    <img src=https://i.imgur.com/MqOE7i1.png>

- **B10 :** Instance được khởi tạo thành công, chọn ***View instances*** :

    <img src=https://i.imgur.com/EDO7o0L.png>

- **B11 :** Có thể thấy được instance đã được gán **Private IPv4 address** (dải địa chỉ của VPC) và **Public IPv4 address** (địa chỉ này có thể dùng để SSH từ ngoài vào IP)

    <img src=https://i.imgur.com/UGf6bHZ.png>

- **B12 :** Thực hiện SSH vào instan vừa tạo theo cú pháp :
    ```
    ssh <user>@<public-IP> -i <cert.pem>
    ```
    > Mỗi **AMI** thường sẽ có 1 user mặc định để SSH. Đối với **AMI** `Red Hat 8` ở đây sử dụng user `ec2-user`.

    <img src=https://i.imgur.com/hFVB2py.png>

    > Ta có thể thấy instance chỉ nhận 1 card mạng duy nhất có IP của dải **VPC** .
    