# PHẦN A — ĐỌC HIỂU (20 điểm)
## Câu A1 (10đ) — Hệ thống lưới
**BẢNG PHÂN TÍCH BỐ CỤC**
| Kích thước màn hình	| < 768px (Mobile)	| 768px - 991px (Tablet / md)	| ≥ 992px (Desktop / lg) |
| Số cột | 12 / 12 (mỗi box chiếm 100% chiều rộng)	| 6 / 12 (mỗi box chiếm 50% chiều rộng)	| 3 / 12 (mỗi box chiếm 25% chiều rộng) |
| Bố cục hộp | Xếp chồng thành 4 hàng(1 box mỗi hàng) | Chia thành 2 hàng(2 box mỗi hàng) | Nằm cùng 1 hàng(4 box trên một hàng) |

1. col-md-6 nghĩa là gì?
- col: Viết tắt của Column (Cột).
- md: Định vị breakpoint Medium (áp dụng cho các màn hình có độ rộng từ 768px trở lên)
- 6: Chiếm 6 phần trong tổng số 12 phần của hệ thống lưới (tương đương với 50% chiều rộng của hàng bọc nó).
- Ý nghĩa đầy đủ: Trên các thiết bị có màn hình từ kích thước Tablet trở lên (>=768px) phần tử này sẽ chiếm một nửa chiều rộng màn hình.
2. Tại sao không cần viết col-sm-12?
- Trong đoạn mã trên, việc viết thêm col-sm-12 là hoàn toàn dư thừa vì 2 lý do cốt lõi của Bootstrap:
  + Bản chất Mobile-First: Bootstrap được thiết kế ưu tiên cho di động trước. Class col-12 không gắn breakpoint sẽ áp dụng cho tất cả các màn hình từ nhỏ nhất trở lên (từ 0px đến vô cực).
  + Cơ chế ghi đè xuôi: col-12 đã đặt độ rộng 100% cho màn hình nhỏ. Khi màn hình tăng dần lên kích thước sm (576px - 767px), do không có class nào chặn lại, nó vẫn sẽ kế thừa độ rộng 100% từ col-12. Phải đến khi chạm mốc md (768px), class col-md-6 mới nhảy vào kích hoạt để ghi đè cấu trúc lên thành 50%.
Do đó, từ khoảng màn hình sm (576px đến 767px) phần tử đã tự động full-width rồi, không cần tốn công khai báo col-sm-12.

