# PHẦN A — KIỂM TRA ĐỌC HIỂU (25 điểm)
## Câu A1 (5đ) — 3 Cách nhúng CSS
1. **CSS Nội tuyến:** Đây là cách viết mã CSS trực tiếp bên trong thuộc tính style của một thẻ HTML cụ thể.
  - Ví dụ mã code:
    <p style="color: blue; font-weight: bold;">Đây là đoạn văn màu xanh.</p>
  - Ưu điểm: Áp dụng nhanh, có độ ưu tiên cao nhất, hữu ích khi muốn thay đổi nhanh một phần tử để kiểm tra (debug).
  - Nhược điểm: Làm code HTML bị rối, khó bảo trì khi dự án lớn dần, không thể tái sử dụng style cho các thẻ khác.
  - Khi nào nên dùng: Khi bạn chỉ cần định dạng cho duy nhất một phần tử đặc biệt hoặc dùng để test nhanh kết quả.
2. **CSS Nội bộ:** Cách này đặt toàn bộ mã CSS bên trong cặp thẻ <style>, thường nằm trong phần <head> của trang HTML.
  - Ví dụ mã code:
    <head>
    <style>
        p {
            font-size: 18px;
            line-height: 1.5;
        }
    </style>
    </head>
  - Ưu điểm: Quản lý tập trung style của một trang web tại một nơi, không cần tạo file riêng.
  - Nhược điểm: Chỉ có tác dụng trên trang hiện tại. Nếu website có nhiều trang, bạn phải copy code CSS sang từng file HTML rất mất thời gian.
  - Khi nào nên dùng: Dùng cho các trang web đơn (Single Page) hoặc khi làm các bài tập nhỏ trên lớp.
3. **CSS Bên ngoài:** Đây là cách chuyên nghiệp nhất: Viết CSS vào một file riêng biệt có đuôi .css và kết nối với HTML bằng thẻ <link>.
    - Ví dụ mã code:
      <!-- Trong file index.html -->
<head>
    <link rel="stylesheet" href="style.css">
</head>

/* Trong file style.css */
body {
    background-color: #f4f4f4;
    font-family: Arial, sans-serif;
}
  - Ưu điểm: Tách biệt hoàn toàn nội dung (HTML) và giao diện (CSS). Giúp code sạch sẽ, dễ quản lý và có thể áp dụng một file CSS cho hàng nghìn trang web khác nhau. Tối ưu tốc độ tải trang nhờ bộ nhớ đệm trình duyệt.
  - Nhược điểm: Cần thêm một yêu cầu (request) tải file từ máy chủ (tuy nhiên ảnh hưởng này là cực nhỏ).
  - Khi nào nên dùng: Luôn luôn sử dụng cho các dự án thực tế và chuyên nghiệp.
**Câu hỏi thêm**
Nếu cùng một phần tử (ví dụ: thẻ <h1>) bị cả 3 cách trên "ép" đổi màu khác nhau, thứ tự ưu tiên sẽ như sau:
- VÔ ĐỊCH: CSS Nội tuyến (Inline CSS) – Luôn thắng vì nó nằm "sát" phần tử nhất.
- HẠNG NHÌ: CSS Nội bộ & CSS Bên ngoài – Hai cách này có độ ưu tiên ngang nhau.
Giải thích tại sao: Trong CSS, có một khái niệm gọi là Độ ưu tiên (Specificity) và Thứ tự xuất hiện:
- Về khoảng cách: Trình duyệt coi CSS Nội tuyến là chỉ thị trực tiếp nhất nên ưu tiên nó hàng đầu.
- Về quy tắc "Thác nước" (Cascading): Đối với CSS Nội bộ và Bên ngoài, trình duyệt đọc code từ trên xuống dưới. Quy tắc nào được đọc sau cùng sẽ đè lên quy tắc trước đó.
Ví dụ: Nếu bạn đặt thẻ <link> (Bên ngoài) ở trên thẻ <style> (Nội bộ), thì CSS Nội bộ sẽ thắng vì nó được trình duyệt đọc sau.
