# Amazon Simple Storage Services (S3)
## **1) Giới thiệu** <img src=https://i.imgur.com/jV29Wz3.png width=12% align=right padding-left=8px>
- **Amazon S3** là dịch vụ lưu trữ **object** có độ bền vững cao, có khả năng lưu trữ và mở rộng không giới hạn. Là dịch vụ lưu trữ trực tuyến, **S3** cung cấp một giao diện web services đơn giản để người dùng dễ dàng lưu trữ hoặc lấy ra bất kỳ phần dữ liệu nào của họ, tại bất cứ thời điểm nào và tại bất kỳ địa điểm nào.
- Dữ liệu được lưu trữ với cam kết `99,99999999%`. Về tính bền vững dữ liệu, người dùng có thể lưu trữ một số lượng không giới hạn và chỉ trả tiền cho phần họ sử dụng.
- Người dùng còn có thể lựa chọn **S3** ở các **region** để tối ưu hóa cho tốc độ truyền dữ liệu, giảm chi phí hoặc phù hợp với yêu cầu bài toán.
- Giá sử dụng **S3**:
    - Được tính dựa trên khối lượng và băng thông dùng thực tế.
    - Tất cả băng thông đi vào **S3** là miễn phí nhưng **Amazon** sẽ tính phí trên băng thông đi ra.
    - Đơn vị lưu trữ được dùng để tính phí khi sử dụng **S3** là `GB/tháng`.
    - **S3** là dịch vụ hiện hữu trên nhiều **region** và giá sử dụng trên từng **region** là khác nhau.
- Một số lưu ý khi sử dụng **S3**:
    - Có một giới hạn về số lượng "`bucket`" có thể tồn tại với mỗi **AWS account** là `100 bucket`.
    - Tên của `bucket` là toàn cục trong 1 **region**, và phải là duy nhất. Nếu `bucket` là rỗng bạn có thể xóa và tái sử dụng tên. Tuy nhiên điều đó không có nghĩa bạn có thể tái sử dụng tên `bucket` đó, ví dụ tên đó vừa được một account khác sử dụng để tạo một `bucket`, vì vậy cần chú ý khi xóa `bucket`.
    - Bạn không thể tạo `bucket` bên trong một `bucket`.
    - Tên `bucket` được sử dụng như một public address trên internet. Vậy nên **Amazon** khuyến nghị tất cả tên `bucket` nên tương thích với chuẩn đặt tên **DNS**: Tên phải có ít nhất `3` ký tự và không dài hơn `63` ký tự. Tên `bucket` phải là một hoặc nhiều chuỗi ký tự, các chuỗi phân cách với nhau bởi dấu chấm (`.`). Tên `bucket` có thể chứa chữ thường, số hoặc dấu gạch ngang. Mỗi chuỗi ký tự phải bắt đầu và kết thúc bằng một ký tự chữ thường hoặc số. Tên `bucket` không được có dạng IP Address.

    