# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

> Đổi tên file này thành `MSSV_HoTen.md` của bạn, ví dụ `2A20260000_NguyenVanAn.md`, rồi điền từng mục. Xoá các dòng hướng dẫn in nghiêng khi xong.

- **MSSV:** 2A202603846
- **Họ và tên:** Nguyễn Tấn Châu
- **SEED** (in ở ô đầu notebook): 9135

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| [`day01_lab.ipynb`](day01_lab.ipynb) — notebook đã chạy, còn output | Có |
| [`lab1_report.json`](lab1_report.json) — do ô "Báo cáo cuối" sinh ra | Có |
| [`hand_calc.jpg`](hand_calc.jpg) — ảnh tính tay có các bước | Có |

## 2. Kết quả chính

*Chép bảng so sánh cuối Phần 5 (F1 test, F1 SUB 40, p95 ms/tin, USD/1k tin) của chính bạn.*

## 3. Dự đoán và thực tế

Dự đoán 1: lr = 50 (Thí nghiệm 1.B): Đoán loss dao động không hội tụ; thực tế loss vọt tăng rồi tự điều chỉnh giảm sâu xuống 0.006 nhờ khả năng thích nghi của thuật toán.   
Dự đoán 2: Thí nghiệm 3.B (Tricky): Đoán Encoder + LogReg thắng tuyệt đối; thực tế cả hai hòa 5/6, đều lọt lưới ở câu phishing giả mạo ngân hàng do thiếu ngữ liệu mẫu tương đương.   
Dự đoán 3: Thí nghiệm 4.B (Few-shot): Đoán F1 tăng vọt; thực tế F1 chỉ giữ ổn định vì zero-shot đã khá cao, trong khi chi phí token tăng mạnh.

## 4. Phân tích 50 case khó

*Model nào tụt nhiều nhất, ở nhóm case nào? Nêu 2 case cụ thể và cơ chế khiến model sai.*

## 5. Thử thách cá nhân

*Đề theo SEED của bạn, cách làm, kết quả, giải thích.*

## 6. Phương án cho sản phẩm thật

*Với yêu cầu p95 < 50 ms/tin cho 10 triệu SMS/ngày: chọn phương án nào, dẫn số liệu nào, chấp nhận đánh đổi gì.*

## 7. AI log và điều đã học

AI log: Dùng AI hỗ trợ debug lỗi PyTorch, tối ưu ma trận NumPy trong hàm top_k_similar và chuẩn hóa prompt gọi API qua Groq. Điều rút ra: Đại diện biểu diễn (representation) quan trọng hơn kiến trúc mạng: Embedding chất lượng cao kết hợp phân loại tuyến tính đơn giản mang lại hiệu quả vượt trội, đồng thời tối ưu hóa được bài toán đánh đổi giữa tốc độ, chi phí và độ chính xác.   
