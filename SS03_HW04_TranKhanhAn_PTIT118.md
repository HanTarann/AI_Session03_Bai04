# BÀI TẬP VỀ NHÀ: SESSION 3 - BÀI 4
**Họ và tên:** Trần Khánh An  
**Mã sinh viên:** PTIT118  
**Tên file:** SS03_HW04_TranKhanhAn_PTIT118.md

---

## ĐÁP ÁN LỰA CHỌN: Phương án C

---

## I. PHÂN TÍCH CHI TIẾT TẠI SAO PHƯƠNG ÁN C LÀ TỐI ƯU NHẤT

Phương án C thể hiện chính xác tư duy cốt lõi của kỹ thuật **Iterative Prompting (Prompt lặp và tối ưu)**, một kỹ năng bắt buộc phải có khi làm việc với AI. Quy trình này diễn ra như sau:

1. **Đánh giá (Evaluate):** Người dùng không mù quáng chấp nhận ngay kết quả của AI. Thay vào đó, họ đánh giá đoạn code do AI trả về và nhận thấy rằng dù code chạy đúng (kiểm tra được số nguyên tố) nhưng hiệu năng (Performance) lại không đạt yêu cầu.
2. **Nhận diện lỗi (Identify):** Người dùng chỉ ra được điểm yếu cốt lõi trong logic của AI: Việc sử dụng vòng lặp từ `2` đến `n-1` khiến độ phức tạp thuật toán là O(n), dẫn đến tốc độ thực thi rất chậm khi xử lý các số nguyên lớn.
3. **Tinh chỉnh (Refine):** Thay vì bắt đầu lại từ đầu, người dùng tiếp tục hội thoại trên cùng một phiên chat (để giữ nguyên ngữ cảnh - context) và cung cấp chỉ dẫn bổ sung cực kỳ cụ thể: Yêu cầu AI đổi giới hạn vòng lặp thành `Math.sqrt(n)` để giảm độ phức tạp xuống O(sqrt(n)). 

Bằng cách này, AI hiểu được chính xác mình sai ở đâu và cần sửa thế nào dựa trên bản nháp (draft) ban đầu, từ đó trả về đoạn code tối ưu 100% đúng mong muốn của người dùng.

---

## II. PHÂN TÍCH TẠI SAO CÁC PHƯƠNG ÁN KHÁC THẤT BẠI

### 1. Phương án A: Bỏ cuộc và tự viết lại bằng tay
* **Lý do thất bại:** Phương án này đi ngược lại hoàn toàn với mục đích ứng dụng AI vào công việc. Khác với công cụ tìm kiếm truyền thống, AI tạo sinh (Generative AI) hoạt động theo nguyên lý "Cộng tác" (Copilot). Kết quả đầu tiên của AI thường chỉ là một **bản nháp (draft)**. Việc bỏ cuộc ngay lần thử đầu tiên chứng tỏ người dùng thiếu kỹ năng điều hướng AI và làm lãng phí một công cụ hỗ trợ đắc lực.

### 2. Phương án B: Mở phiên chat mới và dán lại prompt cũ (có viết hoa)
* **Lý do thất bại:** Đây là một sai lầm rất phổ biến của người mới sử dụng AI (Tư duy "Thử vận may"). 
    * Thứ nhất, khi mở phiên chat mới, AI sẽ **mất toàn bộ ngữ cảnh (Context)** của cuộc trò chuyện trước đó, nó không biết đoạn code trước đó là gì để mà sửa.
    * Thứ hai, việc lặp lại một câu lệnh y hệt (chỉ thay đổi hình thức như viết hoa/viết đậm) sẽ không cung cấp thêm bất kỳ **Ràng buộc (Constraint)** hay thông tin logic mới nào cho AI. Do đó, khả năng rất cao AI sẽ tiếp tục sinh ra một đoạn code chạy từ `2` đến `n-1` y như cũ. Câu nói "Sự điên rồ là lặp đi lặp lại một việc và mong chờ những kết quả khác nhau" diễn tả chính xác sai lầm của phương án này.
