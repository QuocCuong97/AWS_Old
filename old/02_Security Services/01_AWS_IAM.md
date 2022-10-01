# AWS Identify and Access Management - IAM
## **1) Giới thiệu** <img src=https://i.imgur.com/HiNpOWx.png width=10% align=right padding-left=8px>
- **IAM - AWS Identify and Access Management** : là một dịch vụ của **AWS** dùng để kiểm soát quyền truy cập vào các dịch vụ của **AWS**.
    > ***Lưu ý :*** **IAM** không dùng để quản lý quyền truy cập vào ứng dụng. 
- Người dùng nên dùng tài khoản **IAM** để quản lý hệ thống chứ không nên dùng tài khoản master.
- Ngoài ra **IAM** cũng cung cấp nhiều tính năng khác kèm theo như:
    - ***Identity Federation*** : là tính năng cho phép dùng tài khoản của công ty khác như Facebook, Google, Microsoft để đăng nhập vào **AWS**.
    - ***Roles*** : role là một cách chia sẻ các quyền trên **AWS**.
    - ***Cross account API access*** : là một tính năng của **AWS** cho phép cấp quyền cho tài khoản khác sử dụng dịch vụ của tài khoản này.
- Một số khái niệm cơ bản trong **IAM**:
    - **User and Group within Accounts** : **AWS** dùng khái niệm người dùng và nhóm người dùng để quản lý tài khoản.
    - **Unique security credentials** : Với mỗi người dùng chìa khóa đăng nhập là duy nhất không thể chia sẻ với người dùng khác.
    - **Policies control access to AWS APIs** : Để quản lý quyền sử dụng dịch vụ và APIs, **AWS** đặt ra một khái niệm gọi là **policy**.
    - **API calls must be signed by either** : Khi muốn sử dụng một dịch vụ hoặc API nào, người dùng phải tạo ra một request được xác thực bằng **secret key**.
    - **Deep integration into some Services** : **IAM** được dùng kết hợp với tất cả các dịch vụ khác của **AWS**
    - AWS Management Console supports User log on: IAM được dùng kết hợp với giao diện chính của AWS, user có thể đăng nhập giao diện chính bằng tài khoản IAM
    - Not for Operating Systems or Applications: Chú ý IAM không dùng cho hệ điều hành hay ứng dụng, chỉ được dùng để cấp quyền cho ứng dụng của AWS.
## **2) Access ID & Secret Key**
- Mỗi người dùng có một **access ID** và **secret key** riêng.
- **Access ID** và **Secret key** này có thể sử dụng để xác thực tất cả loại request, có nhiều cách để tạo các request bằng dòng lệnh, công cụ của bên thứ 3, chương trình,... Ví dụ để xác thực các request sau:
    - Tạo mới, bật, tắt, xóa máy chủ **EC2**
    - Tạo, tháo lắp, tách ổ đĩa.
    - Cài **security group**.
    - Tất cả các việc có thể làm qua **AWS Management Console** đều được xác thực bằng **access ID** và **secret key**.
- Các bước cụ thể trong mô hình **Identify Federation** dùng tài khoản của tổ chức để đăng nhập vào **AWS** :

    <p align=center><img src=https://i.imgur.com/w28ytH1.png width=60%></p>

    - Đầu tiên một `class` được gọi là `Session Proxy`, nó được cung cấp bởi thư viện của **AWS** có trong tất cả các ngôn ngữ .Net, PHP, Java,..
    - Tiếp theo `sesion proxy` được tích hợp với phần mềm của doanh nghiệp.
    - Bước ba, `session proxy` đăng nhập vào phần mềm quản lý tài khoản của doanh nghiệp bằng tài khoản của người dùng. Việc này thực hiện theo chuẩn **Active Directory Federation Serivces** của **Microsoft**.
    - Sau khi đăng nhập người dùng nhận được một key gọi là `SAML token`.
    - Thứ tư, **session proxy** tự động gửi chìa khóa `SAML token` cho **AWS**, nhận về một key thứ hai gọi là `STS token`.
    - Cuối cùng ứng dụng sử dụng `STS token` để xác thực request cho dịch vụ của **AWS**.