# Memo quyết định: AI Agent Gateway

## 1. Vấn đề và nguyên nhân gốc

Gateway chưa là đường gọi LLM mặc định của các team và chưa có bằng chứng đo được về độ đúng của routing theo từng slice.

Nguyên nhân gốc 1: workflow và hấp thụ chưa được thiết kế, gateway chưa là bước chính thức, chưa có bàn giao giữa team AI và đội hạ tầng, product boundary chưa chốt.

Nguyên nhân gốc 2: độ tin cậy chưa kiểm chứng, eval 95,3% là số tổng chưa tách 7 slice, release gate chưa chạy tự động.

## 2. Framework đã dùng và bằng chứng

Mollick cho chia việc người và AI. Gartner Lite cho readiness và khả năng hấp thụ. ADKAR cho điểm nghẽn Desire của người dùng.

Bằng chứng: PRD v1.0 (20/9/2026) ghi product boundary chưa chốt; eval 95,3% chưa tách slice; case tham khảo Morgan Stanley (độ tin cậy đi trước mở rộng) và Klarna / Watson (số liệu nổi bật chưa đủ).

## 3. Thay đổi sau phản biện

1. Thay "số request mỗi ngày" bằng "tỷ lệ request của team pilot đi qua gateway".
2. Thêm workflow metric: thời gian đối soát chi phí và xử lý sự cố provider.
3. Tách eval 95,3% theo 7 slice, thêm task macro F1 và điều kiện không regression.
4. Thay "số model kết nối" bằng tỷ lệ vi phạm hard policy 0% và tỷ lệ fallback thành công.

## 4. Quyết định

**Sửa**: Chạy shadow pilot nhỏ để sửa readiness và độ tin cậy, chưa rollout rộng, vì hướng đi đạt nhưng dữ liệu, governance và owner chất lượng routing còn thiếu.

## 5. Lý do, bước tiếp theo và owner

Lý do: hướng đi đạt, dữ liệu, governance và owner chất lượng routing còn thiếu.

Bước tiếp theo và owner:

1. Lê Duy Bảo: xin duyệt shadow mode trước 30/10/2026.
2. Nguyễn Anh Trí: dựng CI chạy eval và fault injection trước 06/11/2026.
3. Đỗ Hoàng Nam Khánh: hoàn thành golden set 100 case phủ 7 slice trước 13/11/2026.
