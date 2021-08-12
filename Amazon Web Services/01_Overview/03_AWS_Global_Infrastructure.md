# Tính toàn cầu của AWS Service
## **1) Tổng quan**
- **AWS** hiện nay phục vụ hằng trăm ngàn người dùng ở hơn 190 nước, hệ thống hạ tầng của họ trải rộng ở 4 châu lục : Châu Á, Châu Mỹ, Châu Âu, Châu Úc.

    <img src=https://i.imgur.com/zq0Kc5l.png>

- **AWS** mở rộng hệ thống hạ tầng liên tục trên toàn thế giới, nhằm giúp khách hàng giảm thiểu tối đa độ trễ và tăng throughput đồng thời đảm bảo dữ liệu của khách hàng được nằm trong region mà họ yêu cầu. **AWS** đảm bảo hạ tầng của họ luôn luôn đáp ứng được nhu cầu của khách hàng khi công việc của khách hàng tăng lên.
    - **Region** là vùng địa lý ví dụ EU, US, ASIA,.. nơi đặt Data Center của **AWS** cho phép khách hàng đưa application và các lớp của họ lên, đảm bảo giảm độ trễ tránh phát sinh chi phí cho việc duy trì, vận hành bảo thống.
    - **Edge Location** là data center đặt khắp nơi trên thế giới phục vụ lưu trữ dữ liệu cho hai dịch vụ **Route53** và **Cloudfont**. **Edge Location** giúp giảm chi phí và tăng hiệu năng sử dụng cho khách hàng.
## **2) Availability Zones**

<p align=center><img src=https://i.imgur.com/QTcYVHU.png width=40%></p>

- Mỗi regions đều có ít nhất 2 availability zones , nhằm đảm bảo kiến trúc high availability cho workflow của khách hàng. Availability zones là nhóm vật lý của các data center chia theo khu vực của mỗi region, mỗi region được chia ra nhiều availability zones cho phép khách hàng chia tài nguyên của họ ra nhiều data center tăng tính sẵn sàng cho dịch vụ trong nhiều sự cố ví dụ như động đất.
## **3) Capacity Provisioning ( Khả năng cung cấp )**
- AWS khuyến cáo khách hàng sử dụng nhiều availability zones trong cùng một region, khách hàng không phải thêm tiền cho việc này. Khi một availability zones gặp sự cố, các tài nguyên tính toán trên các availability zones khác sẽ không bị ảnh hưởng.