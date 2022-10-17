# Các thao tác tạo EC2 instance
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