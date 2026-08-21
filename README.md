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

### 2. Bảng Phân Tích Các Bên Liên Quan

| Tên bên liên quan | Vai trò trong hệ thống |
| :--- | :--- |
| **Ban giám đốc / Ban lãnh đạo** | - Đưa ra định hướng chiến lược và kỳ vọng phát triển nền tảng lâu dài.<br>- Theo dõi các báo cáo về doanh thu, số lượng chuyến, tỷ lệ hoàn thành/hủy và hiệu quả vận hành của tài xế để ra quyết định kinh doanh. |
| **Khách hàng** | - Đăng ký, đăng nhập và cập nhật thông tin cá nhân.<br>- Nhập điểm đón/đến, chọn loại xe, gửi yêu cầu đặt chuyến và theo dõi trạng thái chuyến đi.<br>- Thực hiện thanh toán tiền cước và đánh giá tài xế sau khi hoàn thành chuyến. |
| **Tài xế** | - Đăng ký tài khoản, cập nhật hồ sơ cá nhân và thông tin phương tiện.<br>- Bật/tắt trạng thái sẵn sàng làm việc để nhận thông báo chuyến.<br>- Tiếp nhận hoặc từ chối yêu cầu đặt xe.<br>- Cập nhật các trạng thái của chuyến đi (đã đến điểm đón, đã đón khách, đang di chuyển, hoàn thành) và chia sẻ vị trí phương tiện. |
| **Nhân viên vận hành** | - Sử dụng giao diện quản trị để quản lý danh sách khách hàng, tài xế, phương tiện và dữ liệu chuyến đi.<br>- Tạo tài khoản cho tài xế (nếu cần).<br>- Giám sát các chuyến đi đang diễn ra, kiểm tra trạng thái tài xế, hỗ trợ xử lý sự cố/chuyến đi bị lỗi và tra cứu lịch sử giao dịch. |
| **Chuyên viên Phân tích Nghiệp vụ** | - Xác định rõ phạm vi, tác nhân, quy trình nghiệp vụ, yêu cầu chức năng và phi chức năng.<br>- Làm việc với các bên liên quan để làm rõ các quy tắc nghiệp vụ chưa hoàn thiện (cách tính cước, điều phối tài xế, chính sách hủy, xử lý mất mạng, lưu trữ dữ liệu) trước khi phát triển. |
| **Đội ngũ Phát triển & Triển khai** | - Thiết kế kiến trúc hệ thống linh hoạt, có khả năng mở rộng độc lập và chịu tải cao.<br>- Xây dựng và triển khai toàn bộ nền tảng CAB trong khung thời gian 7 tuần. |
| **Nhà cung cấp dịch vụ thanh toán** | - Xử lý các giao dịch thanh toán điện tử bên ngoài hệ thống.<br>- Đảm bảo bảo mật dữ liệu thẻ/tài khoản và phản hồi kết quả giao dịch thanh toán về hệ thống. |
| **Nhà cung cấp dịch vụ thông báo** | - Cung cấp hạ tầng gửi thông báo tự động (thông báo đẩy, tin nhắn) đến khách hàng và tài xế trong suốt hành trình. |


---

<details>
<summary><b>3. Ma Trận Phân Loại Stakeholder (Power - Interest Matrix)</b> [Bấm để xem]</summary>

### 3.1 Sơ đồ Ma trận Quyền lực & Mức độ Quan tâm

```mermaid
flowchart TB
    subgraph MATRIX["MA TRẬN POWER - INTEREST"]
        direction TB

        subgraph ROW1["QUYỀN HẠN CAO (HIGH POWER)"]
            direction LR
            subgraph Q2["KEEP SATISFIED (Đáp ứng hài lòng)<br><i>High Power - Low Interest</i>"]
                direction TB
                D1["- Nhà cung cấp dịch vụ thanh toán"]
                D2["- Nhà cung cấp dịch vụ thông báo"]
            end

            subgraph Q1["MANAGE CLOSELY (Quản lý chặt chẽ)<br><i>High Power - High Interest</i>"]
                direction TB
                A1["- Ban giám đốc / Ban lãnh đạo"]
                A2["- Nhân viên vận hành"]
            end
        end

        subgraph ROW2["QUYỀN HẠN THẤP (LOW POWER)"]
            direction LR
            subgraph Q3["MONITOR (Theo dõi tối thiểu)<br><i>Low Power - Low Interest</i>"]
                direction TB
                M1["- Các dịch vụ hỗ trợ phụ khác"]
            end

            subgraph Q4["KEEP INFORMED (Giữ thông tin thường xuyên)<br><i>Low Power - High Interest</i>"]
                direction TB
                C1["- Khách hàng"]
                C2["- Tài xế"]
                C3["- Chuyên viên Phân tích Nghiệp vụ"]
                C4["- Đội ngũ Phát triển & Triển khai"]
            end
        end
    end

    classDef high fill:#e3f2fd,stroke:#1565c0,stroke-width:2px,color:#0d47a1;
    classDef low fill:#f1f8e9,stroke:#558b2f,stroke-width:2px,color:#33691e;
    classDef monitor fill:#fafafa,stroke:#9e9e9e,stroke-width:1px,color:#616161;
    classDef satisfied fill:#fff8e1,stroke:#f57f17,stroke-width:2px,color:#e65100;

    class Q1 high;
    class Q4 low;
    class Q2 satisfied;
    class Q3 monitor;
