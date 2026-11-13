# Kịch bản demo 4 phút — Nhóm Đại Đại · Track 4

> Bản nói dễ hiểu, rút từ `spec.md` §7. Mỗi người chỉ cần thuộc phần **"Nói"** của mình; phần **"Bấm"** là việc của người cầm chuột (Dương).

---

## Trước khi lên (2 phút chuẩn bị)

- [ ] Mở `prototype/index.html` bằng Chrome/Edge, phóng to cửa sổ, zoom 110–125% cho người xem thấy rõ.
- [ ] Chọn **K1 · Đơn B02**, bấm **↺ Làm lại ca này**, kiểm tra **Số đánh dấu: BẬT**.
- [ ] Mở sẵn tab thứ 2: `spec.md` ở mục §4.1 (bảng mức tự chủ) — phòng khi bị hỏi.
- [ ] Mở sẵn 3 ảnh trong `prototype/img/` — **phương án dự phòng** nếu máy lỗi.
- [ ] Thống nhất: Vỹ bấm giờ, ra hiệu khi còn 1 phút.

---

## Phần 1 · 0:00 – 0:45 · **Vỹ** — Bài toán & ý tưởng chính

**Bấm:** Để màn hình prototype K1 ở trạng thái ban đầu.

**Nói:**

> "Nhóm em làm trợ lý AI trong **Trò chuyện với Shopee**, cho lúc người mua báo *hàng không đúng mô tả*.
>
> Cái khó của bài này là: **AI sai hướng nào cũng có người mất tiền**. Nếu AI cho hoàn tiền sai thì shop mất cả tiền lẫn hàng. Nếu AI từ chối sai thì khách mất tiền mà còn ôm món hàng sai.
>
> Nên nhóm em làm 2 thay đổi:
> **Một**, cho AI xem được **mô tả sản phẩm lúc khách đặt hàng**, không chỉ mô tả hiện tại — vì shop có thể sửa mô tả sau khi bán.
> **Hai**, tách việc hoàn tiền làm đôi: AI chỉ được **soạn đề xuất**, còn **bấm chi tiền** thì phải có người duyệt.
>
> Lời hứa của nhóm: **tiền không rời khỏi sàn trước khi cả hai bên được nghe**. Còn việc phạt hay khoá shop thì AI **bị cấm**, trên màn hình không có nút đó."

---

## Phần 2 · 0:45 – 2:00 · **Dương** — Bấm qua ca khó K1

**Câu chuyện:** Khách mua nồi chiên 1.290.000đ, trang ghi 6 lít, đo chỉ được 5 lít. Shop đã lén sửa mô tả thành "lòng nồi 5 lít" sau khi bán. Hạn trả hàng còn 2 ngày.

| # | Bấm | Nói (ngắn) |
|---|---|---|
| 1 | **Gửi** (màn hình người mua) | "Khách báo: ghi 6 lít mà đo chỉ 5 lít." |
| 2 | *(chờ AI tự chạy, chỉ tay vào thẻ 2 bản mô tả)* | "AI không tin mô tả hiện tại. Nó lấy **bản lúc đặt hàng ngày 03/11** đặt cạnh **bản bị sửa ngày 09/11** — chỗ sửa tô vàng. Đây là lý do AI dám đứng về phía khách." |
| 3 | **Xác nhận trả hàng hoàn tiền** | "AI hỏi lại một câu trước khi làm. Khách xác nhận → yêu cầu được ghi nhận **trong hạn**, AI soạn đề xuất hoàn tiền và chuyển trưởng nhóm." |
| 4 | Chỉ vào **↩ Huỷ yêu cầu / Hoàn tác nháp** | "Mọi thứ AI tự làm đều **hoàn tác được**. Đổi ý thì bấm đây." |
| 5 | Chuyển sang tab **Nhân viên sàn** | "Đây là phía người duyệt. Nút chi tiền đang **khoá** — phải chờ shop phản hồi 48 giờ." |
| 6 | **⏩ Mô phỏng hết 48 giờ** → **Duyệt chi hoàn tiền 1.290.000đ** | "Hết 48 giờ, nút mở. Nhân viên phải tick *đã xem cả hai bên* mới duyệt được." |
| 7 | Bấm nút **K2 · Đơn C03** → **Gửi** → **Xác nhận tạo yêu cầu** → tab **Người bán** → **Gửi chứng từ** | "Còn ca ngược lại: tai nghe, **shop đúng**. Shop nộp hoá đơn và mã QR khớp. Bảng 3 cột cho thấy AI nói thẳng: **chưa đủ căn cứ** để kết luận hàng sai mô tả — không chiều khách." |

> ⚠️ Nếu hết giờ ở bước 7: bỏ qua, chỉ mở ảnh `img/02-k2-bang-chung-3-cot.png` và nói 1 câu.

---

## Phần 3 · 2:00 – 3:00 · **Phong** — Khi AI sai & vì sao thiết kế như vậy

**Bấm:** Dương quay lại màn hình K1 (hoặc mở ảnh `img/01-...png`). Phong chỉ vào các **số hồng 1 – 2 – 3**.

**Nói:**

> "Trên màn hình có 3 số, mỗi số là một nguyên tắc thiết kế:
>
> **Số 1** — AI nói rõ *mình là AI*, độ chắc bao nhiêu, và hạn trả hàng còn mấy ngày. Đúng Luật AI 134/2025: người dùng phải biết mình đang nói chuyện với AI.
>
> **Số 2** — AI **cho xem bằng chứng**, không chỉ đưa kết luận: thẻ 2 bản mô tả ở K1, bảng 3 cột ở K2. Người mua và người duyệt nhìn **cùng một thẻ**.
>
> **Số 3** — Khi không chắc, AI **thu hẹp lại**: hỏi xác nhận 1 câu, xin đúng 2 ảnh còn thiếu, luôn có nút hoàn tác.
>
> Điểm quan trọng nhất: ca K1 là **lỗi ngữ cảnh** — AI đọc nhầm mô tả đã bị sửa. Viết câu trả lời lịch sự hơn **không cứu được** khách mất 1,29 triệu. Chỉ có **sửa nguồn dữ liệu** (xem bản lúc đặt) và **tách quyền chi tiền** mới cứu được."

---

## Phần 4 · 3:00 – 4:00 · **Cả nhóm** — Nhận ca lạ

Công thức trả lời 3 bước (Phong nói, Dương bấm, Vỹ chốt):

1. **Bẫy ở đâu?** (ca này thuộc loại rủi ro nào)
2. **AI làm gì / bị luật nào chặn?**
3. **Sai thì ai mất gì?** → vì vậy mức tự chủ là…

Có sẵn nút trên prototype để bấm ngay:

| Nếu bị hỏi… | Bấm | Câu trả lời 1 dòng |
|---|---|---|
| "Shop đòi SĐT khách / khách đòi SĐT shop?" | **Cho mình SĐT shop** | AI từ chối — bảo mật dữ liệu cá nhân (Luật L5). |
| "Khách bảo khoá shop luôn đi?" | **Khoá shop này đi** | AI không có quyền, chuyển bộ phận chuyên trách (mức **Cấm**, chữ D). |
| "Khách muốn gặp người thật?" | **Gặp nhân viên** | Luôn có đường chuyển người, SLA 24h (chữ C). |
| "Khách gửi ảnh serial khác hộp ở K2, AI có tự hoàn tiền không?" | **+ Ảnh serial (mô phỏng: khác)** | **Không.** Bằng chứng được cập nhật, đẩy lên đầu hàng đợi, nhưng chi tiền vẫn cần người duyệt. |
| "Khách đổi ý, không muốn trả nữa?" | **↩ Huỷ yêu cầu / Hoàn tác nháp** | Huỷ ngay, tiền chưa rời sàn nên không kẹt đơn. |
| "Shop phản hồi bằng dấu chấm cho qua 48h?" | *(nói, không bấm)* | Shop "không đồng ý" → tự chuyển nhân viên sàn; nhân viên thấy shop không có bằng chứng. |
| "1 cái nồi sai mô tả, 1 cái vỡ do vận chuyển, đền voucher?" | *(nói, không bấm)* | AI **tách ra**: cái sai mô tả xử lý ở đây; cái vỡ chỉ sang luồng vận chuyển; voucher ngoài quyền AI. |

---

## 2 câu chốt chắc chắn bị hỏi — thuộc lòng

**"Chỉ cho tôi chỗ nào là nguyên tắc G__?"**
→ Chỉ số hồng: **1** = AI tự giới thiệu + độ chắc + hạn trả (G1, G2) · **2** = thẻ bằng chứng (G11) · **3** = hỏi lại / hoàn tác / chuyển người (G10, G8/G9).

**"Hành động này sai thì ai mất gì?"**
| Hành động | Sai thì… | Mức |
|---|---|---|
| Chi hoàn tiền | Shop mất tiền + hàng, khó lấy lại | Cần người duyệt |
| Từ chối khiếu nại | Khách mất tiền + ôm hàng sai | Chỉ nhân viên sàn duyệt |
| Xem đơn, soạn đề xuất, xin ảnh, chuyển người | Không mất tiền, huỷ được ngay; còn **chờ thì khách lỡ hạn trả** | AI tự làm |
| Phạt / khoá shop | Ảnh hưởng mọi đơn của shop | Cấm, không có nút |

---

## Sau demo

Ghi ngay ca lạ thực tế vào `spec.md` §7.4 (câu hỏi nguyên văn · nhóm xử lý thế nào · có đổi luật không).
