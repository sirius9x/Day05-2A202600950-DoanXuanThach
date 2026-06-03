# Synthesis & Decide Toolkit — ShopeeFood AI Personalized Promotion

Tài liệu đúc kết từ bằng chứng thực tế đến quyết định xây dựng lát cắt sản phẩm (Build Slice) cho dự án ShopeeFood AI Copilot.

---

## 1. Gom evidence thành cụm

Gom nhóm theo cụm điểm đau chính trong trải nghiệm khách hàng:

* **Cụm 1: Quá tải thông tin trang chủ (Discovery Overload)**
  * *Bằng chứng:* Screenshot trang Home ngập tràn flash sale, banner và danh sách món kéo dài vô tận làm người dùng bối rối.
  * *Workflow ảnh hưởng:* Chọn món ban đầu.
* **Cụm 2: Ưu đãi đại trà, thiếu cá nhân hóa (Personalization Deficit)**
  * *Bằng chứng:* Đánh giá của người dùng văn phòng phàn nàn vì nhận được khuyến mãi trà sữa teen quá xa, sinh viên nhận deal sang xịn không hợp ví.
  * *Workflow ảnh hưởng:* Săn voucher & áp mã giảm giá.
* **Cụm 3: Bộ lọc tìm kiếm thô cứng (Filter Deficiency)**
  * *Bằng chứng:* Bộ lọc thủ công không hiểu được ràng buộc ngữ cảnh như "healthy dưới 60k", "không cay gần VinUni".
  * *Workflow ảnh hưởng:* Tìm kiếm món ăn theo nhu cầu tự nhiên.

---

## 2. Viết insight

```text
Người dùng ShopeeFood (Học sinh, Sinh viên, Nhân viên văn phòng) không chỉ cần app hiển thị thật nhiều voucher giảm giá.
Họ thật ra cần hỗ trợ ra quyết định nhanh chóng, an toàn bằng cách tự động lọc bớt các thông tin gây nhiễu và đề xuất chính xác món ăn phù hợp với ngân sách & thói quen sinh hoạt của họ theo thời gian thực,
vì dữ liệu hành vi đặt hàng cho thấy họ có xu hướng từ bỏ giỏ hàng hoặc thoát ứng dụng khi thời gian lướt so sánh món và deal vượt quá 10 phút.
```

---

## 3. Viết opportunity

```text
Cơ hội là dùng AI để tự động phân tích hành vi người dùng (phân cụm độ tuổi/địa điểm), tối ưu hóa việc phân bổ voucher và biên soạn thông điệp quảng cáo cá nhân hóa (Tone of Voice phù hợp),
giúp người dùng rút ngắn thời gian quyết định chọn món xuống dưới 2 phút,
trong khi vẫn kiểm soát rủi ro gợi ý sai lệch bằng cách điều hướng trực tiếp sang trang thực đơn gốc của quán ăn (Restaurant Page) để người dùng xác nhận lại thành phần món ăn.
```

---

## 4. Chọn build slice

Bảng đánh giá lát cắt thử nghiệm qua bộ 5 câu hỏi tự kiểm tra:

| Câu hỏi | Đạt khi | Nhóm đánh giá | Kết luận |
|---|---|---|---|
| **User cụ thể chưa?** | Nói được ai dùng, trong bối cảnh nào. | Học sinh Lê Quý Đôn (chiều tan học), Sinh viên KTX (đêm khuya), Nhân viên văn phòng Centec (trưa). | **ĐẠT** |
| **Task đủ hẹp chưa?** | Demo được trong 3-5 phút. | Chọn món và áp dụng voucher cá nhân hóa trên màn hình giả lập di động. | **ĐẠT** |
| **AI decision rõ chưa?** | AI gợi ý/tự làm một việc cụ thể. | AI tự động đổi giao diện, chọn voucher lý tưởng nhất và viết quảng cáo động phù hợp tone tuổi. | **ĐẠT** |
| **Failure path rõ chưa?** | Có một case AI không chắc hoặc sai để test. | AI đề xuất sai món hoặc sai voucher ngân sách. Người dùng bỏ qua hoặc tự chuyển đổi cấu hình. | **ĐẠT** |
| **Có evidence không?** | Có bằng chứng từ self-use/review/competitor. | Có screenshots trang chủ, 1 sao reviews trên App Store và học hỏi từ Grab/Baemin. | **ĐẠT** |

---

## 5. Quyết định: giữ, giảm scope, hay đổi hướng?

* **Tình huống của nhóm:** Ý tưởng ban đầu bao gồm cả tính năng cứu hộ lỗi giao hàng (Order delay recovery) và chọn món. Nếu xây dựng cả hai sẽ quá rộng cho buổi demo 3-5 phút.
* **Quyết định:** Giữ nguyên tên đề tài cá nhân hóa AI, nhưng **cắt giảm scope** chỉ tập trung vào một flow cốt lõi: *Cá nhân hóa khuyến mãi (Banner, Voucher) và Gợi ý món ngon thông minh liên kết trực tiếp trang thông tin quán ăn theo độ tuổi ngay trên màn hình Home và chat trợ lý.*

---

## 6. Câu chốt cuối

```text
Dựa trên bằng chứng về việc quá tải thông tin khuyến mãi và khó khăn khi chọn món của người dùng,
nhóm sẽ build lát cắt prototype màn hình Home động và màn hình Chat tìm món thông minh có tích hợp linh vật trợ lý mới,
cho học sinh, sinh viên và nhân viên văn phòng,
để giải quyết điểm đau mất thời gian ra quyết định chọn món ăn (Decision Overload),
bằng cách AI tự động phân nhóm người dùng từ dữ liệu lịch sử thói quen chi tiêu, tối ưu phân bổ voucher và biên soạn nội dung quảng cáo động phù hợp tone tuổi (Augment & Assist),
và sẽ test failure path AI gợi ý sai thói quen hoặc sai lệch ngân sách bằng cách hướng dẫn người dùng nhấn back quay lại luồng tự chọn hoặc tự xem thực đơn gốc ở trang quán.
```

---

## 7. Backlog (Không build trong Day 06)

1. Tích hợp cổng thanh toán thực tế ShopeePay/MoMo để đặt hàng thật.
2. Tích hợp API định vị GPS thời gian thực trên bản đồ để tính phí ship động chính xác.
3. Luồng tự động tìm tài xế giao hàng ngoài đời thực và thuật toán ghép đơn tài xế.
