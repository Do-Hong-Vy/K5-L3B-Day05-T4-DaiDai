# Phân công LAB5 — Track 4 · Thương mại điện tử (L3B)

> Lát cắt: trong **Trò chuyện với Shopee**, khi **người mua** báo "hàng nhận không đúng mô tả", **AI tự hướng dẫn gửi yêu cầu trả hàng hoàn tiền, xin thêm bằng chứng, hay chuyển nhân viên**, để người mua biết đúng bước tiếp theo và người bán không bị xử thua khi họ đúng.
>
> Hạn nộp: **23:59 ngày 13/11/2026** · Repo mới, công khai: `K5-L3B-Day05-T4-<TenNhom>` (viết liền, không dấu).

## 1. Nguyên tắc chia việc

- Chia theo **điểm rubric**: mỗi người **sở hữu** khoảng 1/3 số điểm và **trình bày phần đó khi demo** (R7: ai cũng bị hỏi phần có tên mình).
- Chặng 1–4 **cả nhóm cùng bàn**, nhưng mỗi mục có **một người cầm bút** và chịu trách nhiệm cuối.
- Ba khối nặng nhất (R3, R4, R5 — mỗi khối 25 điểm) nằm ở **ba người khác nhau**.

| Thành viên | Mã HV | Sở hữu chính | Điểm phụ trách | Trình bày khi demo |
|---|---|---|---|---|
| **Đỗ Hồng Vỹ** | 2A202604107 | §1 Lát cắt · §2 Kịch bản rủi ro · **§4 Mức tự chủ** · repo & nộp bài | R1 5 + R2 10 + **R4 25** = 40 | Lát cắt (30") + mức tự chủ & "sai thì ai mất gì" |
| **Đinh Hoàng Phong** | 2A202604090 | **§3 Khi AI sai** · §6 Tốt là gì · §7 kịch bản demo | **R3 25** + R6 5 + R7 5 = 35 | Câu AI nói, loại lỗi, HAX/PAIR + dẫn ca lạ |
| **Nguyễn Ánh Dương** | 2A202604087 | **§5 Prototype** · `prototype/` · ảnh đánh số · bonus | **R5 25** + bonus (+3) | Bấm prototype qua ca khó |

> Vỹ cầm nhiều điểm nhất nhưng §1 và §2 xong sớm (phút 45); Dương cầm phần tốn thời gian nhất (prototype 60'); Phong viết nhiều câu chữ nhất và chuẩn bị demo. Khối lượng thời gian gần như bằng nhau.

---

## 2. Việc cụ thể từng người

### Đỗ Hồng Vỹ — Kịch bản & Mức tự chủ

**§1 Lát cắt & phạm vi (R1 · 5đ)**
- [x] Chép lát cắt từ track vào `03-spec-template.md`.
- [x] Viết **3 việc KHÔNG làm**, mỗi việc 1 câu lý do. Gợi ý hướng: không xử phạt/khoá shop (`phat_shop` — thuộc bộ phận chuyên trách); không xử lý nghi hàng giả; không đưa SĐT/địa chỉ giữa hai bên; không xử lý khiếu nại khác ngoài "không đúng mô tả" (giao trễ, mất hàng…).

**§2 Kịch bản rủi ro (R2 · 10đ) — mốc M1, phút 45**
- [x] Gom ý cả nhóm, viết **≥8 kịch bản** dạng bảng: `tin người dùng | lớp ①②③④ | AI có thể sai thế nào | sản phẩm tốt nên làm gì | nhãn`.
- [x] Mỗi lớp ①②③④ ít nhất 1 kịch bản; phủ **đủ 6 Hard tests** của track: mô tả bị sửa sau khi bán · doạ bóc phốt · người bán đúng (tem khớp mô tả) · đòi khoá shop / nghi hàng giả · tin cụt ("hàng sai rồi, xử lý đi") · đòi SĐT bên kia.
- [x] Cột "AI có thể sai thế nào" **phải trỏ về tool cụ thể** (`soan_hoan_tien`, `tu_choi_khieu_nai`, `phat_shop`, `yeu_cau_bang_chung`, `chuyen_truong_nhom`) hoặc dữ liệu (mô tả lúc đặt vs mô tả hiện tại).
- [x] Có ít nhất 1 kịch bản "trông đúng nhưng vẫn rủi ro" (VD: hoàn đúng nhưng chưa cho người bán phản hồi).
- [x] Khoanh **2 kịch bản đắt nhất** + lý do vì sao đắt hơn + kịch bản **suýt được chọn** và vì sao không.

**§4 Mức tự chủ (R4 · 25đ) — mốc M2, phút 125**
- [ ] Tổ chức bước "mỗi người tự xếp mức 5 tool trong 5', không bàn" → ghi lại **ai chọn gì**. _(Đã viết sẵn phương án của Vỹ trong 03-spec-template.md §4.3; **còn thiếu lựa chọn của Phong và Dương**: cần chạy vòng xếp mức thật rồi điền.)_
- [x] Với **từng tool** trong 5 tool: mức (tự làm / cần người duyệt / cấm) · sai thì ai chịu gì · đảo được không · chờ người thì mất gì · phương án đã loại. Nếu cần duyệt: **ai duyệt, thấy gì, quá hạn thì sao**.
- [x] **Tool khó xếp nhất** (gần như chắc là `soan_hoan_tien` hoặc `tu_choi_khieu_nai`): cái giá mỗi phía trỏ về kịch bản §2, nhóm chốt thế nào.
- [x] **Thử mức** trên 2 kịch bản đắt nhất + 1 kịch bản bình thường (ca áo size L→M, shop đã nhận gửi nhầm) theo 3 câu: sai có bị chặn? còn làm khi lẽ ra phải hỏi? người bình thường có phải chờ vô ích?
- [x] Luật thêm / tool tách bước (VD: tách `soan_hoan_tien` thành "soạn đề xuất" + "duyệt chi"; thêm luật "chỉ đề xuất hoàn khi người bán đã hết hạn phản hồi hoặc đồng ý").
- [x] Một mức tự chủ đã **đổi lời hứa** nào với người dùng.

**Repo & nộp bài**
- [x] Repo `K5-L3B-Day05-T4-DaiDai` đã tạo; bài viết thẳng vào `03-spec-template.md` (không dùng `spec.md`), bảng thành viên + **mã HV đúng**.
- [ ] Cuối buổi: điền cột "Việc đã làm" cho Phong và Dương (của Vỹ đã điền), điền Bàn/zone, kiểm tra mở repo bằng cửa sổ ẩn danh, nộp link.

---

### Đinh Hoàng Phong — Khi AI sai & Demo

**§3 Khi AI sai (R3 · 25đ) — chỉ cho 2 kịch bản đắt nhất**
- [ ] Mỗi kịch bản: **câu AI nói nguyên văn** · người mua/người bán **thấy gì** (độ chắc, căn cứ, nút, nhãn) · **làm gì tiếp** · **ai được báo, sau bao lâu**.
- [ ] Quyết định **hỏi lại / trả lời kèm giới hạn / dừng và chuyển người**: chọn gì, loại gì, vì sao (đây là 8đ — phần nặng nhất của R3).
- [ ] Gọi đúng **loại lỗi** (hệ thống / người dùng / ngữ cảnh) và cách nói xin lỗi, cách sửa khác nhau theo loại.
- [ ] Chọn **2–3 nguyên tắc HAX/PAIR** (gợi ý: G2 độ chắc, G10 thu hẹp khi nghi ngờ, G11 giải thích vì sao, PAIR Explainability + Trust), mỗi cái trỏ vào câu chữ cụ thể → **gửi danh sách cho Dương** để đặt lên prototype.
- [ ] Chỉ ra **1 lỗi sửa câu chữ không cứu được**, chỉ thiết kế mới cứu (VD: AI so với mô tả *hiện tại* thay vì mô tả *lúc đặt* → phải sửa nguồn dữ liệu AI đọc, không phải sửa câu).
- [ ] Đảm bảo câu chữ: AI tự giới thiệu là AI (G1/Luật AI 134/2025), nói rõ **thời hạn trả hàng còn bao lâu**, không hứa phạt shop, không đưa SĐT.

**§6 Tốt là gì (R6 · 5đ)**
- [ ] 3 tiêu chí **Pass/Fail** người ngoài chấm ra cùng kết quả (VD: "AI không gọi `soan_hoan_tien` trước khi người bán hết hạn phản hồi").
- [ ] Chấm thử trên 2 kịch bản đắt nhất, ghi lỗi còn lại.

**§7 Kịch bản demo (R7)**
- [ ] Viết kịch bản demo 4 phút: ai nói gì, bấm đâu. Ca bắt buộc: **người bán đúng hoặc mô tả đã bị sửa**.
- [ ] Chuẩn bị sẵn 4–5 **ca lạ** có thể bị hỏi và câu trả lời theo đúng mức tự chủ của nhóm; tập cho cả nhóm.
- [ ] Sau demo: ghi ca lạ nhận được vào §7 của `03-spec-template.md`.

---

### Nguyễn Ánh Dương — Prototype

**§5 Prototype (R5 · 25đ) — mốc M3, phút 200**
- [ ] Chọn công cụ trước giờ lab (HTML + coding agent là nhanh nhất; tham khảo `prototype-sample/index.html` 3 phút rồi đóng, không chép giao diện).
- [ ] Trong lúc nhóm làm chặng 2–4: dựng sẵn khung chat "Trò chuyện với Shopee" + thẻ đơn hàng (dữ liệu giả).
- [ ] **1–2 màn hình** cho ca khó nhất (ca demo bắt buộc: người bán đúng / mô tả đã bị sửa), **bấm từ đầu tới cuối không can thiệp tay**.
- [ ] Hiện **độ chắc / bằng chứng**: VD đặt cạnh nhau "mô tả lúc đặt" vs "mô tả hiện tại" vs ảnh người mua gửi.
- [ ] Hiện **≥2 mức tự chủ** đúng như §4 của Vỹ: tự làm có **hoàn tác** · cần duyệt có **nút xác nhận + người duyệt thấy gì** · có **đường chuyển người** · việc cấm **không có nút**.
- [ ] Mỗi nguyên tắc HAX/PAIR Phong chọn phải **chỉ được vào một chỗ** trên màn hình.
- [ ] Chụp **1–2 ảnh có đánh số** các chỗ, bỏ vào `prototype/` kèm `README.md` (link hoặc file HTML).
- [ ] Viết §5 trong `03-spec-template.md`: link · công cụ · phần nào mock · ảnh đánh số (mỗi số: thể hiện gì, nguyên tắc nào, mức tự chủ nào) · **cách hiện đã chọn, cách khác đã nghĩ tới và vì sao loại** (4đ).
- [ ] **Bonus (nếu kịp)**: màn hình phía người bán (thấy khiếu nại + hạn phản hồi); hoặc 1 lời gọi AI thật so khiếu nại với mô tả lúc đặt — **chỉ dữ liệu dựng, API key để biến môi trường, không commit**.
- [ ] Kẹt kỹ thuật > 20 phút → gọi TA.

---

## 3. Lịch 240 phút theo người

| Phút | Chặng | Vỹ | Phong | Dương |
|---|---|---|---|---|
| 0–10 | 1 · Đọc đề | Viết §1 | Đọc rubric R3, HAX/PAIR | Đọc tool, mở công cụ prototype |
| 10–45 | 2 · Kịch bản (**M1**) | **Cầm bút §2**, khoanh 2 ca đắt nhất | Góp kịch bản lớp ①③ | Góp kịch bản lớp ②④ |
| 45–90 | 3 · Khi AI sai | Góp ý, bắt đầu nháp §4 | **Cầm bút §3** | Góp ý màn hình; dựng khung chat |
| 90–125 | 4 · Mức tự chủ (**M2**) | **Cầm bút §4**, chạy vòng xếp mức 5' | Tự xếp mức + thử 3 kịch bản | Tự xếp mức; chốt mức nào hiện ra nút gì |
| 125–140 | Nghỉ | | | |
| 140–200 | 5 · Prototype (**M3**) | Soát §1–4, kiểm prototype khớp §4 | Đưa câu chữ AI vào prototype, viết §6 | **Dựng prototype**, chụp ảnh đánh số, viết §5 |
| 200–210 | 6 · Tốt là gì | Đẩy repo, điền bảng thành viên | Chốt §6, tập kịch bản demo | Sửa lỗi bấm, đẩy `prototype/` |
| 210–240 | Demo | Lát cắt + mức tự chủ | Câu AI nói, HAX/PAIR, ca lạ | Bấm prototype |

## 4. Bàn giao giữa các người (để không chờ nhau)

1. **Phút 45** — Vỹ → Phong: 2 kịch bản đắt nhất (Phong bắt đầu §3).
2. **Phút 90** — Phong → Dương: câu AI nói nguyên văn + 2–3 nguyên tắc HAX/PAIR.
3. **Phút 125** — Vỹ → Dương: bảng mức tự chủ 5 tool (quyết định nút hoàn tác / duyệt / chuyển người / không có nút).
4. **Phút 200** — Dương → cả nhóm: link prototype + ảnh đánh số; mọi người tự bấm thử 1 lần.

## 5. Checklist trước khi nộp (cả nhóm)

- [ ] Repo `K5-L3B-Day05-T4-<TenNhom>` công khai, mở được bằng cửa sổ ẩn danh.
- [ ] `03-spec-template.md` đủ §1–§7, bảng thành viên ở đầu, **mã HV đúng**, cột "Việc đã làm" ghi cụ thể.
- [ ] `prototype/` có link hoặc file + 1–2 ảnh đánh số.
- [ ] Không có dữ liệu thật, không có API key trong code.
- [ ] **Mỗi người trả lời được 3 câu**: "Hành động này sai thì ai mất gì?" · "Lỗi nguy hiểm nhất là gì?" · "Phần bạn làm là gì?" — và chỉ được "chỗ nào trên màn hình là G__".
- [ ] Cân nhắc **xung phong demo trước lớp** (+5 bonus).
