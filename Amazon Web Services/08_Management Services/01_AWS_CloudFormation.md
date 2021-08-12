# AWS CloudFormation
## **1) Programmable Infrastructure** <img src=https://i.imgur.com/iZyLtnA.png width=15% align=right padding-left=8px>
- Khi sử dụng Amazon Web Services Cloud, các định hướng mô hình và quy trình mới có thể sẽ không phù hợp với mô hình IT truyền thống, do đó trên AWS đưa ra khái niệm Programmable Infrastructure có thể được hiểu là việc  xây dựng hạ tầng, nếu như trước đây là thông qua việc thiết kế phần cứng thì nay sẽ được định nghĩa thông qua lập trình.
- AWS CloudFormation là một công cụ của Amazon cho phép người dùng nhìn cloud của Amazon như là một Programmable Infrastructure.
## **2) AWS CloudFormation**
- Cách dễ nhất để mô tả CloudFormation là nó là một công cụ từ AWS cho phép bạn khởi tạo tài nguyên một cách dễ dàng. Bạn xác định tất cả các tài nguyên mà bạn muốn AWS bật lên trong một bản thiết kế chi tiết, bấm vào một nút, và sau đó AWS sẽ thực hiện giúp bạn phần việc còn lại. Bản thiết kế này được gọi là một template trong CloudFormation. CloudFormation đảm bảo rằng các tài nguyên phụ thuộc trong template của bạn đều được tạo theo đúng thứ tự.
- Là một dịch vụ hỗ trợ người lập trình và người lý hệ thống một cách thức đơn giản để định nghĩa một stack - kết hợp các dịch vụ của AWS thành một hệ thống hoàn chỉnh. Stack có thể đợi khởi tạo thông qua management console, API, hoặc CLI. Khách hàng có thể sử dụng các mẫu CloudFormation cho một số use-case điển hình như :
    - Tạo một biểu mẫu của stack về việc quản lý tài nguyên ( Create templates of stack of resource ).
    - Chạy stack từ biểu mẫu với các điều kiện ( Deploy stack from template with runtime parameters ).
    - Sử dụng các biểu mẫu như là một điểm bắt đầu hoặc tạo các biểu mẫu riêng của bạn ( Use templates as a starting point or create your own ).
- Nếu như trước đây việc triển khai hệ thống cần rất nhiều tài liệu thiết kế như network layout, bảo mật, lưu trữ,.. thì nay với việc sử dụng CloudFormation thì chúng mang lại rất nhiều lợi ích như:
    - Tất cả thiết kế đều được định nghĩa bằng sourcecode, giúp cho việc đánh phiên bản và quản lý thay đổi một cách dễ dàng.
    - Bạn có thể kiểm tra biểu mẫu ( templates) bằng bất cứ công cụ quản lý source nào mà bạn thích.
    - Tạo ra một cách mới trong việc quản trị hệ thống ( Enable new change management controls and operations practices ).
    - Biểu mẫu ( templates) được định nghĩa đơn giản dưới dạng file JSON.


