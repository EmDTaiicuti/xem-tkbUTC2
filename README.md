# 📅 Tra cứu Thời Khóa Biểu theo MSSV

Trang web tĩnh giúp sinh viên nhập **mã số sinh viên (MSSV)** để xem ngay lịch học theo tuần mà không cần tài khoản, không cần backend, mọi thứ chạy trên trình duyệt.

🔗 **Demo:** https://emdtaiicuti.github.io/xem-tkb-utc2/

## ✨ Tính năng

- Tra cứu lịch học theo tuần bằng MSSV, hiển thị dạng lưới thời khóa biểu trực quan
- Điều hướng qua lại giữa các tuần trong học kỳ, tự nhảy tới tuần hiện tại
- Tự nạp sẵn dữ liệu TKB + danh sách lớp học phần từ repo, không cần người dùng tự upload file
- Xử lý toàn bộ trên trình duyệt (dùng [SheetJS](https://sheetjs.com/)) — không gửi dữ liệu sinh viên đi đâu cả
- Vẫn còn cơ chế nạp file thủ công dự phòng nếu auto-load lỗi (ẩn trong code, xem `#setupPanel`)

## 📁 Cấu trúc thư mục

```
.
├── index.html              # Toàn bộ app (HTML + CSS + JS trong 1 file)
└── data/
    ├── tkb.xls            # File thời khóa biểu tổng (thứ, tiết, phòng, GV...)
    └── ds-lop/
        ├── manifest.json    # Danh sách tên các file .xls bên dưới
        └── *.xls            # Mỗi file = danh sách MSSV của các lớp học phần
```

## 🔄 Cập nhật dữ liệu học kỳ mới

1. Đổi file TKB mới thành đúng tên `data/tkb.xls` (ghi đè file cũ)
2. Đổi các file danh sách lớp mới vào `data/ds-lop/`, cập nhật lại `manifest.json` nếu tên file thay đổi
3. Mở `index.html`, tìm dòng `const DATA_VERSION = '1';` → tăng số lên (`'2'`, `'3'`,...) để ép trình duyệt tải bản mới thay vì dùng cache cũ
4. Commit + push lên `main` — GitHub Pages tự build lại, không cần thao tác gì thêm

## 🛠 Công nghệ

- HTML/CSS/JS thuần, không framework, không build step
- [SheetJS (xlsx.js)](https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js) để đọc file Excel ngay trên trình duyệt
- Font: [Be Vietnam Pro](https://fonts.google.com/specimen/Be+Vietnam+Pro) & [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono)
- Host miễn phí trên GitHub Pages

## ⚠️ Lưu ý

- Khớp lớp học phần dựa theo đúng chuỗi **"Lớp học phần"**, không dùng Mã HP — vì 1 Mã HP có thể có nhiều lớp song song (khác GV/phòng)
- Dữ liệu chỉ nằm trong bộ nhớ trình duyệt lúc đang mở trang, không lưu trữ hay gửi đi đâu
