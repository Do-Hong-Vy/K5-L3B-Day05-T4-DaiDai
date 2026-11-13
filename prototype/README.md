# Prototype — Trợ lý khiếu nại "hàng không đúng mô tả" (Track 4 · Nhóm Đại Đại)

> Phụ trách: **Nguyễn Ánh Dương** (2A202604087) · Thiết kế chi tiết và lập luận: `spec.md` §5.

## Mở thế nào

- **File:** [`index.html`](index.html). Chỉ cần mở bằng trình duyệt (Chrome, Edge). Không cần cài đặt, không backend, không đăng nhập, không có API key.
- Trên GitHub: tải `index.html` về rồi mở, hoặc bật GitHub Pages cho repo và mở `/prototype/`.
- Thanh trên cùng có các nút: **K1 / K2** để chọn ca · **Số đánh dấu** để bật/tắt các số 1–3 và chữ A–D · **Làm lại ca này** để chạy lại từ đầu.
- Dải màu vàng dưới thanh tiêu đề luôn ghi **bước tiếp theo cần bấm**, nên bấm từ đầu tới cuối không cần ai can thiệp.

## Bấm qua ca khó (ca demo bắt buộc: K1, mô tả bị sửa sau khi bán)

| Bước | Bấm ở đâu | Thấy gì |
|---|---|---|
| 1 | Màn hình 1 · **Gửi** | Người mua gửi: "Nồi chiên ghi 6 lít mà mình đo lòng nồi chỉ được 5 lít…" |
| 2 | (tự chạy) | AI gọi `xem_don_va_mo_ta_luc_dat`, hiện huy hiệu độ chắc **①**, thẻ hai bản mô tả **②**, câu hỏi xác nhận **③** |
| 3 | **Xác nhận trả hàng hoàn tiền** **(B)** | Yêu cầu được ghi nhận trong hạn, bản nháp được soạn, hồ sơ chuyển Trưởng nhóm **(C)**, hiện nút **Hoàn tác (A)** |
| 4 | Màn hình 2 · tab **Nhân viên sàn** | Hai nút tiền bị **khoá theo Luật L3** |
| 5 | **⏩ Mô phỏng hết 48 giờ** (hoặc tab Người bán → **Không đồng ý**) | Hai nút mở khoá |
| 6 | **Duyệt chi** / **Từ chối** | Hộp xác nhận: phải tick "đã xem cả hai bên" thì nút mới bấm được |

Ca **K2** (tai nghe, người bán đúng): Gửi → **Xác nhận tạo yêu cầu** → tab Người bán **Gửi chứng từ** → xem bảng 3 cột **②** → tab Nhân viên sàn duyệt.

Ca lạ có nút sẵn trong khung chat: **"Cho mình SĐT shop"** (Luật L5), **"Khoá shop này đi"** (`phat_shop` = Cấm **(D)**), **"Gặp nhân viên"**. Ở K2 còn có nút mô phỏng **ảnh serial khớp / khác**.

## Ảnh có đánh số

| Ảnh | Nội dung |
|---|---|
| [`img/01-k1-nguoi-mua-va-nhan-vien-san.png`](img/01-k1-nguoi-mua-va-nhan-vien-san.png) | K1 sau khi người mua xác nhận: màn hình người mua + màn hình nhân viên sàn với nút tiền đang khoá |
| [`img/02-k2-bang-chung-3-cot.png`](img/02-k2-bang-chung-3-cot.png) | K2 sau khi shop nộp chứng từ: bảng 3 cột, độ chắc Thấp, nút tiền đã mở khoá |
| [`img/03-k1-hop-xac-nhan-duyet.png`](img/03-k1-hop-xac-nhan-duyet.png) | K1 sau 48 giờ: nhân viên bấm "Từ chối", hộp xác nhận cảnh báo mô tả bị sửa sau khi bán |

**Số (màu hồng) = nguyên tắc HAX/PAIR**, khớp mã `[#1]`–`[#3]` ở `spec.md` §3.5:

| Số | Nguyên tắc | Chỗ trên màn hình |
|---|---|---|
| **1** | HAX G1 + G2 · Luật AI 134/2025 Đ.11 k.1 | Dải "Trợ lý AI Shopee… Quyết định tiền do Người bán / Nhân viên duyệt"; huy hiệu độ chắc ở đầu tin AI và trong ô "Đề xuất của AI"; hạn trả hàng còn bao lâu |
| **2** | HAX G11 · PAIR Explainability + Trust | Thẻ "Mô tả lúc đặt 03/11" cạnh "Mô tả hiện tại 09/11", phần sửa được tô vàng (K1); bảng 3 cột Mô tả / Bằng chứng người bán / Bằng chứng người mua (K2). Màn hình người mua và người duyệt dùng **cùng một thẻ** |
| **3** | HAX G10 + G8/G9 · PAIR Errors + Graceful Failure | Thanh hành động dưới khung chat: câu hỏi xác nhận (L7), danh sách đúng 2 ảnh còn thiếu (L4), trạng thái hồ sơ, nút hoàn tác |

**Chữ (màu xanh) = mức tự chủ ở `spec.md` §4:**

| Chữ | Mức | Chỗ trên màn hình |
|---|---|---|
| **A** | Tự làm, có hoàn tác | Nút **↩ Huỷ yêu cầu / Hoàn tác nháp** (huỷ bản nháp `soan_de_xuat_hoan_tien`) |
| **B** | Cần duyệt, có xác nhận | Nút xác nhận của người mua; ô "Quyết định của shop" (làn nhanh); ô "Quyết định dòng tiền · chỉ nhân viên sàn" (khoá theo L3, có hộp xác nhận) |
| **C** | Có đường chuyển người | Nút **Gặp nhân viên**; dòng "Đã chuyển Trưởng nhóm · SLA 24h" |
| **D** | Việc cấm không có nút | Ô "Không có nút phạt / khoá shop…"; bấm "Khoá shop này đi" thì AI chuyển cho Bộ phận chuyên trách |

## Phần nào là mock

- Toàn bộ dữ liệu là dữ liệu dựng ở `spec.md` §2.0. Câu chữ của AI được viết sẵn, chép nguyên văn từ §3.1(a) và §3.2(a). **Không có lời gọi AI thật.**
- Các lời gọi tool chỉ được ghi vào bảng **Nhật ký tool & luật** để minh hoạ mức tự chủ, không gọi hệ thống nào.
- Đồng hồ 48 giờ là chữ tĩnh. Nút **⏩ Mô phỏng hết 48 giờ** là nút điều khiển demo, không phải chức năng sản phẩm.
- Ảnh người mua và chứng từ của shop chỉ là dòng chữ giả, không có file ảnh.
- Muốn chụp lại ảnh, mở `index.html?shot=k1`, `?shot=k2` hoặc `?shot=k1modal`: trang tự dựng sẵn đúng trạng thái của từng ảnh.
