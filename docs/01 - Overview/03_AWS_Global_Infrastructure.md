# Tính toàn cầu của AWS Service
## **1) Tổng quan**
- **AWS** hiện nay phục vụ hằng trăm ngàn người dùng ở hơn `190` nước, hệ thống hạ tầng của họ trải rộng ở 4 châu lục : Châu Á, Châu Mỹ, Châu Âu, Châu Úc.
    <img src=https://i.imgur.com/Ev15clG.png>
    <img src=https://i.imgur.com/yPQ6Tei.png>

- **AWS** mở rộng hệ thống hạ tầng liên tục trên toàn thế giới, nhằm giúp khách hàng giảm thiểu tối đa độ trễ và tăng throughput đồng thời đảm bảo dữ liệu của khách hàng được nằm trong **region** mà họ yêu cầu. **AWS** đảm bảo hạ tầng của họ luôn luôn đáp ứng được nhu cầu của khách hàng khi công việc của khách hàng tăng lên.
    - **Region** là vùng địa lý ví dụ EU, US, ASIA,.. nơi đặt Data Center của **AWS** cho phép khách hàng đưa application và các lớp của họ lên, đảm bảo giảm độ trễ tránh phát sinh chi phí cho việc duy trì, vận hành bảo thống.
    - **Edge Location** là data center đặt khắp nơi trên thế giới phục vụ lưu trữ dữ liệu cho hai dịch vụ **Route53** và **Cloudfont**. **Edge Location** giúp giảm chi phí và tăng hiệu năng sử dụng cho khách hàng.
## **2) Region**
**2.1) Danh sách các Region hiện tại của AWS**

| Region name | Code name | 
|-------------|-----------|
| **US East (Ohio)** | `us-east-2` |
| **US East (N. Virginia)** | `us-east-1` |
| **US West (N. California)** | `us-west-1` |
| **US West (Oregon)** | `us-west-2` |
| **Africa (Cape Town)** | `af-south-1` |	
| **Asia Pacific (Hong Kong)** | `ap-east-1` |
| **Asia Pacific (Jakarta)** | `ap-southeast-3` |
| **Asia Pacific (Mumbai)**	| `ap-south-1` |
| **Asia Pacific (Osaka)** | `ap-northeast-3`	|
| **Asia Pacific (Seoul)** | `ap-northeast-2`	|
| **Asia Pacific (Singapore)** | `ap-southeast-1`	|
| **Asia Pacific (Sydney)**	| `ap-southeast-2` |
| **Asia Pacific (Tokyo)** | `ap-northeast-1`	|
| **Canada (Central)** | `ca-central-1` |
| **Europe (Frankfurt)** | `eu-central-1`	|
| **Europe (Ireland)** | `eu-west-1` |
| **Europe (London)** | `eu-west-2` |
| **Europe (Milan)** | `eu-south-1` |
| **Europe (Paris)** | `eu-west-3` |
| **Europe (Stockholm)** | `eu-north-1` |
| **Middle East (Bahrain)**	| `me-south-1` |
| **Middle East (UAE)**	| `me-central-1` |
| **South America (São Paulo)**	| `sa-east-1`	|
| **AWS GovCloud (US-East)** | `us-gov-east-1` |
| **AWS GovCloud (US-West)** | `us-gov-west-1` |

**2.2) Một số tiêu chí để lựa chọn Region**
- ***Tuân thủ các yêu cầu pháp lý và quản trị dữ liệu*** :
    - Tùy thuộc vào công ty và vị trí, có thể cần chạy dữ liệu của ra khỏi các khu vực cụ thể. Ví dụ: nếu công ty yêu cầu tất cả dữ liệu của mình phải nằm trong ranh giới của **United Kingdom**, bạn sẽ chọn **region** `London`.
- ***Gần gũi với khách hàng*** :
    - Chọn **region** gần với khách hàng sẽ giúp đưa nội dung đến với họ nhanh hơn. **VD :** công ty có trụ sở tại **Washington, DC** và nhiều khách hàng sống ở **Singapore**. Có thể cân nhắc việc chạy cơ sở hạ tầng của mình ở **region** `N.Virginia` để gần trụ sở công ty và chạy các ứng dụng từ **region** `Singapore`.
- ***Các services khả dụng trong một **Region***** :
    - Đôi khi, **region** gần nhất có thể không có tất cả các tính năng muốn cung cấp cho khách hàng. **AWS** thường xuyên đổi mới bằng cách tạo ra các dịch vụ mới và mở rộng các tính năng trong các dịch vụ hiện có. Tuy nhiên, việc cung cấp các dịch vụ mới trên toàn thế giới đôi khi yêu cầu **AWS** phải xây dựng phần cứng vật lý tại một **region** tại một thời điểm.
- ***Giá*** :
    - Giả sử rằng đang xem xét việc chạy các ứng dụng ở cả **United States** và **Brazil**. Cách mà cấu trúc thuế của **Brazil** được thiết lập có thể tốn thêm `50%` để chạy cùng một lượng workload ở **region** `São Paulo` so với **region** `Oregon`. Chi phí dịch vụ có thể khác nhau giữa các **region**.
## **3) Availability Zones**

<p align=center><img src=https://i.imgur.com/aUM24CY.png width=60%></p>

- **Availability zones** là một data center đơn lẻ hoặc một nhóm các data center trong một **Region** nhằm đảm bảo kiến trúc ***high availability*** cho workflow của khách hàng. Các **Availability zones** sẵn sàng nằm cách xa nhau hàng chục dặm. Điều này đủ gần để có độ trễ thấp (khoảng thời gian từ khi nội dung được yêu cầu và nhận được) giữa các **availability zones**. Tuy nhiên, nếu thảm họa xảy ra ở một phần của **Region**, chúng sẽ đủ xa để giảm khả năng nhiều **availability zones** bị ảnh hưởng.
## **4) Edge Location**
- **Edge location** là một site mà **Amazon CloudFront** sử dụng để lưu trữ các bản sao nội dung đã lưu trong bộ nhớ cache đến gần khách hàng hơn để phân phối nhanh hơn.

    <img src=https://i.imgur.com/Cb61go5.png>

    - Giả sử công ty có vị trí tại **Brazil**, và có nhiều khách hàng sống ở **Trung Quốc**. Để cung cấp nội dung đến các khách hàng này, không cần thiết phải di chuyển tất cả nội dung đến **region** `China`.
    - Thay vì yêu cầu khách hàng lấy dữ liệu của họ từ **Brazil**, có thể cache 1 bản copy local trên **edge location** ở **Trung Quốc** gần với khách hàng nhất.
    - Khi khách hàng ở **Trung Quốc** request 1 file trong data, **Amazon CloudFront** sẽ lấy file đó trong cache được lưu trên **edge location** và cung cấp chúng tới cho người dùng. File được cung cấp tới người dùng sẽ nhanh hơn vì nó được cung cấp tới người dùng từ một **edge location** gần **Trung Quốc** thay vì từ nguồn **Brazil**.