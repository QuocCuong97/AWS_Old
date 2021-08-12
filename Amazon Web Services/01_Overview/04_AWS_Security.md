# Tính bảo mật của AWS
## **1) Tổng quan**
- **AWS** cung cấp một nền tảng điện toán đám mây có thể mở rộng có khả năng mở rộng với tính khả dụng, độ tin cậy cao và linh hoạt cho phép khách hàng xây dựng một loại ứng dụng. Để cung cấp cho khách hàng sự bảo mật và riêng tư, **AWS** đã cung cấp dịch vụ với rất nhiều tính năng hỗ trợ về bảo mật như: Security group, nhóm bảo mật, Network ALCs,.. AWS cũng cung cấp nhiều tình huống, bài học kinh nghiệm về bảo mật, tài liệu hướng dẫn người sử dụng và thực hành tốt những những tính năng về bảo mật để xây dựng được một môi trường ứng dụng an toàn, phù hợp. Việc đảm bảo tính bảo mật, tính toàn vẹn và tính sãn sàng cho dữ liệu của khách hàng là nhiệm vụ tối quan trọng của AWS nhằm duy trì sự tin tưởng của khách hàng với AWS. Hiện nay đã có rất nhiều hệ thống lớn sử dụng dịch vụ của AWS như NASA, Chính phủ Mỹ,...
- **AWS** đảm bảo bảo mật trên 4 dịch vụ chính sau:
    - Physical ( Bảo mật vật lý ) : Trung tâm Data center được xây dựng thiết kế và quản lý rất an toàn với những yêu cầu như:
        - Data center được xây dựng ở những khu bí mật, không công khai.
        - Bên trong data center, AWS kiểm soát nghiêm ngặt tất cả truy cập vật lý, có khi lại hoạt động và tiến hành kiểm toán định kỳ.
        - Giám đốc công nghệ (CTO) cũng không được vào data center.
        - Quyền truy cập được chia ra làm truy cập vật lý và truy cập phần mềm. Người có quyền truy cập vật lý thì không có quyền truy cập phần mềm và ngược lại
    - Certification & Accreditations : Sau đây là những tiêu chuẩn về bảo mật trên thế giới mà AWS đã đáp ứng bao gồm tất cả những tiêu chuẩn nghiêm ngặt nhất như:
        - ISO 27001: Tiêu chuẩn quốc tế về hệ thống quản lý an toàn thông tin ISMS.
        - SSAE 16/ISAE 3402/ SOC1 (formerly U.S.standard SAS-70 Type III): Tiêu chuẩn hợp tác xác nhận số 16.
        - FISMA Moderate & DIACAp controls; ITAR region: Đạo luật quản lý an ninh thông tin liên bang Mỹ.
        - HIPAA applications certificated on AWS: Đạo luật về quyền riêng tư của thông tin về sức khỏe
        > Khi bạn viết ứng dụng trên AWS, ứng dụng của bạn không tự động có các chuẩn này mà cũng phải tuân thủ và thông qua quá trình xét duyệt nếu muốn đạt chuẩn.
    - Hardware, Software & Network : AWS quản lý phần cứng, phần mềm, mạng của hệ thống một cách an toàn:
        - AWS quản lý toàn bộ mọi thay đổi cho bạn như thay máy mới khi máy bị hỏng, sửa lại mạng khi mạng bị lỗi, cập nhật bản vá an ninh mới nhất.
        - AWS nâng cấp phần cứng theo từng cụm. Giả sử bạn có hai máy chủ A và B ở hai vùng khác nhau, AWS sẽ tắt và nâng cấp máy A trước, khi đó máy B vẫn còn hoạt động. Xong khi máy A bật lại xong và chạy bình thường, AWS sẽ tắt và nâng cấp máy B. Khi đó hệ thống của bạn luôn có 1 máy hoạt động.
        - Khi một máy tính hoặc một ổ địa bị hỏng, hay hết thời hạn sử dụng, AWS có quy trình hủy máy hết sức triệt để sau đó chôn nó ở một địa điểm không xác định. Không có rủi ro rò rỉ dữ liệu khi hủy phần cứng cũ.
        - AWS tự động theo dõi giám sát hoạt động của data center và thực hiện kiểm toán thường xuyên.
    - Security & Compliance Resource : AWS cung cấp các loại tài nguyên về bảo mật rất có lợi cho người dùng:
        - Best practices.
        - Workbook.
        - Hướng dẫn sử dụng.
        - AWS thưỡng xuyên được kiểm toán bởi bên thứ ba và người dùng có thể tra cứu kết quả kiểm toán.
## **2) AWS Security : Shared Responsibility**
<p align=center><img src=https://i.imgur.com/n7p3Uq2.png></p>

- Trách nhiệm bảo mật thuộc về cả hai bên AWS và User
- AWS sẽ đảm bảo:
    - Bảo mật của hạ tầng và các dịch vụ nền tảng căn bản tính toán, lưu trữ, mạng, cơ sở dữ liệu
    - Đảm bảo đạt chứng chỉ tiêu chuẩn về bảo mật của hệ thống sản phẩm, dịch vụ
    - Cung cấp các tài nguyên về bảo mật có ích cho người dùng
- Trách nhiệm của người dùng là:
    - Đảm bảo bảo mật của hệ điều hành, phần mềm, ứng dụng, data.
    - Sử dụng và cấu hình đúng các công cụ về bảo mật của AWS
    - Chú ý AWS không thể cập nhật Windows update hay dò lỗi trong hệ diều hành cho người dùng vì AWS không được quyền truy cập vào máy
## **3) Security Isolation Models**
- Nhằm đảm bảo tính bảo mật, AWS tách biệt tài nguyên của người này với tài nguyên của người khác. Lựa chọn mặc định ban đầu của các cấu hình là deny all, không cho bất kỳ ai sử dụng. Có 4 hình thức tách biệt tài nguyên :
    - **VPC** : mạng của bạn tách biệt hoàn toàn với mạng người khác, default thì máy trong VPC này không thể kết nối tới máy trong VPC khác.
    - **Direct Connect & VPN** : Data center của bạn được kết nối tới AWS bởi một kết nối tách biệt với các kết nối khác. Kết nối này có thể là vật lý hoặc ảo.
    - **Delicated Instance** : Bạn có thể chọn một server để deploy máy ảo mà server này không bị chia sẻ vói người khác
    - **Sercurity Group, Firewall** : Ngăn traffic vào máy ảo

        <p align=center><img src=https://i.imgur.com/cMJ27yo.png width=60%></p>

        - Hình vẽ trên mô tả cách dùng Security Group, giống Firewall nó có thể chặn lưu lượng dữ liệu và chỉ cho phép dữ liệu vào từ một cổng xác định qua các dải IP, địa chỉ định danh xác định.
- Người dùng có thể quản lý tài khoản và truy cập trên AWS bằng cách cách sau :
    - AWS Master Account : chính là tài khoản gốc để sử dụng AWS, tài khoản này có thể làm mọi thứ, theo kinh nghiệm là không nên sử dụng tài khoản này.
    - Multi-Factor Authentication : Khi đăng nhập phải nhập thêm code từ thiết bị di động, nên sử dụng MFA trong trường hợp có yêu cầu an toàn cao.
    - Consolidate Billing : Một tài khoản trả cho các tài khoản con của nó.
    - Invoice Billing : Hằng tháng AWS sẽ gửi bill với đầy đủ thông tin về dịch vụ, thời gian sử dụng, số tiền,.. về email. 