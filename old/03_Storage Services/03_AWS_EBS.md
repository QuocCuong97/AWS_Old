# Amazon Elastic Block Store (EBS)
## **1) Giới thiệu** <img src=https://i.imgur.com/rjtzy54.png width=20% align=right padding-left=8px>
- **Amazon Elastic Block Store (EBS)** là dịch vụ cung cấp giải pháp lưu trữ ở mức block level, được coi như là một ổ cứng (**volume**) dùng cho các máy ảo **EC2**. Đặc trưng của dịch vụ này là tạo ra các volume tối thiểu `1GB` và tối đa là `16TB`. **EBS volume** được thiết kế để hỗ trợ tính sẵn sàng cao và độ tin cậy cao. **EBS** phù hợp với các như cầu ứng dụng về lưu trữ về database hoặc lưu trữ ở mức block level data.
- Khi các bạn tạo **EBS volume** thì **AWS** sẽ tính tiền dựa trên số lượng `GB` mà bạn khởi tạo (tham khảo hình bên dưới về chi tiết cách tính giá dịch vụ khi bạn khởi tạo volume mới).

    <p align=center><img src=https://i.imgur.com/Qc1ybqr.png width=80%></p>

- Đối với **standard volume** là loại ổ ứng dạng vòng quay `7200 RPM` ( vòng trên phút ), giá được tính dựa trên số lượng `GB` bạn tạo theo tháng cho đến khi bạn xóa **volume** này.
- Ngoài ra **Amazon** cũng tính thêm cả giá cho số lần bạn truy cập vào **volume**. Ngoài ra với ổ cứng dạng **IOPS** (ổ **SSD**) thì **AWS** sẽ tính giá dựa trên số `I/O` trên giây nhân với số phần trăm ngày sử dụng trong tháng. Ví dụ bạn tạo `1TB` **IOPS volume** và dùng `15` ngày thì tiền sẽ là `0.01$ * 1TB * (15 ngày/30 ngày)`.
- **EBS volume** tồn tại trong **Avaiability Zone** và có size từ `1GB` đến `16TB`, khi **volume** được tạo nó có thể được attach vào các máy ảo `EC2` với điều kiện máy ảo phải có cùng **availability zone** với nó. Khi được attach vào máy ảo nó sẽ giống như một ổ cứng. Một **volume** chỉ có thể được attach vào một máy ảo, tuy nhiên một máy ảo có thể có nhiều **volume**. Khi attach nhiều **volume** vào máy ảo thì nó sẽ tăng IO throughput, điều này giúp các ứng dụng có đọc/ghi vào volume sẽ tăng được performance.

    <p align=center><img src=https://i.imgur.com/rBVD8SB.png width=60%></p>

## **2) So sánh S3 và EBS**

<p align=center><img src=https://i.imgur.com/DMfDC7o.png width=60%></p>

- Khác biệt rõ nhất giữa **S3** và **EBS** là cách chúng đọc và ghi dữ liệu:
    - **EBS volume** đơn giản là một ổ cứng **block** level, bạn có thể attach vào máy ảo và đọc ghi ở mức block level.
    - **S3** đọc ghi dữ liệu ở mức **object**. Mỗi **object** có thể là một file, và mỗi lần đoc/ghi bạn sẽ phải đọc/ghi cả một file. Mặc dù bạn có thể chia nhỏ file ra để ghi/đọc nhưng sau cùng bạn vẫn phải ghi lại cả một file lần nữa vào **S3** để **S3** nhận biết được chúng. Khi bạn ghi nhiều lần vào cùng một object thì giá sẽ tăng. **S3** được thiết kế phù hợp với các use-case đọc một lần ghi một lần.
    - Cuối cùng là khác biệt về giá cả: **EBS** tính giá dựa trên số `GB` bạn tạo ra còn **S3** tính giá dựa trên số `GB` bạn sử dụng thực sự.
## **3) Snapshots**

<p align=center><img src=https://i.imgur.com/IK1hggu.png width=60%></p>

- **Snapshot** là bản ghi lưu trữ của **EBS volume** được lưu trên **S3**. Mục đích của **snapshot** là tránh mất dữ liệu khi **EBS** bị xóa do nhầm lẫn, bị tấn công hoặc bị tai nạn. 
- **Snapshot** sẽ chỉ lưu các **block** có dữ liệu của **EBS** chứ không lưu các **block** rỗng nên size của **snapshot** sẽ có thể bé hơn size của **EBS**. 
- Khi bạn snapshot **EBS** lần đầu tiên thì **snapshot** sẽ lưu trữ toàn bộ dữ liệu của **EBS**, khi bạn snapshot lần thứ hai thì nó sẽ chỉ lưu trữ những phần dữ liệu có thay đổi so với lần snapshot trước ( gọi là ***incremental snapshot***). Khi bạn xóa một **snapshot** thì chỉ có những dữ liệu không được sử dụng trong các **snapshot** khác mới bị xóa, do đó dù bất cứ **snapshot** nào bị xóa thì các **snapshot** còn lại cũng chứa tất cả những dữ liệu bạn cần khi restore. Ngoài ra thời gian để bạn restore bất kỳ bản **snapshot** nào cũng là như nhau, kể cả bản full backup và bản incremental backup. 
- Ngoài ra khi bạn restore **EBS volume** thông qua **snapshot**, **AWS S3** sẽ nạp dữ liệu một cách không đồng bộ, nghĩa là khi **EBS volume** được tạo bạn không cần đợi đến khi toàn bộ dữ liệu được tạo, khi bạn truy cập vào một dữ liệu chưa được load về, **S3** sẽ download phần dữ liệu đó ngay lập tức và download phần còn lại sau.