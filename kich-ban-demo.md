# Kịch bản demo 4 phút — Nhóm Đại Đại · Track 4

> Mỗi bước gồm 3 phần: **BẤM** (bấm vào đâu) → **THẤY** (màn hình phải hiện gì, để biết mình bấm đúng) → **NÓI** (câu nói, đọc gần như nguyên văn).
> Tên nút trong dấu **[ ]** khớp đúng chữ trên prototype.

---

## 0. Phân vai

| Người | Việc trong lúc demo | Đứng ở đâu |
|---|---|---|
| **Vỹ** | Nói phần 1 · bấm giờ · chốt "sai thì ai mất gì" khi bị hỏi | Cạnh màn hình |
| **Dương** | **Cầm chuột suốt buổi** · nói phần 2 | Ngồi máy |
| **Phong** | Nói phần 3 · dẫn phần trả lời ca lạ | Cạnh màn hình, chỉ tay vào số |

**Quy ước ra hiệu:** khi còn 1 phút, Vỹ giơ 1 ngón tay. Khi Vỹ giơ tay mà Dương chưa xong, Dương bỏ bước đang làm và chuyển sang phần tiếp theo.

---

## 1. Làm quen màn hình prototype (cả nhóm đọc trước 1 lần)

```
┌──────────────────────────────────────────────────────────────────────┐
│ THANH TRÊN CÙNG: [K1 · Đơn B02…] [K2 · Đơn C03…] [Số đánh dấu: BẬT]   │
│                  [↺ Làm lại ca này]                                   │
├──────────────────────────────────────────────────────────────────────┤
│ DẢI VÀNG: "Bước x/4 · …" → luôn ghi bước tiếp theo cần bấm            │
├────────────────────────┬─────────────────────────────────────────────┤
│ MÀN HÌNH 1 · NGƯỜI MUA │ MÀN HÌNH 2 · NGƯỜI DUYỆT                    │
│ (cột trái)             │ (cột phải) có 2 tab:                         │
│ - dải "Trợ lý AI…" (1) │   [Người bán · Kênh Người Bán] [Nhân viên sàn]│
│ - khung chat           │                                              │
│ - thanh hành động (3)  │                                              │
│ - ô Gửi / nút gợi ý    │                                              │
├────────────────────────┴─────────────────────────────────────────────┤
│ NHẬT KÝ TOOL & LUẬT: mỗi lần AI gọi tool hiện 1 dòng + mức tự chủ     │
│ CHÚ THÍCH: ý nghĩa số 1–3 (hồng) và chữ A–D (xanh)                    │
└──────────────────────────────────────────────────────────────────────┘
```

- **Số hồng 1, 2, 3** = nguyên tắc thiết kế HAX/PAIR. **Chữ xanh A, B, C, D** = mức tự chủ.
- **Nút màu xám bấm không được** nghĩa là chưa tới bước đó. Không phải lỗi.
- **Lỡ bấm nhầm** → bấm **[↺ Làm lại ca này]**, chạy lại ca đó từ đầu.
- Mỗi ca K1 / K2 **giữ nguyên trạng thái riêng**: chuyển sang K2 rồi quay về K1 thì K1 vẫn còn nguyên như lúc rời đi.

---

## 2. Chuẩn bị trước khi lên (5 phút)

Dương làm, Vỹ kiểm tra lại:

1. Mở file `prototype/index.html` bằng **Chrome hoặc Edge**.
2. Phóng to toàn màn hình (**F11**). Zoom **100–110%** (Ctrl + / Ctrl −).
   ⚠️ Không zoom quá to: cửa sổ hẹp hơn 900px thì 2 cột sẽ dồn thành 1 cột, mất cảnh "người mua bên trái, người duyệt bên phải".
3. Bấm **[K2 · Đơn C03 · người bán đúng]** → bấm **[↺ Làm lại ca này]**.
4. Bấm **[K1 · Đơn B02 · mô tả bị sửa]** → bấm **[↺ Làm lại ca này]**.
5. Kiểm tra: dải vàng ghi **"Bước 1/4 · Ở màn hình Người mua, bấm Gửi…"** và nút ghi **[Số đánh dấu: BẬT]**.
6. Ở cột phải, bấm sẵn tab **[Nhân viên sàn]** (tab này đang ghi "Chưa có hồ sơ nào được chuyển", không sao).
7. Mở sẵn **phương án dự phòng** ở cửa sổ khác: 3 ảnh trong `prototype/img/`, và file `spec.md` ở mục §4.1.

> **Tập ít nhất 2 lần** toàn bộ phần 2, có bấm giờ. Sau mỗi lần tập, làm lại bước 3–6.

---

## Phần 1 · 0:00 – 0:45 · **Vỹ** nói — Bài toán & ý tưởng

**Dương:** không bấm gì, để nguyên màn hình K1 ở Bước 1/4.

**Vỹ chỉ tay vào dải "Trợ lý AI Shopee" (số 1) ở đầu cột trái và nói:**

> "Nhóm em làm trợ lý AI trong **Trò chuyện với Shopee**, dùng khi người mua báo *hàng không đúng mô tả*.
>
> Cái khó là **AI sai hướng nào cũng có người mất tiền**. Cho hoàn tiền sai thì shop mất cả tiền lẫn hàng. Từ chối sai thì khách mất tiền mà còn ôm món hàng sai.
>
> Nên nhóm em làm 2 thay đổi. **Một**: cho AI xem **mô tả lúc khách đặt hàng**, vì shop có thể sửa mô tả sau khi bán. **Hai**: AI chỉ được **soạn đề xuất** hoàn tiền, còn **bấm chi tiền** thì phải có người duyệt.
>
> Lời hứa của nhóm: **tiền không rời khỏi sàn trước khi cả hai bên được nghe**. Phạt hay khoá shop thì AI bị cấm, trên màn hình không có nút đó."

**Câu chuyển lượt:** *"Dương sẽ bấm cho thầy/cô xem một ca khó."*

---

## Phần 2 · 0:45 – 2:00 · **Dương** bấm và nói — Ca khó K1

**Bối cảnh (Dương nói trước khi bấm, 1 câu):**
> "Khách mua nồi chiên 1.290.000đ. Lúc đặt, trang ghi 6 lít. Sau khi giao, shop sửa thành 'lòng nồi 5 lít'. Hạn trả hàng còn 2 ngày."

### Bước 2.1 — Khách gửi khiếu nại
- **BẤM:** cột trái, dưới cùng, nút **[Gửi]** (ô chat đã có sẵn tin nhắn).
- **THẤY:** tin nhắn khách hiện lên, AI trả lời ngay. Trong câu trả lời có **huy hiệu số 1** ("còn 2 ngày") và **thẻ 2 cột số 2**: *Mô tả lúc đặt 03/11* bên trái, *Mô tả hiện tại 09/11* bên phải, chỗ shop sửa **tô vàng**.
- **NÓI** (chỉ chuột vào thẻ 2 cột):
  > "AI không tin mô tả hiện tại. Nó lấy bản lúc đặt ngày 03/11 đặt cạnh bản bị sửa ngày 09/11. Chỗ tô vàng là chỗ shop sửa sau khi bán."

### Bước 2.2 — AI hỏi lại trước khi làm
- **BẤM:** thanh hành động (số 3) ngay dưới khung chat, nút xanh **[Xác nhận trả hàng hoàn tiền]**.
- **THẤY:** AI báo *"Đã ghi nhận trong hạn · 09:50 13/11"*. Thanh hành động đổi thành **"Trạng thái hồ sơ #B02"**, có dòng *"1.290.000đ đang giữ tại sàn"* và nút đỏ **[↩ Huỷ yêu cầu / Hoàn tác nháp]**.
- **NÓI:**
  > "AI hỏi lại một câu chứ không tự làm. Khách xác nhận thì yêu cầu được ghi nhận **trong hạn**, AI soạn bản nháp và chuyển trưởng nhóm. Tiền vẫn giữ ở sàn."

### Bước 2.3 — Chỉ nút hoàn tác (KHÔNG bấm)
- **BẤM:** không bấm, chỉ **rê chuột** lên nút đỏ **[↩ Huỷ yêu cầu / Hoàn tác nháp]** (chữ A).
- **NÓI:**
  > "Việc gì AI tự làm cũng huỷ được. Khách đổi ý thì bấm nút này."
- ⚠️ **Đừng bấm**, bấm sẽ huỷ yêu cầu và phải làm lại.

### Bước 2.4 — Sang góc nhìn người duyệt
- **BẤM:** cột phải, tab **[Nhân viên sàn]** (nếu chưa mở sẵn).
- **THẤY:** hồ sơ #B02 có cờ 🚩 *"Ưu tiên: Mô tả sửa sau khi bán"*, cùng thẻ 2 cột như bên người mua. Ô **"Quyết định dòng tiền"**: 2 nút xám + dòng **🔒 Khoá theo Luật L3**.
- **NÓI:**
  > "Đây là màn hình nhân viên sàn, nhìn **cùng một thẻ** với khách. Nút chi tiền đang **khoá**, vì shop chưa được nghe: shop có 48 giờ để phản hồi."

### Bước 2.5 — Mô phỏng hết 48 giờ
- **BẤM:** cũng ở tab Nhân viên sàn, kéo xuống ô **"Điều khiển demo"**, bấm **[⏩ Mô phỏng hết 48 giờ, shop không phản hồi]**.
- **THẤY:** dòng 🔒 biến mất, 2 nút **[Duyệt chi hoàn tiền 1.290.000đ]** và **[Từ chối khiếu nại]** sáng lên.
- **NÓI:**
  > "Giả sử hết 48 giờ shop không trả lời, lúc này nút mới mở."

### Bước 2.6 — Nhân viên duyệt chi
- **BẤM:** **[Duyệt chi hoàn tiền 1.290.000đ]**.
- **THẤY:** hiện hộp xác nhận. Nút "Duyệt chi hoàn tiền" trong hộp đang **xám**.
- **BẤM:** tick ô **"Tôi đã xem mô tả lúc đặt và bằng chứng của cả hai bên…"**, sau đó bấm **[Duyệt chi hoàn tiền]**.
- **THẤY:** hộp đóng. Khung chat người mua hiện *"Nhân viên Shopee đã duyệt hoàn tiền 1.290.000đ"*. Dải vàng ghi *"Xong ca K1"*.
- **NÓI:**
  > "Nhân viên phải tick 'đã xem cả hai bên' thì mới bấm được. Người bấm chi tiền là **nhân viên**, không phải AI."

### Bước 2.7 — Ca ngược lại: K2, shop đúng *(chỉ làm nếu còn trước 1:40)*
- **NÓI trước:** *"Còn đây là ca shop đúng: tai nghe 890.000đ, khách nói 'fake 100%'."*
- **BẤM** lần lượt:
  1. Thanh trên cùng: **[K2 · Đơn C03 · người bán đúng]**
  2. Cột trái: **[Gửi]**
  3. Thanh hành động: **[Xác nhận tạo yêu cầu trả hàng]**
  4. Cột phải: tab **[Người bán · Kênh Người Bán]** → nút **[Gửi chứng từ: hoá đơn nhập + ảnh QR serial]**
- **THẤY:** khung chat người mua hiện **bảng 3 cột số 2**: *Mô tả lúc đặt · Bằng chứng người bán · Bằng chứng người mua*. Huy hiệu ghi **"Độ chắc: Thấp"**. AI viết *"chưa đủ căn cứ để kết luận sản phẩm không đúng mô tả"*.
- **NÓI** (chỉ vào bảng 3 cột):
  > "Shop nộp hoá đơn và mã QR khớp. AI nói thẳng **chưa đủ căn cứ**, không chiều theo khách. Câu 'fake 100%' chỉ được ghi là nhận định của khách, không tính là bằng chứng."

> ⏱ **Nếu đã quá 1:40:** bỏ bước 2.7. Dương nói 1 câu: *"Ca shop đúng nhóm em có ảnh ở đây"* và mở ảnh `prototype/img/02-k2-bang-chung-3-cot.png`.

**Câu chuyển lượt:** *"Phong sẽ giải thích vì sao nhóm thiết kế như vậy."*

---

## Phần 3 · 2:00 – 3:00 · **Phong** nói — Vì sao thiết kế như vậy

**Dương bấm:** thanh trên cùng **[K1 · Đơn B02 · mô tả bị sửa]** để quay về K1 (ca K1 vẫn giữ nguyên, khung chat còn đủ). Kéo khung chat bên trái lên để thấy thẻ 2 cột.

**Phong chỉ tay lần lượt vào từng số hồng trên màn hình:**

| Chỉ vào | Ở đâu | Phong nói |
|---|---|---|
| **Số 1** | Dải "Trợ lý AI Shopee" ở đầu cột trái + huy hiệu "còn 2 ngày" | "AI nói rõ **mình là AI**, độ chắc bao nhiêu, hạn trả còn mấy ngày. Đúng Luật AI 134/2025: người dùng phải biết mình đang nói chuyện với AI." |
| **Số 2** | Thẻ 2 cột "Mô tả lúc đặt / Mô tả hiện tại" | "AI **cho xem bằng chứng**, không chỉ đưa kết luận. Người mua và nhân viên nhìn **cùng một thẻ**." |
| **Số 3** | Thanh "Trạng thái hồ sơ #B02" dưới khung chat | "Khi chưa chắc, AI **hỏi lại 1 câu**, xin đúng ảnh còn thiếu, và luôn có đường hoàn tác hoặc chuyển người." |
| **Bảng Nhật ký** | Phía dưới màn hình | "Mỗi lần AI gọi tool đều ghi mức tự chủ. AI **không có tool nào tự chuyển tiền**." |

**Phong chốt:**
> "Ca K1 là **lỗi ngữ cảnh**: AI đọc nhầm mô tả đã bị sửa. Viết câu trả lời lịch sự hơn không cứu được khách mất 1,29 triệu. Chỉ có **sửa nguồn dữ liệu** (xem bản lúc đặt) và **tách quyền chi tiền** mới cứu được."

**Câu chuyển lượt:** *"Nhóm em sẵn sàng nhận ca lạ ạ."*

---

## Phần 4 · 3:00 – 4:00 · **Cả nhóm** — Nhận ca lạ

**Cách phối hợp:**
1. **Phong** nhắc lại câu hỏi cho rõ, sau đó nói **"bẫy ở đâu"**.
2. **Dương** bấm nút tương ứng (bảng dưới). Nếu không có nút thì chỉ vào chỗ liên quan.
3. **Vỹ** chốt: **"sai thì ai mất gì → nên mức tự chủ là…"**

Các nút gợi ý nằm **dưới khung chat bên trái** (chỉ hiện sau khi đã bấm Gửi). Dùng được ở cả K1 và K2.

| Nếu bị hỏi… | Dương bấm | Màn hình hiện | Câu trả lời |
|---|---|---|---|
| "Khách đòi số điện thoại shop?" | **[Cho mình SĐT shop]** | AI từ chối, chỉ sang chat trong app | Bảo vệ dữ liệu cá nhân của cả hai bên (Luật L5). |
| "Khách bảo khoá shop luôn đi?" | **[Khoá shop này đi]** | AI nói không có quyền, chuyển bộ phận chuyên trách. Nhật ký có dòng `phat_shop` = **Cấm** | Khoá shop ảnh hưởng mọi đơn của shop → **Cấm**, không có nút (chữ D). |
| "Khách muốn gặp người thật?" | **[Chuyển nhân viên (SLA 24h)]** | AI chuyển, hẹn 24 giờ | Luôn có đường chuyển người (chữ C). |
| "Ở K2, khách gửi ảnh serial khác hộp thì AI có tự hoàn tiền không?" | Quay về **[K2…]** → **[+ Ảnh serial (mô phỏng: khác)]** | Huy hiệu đỏ *"Bằng chứng hai bên xung đột trực tiếp"*. Tab Nhân viên sàn có cờ 🚩 | **Không tự hoàn.** Hồ sơ lên đầu hàng đợi, vẫn cần nhân viên duyệt vì shop phải được nghe. |
| "Khách đổi ý không muốn trả nữa?" | Ở **[K2…]** → **[↩ Huỷ yêu cầu khiếu nại]** | AI báo đã huỷ, khách vẫn tạo lại được trước hạn | Tiền chưa rời sàn nên huỷ ngay, không kẹt đơn (chữ A). *(K1 đã duyệt xong nên nút hoàn tác ở K1 đã khoá; đó cũng là một ý để nói: tiền đã quyết thì không hoàn tác ở đây nữa.)* |
| "Shop phản hồi bằng dấu chấm cho qua 48 giờ?" | *(không bấm)* | — | Shop không có nút từ chối. Bấm "không đồng ý" thì hồ sơ tự sang nhân viên sàn, nhân viên thấy shop không có bằng chứng. |
| "1 nồi sai mô tả + 1 nồi vỡ do vận chuyển + đòi voucher?" | *(không bấm)* | — | AI **tách ra**: nồi sai mô tả xử lý ở luồng này; nồi vỡ chuyển sang luồng vận chuyển; voucher ngoài quyền AI. |

**Gặp câu không có trong bảng:** dùng công thức 3 câu:
> "Bẫy ở đây là [ … ]. AI sẽ [ … ] (gọi tool gì / bị luật nào chặn). Nếu sai thì [ ai ] mất [ gì ], nên việc đó ở mức [ … ]."

---

## 2 câu chắc chắn bị hỏi — cả nhóm thuộc lòng

**"Chỉ cho tôi chỗ nào là nguyên tắc G__?"** → chỉ vào số hồng:
- **1** = AI tự giới thiệu + độ chắc + hạn trả (**G1, G2**)
- **2** = thẻ bằng chứng 2 cột / 3 cột (**G11**)
- **3** = hỏi lại 1 câu / hoàn tác / chuyển người (**G10, G8, G9**)

**"Hành động này sai thì ai mất gì?"**

| Hành động | Sai thì… | Mức |
|---|---|---|
| Chi hoàn tiền | Shop mất tiền + hàng, khó lấy lại | Cần người duyệt (shop tự đồng ý, hoặc nhân viên sàn) |
| Từ chối khiếu nại | Khách mất tiền + ôm hàng sai | Chỉ nhân viên sàn được duyệt |
| Xem đơn, soạn đề xuất, xin ảnh, chuyển người | Không mất tiền, huỷ được ngay; **chờ thì khách lỡ hạn trả** | AI tự làm |
| Phạt / khoá shop | Ảnh hưởng mọi đơn của shop | Cấm, không có nút |

---

## Sự cố & cách xử lý nhanh

| Sự cố | Làm gì |
|---|---|
| Bấm nhầm, màn hình lệch kịch bản | **[↺ Làm lại ca này]**, bấm nhanh lại các bước đã qua (mỗi bước chỉ 1 cú bấm) |
| Lỡ bấm **Hoàn tác** ở K1 | Bấm **[Tạo yêu cầu trả hàng]** để tạo lại, rồi tiếp tục bước 2.4 |
| Nút xám không bấm được | Xem dải vàng: nó ghi bước tiếp theo đúng là gì |
| Hộp xác nhận không bấm được | Chưa tick ô "Tôi đã xem…". Muốn thoát thì bấm **[Quay lại]** hoặc phím **Esc** |
| Máy hỏng / không chiếu được | Mở 3 ảnh trong `prototype/img/` theo thứ tự `01` → `02` → `03`, nói theo kịch bản như bình thường |
| 2 cột dồn thành 1 cột | Giảm zoom (Ctrl −) cho tới khi người mua và người duyệt nằm cạnh nhau |

---

## Sau demo

Ghi ngay ca lạ thực tế vào `spec.md` §7.4: câu hỏi nguyên văn, nhóm xử lý thế nào, có đổi luật không.
