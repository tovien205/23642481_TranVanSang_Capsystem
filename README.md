# 23642481_TranVanSang_Capsystem

<details>
<summary><b>Phân Tích Vấn Đề của Hệ Thống Hiện Tại (Problem Statement & Q&A)</b> [Bấm để xem]</summary>

Dưới góc nhìn của Business Analyst (BA) kết hợp định hướng xây dựng giải pháp **MVP (Minimum Viable Product)** trong 7 tuần, dưới đây là bộ câu hỏi - câu trả lời làm rõ các vấn đề cốt lõi mà Công ty ABC đang gặp phải:

- **Q1: Quy trình điều phối chuyến xe hiện tại đang gặp bất cập gì lớn nhất?**
  - Thực trạng: Việc phân công tài xế chủ yếu được thực hiện thủ công qua tổng đài hoặc tiếp nhận từ ứng dụng đơn giản.
  - Hậu quả: Tốc độ ghép xe chậm, dễ nhầm lẫn hoặc sót chuyến khi lượng đặt tăng, lãng phí nguồn lực nhân sự tổng đài.
  - Định hướng MVP: Xây dựng cơ chế tự động tìm và gán chuyến cho tài xế gần nhất theo thuật toán định vị GPS, tự động chuyển chuyến tiếp theo nếu tài xế từ chối.

- **Q2: Khách hàng đang gặp khó khăn gì trong quá trình sử dụng dịch vụ?**
  - Thực trạng: Khách hàng không thể chủ động theo dõi trạng thái chuyến đi theo thời gian thực (không biết xe đang ở đâu, bao lâu tài xế đến nơi, ai là người nhận cuốc).
  - Hậu quả: Trải nghiệm khách hàng kém, phát sinh tâm lý sốt ruột dẫn đến tỷ lệ gọi điện hối thúc hoặc tự ý hủy chuyến cao.
  - Định hướng MVP: Cung cấp giao diện bản đồ trực quan theo dõi vị trí tài xế và trạng thái chuyến xe (Tìm tài xế -> Đã nhận -> Đã đến -> Đang chở khách -> Hoàn thành).

- **Q3: Vấn đề trong quản lý thanh toán và doanh thu hiện tại là gì?**
  - Thực trạng: Thông tin thanh toán chưa được quản lý tập trung; phụ thuộc nhiều vào tiền mặt hoặc đối soát rời rạc, chưa có liên kết chuẩn với các cổng thanh toán.
  - Hậu quả: Thất thoát doanh thu, đối soát công nợ với tài xế phức tạp, mất nhiều thời gian tổng hợp thủ công.
  - Định hướng MVP: Quản lý tập trung lịch sử giao dịch, hỗ trợ thanh toán tiền mặt và tích hợp 01 cổng thanh toán điện tử chuẩn bên ngoài đảm bảo tính bảo mật (không lưu trữ thông tin thẻ nhạy cảm).

- **Q4: Bộ phận vận hành (Operations) đang gặp rào cản gì trong việc giám sát và hỗ trợ?**
  - Thực trạng: Chưa có giao diện quản trị (Admin Portal) tập trung; khó theo dõi danh sách chuyến đang diễn ra, trạng thái tài xế và các trường hợp chuyến bị lỗi.
  - Hậu quả: Xử lý khiếu nại chậm trễ, không có dữ liệu để đánh giá hiệu suất (KPI) tài xế cũng như tỷ lệ hủy/hoàn thành chuyến.
  - Định hướng MVP: Xây dựng Dashboard quản trị cơ bản: quản lý tài khoản người dùng/tài xế, giám sát danh sách chuyến đi thực tế và tra cứu lịch sử sự cố.

- **Q5: Hệ thống hiện tại có đáp ứng được mục tiêu mở rộng và chịu tải cao không?**
  - Thực trạng: Kiến trúc cũ phụ thuộc lẫn nhau, hiệu năng kém khi nhu cầu tăng đột biến; một lỗi nhỏ ở khâu thông báo hoặc thanh toán có thể khiến toàn bộ hệ thống tê liệt.
  - Hậu quả: Doanh nghiệp không thể mở rộng quy mô kinh doanh, mở rộng loại hình dịch vụ hoặc tích hợp thêm đối tác bên thứ ba.
  - Định hướng MVP: Thiết kế kiến trúc dạng module hóa (decoupled), đảm bảo lỗi từ các dịch vụ phụ (thanh toán/thông báo) không làm gián đoạn luồng đặt xe cốt lõi.

---

### Bảng Tổng Hợp Vấn Đề & Giải Pháp MVP

| STT | Nhóm vấn đề | Thực trạng hiện tại | Giải pháp cốt lõi cho bản MVP (7 tuần) |
| :-- | :--- | :--- | :--- |
| **1** | **Điều phối xe** | Phân công tài xế thủ công | Tự động hóa thuật toán tìm và gán tài xế gần nhất |
| **2** | **Trải nghiệm khách hàng** | Mù thông tin về tiến trình chuyến đi | Cung cấp luồng Tracking thời gian thực & thông báo trạng thái |
| **3** | **Quản lý thanh toán** | Dữ liệu thanh toán phân tán, dễ thất thoát | Quản trị tập trung, tích hợp cổng thanh toán an toàn |
| **4** | **Vận hành & Giám sát** | Thiếu công cụ quản trị và báo cáo | Xây dựng Admin Dashboard quản lý User, Driver, Trip |
| **5** | **Khả năng mở rộng** | Hệ thống dễ sập khi quá tải hoặc có lỗi | Tách module độc lập, đảm bảo luồng lõi luôn hoạt động |

</details>

<details>
<summary><b>Bước 1. Bảng Phân Tích Các Bên Liên Quan (Stakeholders)</b> [Bấm để xem]</summary>

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

</details>

<details>
<summary><b>Bước 2. Ma Trận Phân Loại Stakeholder (Power - Interest Matrix)</b> [Bấm để xem]</summary>

### 3.1 Sơ đồ Ma trận Quyền lực & Mức độ Quan tâm

### Stakeholder Power-Interest Matrix

```mermaid
quadrantChart
    title Stakeholder Power / Interest Matrix
    x-axis Low Interest --> High Interest
    y-axis Low Power --> High Power
    quadrant-1 Keep Satisfied
    quadrant-2 Manage Closely
    quadrant-3 Monitor
    quadrant-4 Keep Informed
    
    "Ban Giám đốc": [0.85, 0.90]
    "Đội ngũ BA & Dev": [0.80, 0.80]
    "Nhà cung cấp Cổng thanh toán": [0.35, 0.75]
    "Bộ phận Vận hành": [0.85, 0.45]
    "Khách hàng": [0.80, 0.30]
    "Tài xế": [0.75, 0.35]
    "Nhà cung cấp Dịch vụ Thông báo": [0.40, 0.20]
```
</details>
<details>
<summary><b>Bước 3: Vai trò, Mức độ quan trọng / Ảnh hưởng của Stakeholders và Mục đích Nghiệp vụ</b> [Bấm để xem]</summary>

#### 1. Bảng phân tích Vai trò, Mức độ ảnh hưởng và Kỳ vọng Hệ thống đáp ứng

| Stakeholder | Mức độ Quan trọng / Ảnh hưởng | Vai trò chính | Mục đích Nghiệp vụ (Business Goal) | Hệ thống CAB đáp ứng điều gì? |
| :--- | :--- | :--- | :--- | :--- |
| **Khách hàng (Customer)** | **Cao (High Impact)** | Người dùng dịch vụ cuối | Đặt xe nhanh chóng, di chuyển an toàn, minh bạch giá cả và trải nghiệm dịch vụ tiện lợi. | - Đăng ký/Đăng nhập, quản lý thông tin cá nhân.<br>- Nhập điểm đi/đến, chọn loại xe và xem trước giá tiền.<br>- Gửi yêu cầu đặt xe, theo dõi vị trí tài xế & trạng thái chuyến đi theo thời gian thực.<br>- Thanh toán linh hoạt (Tiền mặt / Thẻ / Ví điện tử).<br>- Xem lịch sử chuyến đi và đánh giá chất lượng tài xế. |
| **Tài xế (Driver)** | **Cao (High Impact)** | Đối tác cung cấp dịch vụ vận tải | Tối ưu thời gian chờ, tăng thu nhập, nhận chuyến xe minh bạch và hợp lý về vị trí. | - Quản lý hồ sơ cá nhân và thông tin phương tiện.<br>- Chủ động bật/tắt trạng thái sẵn sàng nhận chuyến.<br>- Nhận thông báo chuyến mới; chấp nhận hoặc từ chối chuyến đi.<br>- Cập nhật lộ trình chuyến đi (*Đã đến điểm đón, Đã đón khách, Đang di chuyển, Hoàn thành*).<br>- Định vị GPS liên tục để hệ thống ghép chuyến gần nhất. |
| **Nhân viên Vận hành (Operator / Admin)** | **Cao (High Importance)** | Quản lý & Giám sát hệ thống | Đảm bảo hệ thống vận hành liên tục, xử lý sự cố kịp thời và kiểm soát chất lượng dịch vụ. | - Cung cấp giao diện Admin Dashboard quản lý Khách hàng, Tài xế, Phương tiện.<br>- Giám sát các chuyến đi realtime, can thiệp xử lý chuyến lỗi/kẹt trạng thái.<br>- Tra cứu lịch sử giao dịch và phân quyền người dùng.<br>- Báo cáo thống kê số chuyến, doanh thu, tỷ lệ hủy và hiệu suất tài xế. |
| **Ban Giám đốc (Board of Directors)** | **Rất cao (Critical)** | Chủ đầu tư & Quyết định chiến lược | Tự động hóa vận hành, mở rộng quy mô kinh doanh, tối ưu chi phí và tăng doanh thu. | - Hệ thống hoạt động ổn định, có khả năng mở rộng độc lập khi tải tăng.<br>- Cung cấp số liệu báo cáo kinh doanh chính xác.<br>- Kiến trúc linh hoạt, cho phép mở rộng tính năng/dịch vụ mới trong tương lai. |
| **Nhà cung cấp Cổng thanh toán (Payment Gateway)** | **Trung bình (Medium)** | Đối tác tích hợp hạ tầng thanh toán | Xử lý giao dịch thanh toán điện tử an toàn, chính xác và đối soát minh bạch. | - Tích hợp API thanh toán không lưu dữ liệu thẻ nhạy cảm trên CAB System.<br>- Phản hồi trạng thái giao dịch (Thành công/Thất bại) tức thì.<br>- Hỗ trợ cơ chế thử lại (retry) khi giao dịch thất bại. |
| **Nhà cung cấp Dịch vụ Thông báo (Notification Provider)** | **Thấp - Trung bình (Low - Medium)** | Đối tác gửi tin nhắn/thông báo | Truyền tải thông điệp và trạng thái chuyến đi tới người dùng nhanh chóng. | - Tích hợp API gửi Push Notification / SMS / Email theo thời gian thực.<br>- Kiến trúc linh hoạt cho phép mở rộng thêm kênh thông báo mới mà không sửa toàn bộ hệ thống. |

---

#### 2. Mục đích Nghiệp vụ Tổng thể (Business Objectives Summary)

1. **Đối với Khách hàng:** Giải quyết triệt để bài toán "chờ đợi trong mơ hồ" bằng việc minh bạch hóa lộ trình, thời gian tài xế đến và giá cước.
2. **Đối với Tài xế:** Tối ưu hóa việc phân công chuyến đi bằng thuật toán ghép chuyến tự động dựa trên vị trí GPS, giảm thời gian chạy xe rỗng.
3. **Đối với Bộ phận Vận hành:** Chuyển đổi từ điều phối thủ công sang quản lý tự động hóa, giám sát tập trung toàn bộ dữ liệu chuyến đi và doanh thu.
4. **Đối với Doanh nghiệp (ABC):** Xây dựng nền tảng MVP vững chắc trong **7 tuần**, đáp ứng lượng tải lớn và sẵn sàng mở rộng các loại hình dịch vụ mới trong tương lai.
    
</details>
<details>
<summary><b>Bước 4. Xác Định Phạm Vi Dự Án MVP Trong 7 Tuần (MVP Scope Baseline)</b> [Bấm để xem]</summary>

### 4.1 Nguyên tắc Xác định Phạm vi (Scoping Principles)
- **Mục tiêu 7 tuần:** Tập trung hoàn thiện luồng nghiệp vụ cốt lõi: Khách đặt xe -> Ghép tài xế -> Thực hiện chuyến -> Tính cước & Thanh toán -> Quản trị cơ bản.
- **Quy tắc MVP:** Đảm bảo hệ thống hoạt động ổn định, phân tách module độc lập, loại bỏ các tính năng phức tạp ngoài phạm vi (như AI dự đoán, gợi ý thông minh, định giá động đa biến).

---

### 4.2 Danh mục Các Phân hệ Cốt lõi (Core Modules in MVP)

#### Module 1: Quản lý Xác thực & Phân quyền (Authentication & Authorization)
- Đăng ký và đăng nhập tài khoản cho Khách hàng và Tài xế (bằng Số điện thoại/Mật khẩu hoặc OTP).
- Đăng nhập và phân quyền truy cập cho Nhân viên vận hành/Quản trị viên (RBAC).
- Quản lý phiên làm việc, mã hóa mật khẩu và bảo mật thông tin đăng nhập.

#### Module 2: Quản lý Hồ sơ Người dùng (User & Driver Profile Management)
- **Khách hàng:** Cập nhật thông tin cá nhân (Họ tên, SĐT, Email), xem lịch sử chuyến đi.
- **Tài xế:** Cập nhật hồ sơ, thông tin phương tiện (Biển số xe, loại xe, màu xe), trạng thái xét duyệt hoạt động.
- **Quản trị viên:** Tra cứu danh sách tài xế, phê duyệt/tạo tài khoản tài xế mới và khóa/mở khóa tài khoản khi có vi phạm.

#### Module 3: Quản lý Trạng thái & Vị trí Tài xế (Driver Status & Geolocation Tracking)
- Bật/tắt trạng thái làm việc của tài xế (Sẵn sàng nhận chuyến / Đang bận / Ngoại tuyến).
- Thu thập và cập nhật tọa độ GPS định kỳ của tài xế khi đang ở trạng thái trực tuyến.
- Lưu trữ vị trí cuối cùng của tài xế phục vụ thuật toán tìm xe theo bán kính.

#### Module 4: Đặt xe & Điều phối Chuyến đi (Booking & Dispatching Engine)
- Tiếp nhận yêu cầu đặt chuyến từ khách hàng (Điểm đón, Điểm đến, Loại xe).
- Thuật toán ghép xe cơ bản dựa trên khoảng cách địa lý (tìm tài xế gần nhất đang sẵn sàng trong bán kính quy định).
- Cơ chế gửi yêu cầu nhận cuốc tới tài xế với thời gian chờ (timeout).
- Tự động chuyển yêu cầu sang tài xế tiếp theo nếu tài xế trước từ chối hoặc hết giờ phản hồi.
- Thông báo cho khách hàng khi tìm thấy tài xế hoặc khi không có xe nào nhận chuyến.

#### Module 5: Quản lý Tiến trình Chuyến đi (Trip Lifecycle Management)
- Máy trạng thái chuyến đi: Khởi tạo -> Đang tìm xe -> Đã nhận chuyến -> Đã đến điểm đón -> Đang di chuyển -> Hoàn thành / Hủy chuyến.
- Cho phép tài xế thao tác cập nhật từng bước trạng thái chuyến đi.
- Cho phép khách hàng và nhân viên vận hành theo dõi trạng thái và vị trí xe theo thời gian thực.
- Xử lý luồng hủy chuyến từ phía khách hàng hoặc tài xế theo quy tắc cơ bản.

#### Module 6: Tính cước & Thanh toán (Pricing & Payment Integration)
- Công thức tính cước cơ bản: Giá mở cửa + (Khoảng cách thực tế × Đơn giá/km) theo từng loại xe.
- Hỗ trợ 02 phương thức thanh toán: Tiền mặt trực tiếp và Tích hợp 01 Cổng thanh toán điện tử (Payment Gateway).
- Xử lý kết quả giao dịch thanh toán (Thành công / Thất bại) và ghi nhận lịch sử giao dịch không lưu trữ dữ liệu thẻ nhạy cảm.

#### Module 7: Quản lý Thông báo (Notification Service)
- Gửi thông báo đẩy (Push Notification/In-app) cho khách hàng và tài xế tại các mốc sự kiện chính của chuyến đi.
- Tách biệt module thông báo độc lập để đảm bảo nghẽn thông báo không gây dừng luồng đặt xe.

#### Module 8: Cổng Quản trị Vận hành & Báo cáo Cơ bản (Admin Portal & Basic Reports)
- Dashboard theo dõi danh sách các chuyến đi đang diễn ra và lịch sử sự cố.
- Chức năng hỗ trợ can thiệp/hủy cuốc khi phát sinh lỗi hệ thống hoặc khiếu nại.
- Báo cáo thống kê cơ bản: Tổng số chuyến đi, doanh thu theo ngày/tuần, tỷ lệ hoàn thành và tỷ lệ hủy chuyến.

---

### 4.3 Bảng Tổng hợp Phạm vi (In-Scope vs Out-of-Scope)

| STT | Phân hệ / Nghiệp vụ | Trong phạm vi MVP (7 tuần) | 
| :-- | :--- | :--- | 
| 1 | **Xác thực** | Đăng ký, đăng nhập chuẩn (Phone/Password/OTP) | 
| 2 | **Điều phối xe** | Tìm theo bán kính gần nhất, chuyển lượt tuần tự | 
| 3 | **Định giá (Pricing)** | Giá cố định theo km và loại xe cơ bản | 
| 4 | **Thanh toán** | Tiền mặt + Tích hợp 01 cổng thanh toán online | 
| 5 | **Thông báo** | Push Notification / In-app cơ bản | 
| 6 | **Báo cáo** | Thống kê số lượng chuyến, doanh thu, tỷ lệ hủy | 

</details>
<details>
<summary><b>Bước 5. Phân Tích Yêu Cầu Nghiệp Vụ & Phạm Vi Bảng MVP (Business Requirements & MVP Scope Table)</b> [Bấm để xem]</summary>

### Bảng Phân tích Yêu cầu Nghiệp vụ (Business Requirements & MVP Scope Table)

Dựa trên yêu cầu của Công ty ABC, các mong muốn vận hành được chuyển đổi thành các Yêu cầu Nghiệp vụ (BR) cốt lõi và phân định phạm vi triển khai trong giai đoạn MVP (7 tuần) và phiên bản Tương lai (Phase 2).

| Nhóm Nghiệp vụ | Mã BR | Yêu cầu Nghiệp vụ (Business Requirement) | Mô tả Chi tiết Nghiệp vụ | Phạm vi MVP (7 tuần) | Giai đoạn Tương lai (Phase 2) |
| :--- | :--- | :--- | :--- | :---: | :---: |
| **Quản lý Tài khoản & Hồ sơ** | BR-01 | Quản lý Tài khoản Khách hàng | Cho phép Khách hàng đăng ký, đăng nhập, xác thực tài khoản và cập nhật thông tin cá nhân. | **[X] Co-Core** | |
| | BR-02 | Quản lý Tài khoản & Hồ sơ Tài xế | Cho phép Tài xế/Nhân viên vận hành tạo tài khoản, cập nhật thông tin cá nhân, hồ sơ pháp lý, thông tin phương tiện và loại xe. | **[X] Co-Core** | |
| | BR-03 | Phân quyền Quản trị (RBAC) | Phân quyền chặt chẽ các thao tác quản trị; Nhân viên vận hành thông thường không được thực hiện các tác vụ nhạy cảm. | **[X] Co-Core** | |
| **Đặt xe & Tìm tài xế** | BR-04 | Đặt xe & Chọn Dịch vụ | Cho phép Khách hàng nhập điểm đón, điểm đến, hệ thống tính trước khoảng cách/giá tiền và cho phép khách chọn loại dịch vụ xe. | **[X] Co-Core** | |
| | BR-05 | Khớp chuyến Tự động (Matching Engine) | Tự động định vị GPS, tìm kiếm và ưu tiên gán chuyến cho tài xế phù hợp gần nhất đang ở trạng thái sẵn sàng. | **[X] Co-Core** | |
| | BR-06 | Xử lý Từ chối / Timeout nhận chuyến | Tự động chuyển tiếp chuyến đi cho tài xế khác nếu tài xế đầu tiên từ chối hoặc hết thời gian phản hồi (timeout) mà không bắt khách tạo lại yêu cầu. | **[X] Co-Core** | |
| | BR-07 | Xử lý Không tìm thấy Tài xế | Đưa ra thông báo rõ ràng cho Khách hàng khi đã hết tài xế khả dụng hoặc tìm kiếm thất bại sau thời gian quy định. | **[X] Co-Core** | |
| | BR-08 | Thuật toán Tăng giá & Ưu tiên nâng cao | Áp dụng Dynamic Pricing (tăng giá giờ cao điểm) và thuật toán phân công nâng cao theo hiệu suất/đánh giá tài xế. | | **[X] Post-MVP** |
| **Thực hiện & Theo dõi Chuyến** | BR-09 | Quản lý Trạng thái Sẵn sàng Tài xế | Cho phép Tài xế chủ động bật/tắt trạng thái sẵn sàng làm việc để nhận thông báo chuyến xe mới. | **[X] Co-Core** | |
| | BR-10 | Quản lý Tiến độ Chuyến đi (Trip Lifecycle) | Hỗ trợ Tài xế cập nhật lần lượt các trạng thái: *Đã nhận chuyến &rarr; Đã đến điểm đón &rarr; Đã đón khách &rarr; Đang di chuyển &rarr; Hoàn thành*. | **[X] Co-Core** | |
| | BR-11 | Theo dõi Hành trình Realtime (Tracking) | Ghi nhận vị trí GPS thời gian thực của Tài xế để Khách hàng theo dõi vị trí xe, lộ trình di chuyển và thời gian dự kiến đến (ETA). | **[X] Co-Core** | |
| | BR-12 | Xử lý Mất kết nối Mạng (Offline Handling) | Cơ chế lưu cache trên ứng dụng di động để tự động đồng bộ lại trạng thái khi thiết bị khôi phục kết nối mạng. | | **[X] Post-MVP** |
| **Tính cước & Thanh toán** | BR-13 | Tính cước Chuyến đi | Tự động tính tổng tiền cước sau khi kết thúc chuyến dựa trên loại xe, khoảng cách thực tế và bảng cước cố định. | **[X] Co-Core** | |
| | BR-14 | Thanh toán Tiền mặt | Cho phép Khách hàng chọn thanh toán trực tiếp bằng tiền mặt cho Tài xế sau khi chuyến đi hoàn thành. | **[X] Co-Core** | |
| | BR-15 | Thanh toán Điện tử qua Cổng bên thứ ba | Tích hợp API với 01 Cổng thanh toán bên thứ ba (Ví/Thẻ) để xử lý thanh toán điện tử; không lưu thông tin thẻ nhạy cảm trên hệ thống CAB. | **[X] Co-Core** | |
| | BR-16 | Xử lý Lỗi Thanh toán Điện tử | Thông báo lỗi thanh toán rõ ràng cho Khách hàng và hỗ trợ cơ chế thanh toán lại (retry) hoặc chuyển sang tiền mặt. | **[X] Co-Core** | |
| | BR-17 | Thêm nhiều Phương thức Thanh toán mới | Tích hợp đa dạng các Ví điện tử (Momo, ZaloPay, ShopeePay) và thẻ quốc tế Visa/Mastercard trực tiếp. | | **[X] Post-MVP** |
| **Thông báo & Đánh giá** | BR-18 | Gửi Thông báo Trạng thái (Notifications) | Tự động gửi thông báo đẩy (Push Notification) cho Khách hàng và Tài xế tương ứng với các mốc thay đổi trạng thái chuyến đi & thanh toán. | **[X] Co-Core** | |
| | BR-19 | Đánh giá & Phản hồi Sau Chuyến đi | Cho phép Khách hàng chấm điểm sao (1-5 star) và để lại phản hồi về chất lượng phục vụ của Tài xế sau khi hoàn thành chuyến đi. | **[X] Co-Core** | |
| | BR-20 | Mở rộng Kênh Thông báo (SMS/Email) | Bổ sung thêm các kênh gửi thông báo tự động qua tin nhắn SMS OTP và Email xác nhận hóa đơn. | | **[X] Post-MVP** |
| **Vận hành & Báo cáo** | BR-21 | Dashboard Quản trị & Giám sát Realtime | Cung cấp giao diện Admin Dashboard cho Nhân viên vận hành quản lý Khách hàng, Tài xế, Phương tiện, tra cứu lịch sử và giám sát các chuyến đi đang diễn ra. | **[X] Co-Core** | |
| | BR-22 | Báo cáo Thống kê Cơ bản | Xuất các báo cáo theo thời gian về: Tổng số chuyến đi, Doanh thu, Tỷ lệ chuyến hoàn thành và Tỷ lệ hủy chuyến. | **[X] Co-Core** | |
| | BR-23 | Báo cáo Hiệu quả Vận hành Nâng cao | Thống kê chi tiết hiệu suất làm việc từng tài xế, biểu đồ nhiệt (Heatmap) khu vực nhu cầu cao và dự báo xu hướng vận hành. | | **[X] Post-MVP** |
| **Kiến trúc & Bảo mật** | BR-24 | Thiết kế Mô-đun Độc lập (Microservices/Modular) | Tách biệt các thành phần (Thanh toán, Thông báo, Khớp chuyến) để có thể mở rộng độc lập và tránh lỗi dây chuyền làm sập toàn bộ ứng dụng. | **[X] Co-Core** | |
| | BR-25 | Nhật ký Thao tác (Audit Trail) | Lưu vết (Log) toàn bộ các thao tác quản trị quan trọng và giao dịch thanh toán để phục vụ công tác tra soát khi xảy ra sự cố. | **[X] Co-Core** | |

</details>
<details>
<summary><b>Bước 6. Phân Rã Yêu Cầu Chức Năng (Functional Requirements Breakdown)</b> [Bấm để xem]</summary>

### Phân Rã Chi Tiết Yêu Cầu Chức Năng (Functional Requirements Breakdown)

Dựa trên các Yêu cầu Nghiệp vụ (BR), dưới đây là chi tiết các chức năng hệ thống cần xử lý cho từng luồng nghiệp vụ cốt lõi:

#### 1. Module Đặt Xe & Tìm Tài Xế (Ride Dispatch & Matching Engine)

* **FR-MATCH-01 (Xác định vị trí Khách hàng):** Hệ thống truy xuất tọa độ GPS điểm đón và điểm đến do khách hàng cung cấp (hoặc tự động lấy từ vị trí thiết bị).
* **FR-MATCH-02 (Lọc danh sách Tài xế khả dụng):**
    * Hệ thống quét danh sách tài xế trong bán kính quy định (ví dụ: 3km - 5km).
    * Điều kiện lọc: Tài xế đang ở trạng thái **Sẵn sàng (Online)**, loại phương tiện trùng khớp với yêu cầu của khách hàng.
* **FR-MATCH-03 (Thuật toán Điểm ưu tiên & Đề xuất):**
    * Xếp hạng tài xế khả dụng dựa trên: Khoảng cách ngắn nhất đến điểm đón, thời gian di chuyển dự kiến (ETA), điểm đánh giá (Rating) cao và tỷ lệ nhận chuyến tốt.
* **FR-MATCH-04 (Gửi yêu cầu & Chờ phản hồi):**
    * Gửi thông báo mời nhận chuyến đến Tài xế có điểm ưu tiên cao nhất kèm đếm ngược thời gian (Timeout, ví dụ: 15 giây).
    * **Trường hợp Tài xế Chấp nhận:** Chuyển trạng thái chuyến đi sang *Đã nhận chuyến*, khóa trạng thái tài xế (Bận), gửi thông báo thông tin tài xế cho khách hàng.
    * **Trường hợp Tài xế Từ chối hoặc Hết giờ (Timeout):** Hệ thống tự động loại tài xế này khỏi lượt tìm kiếm hiện tại, cập nhật danh sách và tự động chuyển gửi yêu cầu đến Tài xế ưu tiên tiếp theo mà không bắt Khách hàng tạo lại yêu cầu đặt xe.
* **FR-MATCH-05 (Xử lý không tìm được tài xế):** Nếu quá thời gian tìm kiếm hoặc đã quét hết danh sách tài xế khả dụng mà không có ai nhận, hệ thống gửi thông báo *"Hiện tại không tìm thấy tài xế, vui lòng thử lại sau"* đến Khách hàng và hủy yêu cầu đặt xe.

#### 2. Module Quản Lý Tiến Độ Chuyến Đi (Trip Lifecycle & Live Tracking)

* **FR-TRIP-01 (Cập nhật tiến độ hành trình):** Cung cấp các nút thao tác trên ứng dụng Tài xế để cập nhật trạng thái theo thứ tự:
    1. *Đã đến điểm đón*: Gửi thông báo báo khách hàng ra xe.
    2. *Đã đón khách*: Bắt đầu tính giờ/khoảng cách hành trình thực tế.
    3. *Đang di chuyển*: Cập nhật lộ trình realtime.
    4. *Hoàn thành chuyến*: Chốt chuyến đi và chuyển sang bước tính cước/thanh toán.
* **FR-TRIP-02 (Theo dõi vị trí Realtime):** Hệ thống thu thập tọa độ GPS của Tài xế định kỳ (mỗi 3-5 giây) và hiển thị trực quan biểu tượng xe di chuyển trên bản đồ phía Khách hàng kèm thời gian dự kiến đến (ETA).

#### 3. Module Tính Cước & Thanh Toán (Pricing & Payment)

* **FR-PAY-01 (Tính cước tự động):** Khi kết thúc chuyến, hệ thống tính cước dựa trên: Bảng cước loại xe + Khoảng cách thực tế di chuyển + Phụ phí (nếu có).
* **FR-PAY-02 (Xử lý Thanh toán Tiền mặt):** Hiển thị số tiền cần thu trên app Tài xế và Khách hàng; Tài xế xác nhận *"Đã thu tiền mặt"* để đóng chuyến đi.
* **FR-PAY-03 (Xử lý Thanh toán Điện tử qua Cổng thứ 3):**
    * Gọi API sang Cổng thanh toán để trừ tiền/khóa tiền khoản thanh toán của Khách hàng.
    * **Thành công:** Xác nhận hoàn tất thanh toán, cập nhật trạng thái hóa đơn.
    * **Thất bại:** Gửi thông báo lỗi cho Khách hàng, cung cấp tùy chọn *Thử lại giao dịch (Retry)* hoặc *Chuyển sang thanh toán tiền mặt*.
* **FR-PAY-04 (An toàn dữ liệu):** Không lưu trữ bất kỳ thông tin nhạy cảm nào về thẻ/tài khoản ngân hàng của người dùng trên hệ thống CAB.

#### 4. Module Đánh Giá & Thông Báo (Feedback & Notifications)

* **FR-NOTI-01 (Hệ thống Thông báo Đẩy - Push Notification):** Tự động bắn thông báo cho Khách hàng/Tài xế ứng với các sự kiện: *Tìm thấy tài xế, Xe đã đến điểm đón, Chuyến đi hoàn thành, Thanh toán thành công/thất bại*.
* **FR-RATING-01 (Đánh giá sau chuyến đi):** Cho phép Khách hàng chấm điểm (1 đến 5 sao) và chọn các nhãn góp ý/viết nhận xét về Tài xế sau khi hoàn thành chuyến.

#### 5. Module Quản Trị & Giám Sát Vận Hành (Admin & Operations Management)

* **FR-ADM-01 (Quản lý Hồ sơ & Phân quyền):** Cho phép Nhân viên vận hành phê duyệt/khóa tài khoản Khách hàng, Tài xế, Phương tiện; Phân quyền thao tác theo nhóm quyền (RBAC).
* **FR-ADM-02 (Giám sát Chuyến đi Realtime):** Hiển thị bản đồ tổng quan các chuyến đi đang thực hiện, hỗ trợ Nhân viên vận hành can thiệp hủy chuyến hoặc gán lại tài xế khi xảy ra sự cố khẩn cấp.
* **FR-ADM-03 (Báo cáo Thống kê):** Xuất các biểu đồ & bảng biểu báo cáo về: Doanh thu theo ngày/tần suất, Tổng số chuyến, Tỷ lệ hủy chuyến, và Báo cáo hiệu suất từng tài xế.

</details>
