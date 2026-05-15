# Cơm Tấm Làng CEO Dashboard - Next.js + Vercel

Dashboard CEO chuỗi F&B chạy bằng Next.js, đọc Google Sheets trực tiếp qua API server-side và deploy lên Vercel.

## Kiến trúc

```text
Browser / Client
  -> Next.js API /api/dashboard
  -> Google Sheets API bằng Service Account
  -> Google Sheet được share quyền Viewer
```

Key không được đưa ra client. Local dùng `.env.local`; production dùng Vercel Environment Variables.

## Cài đặt local

```bash
npm install
npm run dev
```

Mở:

```text
http://localhost:3000
```

Nếu chưa có cấu hình môi trường, copy `.env.example` thành `.env.local` rồi điền key thật.

## Cấu hình Google Sheet

1. Tạo Google Cloud Service Account.
2. Enable Google Sheets API.
3. Tạo JSON key.
4. Share Google Sheet cho email service account quyền Viewer.
5. Điền `.env.local` khi chạy local hoặc Vercel Environment Variables khi deploy:

```env
GOOGLE_SHEET_ID=...
GOOGLE_SERVICE_ACCOUNT_EMAIL=...
GOOGLE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----\n"
DASHBOARD_CACHE_SECONDS=300
GEMINI_API_KEY=...
GEMINI_MODEL=gemini-2.5-flash
CRON_SECRET=...
```

## Chuẩn bị GitHub

Repository chỉ cần push source app Next.js ở thư mục này.

Không push các file/thư mục sau:

- `node_modules`
- `.next`
- `.env.local`
- `.env*.local`
- `.vercel`
- `comtam-dashboard-next-v1_3-visual-standard/` nếu còn là thư mục bản sao cũ bên trong project

Trước khi push, chạy:

```bash
npm run build
```

Build phải thành công trước khi import vào Vercel.

## 11 danh mục đã dựng sẵn

1. Tổng quan CEO
2. Doanh thu & Tăng trưởng
3. Lợi nhuận & P&L
4. Chi phí
5. Kênh bán & Appfood
6. Sản phẩm / Menu
7. Vận hành cửa hàng
8. Nhân sự & Hiệu suất
9. Tồn kho / Giá vốn
10. Khách hàng & Khiếu nại
11. Mở rộng chuỗi

## Sheet đọc mặc định

- DASHBOARD_DATA
- CHI_PHI_
- TON_KHO
- DANH_GIA_KHACH_HANG
- THIET_LAP_MUC_TIEU
- CUA_HANG
- MENU_SALES_DAILY
- HR_EMPLOYEE_MASTER
- HR_TIMESHEET_DAILY
- OPS_AUDIT_SOP
- OPS_INCIDENT_LOG
- OPS_SHIFT_CHECKLIST
- EXP_KITCHEN_CAPACITY
- EXP_OPENING_CHECKLIST
- EXP_PAYBACK
- STORE_LOCATION

Nếu sheet thiếu, dashboard vẫn chạy và hiện empty state.

## Deploy Vercel từ GitHub

1. Tạo GitHub repo mới, ví dụ `comtam-ceo-dashboard`.
2. Push source code lên branch `main`.
3. Import repository vào Vercel.
4. Chọn Framework Preset: `Next.js`.
5. Build Command: `npm run build`.
6. Output Directory: để mặc định của Next.js.
7. Thêm Environment Variables:
   - `GOOGLE_SHEET_ID`
   - `GOOGLE_SERVICE_ACCOUNT_EMAIL`
   - `GOOGLE_PRIVATE_KEY`
   - `DASHBOARD_CACHE_SECONDS`
   - `GEMINI_API_KEY`
   - `GEMINI_MODEL`
   - `CRON_SECRET`
8. Deploy.

Sau khi deploy, kiểm tra:

- Trang chính hiển thị đủ 11 tab.
- `/api/health` trả về `ok: true`.
- `/api/dashboard` đọc được Google Sheets.
- AI assistant hoạt động khi đã cấu hình Gemini key.

## Telegram Cron

Vercel cron đang trỏ đến:

```text
/api/cron/telegram
```

Nếu đặt `CRON_SECRET`, gọi route kèm query `?secret=...` để tránh truy cập không hợp lệ.
