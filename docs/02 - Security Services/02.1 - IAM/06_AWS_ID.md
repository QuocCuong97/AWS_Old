# ID account AWS
- **AWS** chỉ định hai loại ID duy nhất cho tài khoản của mỗi người dùng:
    - **AWS account ID**
    - **Canonical user ID**
### **ID tài khoản AWS**
- **AWS account ID** là một số gồm `12` chữ số, chẳng hạn như `123456780123` có thể được sử dụng để tạo **Amazon Resource Name (ARN)** . Giả sử chúng ta tham chiếu đến các tài nguyên chẳng hạn như người dùng **IAM**, **AWS account ID** phân biệt tài nguyên với tài nguyên trong các tài khoản **AWS** khác.
- Chúng ta có thể tìm thấy **AWS account ID** từ **AWS Management Console**. Các bước sau được thực hiện để xem **AWS account ID** của bạn:
    - Đăng nhập vào tài khoản **AWS** bằng cách nhập địa chỉ email và mật khẩu của bạn, sau đó bạn sẽ chuyển đến **AWS Management Console**.

        <img src=https://i.imgur.com/kXw266C.png>

    - Nhấp vào account name, một menu dropdown xuất hiện, có thể nhìn nhanh thấy **AWS account ID**. Để xem chi tiết, click vào ***My account*** :

        <img src=https://i.imgur.com/h8S234i.png>

        <img src=https://i.imgur.com/FezgU7D.png>

### **Canonical user ID**
- **Canonical user ID** là hệ thập lục phân `64` chữ số được mã hóa thành số `256 bit`.
- **Canonical user ID** được sử dụng trong **group policy** **Amazon S3** để truy cập nhiều tài khoản khác, có nghĩa là tài khoản AWS này có thể truy cập tài nguyên trong tài khoản AWS khác. Ví dụ: nếu bạn muốn truy cập tài khoản AWS vào group của mình, bạn cần chỉ định ID **Canonical user ID** cho **group policy** của mình.
- Để tìm **canonical user ID**, Nhấp vào account name, một menu dropdown xuất hiện, click vào ***My security credentials*** :

    <img src=https://i.imgur.com/CTvZAmm.png>

- Click vào ***Account identifiers*** để xem **canonical user ID** :
    
    <img src=https://i.imgur.com/5ifiwOL.png>