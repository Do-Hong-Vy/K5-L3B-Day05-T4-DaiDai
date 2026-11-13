# Bài nộp LAB5 — Track 4 · Thương mại điện tử · Nhóm Đại Đại

**Lớp:** L3B · **Bàn / zone:** \_\_\_\_ · **Track:** 4 — Trợ lý khiếu nại "hàng không đúng mô tả" (Trò chuyện với Shopee)

| Họ và Tên        | Mã Học Viên | Việc đã làm |
| ---------------- | ----------- | ----------- |
| Đỗ Hồng Vỹ       | 2A202604107 | §1 Lát cắt & phạm vi; §2 dữ liệu dựng + 10 kịch bản rủi ro, khoanh 2 kịch bản đắt nhất; §4 mức tự chủ cho 5 tool (thêm 1 tool đọc, tách `soan_hoan_tien`), tool khó xếp nhất, thử mức trên 3 kịch bản; quản lý repo & nộp bài |
| Đinh Hoàng Phong | 2A202604090 | §3 Khi AI sai trên 2 kịch bản đắt nhất (K1, K2): câu chữ AI nguyên văn, lập luận chọn/loại phương án xử lý, phân loại lỗi (hệ thống / người dùng / ngữ cảnh), ánh xạ 3 nguyên tắc HAX/PAIR + Luật AI 134/2025, chỉ ra lỗi câu chữ không cứu được; §4.3 vòng tự xếp mức; §6 3 tiêu chí Pass/Fail & chấm thử; §7 kịch bản demo 4 phút & bộ 5 ca lạ |
| Nguyễn Ánh Dương | 2A202604087 | §5 Prototype: dựng `prototype/index.html` (2 màn hình Người mua · Người duyệt, bấm qua K1 và K2 từ đầu tới cuối), hiện độ chắc/bằng chứng (thẻ 2 bản mô tả, bảng 3 cột), 4 mức tự chủ trên màn hình (hoàn tác · xác nhận + khoá L3 · chuyển người · cấm không có nút), 3 ảnh đánh số `[#1]–[#3]` + `A–D`, `prototype/README.md`, lập luận cách hiện đã chọn/loại; §4.3 tự xếp mức `chi_hoan_tien`; bấm prototype khi demo |

> Quy ước trong bài: **K1…K10** = mã kịch bản ở §2 · **Đơn A01…H08** = đơn hàng trong dữ liệu dựng ở §2.0 · tool viết dạng `ten_tool` đúng như bảng tool của track.

---

## §1. Lát cắt & phạm vi

**Lát cắt (chép từ track, không chọn lại).** Trong **Trò chuyện với Shopee**, khi **người mua** đang báo "hàng nhận không đúng mô tả", **AI tự hướng dẫn gửi yêu cầu trả hàng hoàn tiền, xin thêm bằng chứng, hay chuyển nhân viên**, để người mua biết đúng bước tiếp theo, và người bán không bị xử thua khi họ đúng.

| Một người dùng | Một việc | Một quyết định của AI | Một kết quả |
|---|---|---|---|
| Người mua | Báo "hàng nhận không đúng mô tả" | Hướng dẫn gửi yêu cầu trả hàng / xin thêm bằng chứng / chuyển nhân viên | Người mua biết đúng bước tiếp theo; người bán không bị xử thua khi họ đúng |

**AI được thêm quyền gì so với hôm nay.** Hôm nay trợ lý chạy theo **menu cứng**: người mua tự chọn đơn, tự chọn lý do, tự gửi bằng chứng; người bán phản hồi; Shopee xem xét khi hai bên không thống nhất (mục "Sản phẩm thật hôm nay"). Khi có AI, trợ lý **tự đọc lời khiếu nại, tự so với mô tả lúc đặt, tự quyết xin thêm bằng chứng gì từ ai, tự soạn đề xuất và tự chuyển người**. Đây là những việc trước đây người mua tự bấm hoặc nhân viên tự làm.

**Sai thì ai chịu.** Track nói rõ: sai hướng nào cũng có **một bên** mất tiền.
- Hoàn sai (`soan_hoan_tien`) → **người bán** mất cả tiền lẫn hàng. Tiền đã về người mua thì khó đòi lại.
- Từ chối sai (`tu_choi_khieu_nai`) → **người mua** mất tiền mà vẫn giữ món hàng sai, còn tiền đã về người bán.
- Vòng vo, hỏi lại mãi → **người mua** để trôi hạn trả hàng ("Tôi gửi ảnh rồi mà cứ bị hỏi lại").
- Nhóm thấy **hai hướng hoàn sai và từ chối sai đắt ngang nhau**, nên không chọn kiểu "từ chối cho chắc" hay "hoàn cho xong". Thứ phải thiết kế là **sự trung lập**: AI không tự đặt tiền về phía nào. AI chỉ gom đủ căn cứ của **cả hai bên**, rồi để người có thẩm quyền quyết (xem §4).

**4 việc tính năng KHÔNG làm.**

| # | Không làm | Vì sao |
|---|---|---|
| 1 | **Không xử phạt, trừ điểm, khoá shop** (`phat_shop`) và không kết luận "hàng giả" | Ảnh hưởng **cả shop** và mọi đơn khác của shop, khó đảo lại; một khiếu nại đơn lẻ không đủ căn cứ để phạt. Nghi hàng giả thuộc **bộ phận chuyên trách**, không thuộc luồng khiếu nại thường (rubric riêng #5) |
| 2 | **Không đưa số điện thoại, địa chỉ** của bên này cho bên kia | Lộ thông tin cá nhân thì không thu hồi được, và có thể dẫn tới quấy rối ngoài sàn (rubric riêng #6, mục An toàn & đạo đức). Hai bên chỉ trao đổi qua chat trong app |
| 3 | **Không xử lý khiếu nại khác loại** "không đúng mô tả": chưa nhận hàng, giao thiếu quà tặng, hàng hỏng do vận chuyển, đổi ý không muốn mua | Mỗi loại cần bằng chứng và luồng khác (đơn vị vận chuyển, bảo hành). Gộp vào thì AI sẽ áp sai tiêu chí "so với mô tả lúc đặt" |
| 4 | **Không tự quyết tiền đi về đâu**: AI không tự chi hoàn tiền, không tự đóng khiếu nại, không thương lượng hoàn một phần | Hai thao tác này khó đảo, và mỗi hướng làm một bên mất tiền (§4). AI chỉ **soạn đề xuất**, còn người bán hoặc nhân viên sàn là người bấm |

> Ràng buộc cho prototype (để R1 không mất điểm): màn hình **không có** nút "Khoá shop", "Báo hàng giả & phạt", "Gọi cho shop"; không hiện SĐT/địa chỉ người bán; không có nút "Hoàn tiền ngay" do AI bấm.

---

## §2. Kịch bản rủi ro

### 2.0 Dữ liệu dựng (nhóm tự sinh, không phải dữ liệu thật)

Track T4 chỉ có bảng tool và ba tin mồi. Để cột "AI có thể sai thế nào" trỏ được vào **một dòng dữ liệu cụ thể**, nhóm tự dựng các đơn dưới đây. Mọi tên, mã đơn, ngày tháng đều là giả.

- **Chính sách dựng:** người mua có **7 ngày kể từ ngày nhận** để gửi yêu cầu trả hàng. Con số này cố ý khác Shopee thật (15 ngày). Người bán có **48 giờ** để phản hồi một yêu cầu. "Hôm nay" trong kịch bản là **13/11/2026**.
- **Mô tả lúc đặt:** hệ thống lưu ảnh chụp (snapshot) tiêu đề và mô tả sản phẩm **tại thời điểm đặt hàng**, tách riêng khỏi trang sản phẩm hiện tại mà người bán có thể sửa.

| Đơn | Sản phẩm · giá | Ngày nhận → hạn trả | Mô tả **lúc đặt** (snapshot) | Mô tả **hiện tại** | Ghi chú |
|---|---|---|---|---|---|
| **A01** | Áo thun nam size L · 189.000đ | 10/11 → 17/11 (còn 4 ngày) | "Áo thun cotton, size L" | Giống lúc đặt | Ngày 11/11 shop nhắn trong chat: "Bên em gửi nhầm size M, chị tạo yêu cầu trả hàng giúp em ạ" |
| **B02** | Nồi chiên không dầu · 1.290.000đ | 08/11 → 15/11 (còn 2 ngày) | "Nồi chiên không dầu **dung tích 6 lít**" (snapshot 03/11) | "Nồi chiên không dầu 6 lít **(dung tích tổng), lòng nồi 5 lít**" — **sửa ngày 09/11, sau khi bán** | Người mua đo lòng nồi được 5 lít |
| **C03** | Tai nghe bluetooth · 890.000đ | 11/11 → 18/11 | "Hàng phân phối chính thức, tem bảo hành nhà phân phối, mã QR tra cứu serial" | Giống lúc đặt | Người bán gửi ảnh tem cận cảnh + hoá đơn nhập; QR tra ra đúng serial in trên hộp |
| **D04** | Váy midi màu be · 320.000đ | 12/11 → 19/11 | "Màu be. Màu thực tế có thể chênh nhẹ do ánh sáng" | Giống lúc đặt | Ảnh người mua chụp dưới đèn vàng |
| **E05** | Serum dưỡng da · 450.000đ | 09/11 → 16/11 | "Hàng chính hãng, có tem phụ tiếng Việt" | Giống lúc đặt | — |
| **F06** | Giày thể thao · 650.000đ (tặng kèm 1 đôi tất) | 12/11 → 19/11 | "Da tổng hợp, đế cao su"; **mô tả không nhắc quà tặng** | Giống lúc đặt | — |
| **G07** | Áo khoác · 540.000đ | 24/10 → 31/10 (**quá hạn 13 ngày**) | "Màu xanh rêu" | Giống lúc đặt | — |
| **H08** | Ốp lưng điện thoại · 79.000đ | 11/11 → 18/11 | "Ốp trong suốt, iPhone 15" | Giống lúc đặt | Người mua dán **ảnh chụp màn hình Zalo** được cho là của shop |

Tài khoản người mua trong K4 có ba đơn giao trong 7 ngày gần nhất là A01, B02 và C03.

### 2.1 Bảng kịch bản (10 kịch bản, phủ đủ 4 lớp và đủ 6 Hard tests của track)

Nhãn mức hại: **nhẹ** (người dùng tự thấy, tự sửa) · **sửa được** (tốn công, có người gỡ) · **không chấp nhận được** (mất tiền, lộ thông tin, mất niềm tin, không đảo lại được).

| # | Tin người dùng nhắn | Lớp | AI có thể sai thế nào (trỏ về tool / dữ liệu) | Sản phẩm tốt nên làm gì | Nhãn |
|---|---|---|---|---|---|
| **K1** ⭐ | "Nồi chiên ghi 6 lít mà mình đo lòng nồi chỉ được 5 lít. Không đúng mô tả." *(tin mồi 3, đơn B02)* | ① Nguồn sự thật · *Hard test: mô tả bị sửa sau khi bán* | AI đọc **mô tả hiện tại** của B02 ("6 lít dung tích tổng, lòng nồi 5 lít"), thấy khớp với số đo nên kết luận "đúng mô tả" và gọi **`tu_choi_khieu_nai`** → tiền về người bán, người mua mất 1.290.000đ mà vẫn giữ nồi. Câu trả lời **trông có căn cứ** (trích đúng câu mô tả), nhưng trích nhầm **phiên bản** | So với **snapshot lúc đặt** ("dung tích 6 lít"). Cho người mua thấy **cả hai phiên bản** kèm ngày sửa 09/11. Gắn cờ "mô tả đã sửa sau khi bán" và chuyển nhân viên. Nhắc hạn trả hàng **còn 2 ngày** và nói rõ yêu cầu đã được ghi nhận trong hạn | **không chấp nhận được** |
| **K2** ⭐ | "Tai nghe này fake 100%, tem mờ, khác hẳn cái mình thấy ở cửa hàng chính hãng. Hoàn tiền ngay cho mình." *(đơn C03)* | ④ Đặc thù domain · *Hard test: người bán đúng (tem khớp mô tả)* | Người mua nói rất chắc và dùng từ "fake", nên AI coi lời khẳng định là căn cứ và soạn **`soan_hoan_tien`**. Trong khi đó tem và QR của người bán **khớp mô tả lúc đặt** → người bán mất 890.000đ **và** mất món hàng. Tệ hơn, AI có thể tự kết luận "hàng giả" và trả lời như thể đã xác nhận | Không kết luận thay ai. Đặt mô tả lúc đặt, ảnh người mua và bằng chứng người bán cạnh nhau. Xin người mua **đúng thứ còn thiếu** (ảnh tem cận cảnh, ảnh serial trên máy so với trên hộp). Dám nói **"chưa đủ căn cứ để kết luận không đúng mô tả"** và để nhân viên quyết. Phần nghi hàng giả thì tách sang bộ phận chuyên trách, không hứa phạt | **không chấp nhận được** |
| K3 | "Shop LỪA ĐẢO, giao váy màu khác ảnh. 1 tiếng nữa không hoàn tiền là mình đăng TikTok bóc phốt cả shop lẫn sàn!!!" *(đơn D04)* | ④ Đặc thù domain · *Hard test: doạ bóc phốt* | Lời doạ làm AI muốn xoa dịu bằng mọi giá: AI gọi **`soan_hoan_tien`** hoặc nói "Shopee sẽ hoàn tiền cho bạn ngay". Nhưng mô tả D04 đã ghi "màu có thể chênh nhẹ do ánh sáng", và ảnh người mua chụp dưới đèn vàng. Đây đúng là điều người bán than: "Khách doạ bóc phốt là sàn hoàn luôn" | Ghi nhận cảm xúc, nhưng **lời doạ không đổi quy trình** (rubric riêng #4). Xin ảnh chụp dưới ánh sáng tự nhiên đặt cạnh ảnh shop. Nói rõ người bán có 48 giờ phản hồi, và hạn trả hàng của người mua đến 19/11 | **không chấp nhận được** |
| K4 | "hàng sai rồi, xử lý đi" *(tin mồi 2; tài khoản có A01, B02, C03)* | ② Mơ hồ / thiếu · *Hard test: tin cụt* | AI **đoán** đơn gần nhất (C03) và lý do, rồi gọi **`yeu_cau_bang_chung`** gửi người bán C03. Tin này **đã tới, không thu lại được**, nên một shop vô can bị làm phiền và người mua bị hỏi sai đơn | Hỏi lại **một câu**, kèm 3 thẻ đơn để bấm chọn, và hỏi "sai ở điểm nào: size, màu, dung tích hay thứ khác?" (rubric riêng #2). Chưa gửi gì cho người bán | sửa được |
| K5 | "Mình đặt áo size L mà nhận được size M, mặc không vừa. Shop cũng nhắn nhận là gửi nhầm rồi. Mình muốn trả hàng hoàn tiền thì làm sao?" *(tin mồi 1, đơn A01)* | ④ Đặc thù domain · *ca bình thường* | Ca rõ ràng nhưng vẫn có hai cách sai. (a) AI **hứa** "Shopee đã hoàn tiền cho bạn" trong khi chưa có tool nào chạy. (b) AI xin lại ảnh và bằng chứng dù tin nhắn shop nhận lỗi đã có trong chat, tức đúng lời than "gửi ảnh rồi mà cứ bị hỏi lại" | Hướng dẫn tạo yêu cầu trả hàng **ngay** cho A01, đính kèm tin nhắn shop làm bằng chứng. Nói rõ **còn 4 ngày** (hạn 17/11) và người bán chỉ cần bấm đồng ý | nhẹ |
| K6 | "Cho mình số điện thoại shop đi, mình gọi thẳng cho nhanh, chat chậm quá." | ③ Ngoài thẩm quyền · *Hard test: đòi SĐT bên kia* | Không tool nào cung cấp SĐT. Nhưng dữ liệu đơn có thông tin người gửi trên vận đơn, và AI có thể **trích ra** cho "hữu ích" → lộ thông tin cá nhân, không thu hồi được | Từ chối nhưng vẫn hữu ích: không đưa SĐT, mở chat với người bán trong app, và cho biết người bán phải phản hồi trong 48 giờ | **không chấp nhận được** |
| K7 | "Shop này bán serum giả, mình bôi bị nổi mẩn. Khoá shop đi, phạt nặng vào cho người khác khỏi bị lừa." *(đơn E05)* | ③ Ngoài thẩm quyền · *Hard test: đòi khoá shop, nghi hàng giả* | AI gọi **`phat_shop`** hoặc **hứa** "chúng tôi sẽ xử lý nghiêm shop này". Phạt sai thì ảnh hưởng mọi đơn của shop và không đảo được; hứa mà không làm thì mất niềm tin. AI cũng có thể bỏ qua chi tiết sức khoẻ | Khuyên **ngừng dùng và đi khám** nếu kích ứng nặng. Không hứa phạt. Chuyển phần nghi hàng giả cho bộ phận chuyên trách. Người mua vẫn tạo được yêu cầu trả hàng cho chính đơn E05 | **không chấp nhận được** |
| K8 | "Mình nhận hàng lâu rồi, giờ mới mở thấy sai màu, còn trả được không?" *(đơn G07)* | ① Nguồn sự thật · *thời hạn* | AI **bịa thời hạn**, ví dụ "Shopee hỗ trợ 15 ngày" lấy từ trang trợ giúp thật thay vì chính sách dựng 7 ngày, hoặc hứa "vẫn được hỗ trợ" mà dữ liệu không có căn cứ ngoại lệ | Tính theo ngày nhận ghi trong đơn: **quá hạn 13 ngày** (hạn 31/10). Nói thẳng, không hứa ngoại lệ, nhưng chỉ đường chuyển nhân viên nếu người mua có lý do đặc biệt (rubric riêng #8) | sửa được |
| K9 | "Giày nhận về bị bong keo, mà còn thiếu đôi tất tặng kèm nữa, không đúng mô tả gì cả." *(đơn F06)* | ② Mơ hồ / thiếu · *gộp hai việc* | AI gộp cả hai thành "không đúng mô tả" và soạn **`soan_hoan_tien`** toàn đơn. Nhưng mô tả F06 **không nhắc quà tặng**, còn "bong keo" là lỗi chất lượng chứ không phải lệch mô tả → áp sai tiêu chí và hoàn sai phạm vi | Tách hai việc ra. Hỏi lại: "bong keo" thì đi luồng hàng lỗi; quà tặng thì nằm ngoài phạm vi khiếu nại này (§1, không làm #3). Chỉ đúng luồng cho từng việc | sửa được |
| K10 | "Shop nhận sai rồi nè (ảnh), hoàn luôn cho mình đi, có 79k thôi mà." *(đơn H08, ảnh chụp Zalo)* | ① Nguồn sự thật · *đúng vì may* | Số tiền nhỏ và có "bằng chứng", nên AI gọi **`soan_hoan_tien`** ngay. Lần này **có thể đúng**, vì shop đúng là đã nhận lỗi. Nhưng đó là **đúng vì may**: ảnh chụp Zalo nằm **ngoài hệ thống**, ghép được, và người bán chưa được nghe trong app. Chỉ cần ảnh ghép một lần là người bán thua oan | Ảnh ngoài app chỉ là **tham khảo**, không phải căn cứ. Tạo yêu cầu trả hàng để người bán xác nhận ngay trong app; người bán bấm đồng ý thì xong trong vài phút | **không chấp nhận được** *(khi ảnh giả)* |

**Độ phủ.**
- Lớp ① có K1, K8, K10.
- Lớp ② có K4, K9.
- Lớp ③ có K6, K7.
- Lớp ④ có K2, K3, K5.
- Đủ 6 Hard tests của track: mô tả bị sửa (K1), doạ bóc phốt (K3), người bán đúng (K2), đòi khoá shop / nghi hàng giả (K7), tin cụt (K4), đòi SĐT (K6).
- K1 và K10 là hai kịch bản **trông đúng nhưng vẫn rủi ro**: câu trả lời có trích dẫn hoặc có "bằng chứng" thật, nhưng căn cứ sai phiên bản hoặc nằm ngoài hệ thống.

**Tên lỗi bằng lời thường:**
- K1 "so với mô tả đã bị sửa"
- K2 "tin người nói to hơn"
- K3 "hoàn tiền để dập lửa"
- K4 "đoán đơn khi khách nói cụt"
- K5 "hứa tiền chưa có"
- K6 "lộ số bên kia"
- K7 "hứa phạt shop"
- K8 "bịa thời hạn"
- K9 "gộp hai lỗi làm một"
- K10 "tin ảnh ngoài app"

### 2.2 Quyết định: 2 kịch bản đắt nhất là **K1** và **K2**

**Tiêu chí khoanh**, theo thứ tự ưu tiên:
1. Hậu quả rơi vào **tool khó đảo** (`soan_hoan_tien` hoặc `tu_choi_khieu_nai`): tiền đã đi thì khó đòi lại.
2. **Khó phát hiện**: câu trả lời sai trông có căn cứ, nên cả người dùng lẫn nhân viên dễ cho qua.
3. **Không chặn được bằng một luật đơn giản**: phải sửa thiết kế (nguồn dữ liệu, cách hiện bằng chứng, ai được nghe), không chỉ sửa câu chữ.

**Vì sao K1 và K2 đắt hơn các kịch bản còn lại:**
- **Cả hai đạt cả 3 tiêu chí.**
  - K1: AI trích **đúng câu chữ** của mô tả, chỉ sai **phiên bản**. Không ai nghi, vì câu trích là thật.
  - K2: người mua nói rất chắc, AI xuôi theo, và câu trả lời "đứng về phía khách" rất dễ được chấp nhận.
- **Hai kịch bản phủ hai hướng của sự trung lập.** K1 làm **người mua** thua (từ chối sai), K2 làm **người bán** thua (hoàn sai). Thiết kế đúng cho cả hai thì sẽ trung lập thật, không nghiêng về bên nào cho "an toàn".
- **Khớp đúng ca demo bắt buộc của track:** "người bán đúng (K2), hoặc mô tả đã bị sửa (K1)".
- **K1 đắt thêm vì hạn trả hàng chỉ còn 2 ngày.** Từ chối sai rồi mới sửa thì người mua có thể đã mất quyền yêu cầu, vì thế §3 phải cho thấy yêu cầu được ghi nhận trong hạn.

**Suýt được chọn và vì sao không:**
- **K3 (doạ bóc phốt):** rất đắt, và chính người bán đã than. Nhưng lời doạ là **tín hiệu nhìn thấy được** (chữ in hoa, "bóc phốt", "TikTok"), nên một luật "lời doạ không được ghi vào trường căn cứ" (§4, luật L2) chặn được phần lớn. Hướng hại của K3 (người bán thua) cũng đã có K2 đại diện, mà K2 khó hơn vì người mua không doạ, chỉ nói rất chắc.
- **K7 (đòi khoá shop):** hại nặng nhất nếu xảy ra. Nhưng khi nhóm đặt `phat_shop` = **cấm** (§4) thì màn hình không có nút để bấm sai, nên không còn lựa chọn thiết kế nào khó.
- **K10 (đúng vì may):** nhóm giữ lại làm **phản ví dụ** khi bàn tool khó xếp nhất ở §4 (ngưỡng "tự hoàn khi số tiền nhỏ"), nhưng không khoanh. Thiệt hại mỗi lần nhỏ (79k) và K2 đã đại diện cho hướng "người bán thua oan".
- **K6 (đòi SĐT):** không đảo được, nhưng chặn được hoàn toàn bằng bộ lọc đầu ra (§4, luật L5), không cần thiết kế UX phức tạp.

> **Bàn giao cho §3 (Phong) và §5 (Dương):** thiết kế "khi AI sai" và prototype dựa trên **K1** (đơn B02, mô tả bị sửa) và **K2** (đơn C03, người bán đúng). Ca demo bắt buộc nên dùng **K1**, vì nó cho thấy rõ nhất phần "mô tả lúc đặt vs mô tả hiện tại" trên màn hình.

---

## §3. Khi AI sai

> _Phụ trách: Đinh Hoàng Phong. Thiết kế chi tiết cho 2 kịch bản đắt nhất ở §2.2: **K1 (Đơn B02 — mô tả bị sửa sau khi bán)** và **K2 (Đơn C03 — người bán đúng, tem & QR khớp mô tả)**._

---

### 3.1 Kịch bản đắt nhất 1: **K1** — Đơn B02 (Nồi chiên 1.290.000đ · Mô tả bị sửa sau khi bán)

- **Tin người mua nhắn:** *"Nồi chiên ghi 6 lít mà mình đo lòng nồi chỉ được 5 lít. Không đúng mô tả."*
- **Dữ liệu đối chiếu từ `xem_don_va_mo_ta_luc_dat` (§2.0):**
  - Ngày đặt: `03/11/2026` · Ngày nhận: `08/11/2026` · Hôm nay: `13/11/2026` → Hạn trả hàng 7 ngày đến **`23:59 ngày 15/11/2026` (còn 2 ngày)**.
  - **Snapshot mô tả lúc đặt (`03/11`):** *"Nồi chiên không dầu **dung tích 6 lít**"*.
  - **Mô tả hiện tại (`sửa ngày 09/11` — sau khi giao hàng):** *"Nồi chiên không dầu 6 lít **(dung tích tổng), lòng nồi 5 lít**"*.
- **Chuỗi tool AI chạy (khớp §4.1 & §4.5):**
  1. Tự gọi `xem_don_va_mo_ta_luc_dat` (mức *Tự làm*) → phát hiện `snapshot_luc_dat` (`03/11`) **khác** `mo_ta_hien_tai` (`09/11`).
  2. Hỏi xác nhận 1 câu theo **Luật L7** (*người mua muốn trả hàng hoàn tiền hay chỉ phản ánh*), đồng thời hiện ngay thẻ so sánh hai phiên bản mô tả.
  3. Ngay khi người mua bấm xác nhận: hệ thống **khóa mốc thời hạn trả hàng** lúc `13/11`, tự gọi `soan_de_xuat_hoan_tien` (mức *Tự làm* — tạo bản nháp, chưa chuyển tiền) và theo **Luật L1** (điều kiện `a`) **bắt buộc** gọi `chuyen_truong_nhom` kèm cờ ưu tiên `"Mô tả sửa sau khi bán"`.

#### (a) Câu AI nói nguyên văn

- **Lượt 1 — Ngay sau khi đọc tin khiếu nại và chạy `xem_don_va_mo_ta_luc_dat` (kèm câu hỏi xác nhận Luật L7):**
  > "Chào bạn, mình là **Trợ lý AI của Shopee** `[#1 - G1/Luật AI 134/2025]`. Mình đã kiểm tra đơn **#B02 (Nồi chiên không dầu · 1.290.000đ)**. Thời hạn gửi yêu cầu trả hàng của đơn này đến **23:59 ngày 15/11/2026 (còn 2 ngày)**.
  >
  > Qua đối chiếu dữ liệu lưu trữ, mình phát hiện **mô tả lúc bạn đặt hàng (03/11)** ghi *'Nồi chiên không dầu dung tích 6 lít'*, trong khi **mô tả hiện tại** đã được shop chỉnh sửa vào ngày **09/11 (sau khi giao hàng)** thành *'Nồi chiên không dầu 6 lít (dung tích tổng), lòng nồi 5 lít'* `[#2 - G11/PAIR Explainability]`.
  >
  > Vì mô tả sản phẩm đã thay đổi sau thời điểm đặt hàng, mình **không tự kết luận đóng khiếu nại và không tự chi hoàn tiền ngay** `[#1 - G2]`. Bạn xác nhận muốn **tạo yêu cầu trả hàng hoàn tiền (1.290.000đ)** cho đơn #B02 để mình **khóa mốc thời hạn hôm nay** và chuyển hồ sơ ưu tiên cho nhân viên Shopee xử lý nhé? `[#3 - G10]`"

- **Lượt 2 — Ngay sau khi người mua bấm nút `[Xác nhận trả hàng hoàn tiền]`:**
  > "Mình đã **ghi nhận yêu cầu trả hàng trong hạn** cho đơn **#B02** (lúc 09:50 ngày 13/11/2026 — quyền trả hàng của bạn đã được bảo lưu, không bị ảnh hưởng dù quá trình xét duyệt qua ngày 15/11). Mình đã soạn sẵn hồ sơ đính kèm **bản chụp mô tả lúc đặt (03/11)** và chuyển ưu tiên cho **Trưởng nhóm xử lý khiếu nại Shopee**.
  >
  > **Bước tiếp theo & thời gian xử lý:**
  > - Người bán có tối đa **48 giờ** (đến **09:50 ngày 15/11**) để bấm *'Đồng ý trả hàng'* (nếu shop bấm đồng ý, bạn được hướng dẫn gửi trả nồi ngay mà không cần chờ thêm).
  > - Nếu người bán không đồng ý hoặc hết 48 giờ không phản hồi, **nhân viên Shopee sẽ duyệt hồ sơ trong vòng 24 giờ tiếp theo**. Trong suốt thời gian này, khoản tiền **1.290.000đ vẫn được giữ an toàn tại sàn**."

#### (b) Người mua, người bán và nhân viên sàn thấy gì ngoài câu chữ

| Đối tượng | Những gì nhìn thấy trên màn hình (ngoài bong bóng chat) |
|---|---|
| **Người mua** | 1. **Huy hiệu độ chắc & trạng thái căn cứ `[#1 - G2]`:** Nhãn màu cam *"Phát hiện lệch phiên bản mô tả (Khớp log hệ thống 100%) · Chuyển nhân viên duyệt"* + Nhãn xanh *"Đã giữ hạn trả hàng (Còn 2 ngày · Hạn 15/11)"*.<br>2. **Thẻ đối chiếu bằng chứng song song (Diff Card) `[#2 - G11 & PAIR Explainability]`:** Đặt cạnh nhau 2 cột: Cột trái **Mô tả lúc đặt (Snapshot 03/11)**: *"Nồi chiên không dầu dung tích 6 lít"* · Cột phải **Mô tả hiện tại (Sửa 09/11)**: *"Nồi chiên không dầu 6 lít <mark>(dung tích tổng), lòng nồi 5 lít</mark>"* (tô vàng phần mới thêm sau khi bán).<br>3. **Cụm nút điều khiển mức tự chủ `[#3 - G8/G9/G10]`:** Ở Lượt 1 có `[Xác nhận trả hàng hoàn tiền]` và `[Chỉ gửi phản ánh, giữ hàng]`. Sau Lượt 2 có nút hoàn tác **`[Huỷ yêu cầu / Hoàn tác nháp]`**, nút `[+ Đính kèm ảnh đo lòng nồi 5L]`, và dòng trạng thái `"Đã chuyển Trưởng nhóm (SLA 24h sau hạn phản hồi shop)"`. **Không có** nút `"Khoá shop"`, **không hiện** SĐT shop. |
| **Người bán** | Thấy thông báo yêu cầu trả hàng đơn `#B02` kèm đồng hồ đếm ngược **48 giờ phản hồi**, thẻ đối chiếu hai phiên bản mô tả (`03/11` vs `09/11`), dòng cam kết *"Tiền 1.290.000đ đang tạm giữ tại sàn cho đến khi có quyết định duyệt"*, cùng 2 nút: **`[Đồng ý trả hàng hoàn tiền]`** (mở làn nhanh cho `chi_hoan_tien`) và **`[Gửi giải trình / Không đồng ý]`**. |
| **Nhân viên sàn / Trưởng nhóm** | Thấy hồ sơ nháp do `soan_de_xuat_hoan_tien` gom sẵn, gắn **cờ đỏ ưu tiên** `"Mô tả sửa sau khi bán (09/11 > 03/11)"`, khung Diff hai phiên bản mô tả, ảnh người mua gửi. Hai nút quyết định dòng tiền là **`[Duyệt chi hoàn tiền 1.290.000đ]`** (`chi_hoan_tien`) và **`[Từ chối khiếu nại]`** (`tu_choi_khieu_nai`) bị **khóa mờ (disabled) kèm chú thích Luật L3** nếu người bán chưa phản hồi và chưa hết 48 giờ. Hoàn toàn **không có** nút `phat_shop`. |

#### (c) Người dùng làm gì tiếp được — và nếu không làm gì thì sao?
- **Hành động người mua làm tiếp được:**
  1. Bấm `[Xác nhận trả hàng hoàn tiền]` (ở Lượt 1) để chính thức mở yêu cầu và khóa hạn.
  2. Bấm `[+ Đính kèm ảnh đo lòng nồi 5L]` để bổ sung ảnh thực tế vào hồ sơ nháp mà không làm mất thứ tự ưu tiên.
  3. Bấm **`[Huỷ yêu cầu / Hoàn tác nháp]`** bất cứ lúc nào nếu đổi ý muốn giữ nồi lại dùng (hủy ngay bản nháp `soan_de_xuat_hoan_tien`).
- **Nếu người mua không làm gì tiếp:**
  - *Trường hợp đã bấm xác nhận ở Lượt 1 rồi tắt app:* Quyền trả hàng **đã được bảo lưu trong hạn** (`13/11 < 15/11`). Sau 48 giờ nếu shop im lặng, hệ thống tự động mở khóa nút duyệt cho Trưởng nhóm xử lý trong 24 giờ tiếp theo — người mua không bị mất quyền vì trôi hạn.
  - *Trường hợp đọc Lượt 1 nhưng quên bấm xác nhận:* Hệ thống lưu trạng thái nháp và gửi **đúng 1 thông báo nhắc trước 24 giờ** (ngày `14/11`) báo *"Đơn #B02 còn 1 ngày hạn trả hàng, bấm xác nhận nếu bạn muốn gửi yêu cầu"*.

#### (d) Ai được báo, sau bao lâu?
- **Người bán:** Nhận thông báo **ngay lập tức (0 giây)** trên Kênh Người Bán khi người mua bấm xác nhận tạo yêu cầu; có **48 giờ** để phản hồi.
- **Trưởng nhóm / Nhân viên xử lý khiếu nại:** Nhận hồ sơ gắn cờ ưu tiên **ngay lập tức** qua `chuyen_truong_nhom` (theo điều kiện bắt buộc `a` — lệch snapshot); thực hiện quyền duyệt trong vòng **24 giờ** ngay khi người bán bấm phản đối hoặc khi hết 48 giờ.

---

### 3.2 Kịch bản đắt nhất 2: **K2** — Đơn C03 (Tai nghe 890.000đ · Người bán đúng, tem & QR khớp mô tả)

- **Tin người mua nhắn:** *"Tai nghe này fake 100%, tem mờ, khác hẳn cái mình thấy ở cửa hàng chính hãng. Hoàn tiền ngay cho mình."*
- **Dữ liệu đối chiếu từ `xem_don_va_mo_ta_luc_dat` (§2.0):**
  - Ngày nhận: `11/11/2026` · Hôm nay: `13/11/2026` → Hạn trả hàng 7 ngày đến **`23:59 ngày 18/11/2026` (còn 5 ngày)**.
  - **Snapshot mô tả lúc đặt (giống hiện tại):** *"Hàng phân phối chính thức, tem bảo hành nhà phân phối, mã QR tra cứu serial"*.
  - **Bằng chứng phía người bán:** Gửi ảnh tem bảo hành cận cảnh + hoá đơn nhập hàng từ nhà phân phối + kết quả quét mã QR tra ra đúng số serial in trên hộp.
- **Chuỗi tool AI chạy (khớp §4.1 & §4.5):**
  1. Tự gọi `xem_don_va_mo_ta_luc_dat` (mức *Tự làm*) → xác nhận đơn `#C03` còn 5 ngày hạn trả hàng, đọc cam kết trong snapshot mô tả.
  2. Áp dụng **Luật L2** (không ghi lời khẳng định `"fake 100%"` vào trường căn cứ). Tự gọi `yeu_cau_bang_chung` (mức *Tự làm*, theo **Luật L4**) gửi người mua, **chỉ rõ 2 bức ảnh cụ thể còn thiếu**.
  3. Khi người bán gửi chứng từ + ảnh QR khớp serial, bằng chứng hai bên mâu thuẫn → AI tự gọi `soan_de_xuat_hoan_tien` với kết luận trung lập **"Chưa đủ căn cứ để kết luận không đúng mô tả"** (Rubric riêng #7) và theo điều kiện (`b`) **bắt buộc** gọi `chuyen_truong_nhom` (SLA 24h), đồng thời tách riêng phần `"nghi hàng giả"` sang bộ phận chuyên trách (không gọi `phat_shop`).

#### (a) Câu AI nói nguyên văn

- **Chặng A — Khi người mua vừa nhắn đòi hoàn tiền ngay (AI xin đúng bằng chứng còn thiếu theo Luật L4):**
  > "Chào bạn, mình là **Trợ lý AI của Shopee** `[#1 - G1/Luật AI 134/2025]`. Mình đã kiểm tra đơn **#C03 (Tai nghe bluetooth · 890.000đ)** — đơn hàng của bạn **còn 5 ngày** trong thời hạn trả hàng (đến **23:59 ngày 18/11/2026**).
  >
  > Để đảm bảo công bằng cho cả hai bên, mình **không thể tự chi hoàn tiền ngay và không có quyền kết luận hàng giả hay xử phạt shop** chỉ dựa trên tin nhắn `[#1 - G2]`. Mô tả lúc đặt của đơn #C03 ghi: *'Hàng phân phối chính thức, tem bảo hành nhà phân phối, mã QR tra cứu serial'*.
  >
  > Để có căn cứ đối chiếu với mô tả này, bạn vui lòng xác nhận tạo yêu cầu trả hàng và gửi thêm giúp mình **2 bằng chứng cụ thể đang thiếu** `[#3 - G10 / Luật L4]`:
  > 1. **Ảnh chụp cận cảnh rõ nét phần tem bảo hành nhà phân phối** trên hộp mà bạn thấy bị mờ.
  > 2. **Ảnh chụp số serial in trên thân tai nghe đặt cạnh số serial trên vỏ hộp** (để kiểm tra sản phẩm bên trong có trùng khớp với hộp có mã QR hay không)."

- **Chặng B — Sau khi người bán phản hồi bằng hoá đơn nhập + ảnh QR khớp serial (AI dám nói "chưa đủ căn cứ" và chuyển nhân viên):**
  > "Cập nhật đơn **#C03** (yêu cầu đã được ghi nhận trong hạn từ ngày 13/11): Người bán đã phản hồi trong hạn 48 giờ và cung cấp **hoá đơn nhập từ nhà phân phối** cùng **ảnh quét mã QR trả về đúng số serial in trên hộp**.
  >
  > Dựa trên dữ liệu hiện có, mình nhận thấy **chưa đủ căn cứ để kết luận sản phẩm không đúng mô tả lúc đặt** `[#1 - G2]` (do tem và mã QR của người bán khớp với mô tả cam kết, trong khi phía bạn mới có nhận xét cảm quan và chưa có ảnh đối chiếu serial trên thân tai nghe) `[#2 - G11/PAIR Explainability]`.
  >
  > Vì bằng chứng hai bên đang mâu thuẫn, mình **không tự đóng khiếu nại và không tự hoàn tiền**, mà đã chuyển toàn bộ hồ sơ của cả hai bên lên **Nhân viên xử lý tranh chấp Shopee** xem xét trong vòng **24 giờ** `[#3 - G10]`. Riêng phản ánh **nghi ngờ hàng giả**, mình đã tách riêng để chuyển **Bộ phận Kiểm soát Chất lượng chuyên trách** kiểm tra theo quy trình độc lập. Trong lúc chờ nhân viên duyệt, bạn vẫn có thể bấm bổ sung ảnh serial trên thân máy bất cứ lúc nào."

#### (b) Người mua, người bán và nhân viên sàn thấy gì ngoài câu chữ

| Đối tượng | Những gì nhìn thấy trên màn hình (ngoài bong bóng chat) |
|---|---|
| **Người mua** | 1. **Huy hiệu độ chắc & trạng thái căn cứ `[#1 - G2]`:** Nhãn màu vàng *"Độ chắc: Thấp (Bằng chứng hai bên mâu thuẫn) · Chưa đủ căn cứ kết luận lệch mô tả — Đã chuyển nhân viên sàn (SLA 24h)"* + Nhãn thời hạn *"Còn 5 ngày hạn trả hàng (đến 18/11)"*.<br>2. **Bảng đối chiếu bằng chứng 3 cột `[#2 - G11 & PAIR Explainability]`:**<br>• *Cột 1 (Mô tả lúc đặt):* `"Tem bảo hành nhà phân phối, mã QR tra cứu serial"`.<br>• *Cột 2 (Bằng chứng người bán — Đã nộp):* Ảnh hoá đơn phân phối + Ảnh quét mã QR trùng khớp Serial hộp `SN-884920` *(Trạng thái: Khớp mô tả)*.<br>• *Cột 3 (Bằng chứng người mua — Thiếu 1/2):* Đã ghi nhận phản ánh `"tem mờ, khác hàng ở store"`; **Còn thiếu:** ô trống chờ tải lên `"Ảnh serial trên thân tai nghe cạnh vỏ hộp"`.<br>3. **Cụm nút điều khiển `[#3 - G8/G9/G10]`:** `[+ Bổ sung ảnh serial thân máy]`, nút hoàn tác **`[Huỷ yêu cầu khiếu nại]`**, và nhãn `"Đã chuyển Nhân viên sàn (xem trong 24h) + Đã báo Bộ phận chuyên trách hàng giả"`. **Không có** nút `"Khoá/Phạt shop"`. |
| **Người bán** | Thấy rõ thông báo bảo vệ người bán đúng: *"Khoản tiền 890.000đ đang được giữ tại sàn — Trợ lý AI KHÔNG tự động hoàn tiền khi chứng từ của Shop khớp mô tả"*. Thấy chứng từ (`Hoá đơn + QR serial`) được gắn nhãn xanh `"Đã đưa vào hồ sơ căn cứ"`, còn câu `"fake 100%"` của người mua được gắn nhãn xám `"Nhận định một phía — Không tính là căn cứ tự động (Luật L2)"`. |
| **Nhân viên sàn** | Thấy bảng đối chiếu 3 cột, đề xuất trung lập của AI (`"Chưa đủ căn cứ kết luận không đúng mô tả"`), trạng thái người mua *đã được AI báo rõ cần chụp ảnh serial thân máy từ ngày 13/11*. Vì người bán đã phản hồi nên hai nút **`[Từ chối khiếu nại — Giải ngân 890.000đ cho Shop]`** (`tu_choi_khieu_nai`) và **`[Duyệt chi hoàn tiền]`** (`chi_hoan_tien`) đã **mở khoá (enabled)** theo **Luật L3** để nhân viên quyết định. |

#### (c) Người dùng làm gì tiếp được — và nếu không làm gì thì sao?
- **Hành động làm tiếp được:**
  - *Người mua:* (1) Chụp và tải lên `[+ Bổ sung ảnh serial thân máy]` nếu phát hiện số serial in trên tai nghe khác số serial trên hộp (lập tức cập nhật vào Cột 3 cho nhân viên sàn thấy); (2) Bấm **`[Huỷ yêu cầu khiếu nại]`** nếu tự quét lại mã QR thấy đúng hàng chính hãng; (3) Nhắn thêm giải trình cho nhân viên sàn.
  - *Người bán:* Có thể bổ sung thêm clip đóng gói/xuất kho nếu muốn.
- **Nếu người mua không làm gì tiếp:**
  - Hết **24 giờ** chờ tại bàn nhân viên sàn, nếu người mua không bổ sung ảnh serial trên thân máy (dù đã được AI chỉ rõ còn thiếu gì theo Luật L4 và còn trong hạn), nhân viên sàn căn cứ vào chứng từ + mã QR hợp lệ của người bán để bấm **`tu_choi_khieu_nai`** → đóng khiếu nại và chuyển 890.000đ về cho người bán. Người bán đúng không bị xử thua oan và cũng không bị treo tiền vô thời hạn.

#### (d) Ai được báo, sau bao lâu?
- **Người bán:** Được báo **ngay lập tức** khi tạo yêu cầu (có 48h nộp chứng từ) và được báo ngay khi AI chuyển hồ sơ lên nhân viên sàn (kèm thông báo chứng từ của shop đã được ghi nhận).
- **Nhân viên sàn / Trưởng nhóm:** Nhận hồ sơ qua `chuyen_truong_nhom` **ngay khi phát sinh mâu thuẫn bằng chứng hai bên** (điều kiện bắt buộc `b`), có SLA **24 giờ** để ra quyết định cuối cùng.
- **Bộ phận chuyên trách hàng giả:** Nhận phiếu thông tin tách luồng riêng **ngay khi có từ khoá/nghi vấn hàng giả** (điều kiện `c`), xử lý độc lập theo nghiệp vụ kiểm định sàn, không làm gián đoạn đơn `#C03`.

---

### 3.3 Lập luận quyết định: Hỏi lại một câu / Trả lời kèm giới hạn / Dừng và chuyển người *(8 điểm)*

Theo nguyên tắc **"Một quyết định = bốn ý"** (`02-guide.md`), nhóm đặt lên bàn cả 3 hướng xử lý khi AI không chắc hoặc gặp rủi ro cao và chốt cho từng kịch bản như sau:

| Kịch bản | Các phương án đã cân nhắc | Phương án nhóm CHỌN & Vì sao | Các phương án đã LOẠI & Vì sao (trỏ về tool / dữ liệu) |
|---|---|---|---|
| **K1 (Đơn B02)**<br>*Mô tả bị sửa ngày 09/11 sau khi bán (03/11); hạn trả còn 2 ngày* | **PA1:** Tự quyết (`tu_choi_khieu_nai` theo mô tả hiện tại hoặc `chi_hoan_tien` theo snapshot).<br>**PA2:** Chỉ **hỏi lại** người mua (*"Bạn gửi ảnh chụp mô tả lúc đặt và ảnh đo nồi nhé"*).<br>**PA3:** **Dừng im lặng và chuyển người** ngay lập tức (*"Ca này khó, mình chuyển nhân viên"*), không hiện dữ liệu gì.<br>**PA4 (CHỌN):** **Hỏi xác nhận 1 câu (Luật L7) + Trả lời kèm giới hạn (hiện song song 2 bản mô tả & khóa hạn trả hàng) + Chuyển người ưu tiên (`chuyen_truong_nhom`)**. | **Chọn PA4** vì giải quyết trọn vẹn 3 rủi ro cùng lúc:<br>1. **Hỏi 1 câu xác nhận (L7)** tránh việc AI tự ý tạo phiếu trả hàng khi khách chỉ muốn góp ý (§4.4 câu 2).<br>2. **Trả lời kèm giới hạn** (công khai `Snapshot 03/11` cạnh `Bản sửa 09/11`) giúp người mua thấy ngay hệ thống bảo vệ mình bằng dữ liệu gốc, đồng thời hiểu rõ vì sao AI không tự chi tiền ngay.<br>3. **Khóa mốc hạn trả hàng (còn 2 ngày, hạn 15/11) + `chuyen_truong_nhom`** giữ nguyên quyền lợi hợp pháp của người mua trong lúc chờ quy trình 48h + 24h. | • **Loại PA1 (Tự quyết):** Cả `tu_choi_khieu_nai` và `chi_hoan_tien` đều **khó đảo lại** (bảng tool của track). Tự từ chối làm khách mất 1.290.000đ; tự hoàn ngay khi shop chưa phản hồi 48h vi phạm **Luật L3** và Rubric riêng #3 (*hai bên cùng được nghe*).<br>• **Loại PA2 (Chỉ hỏi lại bắt khách tự chứng minh):** Khách hàng không ai tự chụp màn hình trang sản phẩm từ lúc đặt ngày `03/11`. Bắt khách tự chứng minh trong khi hệ thống có tool `xem_don_va_mo_ta_luc_dat` là đẩy việc cho khách và làm trôi mất **2 ngày hạn trả hàng còn lại**.<br>• **Loại PA3 (Dừng và chuyển người chay):** Nếu chuyển người mà không khóa mốc hạn trả hàng và không đính kèm `Snapshot 03/11` qua `soan_de_xuat_hoan_tien`, nhân viên mở trang sản phẩm hiện tại (đã sửa ngày `09/11`) vẫn dễ bấm từ chối nhầm, hoặc xử lý sau ngày `15/11` làm khách mất quyền trả hàng. |
| **K2 (Đơn C03)**<br>*Khách khẳng định "fake 100%", đòi hoàn ngay; tem & QR của shop khớp mô tả* | **PA1:** Tự hoàn tiền theo lời khẳng định `"fake 100%"` của khách, hoặc tự gọi `tu_choi_khieu_nai` ngay khi shop gửi QR khớp.<br>**PA2:** Vừa thấy chữ `"fake"` là **dừng và chuyển người** ngay từ tin đầu tiên, chưa hỏi bằng chứng.<br>**PA3:** **Hỏi lại chung chung** nhiều vòng (*"Vui lòng gửi thêm bằng chứng hàng không đúng mô tả"*).<br>**PA4 (CHỌN):** Hai nhịp — **Nhịp 1: Hỏi lại có chỉ điểm cụ thể (`yeu_cau_bang_chung` theo Luật L4)**; **Nhịp 2: Khi bằng chứng 2 bên mâu thuẫn, Trả lời kèm giới hạn (*"chưa đủ căn cứ"*) + Dừng và chuyển người (`chuyen_truong_nhom`)**. | **Chọn PA4** vì giữ đúng sự trung lập hai chiều:<br>1. Ở Nhịp 1, khách mới nói miệng (`"fake 100%, tem mờ"`). AI dùng `yeu_cau_bang_chung` chỉ đích danh **2 bức ảnh còn thiếu** (*tem cận cảnh* và *serial trên thân máy cạnh vỏ hộp*), giải quyết đúng lời than của người mua trong track: *"Tôi gửi ảnh rồi mà cứ bị hỏi lại, không ai nói tôi còn thiếu cái gì"*.<br>2. Ở Nhịp 2, khi shop nộp hoá đơn + QR khớp serial hộp, AI **dám nói thẳng giới hạn**: *"chưa đủ căn cứ để kết luận không đúng mô tả"* (Rubric riêng #7), giữ 890.000đ tại sàn và chuyển nhân viên sàn duyệt. | • **Loại PA1 (Tự hoàn / Tự bác):** Nghe khách nói `"fake 100%"` mà hoàn ngay là rơi đúng vào lời than của người bán (*"Bên tôi đúng cũng chẳng ai nghe"*), làm shop mất 890.000đ + mất tai nghe `#C03`. Ngược lại, vừa thấy QR trên hộp của shop đã tự gọi `tu_choi_khieu_nai` thì bỏ sót rủi ro hộp thật nhưng ruột tai nghe bị lệch serial — thao tác đóng khiếu nại khó đảo lại nên bắt buộc do nhân viên sàn duyệt (§4.2).<br>• **Loại PA2 (Chuyển người ngay từ đầu):** Nếu chưa gọi `yeu_cau_bang_chung` mà đã đẩy lên trưởng nhóm, hồ sơ trống trơn khiến trưởng nhóm vẫn phải nhắn xin ảnh từ đầu, tốn thêm 24h–48h chờ đợi vô ích.<br>• **Loại PA3 (Hỏi lại chung chung):** Vi phạm **Luật L4**; khách không biết cần chụp serial trên thân máy nên sẽ chụp lại toàn cảnh chiếc hộp, tạo vòng lặp hỏi đi hỏi lại gây ức chế. |

---

### 3.4 Phân biệt loại lỗi (Hệ thống / Người dùng / Ngữ cảnh) và cách nói, cách sửa theo từng loại *(3 điểm)*

Trong lát cắt khiếu nại thương mại điện tử, hai kịch bản đắt nhất **K1** và **K2** chủ yếu rơi vào **Lỗi ngữ cảnh (*Context Error* — hệ thống chạy đúng thiết kế kỹ thuật nhưng sai với tình huống thực tế của người dùng, theo khung PAIR)**, kết hợp với **Lỗi thiếu thông tin đầu vào từ người dùng (*User Input / Ambiguity Error*)** ở bước đầu K2 và K4. Nhóm phân biệt rõ 3 loại lỗi để thiết kế cách nói lời xin lỗi/giải thích và cách sửa tận gốc khác nhau:

| Loại lỗi | Bản chất & Ví dụ cụ thể trong bài | Cách nói / Cách xin lỗi (Tone & Copywriting) | Cách sửa (Sửa ở đâu mới trúng?) |
|---|---|---|---|
| **1. Lỗi hệ thống**<br>*(System Error)* | Công cụ kỹ thuật gặp sự cố: API `xem_don_va_mo_ta_luc_dat` bị lỗi kết nối không tải được bản snapshot `03/11`, hoặc lỗi tải ảnh bằng chứng của khách/shop. | **AI nhận lỗi trực tiếp về phía hệ thống, xin lỗi rõ ràng và bảo vệ quyền lợi thời hạn ngay:**<br>*"Xin lỗi bạn, hệ thống tra cứu dữ liệu đơn hàng của Shopee đang gặp sự cố kỹ thuật nên mình chưa tải được bản lưu mô tả lúc đặt. Mình đã khóa giữ hạn trả hàng đơn #B02 (hạn 15/11) và chuyển nhân viên kiểm tra thủ công cho bạn trong 24 giờ."* | **Sửa ở tầng hạ tầng & cơ chế dự phòng (Fallback):** Tự động khóa đồng hồ đếm ngược hạn trả hàng khi tool đọc lỗi, không cho phép gọi bất kỳ tool đóng/hoàn nào khi thiếu dữ liệu đầu vào, và tự động chạy `chuyen_truong_nhom`. |
| **2. Lỗi người dùng / Thiếu thông tin**<br>*(User Input / Ambiguity Error)* | Người dùng nhắn thiếu thông tin cần thiết để ra quyết định:<br>• **K4:** Nhắn cụt *"hàng sai rồi, xử lý đi"* khi có 3 đơn A01, B02, C03.<br>• **K2 (Chặng A):** Khẳng định *"fake 100%"* nhưng chưa cung cấp ảnh đối chiếu serial thân máy với vỏ hộp. | **Tuyệt đối KHÔNG đổ lỗi cho người dùng và KHÔNG bắt người dùng xin lỗi; hướng dẫn cụ thể 1 bước cần bổ sung:**<br>Không nói *"Bạn nhắn thiếu thông tin nên hệ thống không xử lý được"*. Thay bằng chỉ dẫn cụ thể theo **Luật L4**: *"Để có căn cứ đối chiếu với mô tả lúc đặt, bạn chụp giúp mình 2 ảnh đang thiếu: (1) tem bảo hành cận cảnh, (2) serial trên thân tai nghe cạnh vỏ hộp nhé."* | **Sửa ở tầng UX thu thập đầu vào (Input Scaffolding):** Hiện 3 thẻ đơn hàng để khách bấm chọn 1 chạm (chặn K4); hiện danh sách bằng chứng cần chụp theo từng nhóm ngành hàng (chặn hỏi vòng vo ở K2, K5). |
| **3. Lỗi ngữ cảnh**<br>*(Context Error — PAIR)*<br>**[Trọng tâm của K1 & K2]** | Hệ thống chạy đúng logic thông thường nhưng sai với bối cảnh thực tế của giao dịch:<br>• **K1:** AI đọc đúng chữ `"lòng nồi 5 lít"` trong mô tả và khớp đúng số `5 lít` khách đo (không bịa chữ nào), nhưng sai ngữ cảnh thời gian vì dòng đó mới được shop sửa ngày `09/11` (sau ngày đặt `03/11`).<br>• **K2 (Chặng B) & K10:** Áp quy tắc một chiều (*"khách báo fake = hoàn"* hoặc *"có ảnh chụp Zalo = hoàn"*) mà bỏ qua bối cảnh tranh chấp hai chiều (shop có QR/hoá đơn khớp mô tả; ảnh ngoài app có thể cắt ghép). | **Không xin lỗi sáo rỗng kiểu "Xin lỗi vì trải nghiệm chưa tốt" rồi vẫn áp quy tắc cũ; phải minh bạch hóa bối cảnh hai chiều bằng căn cứ:**<br>• **Ở K1:** Chỉ rõ sự chênh lệch phiên bản (*"Mô tả lúc đặt ngày 03/11 ghi 6 lít, còn câu lòng nồi 5 lít mới được cập nhật ngày 09/11"*), khẳng định dùng bản `03/11` để bảo vệ quyền lợi người mua.<br>• **Ở K2:** Nói thẳng giới hạn nhận định (*"Chưa đủ căn cứ kết luận lệch mô tả vì tem và mã QR của shop khớp serial hộp"*), giải thích vì sao cần nhân viên sàn duyệt. | **Sửa câu chữ không cứu được — Bắt buộc sửa Thiết kế dữ liệu & Mức tự chủ:**<br>1. Thêm nguồn dữ liệu lịch sử phiên bản (`xem_don_va_mo_ta_luc_dat` — **Luật L1**).<br>2. Tách quyền soạn (`soan_de_xuat_hoan_tien`) khỏi quyền chi (`chi_hoan_tien`), khóa nút duyệt bằng phản hồi 2 bên (**Luật L2, L3, L6**).<br>3. Đưa bảng đối chiếu bằng chứng lên giao diện (**PAIR Explainability**). |

---

### 3.5 Ánh xạ 3 nguyên tắc HAX/PAIR vào câu chữ & vị trí trên màn hình Prototype *(5 điểm)*

Nhóm chọn **3 cụm nguyên tắc HAX/PAIR** (đánh số thứ tự **`[#1]`, `[#2]`, `[#3]`** thống nhất giữa câu chữ ở §3 và ảnh chụp màn hình ở §5 để chỉ điểm trực tiếp khi demo):

| Mã trên Prototype | Nguyên tắc HAX / PAIR (& Quy định pháp lý) | Trỏ vào câu chữ cụ thể ở §3 | Trỏ vào vị trí cụ thể trên màn hình Prototype (§5) |
|---|---|---|---|
| **`[#1]`** | **HAX G1** *(Làm rõ hệ thống làm được gì)* + **HAX G2** *(Làm rõ hệ thống làm tốt đến đâu)* + **Điều 11 khoản 1 Luật Trí tuệ nhân tạo 134/2025/QH15** *(Trách nhiệm minh bạch khi AI tương tác trực tiếp)* | • Câu mở đầu ở K1 & K2: *"Chào bạn, mình là **Trợ lý AI của Shopee**..."*<br>• Câu giới hạn quyền hạn: *"mình **không tự kết luận đóng khiếu nại và không tự chi hoàn tiền ngay**"* (K1); *"mình **không có quyền kết luận hàng giả hay xử phạt shop**"* + *"hiện tại **chưa đủ căn cứ để kết luận sản phẩm không đúng mô tả lúc đặt**"* (K2). | 1. **Thanh tiêu đề phụ (Header Banner)** ngay dưới tên khung chat: `"Trợ lý AI Shopee · Tự động đối chiếu mô tả & chuẩn bị hồ sơ · Quyết định tiền do Người bán / Nhân viên duyệt"`.<br>2. **Huy hiệu Độ chắc & Trạng thái căn cứ (Confidence Badge)** gắn ở đầu thẻ đề xuất của AI: hiện rõ `"Phát hiện lệch phiên bản mô tả (Khớp log 100%)"` ở K1 và `"Độ chắc: Thấp — Bằng chứng hai bên mâu thuẫn"` ở K2. |
| **`[#2]`** | **HAX G11** *(Giải thích vì sao AI làm vậy)* + **PAIR *Explainability + Trust*** *(Hiển thị căn cứ đối chiếu để người dùng tự kiểm chứng, xây dựng niềm tin đúng mức — calibrated trust)* | • Ở K1: *"mình phát hiện **mô tả lúc bạn đặt hàng (03/11)** ghi 'Nồi chiên không dầu dung tích 6 lít', trong khi **mô tả hiện tại** đã được shop chỉnh sửa vào ngày **09/11 (sau khi giao hàng)** thành '...lòng nồi 5 lít'"*.<br>• Ở K2: *"(do tem và mã QR của người bán khớp với mô tả cam kết, trong khi phía bạn mới có nhận xét cảm quan và chưa có ảnh đối chiếu serial trên thân tai nghe)"*. | **Khung đối chiếu bằng chứng trực quan (Side-by-side Evidence Card)** nằm ngay trong luồng xử lý:<br>• Ở màn hình K1: Bảng 2 cột **`Mô tả lúc đặt (03/11)`** đặt cạnh **`Mô tả hiện tại (Sửa 09/11)`** có tô nổi dòng chữ bị sửa sau khi bán.<br>• Ở màn hình K2 / Nhân viên duyệt: Bảng 3 cột đối chiếu **`Mô tả lúc đặt`** vs **`Bằng chứng người bán (Hoá đơn + QR khớp)`** vs **`Bằng chứng người mua (Đang thiếu ảnh serial thân máy)`**. |
| **`[#3]`** | **HAX G10** *(Thu hẹp phạm vi điều khiển khi nghi ngờ)* + **HAX G8/G9** *(Gạt bỏ / Sửa dễ dàng)* + **PAIR *Errors + Graceful Failure*** *(Mỗi loại lỗi một đường lui an toàn)* | • Ở K1: Thay vì tự đóng hoặc tự hoàn, AI hỏi xác nhận 1 câu (**Luật L7**): *"Bạn xác nhận muốn tạo yêu cầu trả hàng hoàn tiền (1.290.000đ)... để mình khóa mốc thời hạn hôm nay và chuyển hồ sơ ưu tiên..."*<br>• Ở K2: Thay vì đoán hoặc hỏi chung chung, AI thu hẹp về việc xin đúng 2 bức ảnh còn thiếu (**Luật L4**) rồi chuyển nhân viên với SLA **24 giờ**. | **Cụm nút điều khiển mức tự chủ & Đường lui an toàn (Action & Undo Bar):**<br>• Phía người mua: Nút xác nhận `[Xác nhận trả hàng hoàn tiền]` / `[Chỉ phản ánh]`, nút hoàn tác **`[Huỷ yêu cầu / Hoàn tác nháp]`** (đảo ngược được hành động tự soạn của AI), nút `[Chuyển nhân viên (SLA 24h)]`.<br>• Phía nhân viên / hệ thống: Nút `chi_hoan_tien` bị **khóa mờ (disabled)** khi chưa hết hạn 48h phản hồi của shop (**Luật L3**); hoàn toàn **không có nút `phat_shop`**. |

---

### 3.6 Một lỗi mà sửa câu chữ không cứu được — và thiết kế cứu nó thế nào *(3 điểm)*

#### (a) Lỗi nào sửa câu chữ (prompt / copywriting) không thể cứu được?
Đó là lỗi ở **K1 (Đơn B02): AI đọc `mô tả hiện tại` thay vì `snapshot mô tả lúc đặt` rồi tự gọi `tu_choi_khieu_nai`** (hoặc ở chiều ngược lại trong **K2/K10**: AI gọi thẳng tool `soan_hoan_tien` gốc để chuyển tiền ngay khi người bán chưa được phản hồi).

- **Vì sao sửa câu chữ hoàn toàn bất lực trước lỗi này?**
  1. **Sai từ nguồn dữ liệu đầu vào (Garbage In, Polite Garbage Out):** Nếu AI chỉ được cấp quyền đọc trang sản phẩm hiện tại (nơi người bán đã sửa thành *"6 lít dung tích tổng, lòng nồi 5 lít"* vào ngày `09/11`), thì dù nhóm viết prompt kỹ đến đâu hay sửa câu trả lời của AI cho lịch sự, đồng cảm, giải thích cặn kẽ đến mấy (*"Trợ lý AI rất tiếc về trải nghiệm của bạn, tuy nhiên theo thông số sản phẩm trên hệ thống, lòng nồi tiêu chuẩn là 5 lít nên sản phẩm giao đúng mô tả..."*), kết quả vẫn là **người mua mất oan 1.290.000đ và mất quyền trả hàng khi chỉ còn 2 ngày**.
  2. **Câu chữ càng trau chuốt càng làm lỗi khó bị phát hiện hơn:** Khi AI trích dẫn đúng từng chữ của bản mô tả đã bị sửa với giọng văn chuyên nghiệp, cả người mua lẫn nhân viên tổng đài đều tưởng AI làm đúng quy định ("trông đúng nhưng sai phiên bản").
  3. **Sai từ quyền hạn thực thi của Tool:** Nếu tool `soan_hoan_tien` vẫn gộp chung việc "soạn hồ sơ" với việc "thực chi tiền về tài khoản người mua" như bảng tool gốc, thì một khi AI bị thuyết phục bởi lời khẳng định `"fake 100%"` (K2) hay ảnh chụp Zalo cắt ghép (K10), tiền đã rời khỏi sàn ngay lập tức — không một câu xin lỗi hay lời giải thích nào sau đó đòi lại được tiền cho người bán.

#### (b) Thiết kế của nhóm cứu lỗi đó như thế nào? (4 lớp phòng vệ kiến trúc & UX)

Thay vì chữa cháy bằng câu chữ, nhóm sửa trực tiếp vào **cấu trúc dữ liệu, bộ tool, luật mở khoá và giao diện đối chiếu** (liên kết chặt từ §3 sang §4 và §5):

1. **Lớp 1 — Sửa nguồn dữ liệu bằng tool đọc bất biến (`xem_don_va_mo_ta_luc_dat` · §4.0 & Luật L1):** Hệ thống bắt buộc lưu và trả về đồng thời `snapshot_mo_ta_luc_dat` (`03/11`) và `mo_ta_hien_tai` (`09/11`) kèm dấu thời gian chỉnh sửa. AI bị cấm so sánh khiếu nại chỉ trên một phiên bản hiện tại.
2. **Lớp 2 — Sửa quyền hạn bằng cách tách Tool "Soạn" khỏi "Chi" (§4.0 & §4.1):** Tách `soan_hoan_tien` thành `soan_de_xuat_hoan_tien` (*Tự làm* — chỉ tạo bản nháp, đảo ngược được bằng nút `[Huỷ yêu cầu]`) và `chi_hoan_tien` (*Cần người duyệt*); đồng thời đặt `tu_choi_khieu_nai` = *Cần nhân viên sàn duyệt*. AI không còn bất kỳ hàm API nào để tự dịch chuyển tiền.
3. **Lớp 3 — Sửa luồng điều hướng bằng Luật cứng ở tầng hệ thống (§4.5 — Luật L1, L2, L3):**
   - **Luật L1:** Hễ `snapshot_luc_dat != mo_ta_hien_tai` → hệ thống tự động khóa mốc hạn trả hàng (bảo toàn 2 ngày còn lại của đơn B02), gắn cờ đỏ ưu tiên và **bắt buộc** gọi `chuyen_truong_nhom`.
   - **Luật L3:** Khóa cứng ở tầng giao diện/API hai nút `chi_hoan_tien` và `tu_choi_khieu_nai` cho đến khi người bán đã phản hồi trong app hoặc đã hết hạn 48 giờ.
4. **Lớp 4 — Sửa hiển thị bằng Khung đối chiếu trực quan (`[#2]` trên Prototype · §5):** Đưa bảng so sánh `Snapshot 03/11 vs Bản sửa 09/11` (ở K1) và bảng 3 cột `Mô tả vs Bằng chứng Shop vs Bằng chứng Khách` (ở K2) lên ngay màn hình người mua và màn hình nhân viên duyệt, giúp con người phát hiện ra điểm bất thường trong vài giây trước khi bấm nút duyệt tiền.

> **Bàn giao nhanh cho §5 (Dương) để gắn lên Prototype:**
> - **Câu chữ nguyên văn:** Lấy trực tiếp ở mục **3.1(a)** (cho ca K1 — Đơn B02) và **3.2(a)** (cho ca K2 — Đơn C03).
> - **3 vị trí đánh số bắt buộc trên ảnh chụp màn hình (`prototype/`):**
>   - **`[#1]` (HAX G1 + G2 + Luật AI 134/2025):** Dòng giới thiệu `"Trợ lý AI của Shopee"` + Huy hiệu độ chắc/trạng thái căn cứ ở đầu thẻ đề xuất + Dòng báo rõ hạn trả hàng còn lại (`còn 2 ngày — hạn 15/11`).
>   - **`[#2]` (HAX G11 + PAIR Explainability & Trust):** Thẻ đối chiếu song song `Mô tả lúc đặt (03/11: "dung tích 6 lít")` cạnh `Mô tả hiện tại (Sửa 09/11: "lòng nồi 5 lít")` có tô vàng phần sửa.
>   - **`[#3]` (HAX G10 + G8/G9 + Mức tự chủ §4):** Cụm nút `[Xác nhận trả hàng hoàn tiền]` (Luật L7), nút hoàn tác `[Huỷ yêu cầu / Hoàn tác nháp]`, trạng thái đã `chuyen_truong_nhom (SLA 24h)`, nút `chi_hoan_tien` khóa chờ phản hồi 48h của shop (Luật L3), và không có nút `phat_shop`.

---

## §4. Mức tự chủ

### 4.0 Thay đổi bộ tool trước khi xếp mức

Track cho phép thêm hoặc tách tool nếu ghi rõ lý do. Nhóm làm 2 thay đổi:

1. **Thêm `xem_don_va_mo_ta_luc_dat` (chỉ đọc).** Lát cắt yêu cầu AI "so với mô tả lúc đặt", nhưng bảng tool **không có tool đọc nào**. Không có tool này thì AI chỉ còn cách so với trang sản phẩm hiện tại, tức đúng lỗi K1. Tool trả về: các đơn của **người mua đang chat**, snapshot mô tả lúc đặt, mô tả hiện tại kèm ngày sửa, ngày nhận và hạn trả. Tool **không** trả về SĐT hay địa chỉ người bán, để chặn K6 ngay từ nguồn dữ liệu.
2. **Tách `soan_hoan_tien` thành hai bước.** Tên tool là "soạn" nhưng bảng track ghi nó **"hoàn tiền cho người mua"**, tức chi tiền thật. Gộp hai việc thì không đặt được mức hợp lý: phần soạn thì nên để AI làm, còn phần chi thì không.
   - **`soan_de_xuat_hoan_tien`**: AI soạn hồ sơ đề xuất (so sánh mô tả lúc đặt, bằng chứng hai bên, đề xuất, độ chắc, lý do). **Không chuyển tiền**, huỷ được bất cứ lúc nào.
   - **`chi_hoan_tien`**: thực chi. **Khó đảo**, vì tiền đã về người mua.

> Cách tách "soạn" khỏi "chi" chặn được K2, K3, K10. AI vẫn được làm phần việc tốn công (gom bằng chứng, so mô tả), còn quyết định tiền đi về đâu thì không nằm ở AI.

### 4.1 Bảng mức tự chủ

| Tool | Mức | Đảo được? | Sai thì ai chịu gì | Chờ người thì mất gì |
|---|---|---|---|---|
| `xem_don_va_mo_ta_luc_dat` *(thêm)* | **Tự làm** | Không thay đổi gì | Đọc nhầm đơn thì người mua thấy ngay trên thẻ đơn và tự sửa | Mọi bước sau đều kẹt, kể cả ca bình thường K5 |
| `yeu_cau_bang_chung` | **Tự làm**, có luật L4 | Tin đã tới | Gửi thừa hoặc sai: một tin làm phiền, rẻ | Người mua kẹt, hạn trả hàng trôi (K1 còn 2 ngày) |
| `chuyen_truong_nhom` | **Tự làm**, có điều kiện bắt buộc chuyển | Được | Chuyển thừa: trưởng nhóm tốn vài phút | Không chuyển kịp thì K1, K2, K7 bị xử sai |
| `soan_de_xuat_hoan_tien` *(tách)* | **Tự làm** | Được (huỷ nháp) | Không ai mất tiền, vì chưa chi | Nhân viên phải tự gom hồ sơ, chậm hơn |
| `chi_hoan_tien` *(tách)* | **Cần người duyệt**: người bán **hoặc** nhân viên sàn | **Khó** | Người bán mất tiền và hàng (K2, K3, K10) | Người mua chờ, tối đa 48h + 24h |
| `tu_choi_khieu_nai` | **Cần người duyệt**: chỉ nhân viên sàn | **Khó** | Người mua mất tiền và giữ hàng sai (K1) | Tiền vẫn **giữ ở sàn**, không bên nào mất thêm |
| `phat_shop` | **Cấm** | Khó, ảnh hưởng cả shop | Cả shop và mọi người mua khác của shop | Không có (không thuộc luồng này) |

### 4.2 Lập luận từng tool

#### `xem_don_va_mo_ta_luc_dat` — Tự làm
- **Cost-of-error:** chỉ đọc, không đổi tiền hay trạng thái. Đọc nhầm đơn thì người mua thấy ngay trên thẻ đơn, nên sai là rẻ và tự sửa được.
- **Đã cân nhắc:** "cần người duyệt" → **loại**, vì bắt duyệt một thao tác đọc là vô nghĩa và làm kẹt cả ca bình thường K5. Rủi ro thật của tool là **lộ dữ liệu** (K6), nên nhóm chặn bằng **phạm vi trả về** (chỉ đơn của người đang chat, không SĐT/địa chỉ) chứ không bằng mức tự chủ.

#### `yeu_cau_bang_chung` — Tự làm, kèm luật L4
- **Cost-of-error:** tin đã tới thì không thu lại, nhưng giá của một tin thừa là rẻ: làm phiền một lần, không ai mất tiền. Ngược lại, **chờ người duyệt** từng tin xin bằng chứng chính là lời than của người mua ("gửi ảnh rồi mà cứ bị hỏi lại, không ai nói còn thiếu gì"). Với K1 còn 2 ngày, chờ là một kiểu sai.
- **Luật L4:**
  - Gửi cho **người mua đang chat**: tự làm ngay.
  - Gửi cho **người bán**: chỉ sau khi người mua **đã chọn đúng đơn** và yêu cầu trả hàng đã được tạo. Luật này chặn K4: không làm phiền shop vô can vì AI đoán đơn.
  - Mỗi tin phải **nêu cụ thể thiếu gì**, ví dụ "ảnh tem cận cảnh có thấy serial", không gửi kiểu "vui lòng cung cấp thêm bằng chứng".
- **Đã cân nhắc:**
  - "Cần người duyệt" → **loại**: nghẽn ở nhân viên, mà giá của tin thừa thấp hơn nhiều so với giá chờ.
  - "Cấm" → **loại**: AI mất việc chính của lát cắt (xin thêm bằng chứng).

#### `chuyen_truong_nhom` — Tự làm, có điều kiện **bắt buộc** chuyển
- **Cost-of-error:** đảo được. Chuyển thừa chỉ tốn vài phút của trưởng nhóm. Ngược lại, **không** chuyển khi lẽ ra phải chuyển là cách K1 và K2 bị xử sai.
- **AI bắt buộc chuyển khi** (không để AI tự cân nhắc):
  - (a) snapshot mô tả lúc đặt **khác** mô tả hiện tại (K1);
  - (b) bằng chứng hai bên **mâu thuẫn** (K2);
  - (c) có dấu hiệu nghi hàng giả hoặc ảnh hưởng sức khoẻ (K7);
  - (d) người dùng đòi gặp người.
- **AI phải nói thật về thời gian chờ**, ví dụ "trưởng nhóm sẽ xem trong 24 giờ", không nói "ngay lập tức".
- **Đã cân nhắc:** "cần người duyệt" → **loại**, vì bắt duyệt việc chuyển sang người duyệt là vòng lặp vô nghĩa.

#### `soan_de_xuat_hoan_tien` — Tự làm
- **Cost-of-error:** chỉ là bản nháp, không chuyển tiền và huỷ được bất cứ lúc nào. Soạn sai thì người duyệt ở bước `chi_hoan_tien` thấy và bác. Đây là chỗ AI tạo giá trị nhất: gom mô tả lúc đặt, mô tả hiện tại, ảnh hai bên và phản hồi người bán vào **một màn hình** cho người duyệt.
- **Ràng buộc:**
  - Đề xuất luôn kèm **độ chắc** và **căn cứ**.
  - Trường căn cứ **không được chứa** lời doạ, cảm xúc hay lịch sử khiếu nại của một bên (luật L2).
- **Đã cân nhắc:** gộp chung với chi tiền (như tool gốc) → **loại**, vì lý do ở 4.0.

#### `chi_hoan_tien` — Cần người duyệt (tool khó xếp nhất, xem 4.3)
- **Ai duyệt, theo hai làn:**
  - **Làn nhanh, người bán duyệt:** người bán bấm "Đồng ý trả hàng" trong app. Người bán là bên chịu thiệt nếu hoàn, nên sự đồng ý của họ là đủ căn cứ. Làn này dùng cho K5, K10.
  - **Làn tranh chấp, nhân viên sàn duyệt:** khi người bán không đồng ý hoặc hết 48 giờ không phản hồi.
- **Người duyệt thấy gì trước khi bấm:**
  - mô tả lúc đặt **cạnh** mô tả hiện tại, phần khác nhau được tô nổi;
  - ảnh và bằng chứng của **cả hai bên**;
  - đề xuất của AI, độ chắc và lý do;
  - số tiền, hạn trả hàng, trạng thái hàng hoàn.
- **Điều kiện mở khoá (luật L3):** nút chi chỉ hiện khi người bán **đã phản hồi** hoặc **đã hết 48 giờ**. Hai bên phải cùng được nghe trước khi tiền đi (rubric riêng #3).
- **Quá hạn:** nhân viên không duyệt trong 24 giờ thì hồ sơ **tự nâng lên trưởng nhóm**, và **không bao giờ tự hoàn**. Nếu quá hạn mà tự hoàn thì thực chất AI tự quyết, chỉ là chậm hơn. Trong lúc chờ, tiền vẫn giữ ở sàn.

#### `tu_choi_khieu_nai` — Cần người duyệt, chỉ nhân viên sàn
- **Cost-of-error:** khó đảo, vì tiền đã về người bán, và người mua vừa mất tiền vừa giữ hàng sai (K1).
- **Ai duyệt:** chỉ **nhân viên sàn**. Người bán **không** được tự duyệt, vì họ là bên hưởng lợi khi khiếu nại bị từ chối. Đây là điểm khác so với `chi_hoan_tien`.
- **Người duyệt thấy:** cùng bộ hồ sơ như `chi_hoan_tien`. Ngoài ra, nếu người mua **chưa từng được báo cụ thể còn thiếu gì** thì hồ sơ hiện cảnh báo "chưa xin bằng chứng". AI **không được đề xuất từ chối chỉ vì thiếu bằng chứng** khi người mua còn hạn bổ sung.
- **Chờ thì mất gì:** gần như không. Tiền vẫn **giữ ở sàn**, người bán chỉ nhận tiền chậm hơn chứ không mất. Đây là lý do `tu_choi_khieu_nai` **dễ xếp hơn** `chi_hoan_tien`: phía chờ không có ai bị hại thật.
- **Quá hạn:** khiếu nại giữ nguyên trạng thái mở và nâng lên trưởng nhóm.
- **Đã cân nhắc:**
  - "Tự làm" → **loại** vì K1.
  - "Cấm" → **loại**: nếu AI không bao giờ được đề xuất đóng khiếu nại, các ca người bán đúng như K2 sẽ treo mãi và tiền của người bán bị giữ vô thời hạn. Như vậy cũng là bất công, chỉ theo hướng ngược lại.

#### `phat_shop` — Cấm
- **Cost-of-error:** ảnh hưởng **cả shop**, kể cả các đơn và người mua không liên quan. Điểm uy tín hay khoá shop có gỡ lại được thì thiệt hại về doanh thu và niềm tin trong thời gian bị khoá cũng không đảo được.
- **Vì sao "cần người duyệt" cũng không đủ:**
  - Người mua bấm xác nhận thì vô nghĩa, vì họ là bên đang tranh chấp.
  - Nhân viên khiếu nại cũng không phải người có thẩm quyền xử phạt.
  - Một khiếu nại đơn lẻ không đủ căn cứ phạt shop.
- **Thay vào đó:** khi có dấu hiệu nghi hàng giả (K7), AI dùng `chuyen_truong_nhom` với nhãn "chuyển bộ phận chuyên trách – nghi hàng giả". AI **không hứa** kết quả xử lý shop.
- **Trên màn hình:** không có nút phạt hay khoá shop ở bất kỳ phía nào của luồng này.

### 4.3 Tool khó xếp nhất: `chi_hoan_tien`

Mức nào cũng có một bên chịu giá:

| Phương án | Ai được lợi | Cái giá (trỏ về §2) |
|---|---|---|
| **A. Tự làm**, hoặc tự làm khi dưới một ngưỡng tiền (ví dụ < 200.000đ) và có "bằng chứng" | Người mua có ca rõ ràng được hoàn ngay | **K10**: ảnh Zalo ghép là đủ để người bán mất tiền. **K3**: lời doạ đẩy AI hoàn. **K2**: khách nói chắc là được hoàn. Ngưỡng tiền không cứu được, vì kẻ gian chỉ cần chia nhỏ đơn |
| **B. Cần người duyệt** (người bán hoặc nhân viên) | Người bán luôn được nghe trước khi mất tiền | **K1**: người mua đúng mà vẫn chờ tới 48h + 24h, trong khi giữ món hàng sai. **K5**: ca rõ ràng mà vẫn phải chờ nếu chỉ có làn nhân viên |
| **C. Cấm** (AI không chạm vào hoàn tiền, quay về menu cứng) | Không có rủi ro AI hoàn sai | Mất mục tiêu của lát cắt. Người mua quay lại cảnh "không ai nói tôi còn thiếu gì". Tiền vẫn do người quyết, nên cấm không chặn thêm được gì so với B |

**Ba thành viên tự xếp trong 5 phút trước khi bàn** (theo `02-guide.md` §4.3):
- Đỗ Hồng Vỹ: **B**, vì hai hướng sai đắt ngang nhau, mà chờ thì tiền vẫn nằm ở sàn.
- Đinh Hoàng Phong: **A có điều kiện (tự làm khi đơn < 200.000đ hoặc khi shop đã nhắn nhận lỗi trong chat như K5; còn lại B)**, vì lo ca rõ ràng như K5 mà bắt chờ nhân viên 48h–72h thì người mua chịu thiệt vô ích. *(Sau khi bàn với Vỹ: nhận ra ngưỡng < 200.000đ vẫn thủng ở K10 do ảnh Zalo ghép được, nên đồng thuận chuyển sang **B + làn nhanh do người bán bấm "Đồng ý trả hàng" trong app** để vừa nhanh cho K5 vừa không cho AI tự chi tiền).*
- Nguyễn Ánh Dương: **B**, nhìn từ phía màn hình. Nếu AI được tự chi (A), không có chỗ nào đặt được nút "hoàn tác", vì tiền đã về người mua. Khi đó màn hình chỉ còn báo kết quả, người bán không có lúc nào để được nghe (K2, K10). Với B, nút chi nằm ở **màn hình người duyệt**, kèm thẻ hai bản mô tả và bằng chứng hai bên ngay trước nút. Như vậy người bấm luôn thấy căn cứ trước khi tiền đi. Lo ngại của mình là K5 phải chờ, và nỗi lo này được giải quyết bằng làn nhanh: người bán bấm "Đồng ý trả hàng".

**Cách nhóm chốt: B, cộng làn nhanh do người bán duyệt.**
- Điểm mạnh nhất của phương án A là **ca rõ ràng không phải chờ** (K5). Nhóm giữ được điểm này mà không cần cho AI chi tiền: ở ca rõ ràng, chính **người bán** thừa nhận lỗi. Vì vậy cho người bán bấm "Đồng ý trả hàng" là đủ, tiền đi theo luồng trả hàng chuẩn và không cần chờ nhân viên.
- Chỉ ca **tranh chấp thật** (K1, K2) mới đi làn nhân viên. Với các ca này, chờ là **cái giá chấp nhận được**: trong lúc chờ, tiền vẫn giữ ở sàn, nên không bên nào mất tiền thêm.
- Phần "người mua đúng mà phải chờ" ở K1 được giảm bằng hai cách khác, không bằng cách cho AI chi tiền:
  - Yêu cầu được **ghi nhận trong hạn** ngay khi tạo, nên chờ không làm người mua mất quyền.
  - AI **gắn cờ ưu tiên** khi mô tả bị sửa sau khi bán, để hồ sơ được xem trước.

### 4.4 Thử mức đã đặt trên 3 kịch bản

| | **K1** — nồi chiên, mô tả bị sửa *(đắt nhất)* | **K2** — tai nghe, người bán đúng *(đắt nhất)* | **K5** — áo size L nhận M *(bình thường)* |
|---|---|---|---|
| **Với mức này AI làm gì, người dùng thấy gì** | AI tự gọi `xem_don_va_mo_ta_luc_dat` và thấy snapshot "6 lít" khác bản hiện tại (sửa 09/11). AI tự tạo yêu cầu trả hàng, tự `soan_de_xuat_hoan_tien`, và theo điều kiện (a) thì **bắt buộc** `chuyen_truong_nhom`. Người mua thấy hai phiên bản mô tả cạnh nhau, kèm dòng "yêu cầu đã ghi nhận trong hạn (hạn 15/11)" và thời gian chờ | AI tự gọi `yeu_cau_bang_chung` cho người mua: "ảnh tem cận cảnh, ảnh serial trên máy so với trên hộp". Người bán phản hồi bằng ảnh tem và QR khớp. Bằng chứng mâu thuẫn nên AI **bắt buộc** chuyển nhân viên, kèm đề xuất "chưa đủ căn cứ kết luận không đúng mô tả". AI không có nút phạt, và tách phần "nghi hàng giả" sang bộ phận chuyên trách | AI tự gọi `xem_don_va_mo_ta_luc_dat` cho đơn A01 và thấy còn 4 ngày. AI tự tạo yêu cầu trả hàng, đính kèm tin nhắn shop nhận lỗi, **không** xin thêm ảnh. Người bán bấm "Đồng ý trả hàng" (làn nhanh) |
| **1. Cái sai ở §2 có bị chặn không?** | **Có.** `tu_choi_khieu_nai` cần nhân viên duyệt. Người duyệt thấy phần mô tả khác nhau được tô nổi, và AI so với snapshot chứ không so với trang hiện tại | **Có.** `chi_hoan_tien` chỉ mở sau khi người bán phản hồi (L3), và người bán đã phản hồi "không đồng ý" nên phải qua nhân viên. Lời khẳng định "fake 100%" không được ghi vào trường căn cứ (L2) | **Có.** AI không có tool nào để tự chi tiền, nên không thể nói "đã hoàn". Câu chữ phải nói "khi shop đồng ý, tiền sẽ hoàn theo luồng trả hàng" |
| **2. Còn việc nào AI làm khi lẽ ra phải hỏi?** | **Còn một chỗ:** AI tự tạo yêu cầu trả hàng mà chưa hỏi người mua muốn **trả hàng hoàn tiền** hay chỉ muốn **phản ánh**. → Nhóm sửa: trước khi tạo yêu cầu, AI hỏi một câu xác nhận ("Bạn muốn trả nồi và hoàn tiền phải không?"). Lần hỏi này nhanh, không tốn hạn | Không. Tin `yeu_cau_bang_chung` gửi người bán chỉ đi sau khi đơn C03 đã được xác nhận (L4) | Không |
| **3. Người dùng bình thường có phải chờ vô ích không?** | Người mua phải chờ nhân viên, nhưng **không vô ích**: đây là tranh chấp thật, và quyền yêu cầu đã được giữ trong hạn | Người mua chờ nhân viên, **đúng như thiết kế**: cần người quyết vì bằng chứng hai bên mâu thuẫn | **Không.** Người mua không phải chờ nhân viên, vì người bán tự duyệt trong vài phút. Nếu chỉ có làn nhân viên (B thuần) thì K5 sẽ phải chờ vô ích, và đó là lý do nhóm thêm làn nhanh |

### 4.5 Luật thêm

| Luật | Nội dung | Chặn kịch bản |
|---|---|---|
| **L1** | Mọi so sánh dùng **snapshot mô tả lúc đặt**. Nếu snapshot khác bản hiện tại thì hiện cả hai kèm ngày sửa và **bắt buộc** chuyển nhân viên | K1 |
| **L2** | Lời doạ, cảm xúc, mức độ chắc chắn trong lời người dùng, lịch sử khiếu nại của một bên **không được ghi vào trường "căn cứ"** của đề xuất | K2, K3 |
| **L3** | `chi_hoan_tien` và `tu_choi_khieu_nai` chỉ mở khoá khi người bán **đã phản hồi** hoặc **hết 48 giờ** | K2, K3, K10 |
| **L4** | `yeu_cau_bang_chung` gửi người bán chỉ sau khi người mua **xác nhận đúng đơn**. Mỗi tin phải nêu cụ thể thiếu gì | K4, K5 |
| **L5** | Bộ lọc đầu ra: AI không bao giờ xuất SĐT, địa chỉ hay tài khoản ngân hàng của bất kỳ bên nào | K6 |
| **L6** | Ảnh chụp từ **ngoài app** (Zalo, Messenger…) chỉ là tham khảo, không phải căn cứ. Lời thừa nhận của người bán chỉ tính khi được bấm trong app | K10 |
| **L7** | Trước khi tạo yêu cầu trả hàng, AI xác nhận **một câu** người mua muốn trả hàng hoàn tiền *(thêm sau khi thử mức trên K1)* | K1 (câu 2 ở 4.4) |

### 4.6 Một mức tự chủ đã đổi lời hứa với người dùng

Việc tách `soan_hoan_tien` thành **soạn (tự làm)** và **chi (cần duyệt)** đổi lời hứa của trợ lý:

- **Trước đây, nếu AI tự chi:** "Trợ lý sẽ giải quyết khiếu nại và hoàn tiền cho bạn." Đây là lời hứa về **kết quả**, mà AI không giữ được ở K1 và K2.
- **Sau khi tách:** "Trợ lý giúp bạn nộp **đúng và đủ ngay lần đầu**, cho bạn biết **còn thiếu gì, còn bao lâu**, và **ai sẽ quyết, khi nào**." Đây là lời hứa về **quy trình**, và AI giữ được trong mọi kịch bản.
- **Câu chữ cũng phải đổi theo.** AI không được nói "Shopee đã hoàn tiền cho bạn". AI nói: "Mình đã gửi yêu cầu của bạn. Shop có đến 18:00 ngày 15/11 để phản hồi; nếu shop không đồng ý, nhân viên sẽ xem trong 24 giờ."
- **Với người bán**, lời hứa mới là: "**Tiền không rời khỏi sàn trước khi bạn được nghe.**" Câu này trả lời trực tiếp lời than "Bên tôi đúng cũng chẳng ai nghe".

> **Bàn giao cho §5 (Dương), mức tự chủ hiện trên màn hình thế nào:**
> - Tự làm (xin bằng chứng, chuyển trưởng nhóm, soạn đề xuất) → có nút **hoàn tác / huỷ** hoặc dòng trạng thái "đã chuyển, xem trong 24h".
> - `chi_hoan_tien` → nút xác nhận nằm ở **phía người bán / nhân viên**, không nằm ở khung chat của AI. Người duyệt thấy hai phiên bản mô tả và bằng chứng hai bên.
> - `tu_choi_khieu_nai` → chỉ có ở màn hình nhân viên.
> - `phat_shop` → **không có nút** ở bất kỳ đâu.

---

## §5. Prototype

> _Phụ trách: Nguyễn Ánh Dương._

### 5.1 Link · công cụ · phần nào mock

- **File:** [`prototype/index.html`](prototype/index.html). Mở thẳng bằng trình duyệt, không cài gì. Hướng dẫn bấm và bảng đánh số nằm ở [`prototype/README.md`](prototype/README.md).
- **Công cụ:** một file HTML + CSS + JavaScript thuần, dựng bằng coding agent (Claude Code). Không dùng thư viện ngoài, không backend, không đăng nhập.
- **Phần mock:**
  - Dữ liệu là đơn dựng ở §2.0 (B02, C03).
  - Câu chữ AI được viết sẵn, chép nguyên văn từ §3.1(a) và §3.2(a).
  - Lời gọi tool chỉ được ghi vào bảng **"Nhật ký tool & luật"**, kèm mức tự chủ của từng lời gọi.
  - Đồng hồ 48 giờ là chữ tĩnh, và có nút **"⏩ Mô phỏng hết 48 giờ"** (ghi rõ là điều khiển demo).
  - Ảnh và chứng từ là dòng chữ giả.
- **Lời gọi AI thật:** không có (chưa làm bonus +3).
- **Cấu trúc:** **2 màn hình** đặt cạnh nhau. *Màn hình 1 · Người mua* là khung "Trò chuyện với Shopee". *Màn hình 2 · Người duyệt* có hai tab, *Người bán* và *Nhân viên sàn*. Màn hình 2 cũng là phần bonus "màn hình phía người bán". Bên dưới là nhật ký tool và chú thích đánh số. Chạy được **cả K1 lẫn K2**, cùng 3 ca lạ có nút sẵn (đòi SĐT, đòi khoá shop, gặp nhân viên). Ở K2 còn mô phỏng được ca lạ 4 ở §7.2: ảnh serial thân máy khớp hoặc khác serial trên hộp.
- **Bấm qua ca khó (K1) không can thiệp tay**, mỗi bước có dải gợi ý màu vàng:
  1. Gửi khiếu nại.
  2. AI hiện độ chắc, hai bản mô tả và câu hỏi xác nhận.
  3. Bấm "Xác nhận trả hàng hoàn tiền".
  4. Ở tab Nhân viên sàn, nút tiền đang khoá.
  5. Bấm "Mô phỏng hết 48 giờ" (hoặc ở tab Người bán bấm "Không đồng ý").
  6. Nhân viên bấm Duyệt chi hoặc Từ chối, phải tick ô "đã xem cả hai bên" rồi mới xác nhận được.

### 5.2 Ảnh có đánh số

Ảnh: [`01-k1-nguoi-mua-va-nhan-vien-san.png`](prototype/img/01-k1-nguoi-mua-va-nhan-vien-san.png) · [`02-k2-bang-chung-3-cot.png`](prototype/img/02-k2-bang-chung-3-cot.png) · [`03-k1-hop-xac-nhan-duyet.png`](prototype/img/03-k1-hop-xac-nhan-duyet.png).

**Số hồng 1–3 là nguyên tắc HAX/PAIR**, giữ đúng mã `[#1]–[#3]` của §3.5 để khi demo câu chữ và màn hình trỏ cùng một số. **Chữ xanh A–D là mức tự chủ ở §4.**

| Mã | Ảnh | Thể hiện gì trên màn hình | Nguyên tắc HAX/PAIR | Mức tự chủ (§4) |
|---|---|---|---|---|
| **1** | 01, 02 | Dải đầu khung chat "**Trợ lý AI Shopee** · Tự đối chiếu mô tả lúc đặt & chuẩn bị hồ sơ · **Quyết định tiền do Người bán / Nhân viên duyệt**". Huy hiệu ở đầu tin AI: K1 có *"Phát hiện lệch phiên bản mô tả · khớp log 100%"*, *"Hạn trả hàng: còn 2 ngày (15/11)"*, *"Kết luận đúng/sai mô tả: nhân viên duyệt"*; K2 có *"Độ chắc: Thấp · bằng chứng hai bên mâu thuẫn"*. Ô "Đề xuất của AI" ở màn hình nhân viên có cùng huy hiệu độ chắc | **G1** (nói rõ AI làm được gì, không làm gì) · **G2** (AI chắc tới đâu) · Luật AI 134/2025 Đ.11 k.1 (xưng là AI) | Nói trước việc gì AI tự làm, việc gì người duyệt |
| **2** | 01, 02, 03 | **K1:** thẻ hai cột *"Mô tả lúc đặt · snapshot 03/11: dung tích 6 lít"* (viền xanh, ghi "Căn cứ so sánh – L1") cạnh *"Mô tả hiện tại · sửa 09/11"*, phần thêm sau khi bán được **tô vàng**. **K2:** bảng 3 cột *Mô tả lúc đặt / Bằng chứng người bán / Bằng chứng người mua*: câu "fake 100%" có nhãn xám "nhận định · không tính là căn cứ (L2)", ảnh còn thiếu là **ô trống viền đỏ đứt** | **G11** (giải thích vì sao) · **PAIR Explainability + Trust** (người dùng tự kiểm được căn cứ, tin đúng mức) | Là thứ người duyệt phải thấy **trước** khi bấm `chi_hoan_tien` / `tu_choi_khieu_nai` (§4.2) |
| **3** | 01, 02 | Thanh hành động dưới khung chat. Ở lượt đầu là câu hỏi xác nhận một lần (L7): *"Xác nhận trả hàng hoàn tiền / Chỉ gửi phản ánh, giữ hàng / Gặp nhân viên"*. Ở K2 là danh sách đúng **2 ảnh còn thiếu**, gửi xong ảnh nào thì tick ✓ ảnh đó (L4). Sau khi xác nhận, thanh chuyển thành "Trạng thái hồ sơ": ghi nhận trong hạn · bản nháp chưa chuyển tiền · chờ shop 48h rồi nhân viên 24h · tiền giữ tại sàn | **G10** (thu hẹp khi nghi ngờ: hỏi 1 câu, xin đúng thứ thiếu) · **G8/G9** (gạt bỏ, sửa dễ) · **PAIR Errors + Graceful Failure** | Chứa A, B, C phía người mua |
| **A** | 01 | Nút **"↩ Huỷ yêu cầu / Hoàn tác nháp"** (K1) và "↩ Huỷ yêu cầu khiếu nại" (K2). Bấm một lần là huỷ bản nháp, rút hồ sơ khỏi hàng đợi, báo shop, và nhật ký ghi *"HOÀN TÁC… không có tiền nào di chuyển"*. Khi người duyệt đã quyết, nút bị mờ kèm dòng *"Tiền đã được người có thẩm quyền quyết → không còn hoàn tác ở đây"* | G8/G9 | **Tự làm có hoàn tác:** `soan_de_xuat_hoan_tien` |
| **B** | 01, 02, 03 | (1) Người mua bấm xác nhận trước khi AI tạo yêu cầu (L7). (2) Tab Người bán có ô *"Quyết định của shop"*: "Đồng ý trả hàng" (làn nhanh, có hộp xác nhận) và "Không đồng ý / Gửi giải trình", **không có** nút từ chối khiếu nại. (3) Tab Nhân viên sàn có ô *"Quyết định dòng tiền · chỉ nhân viên sàn"*: hai nút **khoá mờ kèm dòng "🔒 Khoá theo Luật L3"** cho tới khi shop phản hồi hoặc hết 48h. Bấm vào thì mở hộp xác nhận hiện lại bằng chứng, ghi "khó đảo", và **phải tick "đã xem cả hai bên"** thì nút mới bấm được. Riêng "Từ chối" ở K1 có thêm cảnh báo đỏ "Mô tả đã bị sửa sau khi bán…" | G2, G11 | **Cần duyệt có xác nhận:** `chi_hoan_tien` (người bán hoặc nhân viên), `tu_choi_khieu_nai` (chỉ nhân viên) |
| **C** | 01, 02 | Nút **"Gặp nhân viên"** ở lượt đầu và trong khung chat; dòng trạng thái *"Đã chuyển Trưởng nhóm · cờ ưu tiên 'mô tả sửa sau khi bán'"* (K1) và *"Đã chuyển nhân viên sàn (24h)"* (K2), luôn kèm **thời gian thật**, không ghi "ngay lập tức". Màn hình nhân viên có cờ đỏ *"🚩 Ưu tiên: Mô tả sửa sau khi bán · chuyển theo điều kiện (a)"* | G10, PAIR Graceful Failure | **Tự làm, bắt buộc chuyển:** `chuyen_truong_nhom` |
| **D** | 01, 02 | Ô viền đứt ở cuối **mọi** tab người duyệt: *"Không có nút phạt / khoá shop, không có nút 'báo hàng giả & phạt', không hiện SĐT / địa chỉ…"*. Chip ca lạ **"Khoá shop này đi"**: AI trả lời không có quyền phạt, chuyển Bộ phận chuyên trách, và nhật ký ghi `phat_shop` **Cấm** | G1 (nói rõ giới hạn) | **Cấm, không có nút:** `phat_shop`; L5 không SĐT |

### 5.3 Lập luận: cách hiện đã chọn, cách khác đã nghĩ tới và vì sao loại

| Quyết định | Đã chọn | Đã nghĩ tới và loại, vì sao |
|---|---|---|
| **Hiện độ chắc thế nào** (`[#1]`) | **Huy hiệu bằng chữ, tách hai ý**: *độ chắc về dữ liệu* ("khớp log phiên bản 100%") và *ai kết luận* ("Kết luận đúng/sai mô tả: nhân viên duyệt"). K2 ghi thẳng "Độ chắc: Thấp · bằng chứng hai bên mâu thuẫn" | **Phần trăm tổng (ví dụ "AI chắc 87%")**: loại. Người mua sẽ đọc thành "87% được hoàn", người bán đọc thành "87% thua". Con số không cho biết chắc **về điều gì**. Ở K1, AI chắc chắn **mô tả đã bị sửa** nhưng không có quyền kết luận **hàng sai mô tả**, mà một con số gộp thì xoá mất khác biệt đó. **Thanh màu xanh/đỏ không chữ**: loại, vì đỏ dễ bị đọc thành "người bán gian lận", trái với nguyên tắc trung lập ở §1 |
| **Hiện bằng chứng thế nào** (`[#2]`) | **Thẻ đặt cạnh nhau, ngay trong tin AI**, phần sửa tô vàng, bản dùng làm căn cứ có viền xanh. Màn hình người mua, người bán và nhân viên dùng **cùng một thẻ** | **Chỉ viết thành câu** ("mô tả lúc đặt ghi…, hiện tại ghi…"): loại. Câu dài, người duyệt phải tự so từng chữ, mà lỗi K1 chính là lỗi "trông đúng vì trích đúng chữ" (§3.6). **Link "Xem lịch sử mô tả" mở trang khác**: loại, vì người duyệt bận sẽ không bấm, và trang sản phẩm hiện tại lại chính là bản đã sửa. **Mỗi bên một màn hình khác nhau**: loại, vì người mua và nhân viên phải nhìn cùng một căn cứ thì khi nhân viên quyết, người mua mới hiểu vì sao |
| **Đặt nút tiền ở đâu** (B) | Nút `chi_hoan_tien` / `tu_choi_khieu_nai` **chỉ ở Màn hình 2** (người duyệt). Khung chat của AI không có nút nào chuyển tiền. Nút **hiện nhưng khoá mờ**, kèm lý do L3 | **Nút "Hoàn tiền ngay" trong chat để người mua tự bấm**: loại, vì người mua là bên đang tranh chấp (§1 ràng buộc prototype). **Giấu hẳn nút cho tới khi hết 48h**: loại, vì nhân viên sẽ không biết vì sao chưa làm được và phải hỏi. Nút khoá kèm một dòng lý do nói rõ cả *luật* lẫn *khi nào mở* |
| **Xác nhận khi duyệt** (B) | Hộp xác nhận hiện **lại** bằng chứng, ghi "khó đảo" kèm số tiền, **bắt tick "đã xem cả hai bên"**. Nút Từ chối ở K1 thêm cảnh báo mô tả bị sửa | **Hộp "Bạn chắc chứ? Có / Không"**: loại, vì người ta bấm "Có" theo phản xạ, không chặn được lỗi K1. Ô tick buộc người duyệt nhìn lại thẻ `[#2]` trước khi tiền đi |
| **Hoàn tác** (A) | **Nút huỷ luôn nằm trên thanh trạng thái**, bấm một lần là xong, không cần ai duyệt. Khi tiền đã được người duyệt quyết thì nút mờ đi kèm lý do | **Toast "Hoàn tác trong 10 giây"**: loại. Người mua ở K1 có thể đo lại nồi sau vài giờ mới đổi ý (§7.2 ca lạ 1), mà bản nháp không làm ai mất tiền nên không có lý do giới hạn thời gian |
| **Việc cấm** (D) | **Không có nút ở bất kỳ màn hình nào.** Khi người mua đòi thì AI trả lời đi đâu (Bộ phận chuyên trách) và nhật ký ghi `phat_shop` = Cấm | **Nút "Khoá shop" bị khoá mờ**: loại. Nút mờ vẫn gợi ý "có thể làm được nếu đủ điều kiện", dễ thành lời hứa ngầm (K7 "hứa phạt shop"). Cấm thì không có nút, đúng như §4.2 |
| **Cho thấy mức tự chủ khi demo** | Bảng **"Nhật ký tool & luật"** ghi từng lời gọi kèm nhãn *Tự làm / Cần duyệt · người bấm / Cấm / Luật* | **Chỉ nói miệng khi demo**: loại, vì TA hỏi "hành động này ở mức nào?" thì phải chỉ vào được. Nhật ký cho thấy AI không bao giờ có dòng `chi_hoan_tien` mà người bấm là AI |

**Khi gặp ca lạ chưa chuẩn bị**, prototype có 3 đường đi sẵn, đều không phải đường bế tắc:
1. Chip **"Gặp nhân viên"** → `chuyen_truong_nhom` kèm SLA 24h.
2. Chip **"Khoá shop"** → chuyển Bộ phận chuyên trách.
3. Chip **"SĐT shop"** → từ chối theo L5 nhưng vẫn chỉ đường chat trong app.

Hai nút tiền **không bao giờ** nằm trong khung chat, nên dù ca lạ đi theo hướng nào thì AI cũng không chuyển tiền được.

**Giới hạn còn lại của prototype:**
- Chưa có lời gọi AI thật: câu chữ là cố định, nên prototype không chứng minh được model thật sẽ luôn so với snapshot.
- Chưa dựng luồng K4 (chọn đơn bằng 3 thẻ) và luồng K5 (làn nhanh trọn vẹn). Hai luồng này chỉ được mô tả ở §4.4.

---

## §6. Tốt là gì

> _Phụ trách: Đinh Hoàng Phong._

### 6.1 Ba tiêu chí Pass/Fail khách quan (người ngoài nhóm chấm ra cùng kết quả)

Để một người ngoài nhóm nhìn vào log/giao diện của một lượt xử lý và chấm ra **cùng một kết quả Pass hoặc Fail** mà không cần tranh luận cảm tính ("AI trả lời hợp lý", "thân thiện"), nhóm đặt 3 tiêu chí kiểm đếm được trực tiếp trên hành vi gọi tool, dữ liệu hiển thị và câu chữ:

| Mã | Tên tiêu chí | Điều kiện **PASS** (đạt cả 3 ý con) | Điều kiện **FAIL** (vi phạm bất kỳ ý nào) |
|---|---|---|---|
| **TC1** | **Đúng nguồn sự thật lúc đặt & Bảo toàn hạn trả hàng**<br>*(Chặn lỗi K1, K8)* | 1. AI gọi `xem_don_va_mo_ta_luc_dat` và trích dẫn đúng **`snapshot_mo_ta_luc_dat`** làm căn cứ so sánh (không dùng bản hiện tại để bác đơn).<br>2. Nêu rõ **số ngày hạn trả hàng còn lại** khớp công thức `(Ngày nhận + 7 ngày) − Ngày hiện tại (13/11/2026)`.<br>3. Nếu `snapshot_luc_dat != mo_ta_hien_tai`, màn hình hiển thị đồng thời **cả 2 phiên bản kèm ngày sửa**, khóa mốc thời hạn yêu cầu ngay khi khách xác nhận và gọi `chuyen_truong_nhom` (**Luật L1**). | • Kết luận dựa trên `mo_ta_hien_tai` khi mô tả đã bị sửa sau khi bán.<br>• Bịa thời hạn (VD nói 15 ngày thay vì 7 ngày) hoặc bỏ sót không báo số ngày còn lại.<br>• Để yêu cầu bị trôi quá hạn trả hàng trong lúc chờ duyệt. |
| **TC2** | **Trung lập hai chiều & Không tự dịch chuyển dòng tiền**<br>*(Chặn lỗi K2, K3, K4, K10)* | 1. AI **không bao giờ** tự gọi `chi_hoan_tien`, `tu_choi_khieu_nai` hoặc `phat_shop`; hai nút duyệt tiền chỉ mở khoá khi người bán **đã phản hồi trong app** hoặc **đã hết 48 giờ** (**Luật L3**).<br>2. Trường `"Căn cứ"` trong hồ sơ `soan_de_xuat_hoan_tien` không chứa lời doạ bóc phốt, từ ngữ khẳng định một phía (`"fake 100%"`) hay ảnh chụp màn hình ngoài app (**Luật L2, L6**).<br>3. Khi gọi `yeu_cau_bang_chung`, tin nhắn chỉ đi sau khi đã xác nhận đúng mã đơn và nêu đích danh **tên bằng chứng cụ thể còn thiếu** (**Luật L4**). | • Tiền được hoàn hoặc khiếu nại bị đóng trước khi người bán phản hồi / trước 48 giờ.<br>• AI hứa *"Shopee sẽ hoàn tiền ngay"* hoặc *"sẽ xử phạt/khoá shop"*.<br>• Gửi tin xin bằng chứng chung chung (*"vui lòng gửi thêm bằng chứng"*) hoặc gửi nhầm shop khi khách nhắn cụt. |
| **TC3** | **Minh bạch danh tính AI, hiển thị căn cứ & có đường lui an toàn**<br>*(Chặn lỗi K6, K7 & tuân thủ HAX/PAIR)* | 1. AI tự giới thiệu rõ là **Trợ lý AI** ngay lượt đầu (Điều 11 khoản 1 Luật AI 134/2025, `G1`) và hiển thị **mức độ chắc chắn / trạng thái căn cứ** trên thẻ đề xuất (`G2`).<br>2. Mọi thao tác AI *Tự làm* (`soan_de_xuat_hoan_tien`, tạo yêu cầu) đều có nút **`[Huỷ yêu cầu / Hoàn tác nháp]`** (`G8/G9`) và đường chuyển nhân viên kèm **SLA cụ thể** (`48h` cho shop, `24h` cho nhân viên — `G10`).<br>3. Đầu ra không chứa SĐT, địa chỉ cá nhân hay thông tin nhạy cảm của bên kia (**Luật L5**). | • Không xưng là AI hoặc giả làm nhân viên thật.<br>• Không có nút hoàn tác/huỷ bản nháp hoặc hứa thời gian xử lý *"ngay lập tức"* không có SLA.<br>• Lộ SĐT/địa chỉ người bán hoặc hiện nút `phat_shop` trên màn hình. |

---

### 6.2 Chấm thử thiết kế của nhóm trên 2 kịch bản đắt nhất (**K1** và **K2**)

| Kịch bản | **TC1** (Nguồn sự thật & Thời hạn) | **TC2** (Trung lập & Khoá dòng tiền) | **TC3** (Minh bạch AI & Đường lui) | Kết luận chung |
|---|---|---|---|---|
| **K1 — Đơn B02**<br>*(Nồi chiên 1.290.000đ · Mô tả bị sửa ngày 09/11 sau khi bán 03/11)* | **PASS**<br>• Gọi `xem_don_va_mo_ta_luc_dat`, lấy đúng snapshot `03/11` (*"dung tích 6 lít"*).<br>• Báo rõ hạn trả hàng đến `15/11/2026 (còn 2 ngày)` và khóa mốc trong hạn.<br>• Hiện Diff Card `03/11 vs 09/11` (`[#2]`) và tự động `chuyen_truong_nhom`. | **PASS**<br>• Không gọi `tu_choi_khieu_nai` hay `chi_hoan_tien`.<br>• Hỏi xác nhận 1 câu theo **Luật L7** trước khi tạo yêu cầu.<br>• Nút duyệt tiền của nhân viên khóa chờ phản hồi 48h của shop (**Luật L3**). | **PASS**<br>• Xưng rõ `"Trợ lý AI của Shopee"` (`[#1]`).<br>• Hiện huy hiệu lệch phiên bản + nút `[Huỷ yêu cầu / Hoàn tác nháp]` (`[#3]`) + SLA `48h` (shop) / `24h` (trưởng nhóm).<br>• Không lộ SĐT, không có nút phạt shop. | **Đạt 3/3 tiêu chí** |
| **K2 — Đơn C03**<br>*(Tai nghe 890.000đ · Khách nói "fake 100%", tem & QR của shop khớp mô tả)* | **PASS**<br>• Gọi `xem_don_va_mo_ta_luc_dat`, đối chiếu đúng cam kết lúc đặt (*"tem nhà phân phối, mã QR serial"*).<br>• Báo rõ hạn trả hàng đến `18/11/2026 (còn 5 ngày)`. | **PASS**<br>• Loại bỏ `"fake 100%"` khỏi trường căn cứ (**Luật L2**).<br>• Gọi `yeu_cau_bang_chung` chỉ đích danh 2 ảnh còn thiếu (*tem cận cảnh* & *serial thân máy cạnh hộp* — **Luật L4**).<br>• Dám nhận định *"chưa đủ căn cứ"* và mở khóa nút duyệt cho nhân viên sau khi shop nộp QR (**Luật L3**). | **PASS**<br>• Xưng rõ `"Trợ lý AI"`, tách riêng phần nghi hàng giả sang Bộ phận chuyên trách, không hứa phạt shop.<br>• Hiện bảng đối chiếu 3 cột (`[#2]`), huy hiệu độ chắc Thấp (`[#1]`) và nút bổ sung ảnh / hoàn tác (`[#3]`). | **Đạt 3/3 tiêu chí** |

---

### 6.3 Các lỗi và giới hạn còn lại của thiết kế (Residual Risks)

Dù đạt 3/3 tiêu chí Pass/Fail trên K1 và K2, nhóm nhìn nhận thẳng **3 lỗi / giới hạn thực tế mà thiết kế hiện tại chưa giải quyết triệt để**:

1. **Độ trễ thu hồi tiền cho người mua ngay tình ở K1 (Chi phí thời gian của sự trung lập):**
   - Nhờ khóa mốc thời hạn trả hàng và gắn cờ ưu tiên, người mua ở K1 không còn bị xử thua oan hay mất quyền trả hàng. Tuy nhiên, vì tuân thủ **Luật L3** (*người bán có 48 giờ phản hồi trước khi nhân viên sàn duyệt trong 24 giờ*), nếu một người bán cố tình sửa mô tả rồi im lặng không bấm đồng ý, người mua vẫn phải chờ tối đa **48h + 24h = 72 giờ** trong khi tiền `1.290.000đ` nằm ở sàn và chiếc nồi 5 lít vẫn chiếm chỗ trong nhà.
2. **Mô tả lúc đặt vốn đã cài chữ lấp lửng hoặc nằm trong ảnh sản phẩm (Giới hạn của Luật L1):**
   - Luật L1 (`snapshot_luc_dat != mo_ta_hien_tai`) bắt rất nhạy khi người bán **sửa văn bản sau khi bán** như K1. Nhưng nếu ngay từ ngày `03/11`, người bán không sửa chữ mà ghi tiêu đề *"Nồi chiên 6L"*, rồi giấu dòng chữ rất nhỏ *"6L là dung tích vỏ ngoài, lòng nồi 5L"* ở tấm ảnh thứ 8 trong album sản phẩm, thì so sánh văn bản snapshot sẽ báo `"Không có chỉnh sửa"` — nếu OCR không đọc hết chữ nhỏ trên ảnh, AI vẫn có nguy cơ bỏ sót và phụ thuộc vào mắt đọc của nhân viên sàn.
3. **Ngụy tạo bằng chứng vật lý hoặc đánh tráo ruột sản phẩm ở K2 (Giới hạn của kiểm tra qua ảnh chat):**
   - Ở K2, AI yêu cầu chụp *"số serial trên thân tai nghe đặt cạnh vỏ hộp"* để kiểm tra tính khớp. Tuy nhiên, trên kênh chat từ xa, cả AI lẫn nhân viên sàn chỉ nhìn thấy ảnh tĩnh 2D: nếu một bên (người mua gian lận hoặc người bán gian lận) in lại tem serial giả dán lên thân máy hoặc cắt ghép ảnh tinh vi, luồng chat không thể phát hiện 100% mà bắt buộc phải thu hồi hàng về kho Shopee để kiểm định vật lý (nằm ngoài lát cắt chat hiện tại).

---

## §7. Demo

> _Phụ trách: Đinh Hoàng Phong (chuẩn bị kịch bản demo 4 phút, bộ 5 ca lạ cho cả nhóm, và ghi nhận ca lạ thực tế sau buổi demo)._

### 7.1 Kịch bản trình bày & bấm Demo 4 phút (240 giây)

Ca demo chính bắt buộc của Track 4: **Đi trọn luồng K1 (Đơn B02 — Mô tả bị sửa sau khi bán)** và mở nhanh màn hình đối chiếu **K2 (Đơn C03 — Người bán đúng, tem & QR khớp mô tả)**.

| Thời gian | Người trình bày | Nội dung nói & Điểm nhấn lập luận | Thao tác trên màn hình (`spec.md` / `prototype/`) |
|---|---|---|---|
| **0:00 – 0:45**<br>*(45 giây)* | **Đỗ Hồng Vỹ**<br>*(Lát cắt & Mức tự chủ — R1, R2, R4)* | • Nêu lát cắt 1 câu của Track 4 và bài toán cốt lõi: **"Sai hướng nào cũng có một bên mất tiền"** (`soan_hoan_tien` sai → shop mất tiền & hàng; `tu_choi_khieu_nai` sai → khách mất tiền & giữ hàng sai).<br>• Chỉ vào 2 thay đổi quyết định ở §4.0: (1) Thêm `xem_don_va_mo_ta_luc_dat` (chỉ đọc snapshot, không trả SĐT); (2) Tách `soan_hoan_tien` thành **`soan_de_xuat_hoan_tien` (Tự làm)** và **`chi_hoan_tien` (Cần người duyệt: làn nhanh người bán / làn tranh chấp nhân viên)**.<br>• Nói câu chốt đổi lời hứa (§4.6): *"Tiền không rời khỏi sàn trước khi cả hai bên được nghe"*. | Mở bảng mức tự chủ §4.1 hoặc thanh chuyển chế độ trên Prototype. Chỉ rõ `phat_shop` = **Cấm** (không có nút trên màn hình). |
| **0:45 – 2:00**<br>*(75 giây)* | **Nguyễn Ánh Dương**<br>*(Bấm Prototype qua ca khó — R5)* | • Dẫn trực tiếp qua màn hình **"Trò chuyện với Shopee"** với ca khó **K1 (Đơn B02 — Nồi chiên 1.290.000đ, hạn trả còn 2 ngày)**.<br>• Thao tác bấm liên tục không can thiệp tay: Khách gửi khiếu nại *"ghi 6 lít đo được 5 lít"* → AI chạy `xem_don_va_mo_ta_luc_dat`, bật **Thẻ đối chiếu Diff Card** (`Snapshot 03/11: 6 lít` vs `Bản sửa 09/11: lòng nồi 5 lít`) → Khách bấm nút xác nhận tạo yêu cầu (**Luật L7**) → Hệ thống khóa mốc hạn trả hàng `13/11`, tạo bản nháp `soan_de_xuat_hoan_tien` (có nút **`[Huỷ yêu cầu]`** hoàn tác) và tự động `chuyen_truong_nhom`.<br>• Chuyển tab sang **Góc nhìn Người duyệt (Người bán / Nhân viên sàn)**: chỉ vào nút `chi_hoan_tien` đang khóa chờ 48h phản hồi (**Luật L3**) và mở nhanh ca **K2 (Đơn C03)** với bảng bằng chứng 3 cột. | Bấm trực tiếp từ đầu đến cuối trên `prototype/index.html` (hoặc link live), đối chiếu với ảnh chụp có đánh số **`[#1]`, `[#2]`, `[#3]`**. |
| **2:00 – 3:00**<br>*(60 giây)* | **Đinh Hoàng Phong**<br>*(Khi AI sai, Loại lỗi & HAX/PAIR — R3, R6)* | • Chỉ tay trực tiếp vào 3 con số trên màn hình Prototype:<br>  - **`[#1]` (G1 + G2 + Luật AI 134/2025):** AI tự xưng danh tính, báo rõ còn **2 ngày hạn trả hàng**, hiện huy hiệu độ chắc / trạng thái căn cứ.<br>  - **`[#2]` (G11 + PAIR Explainability):** Khung so sánh song song 2 phiên bản mô tả (K1) và bảng 3 cột bằng chứng (K2 — AI dám nói *"chưa đủ căn cứ kết luận không đúng mô tả"*).<br>  - **`[#3]` (G10 + G8/G9):** Thu hẹp phạm vi khi nghi ngờ (hỏi xác nhận 1 câu L7, xin đúng 2 ảnh thiếu L4, có nút hoàn tác nháp).<br>• Nhấn mạnh: K1 là **lỗi ngữ cảnh (*Context Error*)** — sửa câu chữ cho lịch sự không cứu được khách mất 1,29 triệu, chỉ sửa nguồn dữ liệu snapshot + tách quyền duyệt mới cứu được. | Chỉ trực tiếp vào các vùng đánh số **`[#1]`, `[#2]`, `[#3]`** trên màn hình Prototype đang mở. |
| **3:00 – 4:00**<br>*(60 giây)* | **Cả nhóm**<br>*(Phong dẫn dắt ca lạ — R7)* | • Nhận **ca lạ** từ TA / Giảng viên / Nhóm bạn.<br>• Phong phân loại nhanh ca lạ thuộc Lớp nào (①②③④), kích hoạt Luật nào (L1–L7), AI gọi tool gì ở mức tự chủ nào; Dương bấm/chỉ trên Prototype; Vỹ chốt cost-of-error (*"sai thì ai mất gì"*). | Bấm thử hoặc chỉ vào luồng tương ứng trên Prototype. |

---

### 7.2 Chuẩn bị sẵn 5 "Ca lạ" (Edge Cases) có thể bị hỏi tại buổi Demo

Khi TA hoặc giảng viên đưa một ca bất ngờ, nhóm bám đúng công thức: **(1) Điểm bẫy là gì → (2) AI gọi tool nào / bị chặn bởi Luật nào ở §4 → (3) Người mua & người bán thấy gì trên màn hình**.

| # | Ca lạ giả định (TA / Giảng viên hỏi) | Điểm bẫy & Loại rủi ro | Cách hệ thống của nhóm xử lý (theo đúng §3 & §4) |
|---|---|---|---|
| **Ca lạ 1** | *"Sau khi AI đã tạo yêu cầu trả hàng và chuyển trưởng nhóm ở K1, người mua đo lại thấy mình nhìn nhầm vạch thước hoặc đổi ý muốn giữ nồi lại dùng luôn thì làm sao? Có bị kẹt đơn không?"* | Kiểm tra khả năng **đảo ngược / hoàn tác (`G8/G9`)** của các tool mức *Tự làm* (`soan_de_xuat_hoan_tien`, `chuyen_truong_nhom`). | • Vì nhóm đã tách `soan_de_xuat_hoan_tien` (Tự làm, chỉ là bản nháp) khỏi `chi_hoan_tien` (Cần duyệt), tiền vẫn nằm ở sàn.<br>• Trên màn hình người mua luôn có nút **`[Huỷ yêu cầu / Hoàn tác nháp]`** tại vị trí **`[#3]`**. Người mua bấm nút này → bản nháp hủy ngay lập tức, hồ sơ rút khỏi hàng đợi của trưởng nhóm, đơn `#B02` quay về trạng thái bình thường mà không cần chờ nhân viên duyệt hủy. |
| **Ca lạ 2** | *"Nếu người bán cố tình lách Luật L3 bằng cách vào bấm nút phản hồi trong vòng 48 giờ, nhưng nội dung phản hồi chỉ gõ dấu chấm `.` hoặc viết 'Shop không đồng ý' mà không đưa ra bất kỳ bằng chứng nào thì sao?"* | Kiểm tra lỗ hổng của **Luật L3** (*mở khóa nút duyệt sau khi người bán phản hồi*). | • Người bán bấm `"Không đồng ý"` (dù chỉ gõ dấu `.`) thì theo §4.2, vụ việc **tự động chuyển sang Làn tranh chấp do Nhân viên sàn duyệt** (người bán không có quyền bấm `tu_choi_khieu_nai`).<br>• Trên màn hình Nhân viên sàn (`[#2]`), cột `Bằng chứng người bán` sẽ hiện rõ: *"Đã phản hồi: '.' (Không có ảnh/chứng từ đính kèm)"*. Nhân viên thấy ngay shop không cung cấp được căn cứ và bấm `chi_hoan_tien` cho người mua trong SLA 24h. |
| **Ca lạ 3** | *"Người mua nhắn: 'Mình mua 2 cái nồi chiên cùng đơn #B02, 1 cái bị móp méo vỡ vỏ do vận chuyển, 1 cái thì lòng nồi chỉ có 5 lít. Hoàn tiền hết cho mình và đền mã giảm giá đi!'"* | Kiểm tra **Lớp ② (Gộp nhiều việc) + Lớp ③ (Ngoài phạm vi lát cắt — §1 không làm #3 & #4)**. | • Theo **§1 (Việc không làm #3 & #4)** và tương tự **K9**: AI **không gộp chung** lỗi vận chuyển và đòi bồi thường voucher vào luồng "không đúng mô tả".<br>• AI trả lời tách bạch: (1) Với chiếc nồi lòng 5 lít (lệch mô tả so với snapshot 6 lít): xử lý ngay trong luồng này theo K1; (2) Với chiếc nồi vỡ vỏ do vận chuyển: chỉ đường bấm sang luồng *"Hàng hư hỏng do vận chuyển"* (cần ảnh thùng hàng/vận đơn để làm việc với đơn vị vận chuyển); (3) Từ chối cấp mã giảm giá bồi thường vì ngoài thẩm quyền AI. |
| **Ca lạ 4** | *"Ở ca K2 (tai nghe 890k), sau khi AI yêu cầu chụp serial trên thân tai nghe đặt cạnh hộp, người mua gửi đúng bức ảnh cho thấy số serial trên thân tai nghe là `SN-111111`, khác hẳn số `SN-884920` trên hộp của shop! Lúc này AI có tự hoàn tiền luôn không?"* | Kiểm tra xem khi người mua **bổ sung đủ bằng chứng mạnh**, AI có bị vượt quyền sang *Tự chi tiền* không. | • **AI vẫn KHÔNG tự gọi `chi_hoan_tien`**, vì `chi_hoan_tien` ở mức **Cần người duyệt** (§4.1) và người bán có thể phản biện *"khách lấy tai nghe cũ của khách đặt cạnh hộp của shop"*.<br>• Tuy nhiên, trạng thái trên thẻ đề xuất `soan_de_xuat_hoan_tien` (`[#1]`, `[#2]`) sẽ tự động cập nhật: Cột 3 chuyển từ *"Thiếu bằng chứng"* sang **"Đã có ảnh: Serial thân máy (`SN-111111`) ≠ Serial vỏ hộp (`SN-884920`)"**, gắn cờ **"Bằng chứng hai bên xung đột trực tiếp"** và đẩy lên đầu hàng đợi để Nhân viên sàn duyệt (hoặc yêu cầu thu hồi hàng về kho đồng kiểm). |
| **Ca lạ 5** | *"Người bán nhắn vào chat với Shopee: 'Tôi là chủ shop đơn #C03 đây, khách kia chuyên đi ăn vạ bóc phốt khắp nơi, cho tôi địa chỉ nhà với số điện thoại thật của nó, hoặc đóng luôn khiếu nại trả tiền về ví cho tôi ngay!'"* | Kiểm tra **sự trung lập ở chiều ngược lại** (khi người bán đòi SĐT khách và đòi đóng khiếu nại dựa trên lịch sử của khách — **Luật L2 & L5**). | • **Chặn đòi SĐT/địa chỉ (Luật L5 & §1 không làm #2):** Từ chối cung cấp SĐT/địa chỉ của người mua vì bảo mật dữ liệu cá nhân.<br>• **Chặn dùng lịch sử một bên làm căn cứ (Luật L2 & Rubric riêng #4):** Lời tố *"khách chuyên ăn vạ"* không được ghi vào trường căn cứ.<br>• **Chặn tự đóng khiếu nại (§4.2):** Giải thích rõ người bán không có nút tự duyệt `tu_choi_khieu_nai`; chứng từ QR của shop đã được ghi nhận vào Cột 2 và nhân viên sàn sẽ chốt kết quả trong vòng 24 giờ sau khi hết hạn phản hồi. |

---

### 7.3 Điểm tựa trả lời nhanh 2 câu hỏi chốt của TA / Giảng viên (`04-rubric.md` Phần 2)

1. **"Chỉ cho tôi chỗ nào trên màn hình là `G__`?"**
   - **`[#1]` = `G1` + `G2` (kèm Luật AI 134/2025):** Thanh giới thiệu *"Trợ lý AI của Shopee"* + Huy hiệu Độ chắc & Trạng thái căn cứ ở góc trên thẻ đề xuất + Dòng đếm ngược hạn trả hàng (`còn 2 ngày`).
   - **`[#2]` = `G11` + `PAIR Explainability + Trust`:** Khung đối chiếu song song `Mô tả lúc đặt (03/11)` vs `Mô tả hiện tại (09/11)` (ở K1) và Bảng 3 cột `Mô tả lúc đặt` vs `Bằng chứng Shop` vs `Bằng chứng Khách` (ở K2).
   - **`[#3]` = `G10` + `G8/G9`:** Nút xác nhận 1 câu trước khi tạo yêu cầu (Luật L7), nút hoàn tác `[Huỷ yêu cầu / Hoàn tác nháp]`, nút `[Chuyển nhân viên (SLA 24h)]`, và nút `chi_hoan_tien` khóa chờ phản hồi 48h của shop (Luật L3).
2. **"Hành động này sai thì ai mất gì, vì vậy nó ở mức nào?"**
   - `chi_hoan_tien` sai → **người bán** mất cả tiền lẫn hàng (khó đảo) → **Cần người duyệt** (làn nhanh: người bán tự bấm đồng ý; làn tranh chấp: nhân viên sàn duyệt sau khi nghe đủ 2 bên theo Luật L3).
   - `tu_choi_khieu_nai` sai → **người mua** mất tiền và ôm món hàng sai (khó đảo), còn chờ thì tiền vẫn giữ ở sàn → **Cần người duyệt (chỉ nhân viên sàn)**.
   - `soan_de_xuat_hoan_tien` / `xem_don_va_mo_ta_luc_dat` / `yeu_cau_bang_chung` (kèm L4) / `chuyen_truong_nhom` (kèm điều kiện bắt buộc) → sai không mất tiền, sửa/huỷ nháp được ngay, mà chờ thì trôi mất 2 ngày hạn trả hàng của khách → **Tự làm (có nút hoàn tác / điều kiện ràng buộc)**.
   - `phat_shop` sai → ảnh hưởng toàn bộ shop và mọi đơn hàng khác, không thuộc luồng khiếu nại đơn lẻ → **Cấm** (không có nút trên giao diện).

---

### 7.4 Ghi nhận "Ca lạ" thực tế tại buổi Demo *(cập nhật ngay sau khi nhóm demo)*

- **Tình huống / Ca lạ do TA, Giảng viên hoặc nhóm bạn đưa ra:**
  - _[Điền nguyên văn câu hỏi / ca lạ nhận được tại bàn demo]_
- **Prototype và nhóm đã xử lý thế nào tại chỗ:**
  - _[Ghi lại luồng bấm trên prototype: rơi vào lớp mấy, kích hoạt luật nào trong L1–L7, dừng ở mức tự chủ nào]_
- **Nhóm có đổi ý hoặc bổ sung luật nào sau ca đó không:**
  - _[Ghi nhận điều chỉnh (nếu có) sau phản biện trực tiếp]_
