# Vitrual Private Cloud (VPC)
## **1) Giới thiệu** <img src=https://i.imgur.com/KrHEPVD.png width=15% align=right padding-left=8px>
- **VPC** là tên một dịch vụ của **Amazon Web Services (AWS)**. Dịch vụ này cho phép bạn xây dựng một vùng biệt lập về logical, trong đó bạn có thể chạy được các tài nguyên và dịch vụ của **AWS** trong một mạng ảo mà bạn định nghĩa. Bạn có thể toàn quyền kiểm soát môi trường mạng ảo của mạng, bao gồm cả việc chọn dải mảng, tạo subnet, cấu hình gateway,.. Bạn có thể dễ dàng tùy chỉnh cấu hình mạng cho **VPC** của bạn, tạo public subnet để chạy những server cần truy cập internet như WebServer, bạn có thể tạo những private subnet để chạy những server không cần kết nối internet như backend system, database,..
- Về bảo mật bạn có thể cấu hình ở nhiều mức **security group** và **network ACLs** để kiểm soát việc truy cập vào từng máy ảo trong từng subnet.
- Ngoài ra bạn có thể xây dựng kết nối mạng riêng ảo còn gọi là **VPN (Vitual Private Network)** giữa trung tâm dữ liệu của doanh nghiêp với môi trường cloud trên **AWS**, qua đó có thể sử dụng môi trường cloud trên **AWS** như phần mở rộng của trung tâm dữ liệu.

    <p align=center><img src=https://i.imgur.com/hJE9Ydm.png></p>
## **2) Hạ tầng và ứng dụng ( Infrastructure and Applications)**
- **Amazon** và **Oracle** đã kết hợp cùng với nhau cung cấp giải pháp cho khách hàng trong việc chuyển khai và chuyển các ứng dụng lên **Cloud**. Khách hàng không nhũng có thể xây dựng giải pháp sử dụng Database và Middleware của **Oracle** mà họ có thể chạy toàn bộ gói phần mềm cho doanh nghiệp của khách hàng trên **EC2**.
- Khách hàng cũng hoàn toàn có thể triển khai các giải pháp của **SAP** trên **EC2**. **AWS** đảm bảo tính tương thích và hiệu năng của máy ảo **EC2** với giải pháp của **SAP**.
- **AWS** cung cấp dịch vụ về hạ tầng, cho phép bạn triển khai và chạy các ứng dụng trên **Microsoft Window Server** một cách dễ dàng.
## **3) Các thao tác với VPC và các thành phần Network**
### **3.1) Tạo VPC**
- **B1 :** Đăng nhập **AWS Management Console**, chọn **Services** -> **Networking & Content Delivery** -> **VPC** :

    <img src=https://i.imgur.com/JXBzUJt.png>

- **B2 :** Chọn **Your VPCs** :

    <img src=https://i.imgur.com/8H5YlTa.png>

- **B3 :** Chọn ***Create VPC*** :

    <img src=https://i.imgur.com/Heipo2T.png>

- **B4 :** Điền các thông tin cơ bản của **VPC** bao gồm :
    - **Name tag** : tên của **VPC**
    - **IPv4 CIDR block** : dải IPv4 của **VPC**. Cần để dải IP rộng 1 chút vì sau này còn tạo nhiều subnet bên trong nó. **VD :** `10.0.0.0/16`
    - Sau khi điền xong -> ***Create VPC*** 

    <img src=https://i.imgur.com/bzRtiGj.png>

- **B5 :** **VPC** đã được tạo thành công :

    <img src=https://i.imgur.com/leO2bGf.png>

### **3.2) Tạo Internet Gateway**
- **B1 :** Trên **VPC Dashboard** chọn **Internet Gateways** :

    <img src=https://i.imgur.com/Pq2BYhR.png>

- **B2 :** Chọn ***Creat Internet gateway*** :

    <img src=https://i.imgur.com/ddZcDaU.png>

- **B3 :** Điền tên của gateway trong phần **name tag** -> ***Create internet gateway*** :

    <img src=https://i.imgur.com/FyTk28D.png>

- **B4 :** Sau khi **internet gateway** được tạo, chọn ***Action*** -> ***Attach to VPC*** để attach **VPC** :

    <img src=https://i.imgur.com/ZZeOw2J.png>

- **B5 :** Chọn **VPC** muốn attach -> ***Attach internet gateway*** :

    <img src=https://i.imgur.com/Mj5OZjI.png>

- **B6 :** **VPC** đã được attach thành công vào **internet gateway** :

    <img src=https://i.imgur.com/4VhhXSN.png>

### **3.3) Cách tạo Subnet**
- **B1 :** Trên **VPC Dashboard**, chọn **Subnets** :

    <img src=https://i.imgur.com/Q7xOrsx.png>

- **B2 :** Chọn ***Create subnet*** :

    <img src=https://i.imgur.com/8sRvtX7.png>

- **B3 :** Điền các thông tin cơ bản của **subnet** bao gồm :
    - **VPC ID** : chọn **VPC** sẽ chứa **subnet**
    - **Subnet name** : tên của **subnet**
    - **IPv4 CIDR Block** : dải IP của **subnet**. Dải IP này phải nằm gọn trong dải IP của **VPC**.
    - Sau khi điền xong -> ***Create subnet*** 

    <img src=https://i.imgur.com/yiTxSsZ.png>

- **B4 :** **Subnet** được tạo thành công :

    <img src=https://i.imgur.com/WQSWSan.png>

### **3.4) Tạo Default Route**
- **B1 :** Trên **VPC Dashboard**, chọn **Route Tables** :

    <img src=https://i.imgur.com/S6g17V5.png>

- **B2 :** Chọn dòng có chứa thông tin **VPC** muốn tạo route :

    <img src=https://i.imgur.com/XSTASnp.png>

- **B3 :** Chọn ***Edit routes*** :

    <img src=https://i.imgur.com/4LZZc24.png>

- **B4 :** Chọn ***Add route*** :

    <img src=https://i.imgur.com/hW7IxU4.png>

- **B5 :** Điền các thông tin cơ bản của **route** bao gồm :
    - **Destination** : do tạo default route nên để là `0.0.0.0/0`.
    - **Target** : chọn **internet gateway** vừa tạo
    - Sau khi điền xong -> ***Save changes*** 

    <img src=https://i.imgur.com/MsH8Dwx.png>

- **B6 :** Route đã được tạo thành công :

    <img src=https://i.imgur.com/Xpd0dtR.png>

### **3.5) Tạo security group**
- **B1 :** Trên **VPC Dashboard**, chọn **Security Groups** :

    <img src=https://i.imgur.com/lCZkuwO.png>

- **B2 :** Chọn ***Create security group*** :

    <img src=https://i.imgur.com/VQMlyKv.png>

- **B3 :** Điền các thông tin cơ bản của **security group** bao gồm :
    - **Security group name** : tên của **security group**
    - **Description** : mô tả cho **security group**
    - **VPC** : chọn **VPC** sẽ áp dụng **security group**
    - **Inbound rules** : các rule cho traffic đi vào instance
        - **Type** : giao thức. Ở đây ta sẽ chọn **SSH** để cho phép bên ngoài SSH được vào instance.
        - **Source** : IP source được áp dụng. Ở đây ta sẽ chọn **Anywhere-IPv4** - cho phép truy cập instance từ bất cứ đâu
    - **Outbound rules** : các rule cho traffic đi ra khỏi instances. Các option tương tự như **Inbound rules**.
    - Sau khi điền xong -> ***Add rule*** -> ***Create security group*** :

    <img src=https://i.imgur.com/hPrndNX.png>

- **B4 :** **Security group** được tạo thành công :

    <img src=https://i.imgur.com/jQPGMV4.png>