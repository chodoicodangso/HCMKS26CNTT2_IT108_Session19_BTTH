**Phần 1 – Nhận diện rủi ro và xử lý sự cố**  
**Tình huống 1:** Là tấn công **Phishing (Typosquatting)**. Dấu hiệu giả mạo là tên miền githuh-security.com sai chữ "b" thành chữ "h".  
**Tình huống 2:** Là cạm bẫy **Mã độc (Malware)** ngụy trang phần mềm Crack. Việc yêu cầu "tắt Windows Defender" cực kỳ nguy hiểm vì nó gỡ bỏ lá chắn bảo vệ, tạo điều kiện cho mã độc lây nhiễm và phá hoại hệ thống.  
**Quy tắc 5 KHÔNG:**  
Tình huống 1: KHÔNG bấm vào đường link lạ/khả nghi.  
Tình huống 2: KHÔNG tải/chạy phần mềm crack.  
**4 Bước Cấp cứu:**  
Ngắt kết nối mạng ngay lập tức.  
Bật lại Windows Defender và quét diệt virus toàn bộ hệ thống.  
Dùng thiết bị khác an toàn để đổi mật khẩu các tài khoản.  
Theo dõi và báo cáo bộ phận IT/Bảo mật.  
**Phần 2 – Chuyển sang Password Manager**  
**Hậu quả & Loại tấn công:** 2 tài khoản (GitHub tổ chức, Vercel) sẽ bị hacker đăng nhập trái phép do dùng chung mật khẩu. Đây là kiểu tấn công **Credential Stuffing** (hoặc Password Reuse).  
**Zero-Knowledge Architecture:** Dữ liệu mật khẩu được mã hóa tại thiết bị cá nhân bằng Master Password trước khi gửi lên máy chủ. Hacker xâm nhập máy chủ Bitwarden chỉ lấy được dữ liệu đã mã hóa, không thể đọc được mật khẩu thật.  
**Cấu hình Generator:** Độ dài: **16+** \| Chữ hoa: **Có** \| Chữ thường: **Có** \| Chữ số: **Có** \| Ký tự đặc biệt: **Có**.  
**Phần 3 – Kích hoạt 2FA cho tài khoản GitHub tổ chức**  
**Chọn Authenticator (TOTP) thay vì SMS OTP:** App tạo mã trực tiếp offline an toàn hơn. **2 nhược điểm của SMS OTP:**  
Dễ bị tấn công cướp SIM (SIM Swapping) hoặc nghe lén SS7.  
Phụ thuộc sóng di động, ra nước ngoài/mất sóng sẽ không nhận được mã  
**Các bước Google Authenticator:** 1\. Mở cài đặt bảo mật GitHub \-\> 2\. Chọn kích hoạt Authenticator App \-\> 3\. Mở app Google Authenticator \-\> 4\. Quét mã QR \-\> 5\. Nhập mã 6 số vào GitHub.  
**Lưu trữ 10 mã khôi phục:**  
**NÊN:** In ra giấy cất két sắt, hoặc lưu trong Password Manager mã hóa.  
**KHÔNG NÊN:** Chụp màn hình, lưu file chữ (plaintext) trên máy, gửi qua email/tin nhắn chat.  
**Phần 4 – Bảo vệ Secrets trước khi push code**  
**2 giá trị Secrets đang hardcode:** sk-proj-abc123456789 và SmartCampus@2026.  
**Viết lại code:** const API\_KEY \= process.env.API\_KEY; const DB\_PASSWORD \= process.env.DB\_PASSWORD;  
**Nội dung các file:**  
File .env: API\_KEY="sk-proj-abc123456789" và  
DB\_PASSWORD="SmartCampus@2026"  
File .gitignore: .env  
File .env.example: API\_KEY= và DB\_PASSWORD=  
**4 Bước Kiểm tra trước khi Push:**  
Bước 1: Kiểm tra file .gitignore đã chặn file .env chưa.  
Bước 2: Dùng git status đảm bảo file .env không nằm trong danh sách chuẩn bị commit.  
Bước 3: Dùng git diff xem lại code đảm bảo không còn Secret bị hardcode.  
Bước 4: Thực hiện git push an toàn.