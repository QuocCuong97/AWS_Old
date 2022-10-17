# Tạo một Function trên Lambda
## **1) Tạo một Python Fuction**
- **B1 :** Login vào AWS Management Console và tìm service Lambda :

    <img src=https://i.imgur.com/2Vc4Fgx.png>

- **B2 :** Chọn **Create function** :

    <img src=https://i.imgur.com/9L11fW7.png>

- **B3 :** Tại màn hình Create function, chọn một số thông tin cơ bản để tạo 1 function :
    - **Author from scratch** : tạo 1 ví dụ đơn giản với Lambda qua code template có sẵn :
    - **Function name** : tên function
    - **Runtime** : môi trường chạy code có sẵn (ở đây chọn **Python 3.9**)
    - **Architecture** : kiến trúc hạ tầng run code (ở đây chọn **x86_64**)
    - Chọn ***Create Function*** để tạo sau khi chọn đủ thông tin cho function

    <img src=https://i.imgur.com/DjDzU77.png>
    <img src=https://i.imgur.com/RGcgvGy.png>

- **B4 :** Sau khi hoàn thành tạo function, sẽ thấy 1 đoạn code example ở dưới. Chọn ***Test*** để chạy function :

    <img src=https://i.imgur.com/vZCN1s8.png>
    <img src=https://i.imgur.com/vNY91Wq.png>

- **B5 :** Nhập eventname sẽ tạo ra sau khi trigger function -> ***Save*** :

    <img src=https://i.imgur.com/0x1iJz1.png>

- **B6 :** Kiểm tra kết quả test :

    <img src=https://i.imgur.com/enudKzI.png>

- **B7 :** Có thể view chi tiết log các bước khi chạy function tại **CloudWatch** :

    <img src=https://i.imgur.com/tbqYaju.png>