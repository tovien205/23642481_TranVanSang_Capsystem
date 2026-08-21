# 23642481_TranVanSang_Capsystem


## 1. Phân tích Vấn đề của Hệ thống Hiện tại (Problem Statement & Q&A)

Dưới góc nhìn của Business Analyst (BA) kết hợp định hướng xây dựng giải pháp **MVP (Minimum Viable Product)** trong 7 tuần, dưới đây là bộ câu hỏi - câu trả lời làm rõ toàn bộ các vấn đề (pain points) mà Công ty ABC đang gặp phải:

### Q1: Quy trình điều phối chuyến xe hiện tại đang gặp bất cập gì lớn nhất?
* **Thực trạng:** Việc phân công tài xế chủ yếu được thực hiện thủ công qua tổng đài hoặc tiếp nhận từ ứng dụng đơn giản.
* **Hậu quả:** Tốc độ ghép xe chậm, dễ nhầm lẫn hoặc sót chuyến khi lượng đặt tăng, lãng phí nguồn lực nhân sự tổng đài.
* **Định hướng MVP:** Xây dựng cơ chế tự động tìm và gán chuyến cho tài xế gần nhất theo thuật toán định vị GPS, tự động chuyển chuyến tiếp theo nếu tài xế từ chối.

### Q2: Khách hàng đang gặp khó khăn gì trong quá trình sử dụng dịch vụ?
* **Thực trạng:** Khách hàng không thể chủ động theo dõi trạng thái chuyến đi theo thời gian thực (không biết xe đang ở đâu, bao lâu tài xế đến nơi, ai là người nhận cuốc).
* **Hậu quả:** Trải nghiệm khách hàng kém, phát sinh tâm lý sốt ruột dẫn đến tỷ lệ gọi điện hối thúc hoặc tự ý hủy chuyến cao.
* **Định hướng MVP:** Cung cấp giao diện bản đồ trực quan theo dõi vị trí tài xế và trạng thái chuyến xe (Tìm tài xế -> Đã nhận -> Đã đến -> Đang chở khách -> Hoàn thành).

### Q3: Vấn đề trong quản lý thanh toán và doanh thu hiện tại là gì?
* **Thực trạng:** Thông tin thanh toán chưa được quản lý tập trung; phụ thuộc nhiều vào tiền mặt hoặc đối soát rời rạc, chưa có liên kết chuẩn với các cổng thanh toán.
* **Hậu quả:** Thất thoát doanh thu, đối soát công nợ với tài xế phức tạp, mất nhiều thời gian tổng hợp thủ công.
* **Định hướng MVP:** Quản lý tập trung lịch sử giao dịch, hỗ trợ thanh toán tiền mặt và tích hợp 01 cổng thanh toán điện tử chuẩn bên ngoài đảm bảo tính bảo mật (không lưu trữ thông tin thẻ nhạy cảm).

### Q4: Bộ phận vận hành (Operations) đang gặp rào cản gì trong việc giám sát và hỗ trợ?
* **Thực trạng:** Chưa có giao diện quản trị (Admin Portal) tập trung; khó theo dõi danh sách chuyến đang diễn ra, trạng thái tài xế và các trường hợp chuyến bị lỗi.
* **Hậu quả:** Xử lý khiếu nại chậm trễ, không có dữ liệu để đánh giá hiệu suất (KPI) tài xế cũng như tỷ lệ hủy/hoàn thành chuyến.
* **Định hướng MVP:** Xây dựng Dashboard quản trị cơ bản: quản lý tài khoản người dùng/tài xế, giám sát danh sách chuyến đi thực tế và tra cứu lịch sử sự cố.

### Q5: Hệ thống hiện tại có đáp ứng được mục tiêu mở rộng và chịu tải cao không?
* **Thực trạng:** Kiến trúc cũ phụ thuộc lẫn nhau, hiệu năng kém khi nhu cầu tăng đột biến; một lỗi nhỏ ở khâu thông báo hoặc thanh toán có thể khiến toàn bộ hệ thống tê liệt.
* **Hậu quả:** Doanh nghiệp không thể mở rộng quy mô kinh doanh, mở rộng loại hình dịch vụ hoặc tích hợp thêm đối tác bên thứ ba.
* **Định hướng MVP:** Thiết kế kiến trúc dạng module hóa (decoupled), đảm bảo lỗi từ các dịch vụ phụ (thanh toán/thông báo) không làm gián đoạn luồng đặt xe cốt lõi.


