# Group Report — Day 02

## Thành viên nhóm

| STT | Họ và tên | Mã học viên | Vai trò trong nhóm |
|-----|-----------|-------------|--------------------|
| 1   | Lã Phan Hoài An | 2A202601846 | Nhóm trưởng |
| 2   | Nguyễn Hữu Huy | 2A202601220 | Thành viên |
| 3   | Nguyễn Nam Phong | 2A202601320 | Thành viên |
| 4   | Nguyễn Châu Thanh | 2A202601382 | Thành viên |
| 5   | Lê Hồ Quang Huy | 2A202602026 | Thành viên |

---

## Phase 3: Nhật ký hội tụ (Group Convergence)
*   **Các vấn đề nhóm đã đem ra bàn luận:**
    1. Ý tưởng của Hoài An: Trôi tin nhắn quan trọng trong group học tập.
    2. Ý tưởng của Hữu Huy: Lên kế hoạch và chia tiền sau khi đi chơi.
    3. Ý tưởng của Nam Phong: Tổng hợp Meeting Notes sau buổi họp.
    4. Ý tưởng của Châu Thanh: Tìm kiếm tài liệu chuyên ngành khó khăn.
    5. Ý tưởng của Quang Huy: Nhắc nhở deadline bài tập bị trôi.
*   **Vấn đề nhóm quyết định CHỌN:** Lên kế hoạch và chia tiền sau khi đi chơi (Vấn đề giả định).
*   **Lý do chọn:** Sau khi bàn luận, nhóm nhận thấy đây là "nỗi đau" chung mà tất cả các thành viên đều từng trải qua. Nút thắt rất rõ ràng (nhập liệu thủ công dễ sai sót và tâm lý ngại đi đòi nợ). Metric để đo lường cũng rất dễ xác định bằng thời gian thực tế.

---

## Phase 4: Kiểm chứng thực tế (Validation & Research)
*   **Phương pháp:** Phỏng vấn nhanh 5 bạn bất kì trong trường về trường hợp chia tiền sau khi đi chơi..
*   **Kết quả thu được:**
    *   100% người được hỏi đều thừa nhận việc tính toán chia bill thủ công trên Excel rất mất thời gian (thường tốn 15-20 phút cho nhóm 10 người).
    *   4/5 người cho biết họ cảm thấy ngại khi phải copy số tiền và nhắn tin đi đòi từng người, đôi khi quên thu tiền dẫn đến tự bù lỗ.
*   **Kết luận sau kiểm chứng:** Bài toán hoàn toàn có thật, nhu cầu giải quyết rất cao. Nhóm quyết định giữ nguyên mục tiêu ban đầu là giảm thời gian tính toán và tạo tin nhắn tự động.

---

## Phase 5: Problem Statement & Workflow 

**1. Khung Vấn Đề (Problem Statement)**
*   **Actor (Ai bị):** Trưởng nhóm / Người đứng ra thanh toán hộ trong các buổi đi chơi.
*   **Workflow hiện tại:** (1) Gom hóa đơn -> (2) Nhập liệu từng khoản vào Excel -> (3) Gán tên người phải trả -> (4) Tính tổng tiền -> (5) Nhắn tin đòi nợ từng người.
*   **Bottleneck (Nút thắt):** Bước nhập liệu thủ công dễ nhầm lẫn và bước nhắn tin đòi nợ gây tốn thời gian, tâm lý ngại ngùng.
*   **Impact (Hậu quả):** Mất thời gian, rủi ro tự bù lỗ do tính nhầm/quên thu tiền, dễ làm mất lòng nhau.
*   **Success Metric (Mục tiêu đo lường):** Giảm thời gian chia tiền và gửi tin nhắn nhắc nợ từ **20 phút** xuống **< 2 phút**. Độ chính xác đạt 100%.
*   **Boundary (Giới hạn):** 
    *   AI CHỈ đọc hóa đơn, chia tiền và soạn tin nhắn nhắc nợ. 
    *   AI KHÔNG được tự động trừ tiền trong thẻ ngân hàng của người dùng. Bắt buộc phải có bước Human-in-the-loop (người dùng duyệt lại bảng chia tiền) trước khi gửi tin nhắn.

**2. Sơ đồ Workflow (Trước và Sau khi có AI)**

*   **Workflow Trước (20 phút):** 
    `[Gom bill: 2']` → `[Nhập Excel thủ công: 10'] (Nút thắt)` → `[Kiểm tra lại: 3']` → `[Nhắn tin đòi từng người: 5'] (Nút thắt)`

*   **Workflow Sau (2 phút):** 
    `[Chụp bill gửi Bot]` → `[AI tự nhận diện món, chia tiền & tạo sẵn tin nhắn tag tên vào group]` → `[Human-in-the-loop: Trưởng nhóm duyệt lại thông tin (1')]` → `[Bấm gửi: 1']`

---

## Phase 6: So sánh giải pháp & Quyết định cuối cùng

**1. Đánh giá độ phù hợp (Rule vs Workflow vs Agent)**
*   **Nếu dùng Rule (Logic cứng - Code app chia tiền truyền thống):** Khó thực hiện vì mỗi bill (hóa đơn) có format khác nhau, code cứng không thể đọc chữ từ ảnh (OCR) một cách linh hoạt. Phải bắt người dùng tự nhập tay lại.
*   **Nếu dùng Agent (AI tự trị):** Không cần thiết và quá rủi ro. Việc liên quan đến tiền bạc không thể giao phó hoàn toàn cho AI tự ra quyết định và tự động đi đòi tiền mà không có người duyệt.
*   **Nếu dùng Workflow (Quy trình tự động hóa có AI):** Cực kỳ phù hợp. AI (Vision Model) xử lý tốt khâu nhận diện chữ trên bill không có cấu trúc cố định, sau đó đưa kết quả cho con người duyệt và tự động hóa khâu tạo tin nhắn.

**2. Quyết định (Decision)**
*   **Nhóm chọn:** **Workflow** (kết hợp AI Vision để đọc ảnh).
*   **Quyết định GO hay NO-GO:** **GO**
*   **Lý do chốt:** Vấn đề có tính ứng dụng cao, metric đo lường rõ ràng. Việc dùng Workflow kết hợp bước duyệt của con người (Human-in-the-loop) giải quyết đúng nút thắt tốn thời gian mà vẫn đảm bảo an toàn về mặt tiền bạc.
