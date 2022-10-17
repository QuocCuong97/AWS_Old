# Sử dụng Lambda Function với Amazon S3
## **Tình huống**
- Tình huống sau đưa ra sự tương tác cơ bản giữa **Lambda** và **S3** :
    - User upload file lên **S3 bucket**
    - Khi file được upload, nó sẽ triggger một **Lambda function** hiển thị output ở dạng console mesage rằng file đã được upload.
    - User có thể nhìn thấy message trong **Cloudwatch** logs khi file được upload.

        <img src=https://i.imgur.com/wT1Ui1a.png>
## **Step thực hiện**
### **Tạo S3 bucket**
- **B1 :** Trên AWS Management Console, tìm service **S3** :

    <img src=https://i.imgur.com/0DkeLZu.png>

- **B2 :** Chọn **Create Bucket** :

    <img src=https://i.imgur.com/ct5ZOQq.png>

- **B3 :** Điền một số thông tin cơ bản như Bucket name, Region -> ***Create bucket*** để tạo bucket :

    <img src=https://i.imgur.com/qswqfHw.png>

- **B4 :** Chọn bucket `s3workingwithlambda` vừa tạo :

    <img src=https://i.imgur.com/J15cmjg.png>

- **B5 :** Ta thấy bucket đã được tạo thành công và hiện chưa có object :

    <img src=https://i.imgur.com/brTdtkb.png>

### **Tạo IAM Role để làm việc với S3 và Lambda**
- **B6 :** Trên AWS Management Console, tìm service **IAM** :

    <img src=https://i.imgur.com/0DkeLZu.png>

- **B7 :** Chọn **Roles** :

    <img src=https://i.imgur.com/1S8mqjE.png>

- **B8 :** Chọn **Create Role** :

    <img src=https://i.imgur.com/dYr6ZWG.png>

- **B9 :** Chọn service sẽ sử dụng role (ở đây là **Lambda**) -> ***Next*** :

    <img src=https://i.imgur.com/acgVOMr.png>

- **B10 :** Chọn các policy sau : `AWSLambda_FullAccess`, `CloudWatchFullAccess`, `AmazonS3FullAccess` -> ***Next*** :

    <img src=https://i.imgur.com/BItSvMw.png>

- **B11 :** Review lại role, điền tên của role -> ***Create role*** để tạo :

    <img src=https://i.imgur.com/W0m1xiq.png>

- **B12 :** Role được tạo thành công :

    <img src=https://i.imgur.com/kxaw9US.png>

### **Tạo Lambda Function và thêm S3 trigger**
- **B13 :** Trên AWS Management Console, tìm service **Lambda** :

    <img src=https://i.imgur.com/BYDiMUB.png>

- **B14 :** Chọn ***Create Function*** :

    <img src=https://i.imgur.com/GtWQzU5.png>

- **B15 :** Nhập một số thông tin cơ bản của **Lambda function** -> ***Create function*** :
    - Function name : `lambdawiths3bucket`
    - Runtime : `Node.js 16.x`
    - Architecture : `x86_64`
    - Execution role : `s3workingwithlambda_role`

    <img src=https://i.imgur.com/gN3cNBT.png>

- **B16 :** Chọn ***+ Add Trigger*** để thêm trigger cho function :

    <img src=https://i.imgur.com/85CWZeC.png>

- **B17 :** Thêm các cấu hình cho **trigger** -> ***Add*** :
    - Source : `S3`
    - Bucket : `s3/s3workingwithlambda`
    - Event type : `All object create events`

    <img src=https://i.imgur.com/Si1QW2D.png>

- **B18 :** Thay đổi code của function để đưa log vào **Cloudwatch** :
    ```js
    exports.handler = function(event, context, callback) {
        console.log("Incoming Event: ", event);
        const bucket = event.Records[0].s3.bucket.name;
        const filename = decodeURIComponent(event.Records[0].s3.object.key.replace(/\+/g, ' '));
        const message = `File is uploaded in - ${bucket} -> ${filename}`;
        console.log(message);
        callback(null, message);
    };
    ```
    <img src=https://i.imgur.com/IlsyTZU.png>

### **Upload object lên S3 và kiểm tra kết quả**
- **B19 :** Upload file lên bucket `s3workingwithlambda` :

    <img src=https://i.imgur.com/9XlV6cp.png>

- **B20 :** Log đã được đẩy ra **Cloudwatch** :

    <img src=https://i.imgur.com/Obg48Fc.png>