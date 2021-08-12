# Vitrual Private Cloud (VPC)
## **1) Giới thiệu** <img src=https://i.imgur.com/KrHEPVD.png width=15% align=right padding-left=8px>
- VPC là tên một dịch vụ của Amazon Web Services (AWS). Dịch vụ này cho phép bạn xây dựng một vùng biệt lập về logical, trong đó bạn có thể chạy được các tài nguyên và dịch vụ của AWS trong một mạng ảo mà bạn định nghĩa. Bạn có thể toàn quyền kiểm soát môi trường mạng ảo của mạng, bao gồm cả việc chọn dải mảng, tạo subnet, cấu hình gateway,.. Bạn có thể dễ dàng tùy chỉnh cấu hình mạng cho VPC của bạn, tạo public subnet để chạy những server cần truy cập internet như WebServer, bạn có thể tạo những private subnet để chạy những server không cần kết nối internet như backend system, database,..
- Về bảo mật bạn có thể cấu hình ở nhiều mức security group và network access control list để kiểm soát việc truy cập vào từng máy ảo trong từng subnet.
- Ngoài ra bạn có thể xây dựng kết nối mạng riêng ảo còn gọi là VPN(Vitual Private Network) giữa trung tâm dữ liệu của doanh nghiêp với môi trường cloud trên AWS, qua đó có thể sử dụng môi trường cloud trên AWS như phần mở rộng của trung tâm dữ liệu.

    <p align=center><img src=https://i.imgur.com/hJE9Ydm.png></p>
## **2) Hạ tầng và ứng dụng ( Infrastructure and Applications)**
- Amazon và Orcale đã kết hợp cùng với nhau cung cấp giải pháp cho khách hàng trong việc chuyển khai và chuyển các ứng dụng lên Cloud. Khách hàng không nhưng có thể xây dựng giải pháp sử dụng Database và MiddileWay của Oracle mà họ có thể chạy toàn bộ gói phần mèm cho doanh nghiệp của khách hàng trên EC2.
- Khách hàng cũng hoàn toàn có thể triển khai các giải pháp của SAP trên EC2. AWS đảm bảo tính tương thích và hiệu năng của máy ảo EC2 với giải pháp của SAP.
- AWS cung cấp dịch vụ về hạ tầng, cho phép bạn triển khai và chạy các ứng dụng trên Microsoft Window Server một cách dễ dàng.
