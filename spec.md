# Dàn ý bài nộp *(spec.md — nộp trước 23:59 ngày lab của lớp)*

> Copy dàn ý này vào `spec.md` của nhóm. Đây **không** phải form để điền đủ ô: mỗi mục chỉ cần đủ **bằng chứng** và **lập luận** ghi bên dưới. Viết ngắn, gạch đầu dòng là được. Hướng dẫn từng chặng: `02-guide.md`. Cách chấm: `04-rubric.md`.
>
> **Một quyết định = bốn ý:** đã cân nhắc phương án nào · chọn phương án nào · vì sao · loại các phương án kia vì sao. Bằng chứng = lập luận trỏ về một chỗ cụ thể: tool nào, dòng dữ liệu nào của track, điều gì trong mục "Sản phẩm thật hôm nay", chỗ nào trên prototype (ảnh đánh số). Không chạy agent.

```markdown
# Bài nộp LAB5 — [Track] · Nhóm [tên]
[Danh sách thành viên và việc mỗi người làm — copy bảng từ README]
| Họ và Tên | Mã Học Viên | Việc đã làm |
|---|---|---|
| | | A · Kịch bản & khung: chặng 1–2, bảng kịch bản, §1, §2, §6, repo và kịch bản demo |
| | | B · UX khi AI sai & Prototype: chặng 3, 5, §3, prototype/ và demo màn hình |
| | | C · Mức tự chủ & Kiểm thử: chặng 4, §4, hard tests và kiểm thử prototype |
## §1. Lát cắt & phạm vi
- Lát cắt (chép từ track).
- 3 việc tính năng KHÔNG làm, mỗi việc một câu vì sao.

## §2. Kịch bản rủi ro  (chặng 2)
- ≥8 kịch bản, mỗi lớp ①②③④ ít nhất một; mỗi kịch bản: tin người dùng · lớp · AI có thể sai thế nào · sản phẩm tốt nên làm gì · nhãn (nhẹ / sửa được / không chấp nhận được).
- Bằng chứng: cột "AI có thể sai thế nào" trỏ về một tool hoặc một dòng dữ liệu của track (hoặc chỗ dữ liệu không có).
- Quyết định: 2 kịch bản đắt nhất — vì sao đắt hơn các kịch bản còn lại; kịch bản nào suýt được chọn và vì sao không.

## §3. Khi AI sai  (chặng 3)
Ca 1 · Đổi chuyến nhầm (S2, lớp ②, tool doi_chuyen_bay)
Tin mồi: “Đổi giúp mình sang sáng mai nhé.”
Dữ liệu nguồn: tra_cuu_dat_cho trả về hai chuyến sáng 13/11: BM 201 lúc 07:00 (còn 9 chỗ) và BM 205 lúc 09:30 (còn 4 chỗ).
Câu AI nói nguyên văn: “Mình chưa chắc: sáng mai có hai chuyến còn chỗ. Bạn chọn chuyến nào, cho ai bay?”
Người dùng thấy: hai thẻ chuyến ghi giờ và số chỗ còn lại, ô chọn hành khách, nguồn “Theo tra_cuu_dat_cho”. Nút “Giữ chỗ 20 phút” chỉ bật khi đã chọn chuyến và người bay.
Người dùng làm tiếp: chọn chuyến và người bay, bấm giữ chỗ 20 phút (đếm ngược hiện trên màn hình), rồi bấm “Xác nhận đổi”. Sau khi xác nhận, vé mới ở trạng thái chờ thanh toán: vé cũ vẫn còn, lần đổi miễn phí chưa dùng (0/1) cho tới khi thanh toán xong.
Hoàn tác: giữ chỗ hết 20 phút thì tự nhả. Sau khi đã thanh toán thì không đổi lại bằng nút; màn hình ghi rõ điều này và có nút “Gặp nhân viên”.
Ai được báo: hành khách thấy trạng thái ngay. Nếu khách báo đổi nhầm, ca được chuyển cho nhân viên kèm tóm tắt hội thoại và các thao tác đã làm.
Phương án đã loại:
AI tự chọn chuyến sớm nhất: loại, vì khách có thể cần 09:30 để kịp việc.
AI tự đổi rồi xin lỗi: loại, vì lần đổi miễn phí đã mất.
Đổi khi chưa có tên người bay: loại, vì đổi sai người là lỗi không đảo được.
Mức tự chủ đề xuất (chốt ở chặng 4): tra cứu và giữ chỗ tự làm; doi_chuyen_bay cần khách xác nhận.
Ca 2 · Gửi yêu cầu hoàn vé (S6, lớp ④, tool gui_yeu_cau_hoan_ve)
Tin mồi: “Thôi huỷ hết đi, hoàn tiền cho mình.”
Dữ liệu nguồn: chuyến BM 213 đã huỷ do bão. Chính sách Bay Mẫu: đổi miễn phí một lần trong 48 giờ hoặc hoàn toàn bộ; bão không bồi thường tiền mặt.
Câu AI nói nguyên văn: “Trước khi gửi yêu cầu hoàn: gửi rồi không huỷ được. Tiền về phương thức thanh toán gốc, có thể mất tới 90 ngày, có thể bằng voucher. Huỷ do bão không có bồi thường tiền mặt. Bạn muốn tiếp tục không?”
Người dùng thấy: khung cảnh báo nổi bật ghi rõ điều kiện hoàn. Nút “Đổi sang chuyến còn chỗ” đặt ngang nút “Tiếp tục yêu cầu hoàn”.
Người dùng làm tiếp: chọn hành khách, bấm “Tiếp tục yêu cầu hoàn”, rồi gõ HOÀN để xác nhận lần hai. Nút gửi chỉ bật khi gõ đúng. Có nút “Quay lại”.
Hoàn tác: không. Màn hình sau khi gửi ghi rõ điều này và có mã yêu cầu HT-TRV7Q2K-01.
Ai được báo: nhân viên nhận ca để theo dõi. Khách nhận mã yêu cầu.
Phương án đã loại:
Gửi ngay khi khách nói “huỷ hết”: loại, vì không đảo được.
Tự chọn lý do huỷ thay khách: loại, vì lý do phải do khách chọn.
Chuyển nhân viên cho mọi ca hoàn: loại, vì khách chỉ cần hoàn thật thì chờ là vô ích.
Ánh xạ nguyên tắc HAX/PAIR lên prototype
Ghi chú	Chỗ trên màn hình	Nguyên tắc
①	Dòng “Mình chưa chắc: sáng mai có hai chuyến”	HAX: làm rõ AI làm tốt tới đâu
②	Dòng “Theo tra_cuu_dat_cho”	PAIR: nêu nguồn để khách kiểm được
③	Hai thẻ chuyến và ô chọn người bay	HAX: hỏi lại khi input mơ hồ
④	Khung đỏ cảnh báo hoàn vé; dòng “Giữ chỗ 20 phút”	HAX: cảnh báo trước việc không đảo được
⑤	Bước xác nhận; trạng thái “chờ thanh toán”	PAIR: để người dùng kiểm soát
⑥	Nút “Gặp nhân viên”	PAIR: đường thoát và tóm tắt
⑦	Đếm ngược hoàn tác 10 phút	PAIR: phản hồi và điều khiển
⑧	Nút “Đổi sang chuyến còn chỗ” ở ca 2	HAX: sửa hiệu quả, không chỉ từ chối
Prototype

File: prototype/index.html (một file HTML, mở bằng trình duyệt, không gọi AI thật, không gửi dữ liệu đi đâu).

Có hai ca và công tắc mức tự chủ của doi_chuyen_bay (khách xác nhận / AI tự đổi + hoàn tác). Ghi chú ①–⑧ có thể bật tắt để chụp ảnh có đánh số.

Kiểm tra trước khi nộp:

Ca 1 mức “Khách xác nhận”: chọn chuyến, chọn người, giữ chỗ, xác nhận, thấy trạng thái chờ thanh toán.
Ca 1 mức “AI tự đổi”: chọn chuyến và người, bấm “AI đổi ngay”, thấy bảng vé cũ/vé mới, “đã dùng (1/1)” và đếm ngược 10 phút.
Ca 2: nút gửi chỉ bật khi gõ đúng HOÀN.
Bấm “Gặp nhân viên” ở cả hai ca.
## §4. Mức tự chủ  (chặng 4)
Với mỗi tool:
- Mức của nhóm (tự làm / cần người duyệt / cấm). Nếu cần người duyệt: ai duyệt · người duyệt thấy gì · quá hạn thì sao.
- Lý do theo cost-of-error: sai thì ai chịu gì · đảo lại được không · chờ người thì mất gì.
- Phương án đã cân nhắc và vì sao loại.
Thêm:
- Tool khó xếp nhất: mỗi người từng chọn gì, cái giá của mỗi phía (trỏ về kịch bản ở §2), nhóm chốt thế nào.
- Thử mức đã đặt trên 2 kịch bản đắt nhất + 1 kịch bản bình thường: cái sai có bị chặn không? còn việc nào làm khi lẽ ra phải hỏi? người dùng bình thường có phải chờ vô ích không?
- Luật thêm hoặc tool tách bước (nếu có), và vì sao.
- Một mức tự chủ đã đổi lời hứa nào với người dùng.

## §5. Prototype  (chặng 5)
- Link hoặc file · công cụ · phần nào mock · có lời gọi AI thật không.
- 1–2 ảnh có đánh số; mỗi số: thể hiện gì · nguyên tắc HAX/PAIR nào · mức tự chủ nào.
- Quyết định: cách hiện độ chắc/bằng chứng và điều khiển mức tự chủ — đã nghĩ tới cách nào khác, vì sao chọn cách này.

## §6. Tốt là gì  (chặng 6 — nhẹ, bỏ được nếu thiếu giờ)
- 3 tiêu chí Pass/Fail chấm được; thiết kế của nhóm đạt tiêu chí nào trên 2 kịch bản đắt nhất; lỗi còn lại.

## §7. Demo
- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
```
