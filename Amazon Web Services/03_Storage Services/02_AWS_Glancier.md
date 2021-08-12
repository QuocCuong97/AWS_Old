# Amazon Glacier
## **1) Giới thiệu** <img src=https://i.imgur.com/tIxzMSp.png width=12% align=right padding-left=8px>
- Amazon Glacier là dịch vụ lưu trữ siêu rẻ, dùng cho trường hợp lưu trữ data dài hạn, backup. Giá bắt đầu từ 0.01$ cho mỗi GB hàng tháng tại Mỹ.
- Amazon Glacier được thiết kế để đảm bảo tính bền vững của dữ liệu ở mức 99,9999999999% đối với mỗi bản lưu trữ.
- Amazon Glacier được tối ưu hóa cho những data không được truy cập thường xuyên, và việc lấy thông tin ra cho phép thực hiện trong vài giờ đồng hồ. Việc lấy data từ Amazon Glacier sẽ mất từ 4 -5 giờ đồng hồ mới hoàn thành.
- Glacier được design cho những data không được truy cập thường xuyên, những data này sẽ được lưu trữ trong thời gian dài. Hàng tháng bạn có thể truy xuất một cách miễn phí 5% dung lượng data đang lưu trữ đang lưu trữ trên Glacier. Nếu bạn truy xuất nhiều hơn bạn sẽ phải trả chi phí mỗi 0,01% trên môi GB ( giá tại Mỹ ). Ngoài ra bạn sẽ phải trả chi phí 0,03$ mỗi GB nếu xóa data trước 90 ngày. Việc chuyển data từ Glacier ra ngoài Internet cũng bị tính phí với từng GB.
- Trong môi trường truyền thống, việc backup hoặc lưu trữ dài hạn dữ liệu thường gặp vấn đề, tính bền vững thấp, mất nhiều thời gian để phục hồi và tốn nhiều chi phí. Với Amazon Glacier
    - Hệ thống được tối ưu hóa cho những data mà không được truy cập thường xuyên.
    - Thời gian truy xuất dữ liệu được tính bằng giờ thay vì bằng ngày hay tuần và với chi phí rất rẻ.
    - Mức độ đảm bảo rất cao về tính bền vững.
    - Dữ liệu được mã hóa bằng AES 256.

    