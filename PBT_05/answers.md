# PHẦN A — KIỂM TRA ĐỌC HIỂU (20 điểm)
## Câu A1 (5đ) — Viewport & Mobile-First
1. Thẻ <meta viewport> và giải thích các thuộc tính
- Cú pháp chính xác:
<meta name="viewport" content="width=device-width, initial-scale=1.0">
- Giải thích từng thuộc tính:
  + name="viewport": Khai báo với trình duyệt rằng thẻ này dùng để thiết lập vùng hiển thị (viewport) cho màn hình thiết bị.
  + width=device-width: Đặt chiều rộng của trang web bằng đúng chiều rộng màn hình của thiết bị.
  + initial-scale=1.0: Đặt tỷ lệ phóng to (zoom) ban đầu là 1.0 (kích thước gốc 100%) ngay khi trang web vừa được tải xong, giúp trang không bị tự động phóng to hay thu nhỏ.
2. Nếu THIẾU thẻ này, iPhone sẽ hiển thị trang web như thế nào?
- iPhone sẽ tự động coi trang web đó là trang web dành riêng cho máy tính (Desktop).
- Giao diện sẽ bị thu nhỏ xíu lại để nhét vừa toàn bộ trang web vào màn hình điện thoại.
- Hậu quả trực tiếp: Chữ nhỏ xíu, các nút bấm chồng lên nhau, người dùng phải zoom in để đọc và phải scroll ngang liên tục để xem nội dung.
3. Phân biệt Mobile-First và Desktop-First
- Sự khác nhau:
  + Mobile-First: Viết code CSS cho màn hình điện thoại (nhỏ nhất) trước làm mặc định, sau đó dùng Media Queries với min-width để bổ sung, mở rộng layout khi màn hình lớn dần lên (Tablet, Desktop).
  + Desktop-First: Viết code CSS cho màn hình máy tính (lớn nhất) trước làm mặc định, sau đó dùng Media Queries với max-width để thu gọn, co nhỏ layout lại cho phù hợp với các màn hình nhỏ hơn.
- Ví dụ CSS với breakpoint 768px:
  + Cách 1: Mobile-First (Dùng min-width)
CSS
/* 1. Code cho mobile trước (mặc định dưới 768px) */
.col { 
    width: 100%; 
}

/* 2. Từ kích thước 768px trở lên (Tablet/Desktop) */
@media (min-width: 768px) {
    .col { 
        width: 50%; 
    }
}
  + Cách 2: Desktop-First (Dùng max-width)
CSS
/* 1. Code cho desktop trước (mặc định màn hình lớn) */
.col { 
    width: 50%; 
}
/* 2. Khi màn hình nhỏ dưới 768px (Mobile) */
@media (max-width: 767.98px) {
    .col { 
        width: 100%; 
    }
}
- Tại sao Mobile-First được khuyên dùng?
  + Tối ưu hiệu năng & tốc độ: Điện thoại di động tải ít CSS hơn sẽ xử lý nhanh hơn. Thiết bị di động có cấu hình và mạng yếu hơn máy tính, việc chạy code mặc định nhẹ nhàng rồi "thêm" CSS cho desktop thì tốt hơn là bắt mobile gánh đống CSS nặng nề của desktop rồi "giảm tải/ẩn bớt" đi (gây lãng phí).
  + Lượng người dùng áp đảo: Hiện nay có tới 60% lượt truy cập web đến từ MOBILE. Thiết kế ưu tiên nơi có nhiều người dùng nhất là chiến lược thông minh.
  + Tránh bị phạt SEO: Google áp dụng cơ chế đánh giá ưu tiên di động, nếu trang web không thân thiện với mobile (mobile-friendly) thì sẽ bị Google phạt SEO, làm giảm thứ hạng tìm kiếm một cách nghiêm trọng.

## Câu A2 (5đ) — Điểm ngắt
BẢNG TIÊU CHUẨN BREAKPOINTS & BỐ TRÍ LƯỚI SẢN PHẨM
| Tên Breakpoint	| Kích thước Pixel	| Thiết bị đại diện	| Số cột hiển thị (Lưới sản phẩm) |
| :--- | :----: | ---: |---: |
| xs	| < 576px	| Điện thoại dọc (Mobile Portrait) |	1 cột (Layout mặc định, xếp chồng dọc) |
| sm	| ≥ 576px	| Điện thoại ngang (Mobile Landscape)	| 1 - 2 cột (Tùy thuộc vào kích thước sản phẩm) |
| md	| ≥ 768px	| Máy tính bảng (Tablet)	|2 cột (grid-template-columns: repeat(2, 1fr)) |
| lg	| ≥ 992px	| Máy tính màn hình nhỏ (Small Desktop/Laptop)	| 3 - 4 cột (Bắt đầu chia nhiều cột hơn) |
| xl	| ≥ 1200px	| Máy tính màn hình lớn (Large Desktop)	| 4 cột (grid-template-columns: repeat(4, 1fr)) |

