# GIẢI PHÁP TỔ CHỨC ENTERPRISE WORKSPACE & GIAO TIẾP BẤT ĐỒNG BỘ — DỰ ÁN BÃI ĐỖ XE THÔNG MINH

---

## PHẦN 1: SƠ ĐỒ KIẾN TRÚC KÊNH (CHANNEL ARCHITECTURE)

Để giải quyết tình trạng thông tin kỹ thuật bị lẫn lộn với tin nhắn tán gẫu và meme trên Messenger, không gian làm việc trên Lark/Slack được phân tách rành mạch thành các Channel chuyên đề sau:

### 1. Danh sách Channels & Quy định nội dung

* **`#01-thong-bao-chung` (Announcements)**
* *Mục đích:* Phát sóng các thông báo tối quan trọng từ Trưởng nhóm, mốc deadline cốt lõi, lịch họp toàn dự án và các quyết định kiến trúc chính thức.
* *Quy định đăng bài:* **Hạn chế nghiêm ngặt**. Chỉ Trưởng nhóm hoặc Thư ký dự án mới có quyền đăng bài (`Post`). Thành viên khác chỉ được thả cảm xúc (React).


* **`#02-ky-thuat-cam-bien` (Technical & IoT)**
* *Mục đích:* Nơi các lập trình viên và kỹ sư phần cứng trao đổi chuyên sâu về sơ đồ mạch, mã nguồn tích hợp cảm biến, xử lý lỗi API và thuật toán bãi đỗ xe.
* *Quy định đăng bài:* Mọi thảo luận về một lỗi (bug) cụ thể hoặc một tính năng mới bắt buộc phải được đưa vào **Thread (Luồng trả lời riêng)** của tin nhắn gốc.


* **`#03-quan-ly-tien-do` (Project Management)**
* *Mục đích:* Cập nhật tiến độ hoàn thành công việc, báo cáo Daily Standup, chia sẻ bảng phân công task và theo dõi trạng thái hoàn thành deadline của từng thành viên.
* *Quy định đăng bài:* Thành viên tự động cập nhật tiến độ công việc của mình tại đây theo khung giờ quy định trong ngày.


* **`#04-giai-tri-watercooler` (Off-topic & Memes)**
* *Mục đích:* Không gian tự do để chia sẻ ảnh chế (memes), câu chuyện vui, link giải trí hoặc tán gẫu xả stress.
* *Quy định đăng bài:* Tuyệt đối mọi nội dung giải trí, hình ảnh hài hước không liên quan đến đồ án phải được gom gọn vào kênh này, giữ cho các kênh chuyên môn hoàn toàn sạch sẽ.



---

## PHẦN 2: BẢN QUY ƯỚC GIAO TIẾP VÀ XỬ LÝ SỰ CỐ NHÀ PHÁT TRIỂN (COMMUNICATION PROTOCOL)

### 1. Ba quy tắc vàng tránh No-Hello Trap và Spam `@all`

* **Quy tắc 1: Triệt tiêu No-Hello Trap (Cung cấp đầy đủ ngữ cảnh ngay từ tin nhắn đầu tiên)**
* *Sai:* Nhắn tin *"Alo bạn ơi"*, *"Cho mình hỏi tý"* rồi ngồi chờ người khác đáp lại mới đặt câu hỏi. Thao tác này làm mất thời gian của cả hai phía.
* *Đúng:* Gom toàn bộ thông tin thành 1 khối (Context-First): **Vấn đề là gì + Đang gặp ở file/module nào + Hình ảnh lỗi/Log kèm theo**. Người nhận khi rảnh có thể đọc và hỗ trợ ngay lập tức dù không online cùng thời điểm.


* **Quy tắc 2: Kỷ luật Threading (Reply in Thread để giữ khung chat sạch đẹp)**
* *Nguyên tắc:* Bất kỳ phản hồi nào mang tính chất chi tiết, tranh luận sâu hoặc giải quyết một chủ đề cụ thể đều phải bấm vào **Reply in Thread**.
* *Lợi ích:* Kênh chính (`Main Channel`) chỉ hiển thị các đầu mục thông tin lớn, không bị che lấp bởi hàng chục dòng chat qua lại, giúp thành viên mới dễ dàng bắt kịp thông tin.


* **Quy tắc 3: Xử lý triệt để Spam `@all` và Tôn trọng giờ nghỉ (Anti-Spam & Schedule Send)**
* *Nguyên tắc:* Cấm tuyệt đối lạm dụng thẻ `@all` hoặc `@channel` cho các việc cá nhân hoặc nhắc nhở tiến độ thông thường. Chỉ tag đích danh (`@tên_thành_viên`) người chịu trách nhiệm trực tiếp.
* *Xử lý giờ khuya:* Khi phát sinh công việc cần nhắc nhở vào đêm muộn hoặc ngoài giờ hành chính, bắt buộc phải sử dụng tính năng **Schedule Send (Hẹn giờ gửi)** để tin nhắn tự động phát vào sáng hôm sau, không làm phiền không gian nghỉ ngơi của nhóm.



### 2. Giải pháp bảo vệ lập trình viên khỏi việc "Bị ép rep ngay lập tức" (Deep Work Protection)

Lập trình viên khi đang gõ code đòi hỏi độ tập trung cao độ (Deep Work); việc bị gián đoạn liên tục bởi thông báo chat sẽ làm giảm năng suất nghiêm trọng và dễ sinh ra lỗi logic. Giải pháp áp dụng cho nhóm:

* **Khung giờ tập trung (Focus Hours):** Thiết lập các khoảng thời gian lập trình viên bật chế độ **Do Not Disturb (Không làm phiền)** trên hệ thống Workspace.
* **Cam kết thời gian phản hồi (SLA bất đồng bộ):** Thống nhất trong nhóm rằng các tin nhắn hỏi đáp công việc **không bắt buộc phải phản hồi tức thì (real-time)** trong vòng 1-2 phút như Messenger, mà có khoảng thời gian phản hồi hợp lý (trong vòng 2–4 tiếng). Điều này giúp lập trình viên chủ động hoàn thành dở dang đoạn code của mình rồi mới quay sang hỗ trợ đồng đội.