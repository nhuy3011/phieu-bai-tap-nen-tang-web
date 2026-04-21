# PHẦN A — KIỂM TRA ĐỌC HIỂU
## Câu A1 (5đ) — HTTP & Browser
### 1. Khi gõ https://shopee.vn vào trình duyệt và nhấn Enter, thứ tự ít nhất 5 bước xảy ra (từ DNS lookup đến render) là:
- *Nguồn tham chiếu: tuan_1_html5/01_introduction_html_universe.md/1.WEB HOẠT ĐỘNG NHƯ THẾ NÀO?*
- **B1. Gọi Shipper tìm địa chỉ (DNS Lookup):**
Trước khi gửi yêu cầu HTTP Request, trình duyệt cần biết địa chỉ chính xác của nhà hàng Shopee. Trình duyệt hỏi máy chủ DNS: "Shopee.vn ở địa chỉ IP nào?". DNS trả về cho trình duyệt một địa chỉ số (ví dụ: 111.222.33.44) để biết chính xác máy chủ đang nằm ở đâu trên Internet.
- **B2. Thiết lập kết nối an toàn (TCP/TLS Handshake):**
Vì Shopee dùng HTTPS, trình duyệt cần thiết lập một kết nối bảo mật trước khi truyền tin.
Hành động: Đây là bước "bắt tay" giữa Client và Server để thống nhất cách mã hóa dữ liệu, đảm bảo không ai có thể "ăn trộm" thông tin đơn hàng hay tài khoản của bạn trên đường đi.
- **B3. Gửi thực đơn yêu cầu (HTTP Request - GET):**
Bây giờ, "anh shipper" Internet sẽ mang yêu cầu của bạn đến đúng địa chỉ máy chủ Shopee.
Hành động: Trình duyệt gửi một lệnh GET / HTTP/1.1.
Ý nghĩa: "Cho tôi xem trang chủ của Shopee" (tương đương với việc yêu cầu xem menu tại nhà hàng).
- **B4. Nhà bếp xử lý và trả món (HTTP Response - 200 OK):**
Máy chủ Shopee (Server) tiếp nhận yêu cầu, vào "bếp" để chuẩn bị dữ liệu.
Hành động: Server gửi trả về một gói phản hồi kèm mã trạng thái 200 OK.
Kết quả: Gói hàng này chứa các tệp nguyên liệu thô: HTML (khung xương), CSS (màu sắc) và JavaScript (máy móc vận hành).
- **B5. Kiến trúc sư xây dựng giao diện (Browser Rendering):**
Đây là lúc trình duyệt của bạn làm việc cật lực để biến "nguyên liệu thô" thành trang web đẹp mắt:
Parse HTML: Dựng khung nhà (Tiêu đề, các nút mua sắm).
Parse CSS: Sơn màu cam đặc trưng của Shopee, chỉnh font chữ, sắp xếp các banner.
Execute JS: Chạy các hiệu ứng trượt banner, thông báo nhảy số trong giỏ hàng.
Paint: Cuối cùng, hình ảnh sản phẩm và giá cả hiện lên hoàn chỉnh trên màn hình của bạn.
### 2.
