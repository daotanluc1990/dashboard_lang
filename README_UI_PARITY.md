# comtam-dashboard-next-v1.1-appscript-ui

Bản này giữ kiến trúc Next.js đọc Google Sheet trực tiếp, nhưng chỉnh lại UI để bám sát dashboard Apps Script v7.6 production hơn.

## Điểm đã chỉnh

- Sidebar giống bản Apps Script: logo 🍛, Cơm Tấm Làng CEO BI, menu compact, collapse icon-only.
- Header giống bản Apps Script: title/subtitle trái, pill Owner/CEO + source + Đọc lại Sheet bên phải.
- Filter giống bản Apps Script: 8 cột, chiều cao compact, label uppercase.
- Layout grid giống Apps Script: 12 cột, các class overview/revenue/std layout.
- KPI render thành một widget riêng, không còn rải auto-fit chung chung.
- Widget/panel dùng class `widget`, `widget-head`, `widget-body` giống Apps Script.
- Màu, spacing, font, border, shadow lấy từ `Styles.html` Apps Script v7.6.12.

## Chạy local

```bat
cd C:\Users\luc\Downloads\comtam-dashboard-next-v1\comtam-dashboard-next
copy .env.example .env.local
npm install
npm run dev
```

Nếu đã có `.env.local`, chỉ cần copy code mới đè vào project rồi chạy lại:

```bat
Ctrl + C
npm run dev
```

## Lưu ý bảo mật

Private key và Gemini key đã từng lộ trên màn hình/chat. Sau khi chạy ổn nên tạo key mới và thay trong `.env.local`.
