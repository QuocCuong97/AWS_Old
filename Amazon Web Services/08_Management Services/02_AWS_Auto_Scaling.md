# Amazon Auto Scaling
## **1) Giới thiệu** <img src=https://i.imgur.com/io9eCyR.png width=15% align=right padding-left=8px>
- Auto Scaling là một dịch vụ rất quan trọng của Amazon Web Services (AWS). Dịch vụ này cho phép bạn tăng/giảm năng lực tính toán của amazon EC2 tự động dựa trên những điều kiện bạn đặt ra trước. Với Auto Scaling bạn có thể cấu hình để hệ thống của bạn tự động tăng số lượng máy ảo khi cần phục vụ nhiều người sử dụng, tự động giảm số lượng máy ảo khi lượng tải của hệ thống ở mức thấp. Qua đó tối ưu nguồn lực và giảm thiểu chi phí. Auto Scaling cũng rất phù hợp với những hệ thống có lượng sử dụng biến thiên như hệ thống tra điểm thi đại học lượng truy cập chủ yếu và mùa thi.
- Thông thường Auto Scaling được cấu hình để chạy cùng các dịch vụ Elastic Load Balancing và Amazon CloudWatch

    <p align=center><img src=https://i.imgur.com/kaIPbgd.png width=40%></p>

- Cơ chế hoạt động được mô tả trong hình vẽ dưới đây :

    <p align=center><img src=https://i.imgur.com/9UYEWZw.png width=40%></p>

- Những số liệu còn được gọi là matrix trong quá trình hoạt động của Elastic Load Balancer và máy ảo EC2 được đẩy về CloudWatch để theo dõi. Các máy ảo đó có thể tình trạng sử dụng latency, Ram, CPU, network của từng máy ảo EC2,.. Về phía dịch vụ của CloudWatch, tại đây người dùng có thể định nghĩa các Alarm là các ngưỡng báo động dựa trên các matrix, khi matrix tới ngưỡng báo động sẽ thực thi 1 hay nhiều hoạt động nào đó.
- Ví dụ khi CPU hoạt động quá 80% trong 3 phút sẽ gửi mail cảnh bảo tới  quản trị hệ thống và gửi lệnh tới Auto Scaling để tạo thêm EC2. Auto Scaling khi nhận được lệnh từ Alarm của CloudWatch sẽ tạo mới máy ảo của EC2 rồi đăng ký với Elastic Load Balancer,  hoặc tắt một máy ảo khỏi Elastic Load Balancer.
- Những thông số của máy ảo cần chạy, số lượng máy ảo, thông tin của Elastic Load Balancer được người dùng cấu hình thông qua Auto Scaling Group và Auto Scaling Security.
- Giả sử bạn cần đảm bảo hệ thống của bạn luôn có 2 máy ảo hoạt động tốt phía sau Elastic Load Balancer. Bạn có thể định nghĩa điều kiện đó với Auto Scaling, khi phát hiện điều kiện đó bị vi phạm Auto Scaling sẽ tự động tạo thêm máy ảo vào Auto Scaling Group của bạn. Bạn có thể tự động co dãn theo latency, ví dụ khi latency của bất cứ máy ảo EC2 nào vượt quá 4s trong 15 phút, bạn có thể cài đặt điều kiện đó với Auto Scaling, khi điều kiện đó xảy ra Auto Scaling sẽ thực hiện các sự kiện bạn đã cài đặt. Auto Scaling có thể hoạt động tốt với các máy ảo EC2 trong trường hợp có hoặc không có Elastic Load Balancer.

    <p align=center><img src=https://i.imgur.com/DvywE4n.png width=40%></p>

















