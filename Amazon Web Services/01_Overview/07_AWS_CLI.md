# Cài đặt AWS CLI
## **1) Giới thiệu**
- **AWS CLI** là một chương trình lệnh sử dụng cho các quản trị viên tương tác với dịch vụ AWS từ máy chủ bất kì. **AWS CLI** hỗ trợ cài đặt trên Windows, Linux và MacOS.
## **2) Cài đặt AWS CLI**
### **2.1) Cài đặt trên Ubuntu 20.04**
- **B1 :** Cài đặt **Python** :
    ```
    $ sudo apt-get install python3 -y
    ```
- **B2 :** Cài đặt `pip` :
    ```
    $ curl -O https://bootstrap.pypa.io/get-pip.py
    $ python3 get-pip.py
    $ pip3 install --upgrade pip
    ```
- **B3 :** Cài đặt **AWS CLI** :
    ```
    $ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    $ unzip awscliv2.zip
    $ sudo ./aws/install
    ```
- **B4 :** Kiểm tra lại version của **AWS CLI** :
    ```
    $ aws --version
    ```
    <img src=https://i.imgur.com/A8kaMrk.png>
## **3) Cấu hình AWS CLI**
- Trước khi bắt đầu sử dụng công cụ **AWS CLI** để tương tác và quản trị với hệ thống dịch vụ **AWS**, cần cấu hình các thông tin bao gồm sau để chứng thực người dùng được quyền tương tác với tài khoản **AWS** :
    - AWS Access Key ID
    - AWS Secret Access Key
    - Default region name
    - Default output format
### **3.1) Lấy thông tin AWS Access Key & Secret Access Key**
- **B1 :** Truy cập https://console.aws.amazon.com/iam/home#/security_credentials, chọn ***Create New Access Key*** :

    <img src=https://i.imgur.com/QDdKQo7.png>

- **B2 :** Key được tạo thành công, chọn ***Download Key File*** :

    <img src=https://i.imgur.com/kfzrQlW.png>

- **B3 :** File `rootkey.csv` sẽ được download, trong đó chứa `AWSAccessKeyId` và `AWSSecretKey` :

    <img src=https://i.imgur.com/j5jFhwh.png>
### **3.2) Cấu hình AWS CLI**
> ***Cách 1 :*** Sử dụng lệnh `aws configure` :
- Cú pháp :
    ```
    $ aws configure
    ```
    - Nhập các thông tin :
        - `AWS Access Key ID [None]`: AWS Access Key
        - `AWS Secret Access Key [None]`: Secret Access Key
        - `Default region name [None]`: region mặc định để tương tác trên AWS
        - `Default output format [None]`: định dạng output trả về (`json` - default, `text`, `yaml`, `table`)

    <img src=https://i.imgur.com/DDTcOxy.png>

- Sau khi cấu hình, sẽ thấy có 2 file config lưu trữ thông tin bạn đã input ở thư mục `$HOME` :
    ```
    $ cat ~/.aws/config
    ```
    <img src=https://i.imgur.com/OVo3Scs.png>

    ```
    $ cat ~/.aws/credentials
    ```
    <img src=https://i.imgur.com/QAReAeN.png>

> ***Cách 2 :*** Export biến môi trường :
- Cú pháp :
    ```
    # export AWS_ACCESS_KEY_ID="AKIA3WTETKMPAQUG7GWE"
    # export AWS_SECRET_ACCESS_KEY="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"
    # export AWS_DEFAULT_REGION="us-east-2"
    # export AWS_DEFAULT_OUTPUT="json"
    ```