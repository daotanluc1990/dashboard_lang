# ComTam Dashboard Next.js v1.2 Professional

Bản này nâng cấp từ v1.1 để dashboard Next.js chuyên nghiệp hơn và bám sát bộ Apps Script production.

## Điểm đã chỉnh

1. Chuẩn hóa toàn bộ 11 danh mục, giảm empty state và khai thác dữ liệu thật nếu sheet phụ đã có.
2. Bỏ thông số/cột “phí Appfood” giả định trong tab Kênh bán.
3. Thay bằng thông số quan trọng hơn: **mức phụ thuộc Appfood / tỷ trọng kênh**.
4. Tab Kênh bán giờ có:
   - Doanh thu theo kênh.
   - Cơ cấu kênh bán.
   - Offline vs Appfood.
   - Số đơn + AOV theo kênh.
   - Doanh thu kênh + tỷ trọng %.
   - Bảng hiệu quả kênh bán.
5. Bổ sung mapping dữ liệu chuyên sâu cho:
   - MENU_SALES_DAILY
   - OPS_AUDIT_SOP
   - OPS_INCIDENT_LOG
   - OPS_SHIFT_CHECKLIST
   - HR_TIMESHEET_DAILY
   - TON_KHO
   - DANH_GIA_KHACH_HANG
   - EXP_KITCHEN_CAPACITY
   - EXP_OPENING_CHECKLIST
   - EXP_PAYBACK
6. Không thêm dữ liệu giả, không hard-code chi nhánh.
7. Nếu sheet phụ thiếu dữ liệu, widget sẽ hiển thị empty state rõ ràng.

## Cách dùng

Copy đè toàn bộ file trong thư mục này vào project Next.js hiện tại, giữ nguyên `.env.local` của Lực.

Sau đó chạy lại:

```bat
Ctrl + C
npm run dev
```

Mở:

```text
http://localhost:3000
```

## Lưu ý bảo mật

Không đưa `.env.local` lên GitHub. Nếu đã lộ private key hoặc Gemini key, nên rotate key mới.
