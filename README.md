# Day26_Track01_AI_Gateway

## 1. Thành viên

| Họ tên | MSSV | Phần phụ trách | Góp ý đã đưa cho nhóm bạn |
| --- | --- | --- | --- |
| Lê Duy Bảo | 2A202602749 | Phạm vi, ADKAR, memo quyết định | Góp ý làm rõ vấn đề người dùng, giá trị sản phẩm, phạm vi MVP và tiêu chí thành công; ưu tiên tính năng theo bằng chứng nghiên cứu. |
| Đỗ Hoàng Nam Khánh | | Gartner Lite phần readiness, chỉ số chất lượng và hard policy | Góp ý kiểm tra chất lượng dữ liệu, thống nhất cách tính chỉ số và bổ sung cơ chế xử lý lỗi ở backend. |
| Nguyễn Anh Trí | | Mollick, kiến trúc tin cậy, lộ trình vận hành | Góp ý hoàn thiện luồng frontend–backend, bổ sung giám sát hệ thống và chuẩn hóa quy trình triển khai trên cloud. |
| Đinh Tuấn Long | | AS IS / TO BE, phỏng vấn người dùng, workflow metric | Góp ý đơn giản hóa thao tác, làm rõ trạng thái và phản hồi trên giao diện; kiểm chứng thiết kế qua thử nghiệm với người dùng. |

## 2. Phạm vi

Sản phẩm AI: AI Agent Gateway. Nhóm người dùng chính: nhân viên quản lý hạ tầng và tài nguyên AI tại doanh nghiệp có nhiều team phát triển AI.

Bốn quy trình: đăng ký team và cấp quyền model; định tuyến request theo task, policy, ngân sách; xử lý lỗi provider và fallback; theo dõi chi phí, latency, usage.

## 3. Nguyên nhân gốc

Nguyên nhân 1: workflow và hấp thụ chưa thiết kế (Mollick, Gartner Lite), bằng chứng là PRD v1.0 ghi product boundary chưa chốt và survey, interview đang thu thập.

Nguyên nhân 2: độ tin cậy chưa kiểm chứng (ADKAR Desire, Gartner Lite Readiness), bằng chứng là eval 95,3% chưa tách 7 slice và case Morgan Stanley, Klarna / Watson.

## 4. Cách làm mới

Nguồn kiểm chứng: log lý do route, model, policy, chi phí, catalog giá có ngày cập nhật. Người chịu trách nhiệm: chủ hạ tầng AI duyệt policy, owner chất lượng routing. Khi AI không chắc: route về model an toàn và gắn cờ review, fallback khi provider lỗi, chặn và chuyển người khi hard policy không còn model hợp lệ.

## 5. Chỉ số

Product metric: tỷ lệ routing đúng theo 7 slice (mốc đầu 95,3%, mục tiêu giữ ≥95,3%, nguồn bộ eval và replay suite, owner Đỗ Hoàng Nam Khánh). Workflow metric: thời gian đối soát chi phí và xử lý sự cố mỗi tháng (mốc đầu đo 2 tuần đầu, mục tiêu giảm ≥50%, nguồn ghi nhận của đội hạ tầng AI, owner trưởng đội hạ tầng AI của doanh nghiệp pilot).

## 6. Quyết định

Sửa: chạy shadow pilot nhỏ để sửa readiness, chưa rollout rộng. Hai thay đổi so với v1: thay số request mỗi ngày bằng tỷ lệ request qua gateway; thêm workflow metric thời gian đối soát.
