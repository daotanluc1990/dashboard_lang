# ComTam Dashboard Next.js v1.3 - Visual Standard CFO/COO Balanced

Bản này cập nhật dashboard theo file `nguyen_tac_bo_visual_dashboard_ceo_fnb.md`.

## Phạm vi chỉnh sửa

- Giữ nguyên kiến trúc Next.js + API đọc Google Sheet.
- Giữ nguyên palette Minimalist Light, sidebar, header, filter và nguyên tắc layout hiện tại.
- Chuẩn hóa lại bộ visual theo phương án CFO/COO Balanced.
- Bỏ toàn bộ visual liên quan phí app.
- Bỏ chỉ số chi phí lỗi khách hàng, thay bằng tỷ lệ xử lý đúng SLA.

## Thay đổi chính

### 1. Tổng quan CEO
- KPI chuyển về 6 KPI đúng file: Doanh thu thuần, Lợi nhuận ròng, Net Margin %, Số đơn hàng, AOV, Số chi nhánh dưới chuẩn.
- 6 visual: Combo doanh thu/lợi nhuận, Actual vs Target, Ranking chi nhánh, Cơ cấu doanh thu theo kênh, Bảng sức khỏe chi nhánh, Bảng cảnh báo CEO.

### 2. Kênh bán hàng & Appfood
- Bỏ Gross vs Net Appfood.
- Bỏ Doanh thu app + phí app %.
- Thay bằng: Doanh thu thuần theo kênh và Tăng trưởng doanh thu theo kênh.
- Bảng hiệu quả kênh có doanh thu, số đơn, AOV, tỷ trọng, tăng trưởng.

### 3. Đánh giá & Khách hàng
- 7 KPI: Rating trung bình, Tổng đánh giá, % tiêu cực, Phản ánh chưa xử lý, Tỷ lệ phản hồi, Thời gian phản hồi TB, Tỷ lệ xử lý đúng SLA.
- 7 visual: Rating + số đánh giá theo thời gian, Đánh giá theo kênh, Ranking CSAT theo chi nhánh, Top nguyên nhân phàn nàn, Chi nhánh × ca/ngày, SLA xử lý phản ánh, Bảng phản ánh nghiêm trọng & hành động.

## Sheet/cột nên có cho Đánh giá & Khách hàng

Sheet `DANH_GIA_KHACH_HANG` nên có một số cột sau để visual đầy đủ:

- Ngày
- Mã CH / Chi nhánh / Cửa hàng
- Kênh
- Ca
- Rating / Số sao / CSAT
- Cảm xúc / Sentiment
- Nhóm lỗi / Vấn đề
- Nội dung phản hồi
- Mức độ
- Trạng thái xử lý
- Người phụ trách
- Thời gian phản hồi
- SLA giờ

Nếu thiếu một số cột, dashboard vẫn chạy và hiển thị phần dữ liệu có thể tính được.

## Cách cập nhật

Copy đè toàn bộ file trong gói này vào project Next.js hiện tại, giữ nguyên `.env.local`, sau đó chạy:

```bash
npm run dev
```

