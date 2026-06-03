# Thin SPEC — ShopeeFood AI Personalized Promotion

Đây là bản cam kết kỹ thuật và thiết kế tính năng AI cá nhân hóa chương trình khuyến mãi ShopeeFood.

---

## 1. Track, product/app và user

**Nhóm:** "Xứ Sở Ba Tư"

**Thành Viên:**

Phan Tân Hưng - 2A202600825

Khưu Minh Toàn - 2A202601011

Đoàn Xuân Thạch - 2A202600950

Nguyễn Bùi Tấn Dũng - 2A202600546

**Track:** C - Food & Local Delivery

**Product/app đã chọn:** ShopeeFood
* **User cụ thể:**
  1. **Học sinh (Dưới 18 tuổi):** Đặt đồ ăn vặt giá rẻ (15k-25k) vào giờ tan học 15h-17h, thích trà sữa, bánh tráng, giao nhanh cổng trường.
  2. **Sinh viên (18-22 tuổi):** Tiết kiệm ngân sách (35k-50k), đặt cơm trưa bình dân hoặc mì trộn cày đêm khuya tại KTX.
  3. **Nhân viên văn phòng (23+ tuổi):** Ngân sách cao (65k-150k), đặt cà phê sáng 8h30 hoặc cơm trưa đặt nhóm/healthy salad lúc 11h45 tại tòa nhà văn phòng.
* **Nhóm có phải user thật không? Nếu không, khác ở đâu?**
  * Nhóm là sinh viên và người trẻ đi làm, hoàn toàn thuộc nhóm đối tượng mục tiêu 2 & 3, thường xuyên gặp điểm đau chọn món lâu và khuyến mãi không khớp nhu cầu.

---

## 2. Evidence summary

| Evidence | Nguồn | User/pain nói lên điều gì? | SPEC phải đổi gì? |
|---|---|---|---|
| Banners & deals quá tải trên Home screen | Self-use Screenshots | User bị mệt mỏi tinh thần khi so sánh giá/deal. | Tự động hóa thay đổi Banner & Vouchers theo phân khúc độ tuổi và mốc giờ. |
| Người dùng phàn nàn khuyến mãi không đúng hành vi ăn uống | App Store Reviews | Voucher gửi sai nhóm chi tiêu (AOV) sẽ bị bỏ qua. | AI tự động tính toán độ co giãn ngân sách để phân bổ voucher (Freeship tối đa cho học sinh, voucher nhóm cho văn phòng). |

---

## 3. Pain statement

```text
User học sinh, sinh viên và nhân viên văn phòng đang gặp khó ở khâu ra quyết định chọn món trưa/ăn vặt và săn voucher phù hợp trên trang chủ ShopeeFood,
vì ứng dụng hiển thị tràn ngập thông tin ưu đãi đại trà không được cá nhân hóa theo độ tuổi và thói quen sinh hoạt,
dẫn tới mất thời gian lướt tìm kiếm (trên 10 phút), gây ức chế tâm lý hoặc bỏ app sang đối thủ cạnh tranh.
Bằng chứng chính là review 1 sao phàn nàn về spam khuyến mãi trên App Store và các screenshot thực tế từ giao diện app.
```

---

## 4. Build Slice

```text
Cho người dùng đang mở ShopeeFood để tìm đồ ăn/uống,
prototype sẽ dùng AI để phân loại nhóm đối tượng (Học sinh/Sinh viên/Văn phòng) kết hợp phân tích ngữ cảnh thời gian (Sáng/Trưa/Chiều/Đêm), tự động tối ưu hóa phân bổ voucher và biên soạn nội dung banner/notification phù hợp với văn phong của nhóm tuổi đó,
tạo ra giao diện trang chủ động cập nhật thời gian thực (Banner, danh sách voucher cá nhân hóa, gợi ý món ăn có biểu tượng linh vật mini trợ lý),
và xử lý failure mode đề xuất sai lệch bằng cách cho phép click trực tiếp vào thẻ món ăn để chuyển hướng mượt mà sang trang thông tin chi tiết quán ăn (Restaurant Page) giúp đối chiếu thực đơn gốc trước khi đặt hàng.
```

---

## 5. Auto/Aug decision

Chọn một:
- [x] **Augmentation:** AI gợi ý/draft/phân loại, user quyết cuối.
- [ ] **Conditional automation:** AI tự làm trong case hẹp; case mơ hồ/rủi ro chuyển người.
- [ ] **Automation:** AI tự quyết và tự hành động.

* **Lý do chọn:** Lựa chọn đồ ăn là hành vi mang tính cá nhân hóa và cảm tính cao. AI chỉ đóng vai trò trợ lý thông minh giúp thu hẹp phạm vi lựa chọn từ hàng ngàn quán xuống 3 gợi ý tốt nhất và chuẩn bị sẵn voucher. Khách hàng vẫn là người duyệt cuối cùng để đảm bảo sự hài lòng tuyệt đối.
* **Human role:** *decider* (khách hàng chọn món và đặt hàng) & *trainer* (hành vi click của người dùng gửi dữ liệu feedback loop để huấn luyện AI).

---

## 6. Four paths

| Path | Prototype phải thể hiện gì? |
|---|---|
| **Happy** | Người dùng chuyển phân khúc trên Admin panel, giao diện điện thoại đổi theme, cập nhật banner động, voucher phù hợp túi tiền, hiện đề xuất món có badge linh vật và click dẫn trực tiếp đến trang quán để thanh toán. |
| **Low-confidence** | Người dùng mở khung chat **AI Tìm Món**, AI đưa ra các gợi ý chips phân khúc thói quen ăn uống (Trà sữa 15k, Salad organic...) để người dùng chọn thay vì bắt nhập liệu thô. |
| **Failure** | AI gợi ý sai thói quen hoặc không tương thích ngân sách. Khách hàng bỏ qua thẻ đề xuất hoặc nhấn nút **◀ App** để quay về luồng tự tìm kiếm thủ công của ShopeeFood. |
| **Correction** | Khách hàng claim voucher hoặc thêm món vào giỏ hàng tại trang quán, hệ thống ghi nhận sự kiện Click-Through Rate (CTR) đẩy về nhật ký suy luận AI để tự chỉnh sửa mô hình (Feedback Loop). |

---

## 7. Failure mode nguy hiểm nhất

```text
Nếu user bấm tìm các món healthy hoặc không cay do có bệnh lý nền/dị ứng/chế độ ăn kiêng,
AI có thể gợi ý sai lệch món ăn chứa chất gây dị ứng hoặc cực kỳ cay do nhầm lẫn nhãn dữ liệu từ phía đối tác quán ăn,
hậu quả là ảnh hưởng trực tiếp tới sức khỏe và an toàn của khách hàng.
Prototype sẽ xử lý bằng cách: Loại bỏ việc đặt hàng tự động từ xa; bắt buộc hiển thị nhãn cảnh báo độ cay/dị ứng và chuyển hướng trực tiếp sang Restaurant Page để khách hàng xem thực đơn gốc chi tiết trước khi đặt.
Owner kiểm thử path này là: Prototype Owner (đảm bảo luồng chuyển hướng quán ăn hoạt động chính xác).
```

---

## 8. Owner plan cho sáng Day 06

| Thành viên | Việc phụ trách | Bằng chứng cần có trong repo |
|---|---|---|
| Nguyễn Bùi Tấn Dũng | **Research Owner** Tìm kiếm dữ liệu & evidence | Tệp `evidence_pack.md` hoàn thành đầy đủ. |
| Đoàn Xuân Thạch | **SPEC Owner** Hoàn thiện Thin SPEC kỹ thuật | Tệp `thin_spec.md` đã được biên soạn và duyệt. |
| Khưu Minh Toàn | **Prototype Owner** Xây dựng giao diện web tương tác | Bộ mã nguồn HTML/CSS/JS hoạt động tốt tại thư mục `/prototype/`. |
| Khưu Minh Toàn | **Test Owner** Kiểm thử các paths & rủi ro | Báo cáo kiểm thử 4 paths tích hợp trực tiếp trong nhật ký Console của Prototype. |
| Phan Tân Hưng | **Demo Owner** Soạn kịch bản thuyết trình & quay video | Kịch bản demo và Sequence Diagram tích hợp trong tệp `walkthrough.md`. |
