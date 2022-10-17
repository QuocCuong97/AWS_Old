# Các gói dịch vụ EC2 Instances
## **On-Demand Instance**
- **On-demand** khá là an toàn cũng như là thuận tiện. Sử dụng bao nhiêu thì trả tiền bấy nhiêu, tính tiền theo giờ. Nó khá là thuận tiện khi muốn sử dụng một instance mà không có kế hoạch lên trước, bạn có thể dùng bất cứ lúc nào và xóa lúc bất cứ lúc nào nếu muốn.
- Về giá thì **On-Demand** có mức giá khá là cao so với các loại khác tuy nhiên không cần phải trả bất cứ phí gì trước, cứ start xong là trả tiền thôi.
## **Reserved Instances**
- Là 1 loại instance mà bạn muốn đăng kí sử dụng trong một khoảng thời gian dài, do là nó đã được đặt từ trước vì thế **AWS** đã có mức discount lên đến `72%` so với giá của **on-demand** đối với loại instance này. Vì vậy bạn sẽ cần phải trả trước để cam kết sẽ sử dụng lâu dài, bạn có thể trả trước ngay 1 lúc hoặc có thể đặt trước, ngoài ra khi không dùng đến thì có thể bảo lưu 1 hoặc 3 năm tùy ý.
- Khi đã đăng kí sử dụng **reserved instance**, phải xác định loại instance type sẽ sử dụng như `a1.medium` hay `t2.micro` ...
- Thường loại **Reserved Instance** này khá hữu dụng khi cần tạo 1 database, thì việc này khá là hợp lí vì nó sẽ giảm giá cho bạn đến `72%`.
- Dưới đây là mô hình tổng thể về Reserved Instances :

    <img src=https://i.imgur.com/0CvH5Us.png>

- Tuy nhiên Reserved Instance sẽ chia ra làm 2 loại để các bạn có thể linh hoạt hơn trong việc sử dụng chúng :
    
## **Spot Instances**
## **Dedicated Hosts**
## **Saving Plans**