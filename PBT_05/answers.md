# PHẦN A — KIỂM TRA ĐỌC HIỂU (20 điểm)
## Câu A1 (5đ) — Viewport & Mobile-First
1. Thẻ <meta viewport> và giải thích các thuộc tính
- Cú pháp chính xác:
```<meta name="viewport" content="width=device-width, initial-scale=1.0">```
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
```
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
```
  + Cách 2: Desktop-First (Dùng max-width)
```
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
```
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

## Câu A3 (5đ) — Truy vấn phương tiện
| Kích thước màn hình	| .container chiều rộng |
| :--- | :---- |
| 375px (iPhone SE) |	100% |
| 600px	| 540px |
| 800px	| 720px |
| 1000px	| 960px |
| 1400px	| 1140px |

## Câu A4 (5đ) — Kiến thức cơ bản về SCSS
**1. Biến ( $primary-color)**
- **Giải thích:** Giúp lưu trữ các giá trị được sử dụng lặp đi lặp lại nhiều lần (như mã màu, font chữ, bo góc) vào một cái "tên gợi nhớ" bắt đầu bằng ký hiệu $. Khi muốn thay đổi giao diện, bạn chỉ cần sửa giá trị của biến ở một nơi duy nhất, toàn bộ những chỗ sử dụng biến đó sẽ tự động cập nhật theo.
- **Ví dụ:**
```
// Khai báo biến
$primary-color: #805ad5; 
$radius-base: 8px;
// Sử dụng
.button {
    background-color: $primary-color;
    border-radius: $radius-base;
}
.sidebar-title {
    color: $primary-color; // Đổi biến ở trên, chỗ này tự đổi theo
```

**2. Nesting (viết CSS lồng nhau)**
- **Giải thích:** Cho phép chúng ta viết các bộ chọn (selectors) lồng vào trong nhau, mô phỏng trực quan theo đúng cấu trúc phân cấp các thẻ của sơ đồ HTML. Điều này giúp code gọn gàng, tránh việc phải viết đi viết lại thẻ cha. Ký tự & được dùng để đại diện trực tiếp cho thẻ cha ngay trước nó (thường dùng cho :hover, :focus).
- **Ví dụ:**
```
.navbar {
    background: #1a202c;
    padding: 16px;

    ul {
        list-style: none;
        display: flex;

        li {
            margin-right: 24px;

            a {
                color: white;
                
                &:hover { // & tương đương với "a:hover"
                    color: $primary-color;
                }
            }
        }
    }
}
```

**3. Mixins ( @mixin, @include)**
- **Giải thích:** Đóng vai trò như một chiếc "hàm" trong lập trình. Nó cho phép bạn gom một tập hợp nhiều thuộc tính CSS hay dùng chung lại với nhau. Khi cần xài, bạn chỉ việc gọi tên nó ra thay vì viết lại toàn bộ các dòng code đó.
  + Định nghĩa bằng từ khóa: @mixin
  + Sử dụng bằng từ khóa: @include
- **Ví dụ:**
// Định nghĩa một mixin để căn giữa nhanh bằng flexbox
```
@mixin flex-center {
    display: flex;
    justify-content: center;
    align-items: center;
}
// Sử dụng mixin cho vùng Hero
.hero {
    height: 100vh;
    @include flex-center; // Gọi hàm ra dùng
}
```

**4. @extend/ Thừa kế**
- **Giải thích:** Cho phép một selector có thể "gộp chung" và thừa hưởng lại toàn bộ tất cả các thuộc tính CSS của một selector khác đã có sẵn. Tính năng này giúp giảm thiểu việc lặp lại code và giữ cho các component có chung một kiểu thiết kế nền tảng (Ví dụ: Các loại nút bấm khác nhau nhưng chung một kiểu khung cơ bản).
- **Ví dụ:**
```
// Lớp cơ sở (Base)
.btn-base {
    padding: 10px 20px;
    border-radius: 5px;
    font-weight: bold;
}
// Các nút kế thừa lại lớp cơ sở và chỉ đổi màu sắc
.btn-success {
    @extend .btn-base; // Thừa kế toàn bộ padding, radius, font-weight
    background-color: green;
    color: white;
}
.btn-danger {
    @extend .btn-base; // Thừa kế toàn bộ padding, radius, font-weight
    background-color: red;
    color: white;
}
```

**Tại sao trình duyệt KHÔNG đọc được tệp .scss? Bước chuyển đổi cụ thể**
- **Tại sao trình duyệt không đọc được?** Bởi vì Hiệp hội Web Quốc tế (W3C) chỉ quy định các trình duyệt (Chrome, Safari, Edge, Firefox) hiểu và thực thi được mã nguồn CSS thuần chuẩn (.css). Các tính năng nâng cao của SCSS như biến ($), vòng lặp, lồng nhau hay hàm (@mixin) hoàn toàn không nằm trong đặc tả kỹ thuật cốt lõi của trình duyệt; nếu đưa trực tiếp file .scss vào, trình duyệt sẽ báo lỗi cú pháp và không thể hiển thị giao diện.
- **Cần bước gì để chuyển SCSS $\rightarrow$ CSS?** Chúng ta cần một bước gọi là Compile (Biên dịch). Mã nguồn SCSS sau khi viết xong phải được chạy qua một công cụ dịch thuật (Sass Compiler) để quét sạch các cú pháp nâng cao, tính toán và xử lý chúng rồi xuất ra thành một file .css tiêu chuẩn mà trình duyệt có thể đọc hiểu bình thường.
  + Các cách thực hiện bước biên dịch này trong thực tế:
    + Dùng công cụ hỗ trợ trong VS Code: Cài đặt Extension có tên là "Live Sass Compiler", sau đó nhấp vào nút "Watch Sass" ở thanh trạng thái bên dưới. Mỗi khi bạn nhấn Ctrl + S để lưu file .scss, extension này sẽ tự động biên dịch ngay lập tức ra file .css.
    + Dùng các bộ đóng gói trong dự án lớn: Trong các dự án thực tế sử dụng các framework lớn, các công cụ tự động hóa như Webpack hoặc Vite đã được cấu hình tích hợp sẵn bộ biên dịch ngầm, bạn chỉ việc code và hệ thống sẽ tự lo phần chuyển đổi.
