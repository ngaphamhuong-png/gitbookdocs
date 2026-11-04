# SỔ TAY HƯỚNG DẪN VẬN HÀNH DÀNH CHO NHÂN VIÊN THU NGÂN (CASHIER SOP)

> **Tài liệu Hướng dẫn Thao tác Chuẩn (SOP - Standard Operating Procedure)**  
> **Đối tượng áp dụng:** Nhân viên Thu ngân / Kế toán Quầy Dịch vụ Sân Golf  
> **Hệ thống áp dụng:** AloGolf Management System - Phân hệ Check-out & Quyết toán (Settlement)  
> **Phiên bản:** 1.0 | **Ngày ban hành:** 2026-10-23

---

## 1. MỤC TIÊU & NHIỆM VỤ CỦA NHÂN VIÊN THU NGÂN

Nhân viên Thu ngân là điểm chốt chặn tài chính cuối cùng trong quy trình phục vụ khách hàng tại sân golf. Nhiệm vụ trọng tâm bao gồm:
1. **Kiểm soát dòng tiền & đối soát chi phí:** Tổng hợp đầy đủ, minh bạch toàn bộ các khoản phí của vòng chơi (tiền sân, xe điện, caddie, phụ phí F&B, mua sắm ProShop).
2. **Khấu trừ tài chính hợp lý:** Khấu trừ chính xác các khoản tiền đã đặt cọc trước của golfer.
3. **Linh hoạt phân bổ hóa đơn (Split Billing):** Hỗ trợ khách tách hóa đơn riêng cho từng người hoặc gộp chung cho một cá nhân/doanh nghiệp thanh toán.
4. **Thực hiện thu tiền chuẩn xác:** Thu tiền mặt hoặc sinh mã VietQR động qua cổng thanh toán PayOS / SePay để golfer quét mã chuyển khoản.
5. **Thu hồi tài sản sân:** Thu hồi thẻ chìa khóa tủ Locker, giải phóng tài nguyên trên hệ thống và in hóa đơn thanh toán cho khách.

---

## 2. QUY TRÌNH CHUẨN 5 BƯỚC THAO TÁC TẠI QUẦY THU NGÂN (CASHIER SOP)

```
[BƯỚC 1: TÌM HÓA ĐƠN] ➔ [BƯỚC 2: ĐỐI SOÁT CHI PHÍ] ➔ [BƯỚC 3: PHÂN BỔ HÓA ĐƠN] ➔ [BƯỚC 4: THU TIỀN MẶT/QR] ➔ [BƯỚC 5: ĐÓNG HỒ SƠ & IN PHIẾU]
  Quét Bag Tag / Locker      Kiểm tra Greenfee, Caddie, Buggy     1 người trả hết HOẶC             Tiền mặt: Gạch nợ ngay         Kiểm tra công nợ = 0
  HOẶC chọn Flight TIME_OUT  Thêm phụ phí ăn uống/thuê đồ         Từng người tự thanh toán         PayOS: Quét mã VietQR động     Nhả tủ Locker & In hóa đơn
```

---

### BƯỚC 1: TIẾP NHẬN & TÌM KIẾM LƯỢT THANH TOÁN (LOOKUP BILL)

1. Đăng nhập vào hệ thống AloGolf bằng tài khoản Thu ngân được cấp.
2. Trên menu bên trái, chọn: **Vận hành (Operations)** ➔ **Thanh toán & Trả đồ (Check-out)**.  
   *(Đường dẫn giao diện: `apps/webapp/src/app/(admin)/business/operations/check-out/page.tsx`)*.
3. Khi khách đánh xong vào quầy thanh toán:
   - **Cách 1 (Khuyên dùng - Nhanh nhất):** Bấm nút **"Quét thẻ Check-out"** góc trên bên phải màn hình. Cầm thẻ chìa khóa Locker hoặc thẻ Bag Tag của golfer đưa vào đầu đọc máy quét. Hệ thống sẽ mở ngay bảng kê chi phí chính xác của nhóm khách đó trong vòng 1 giây.
   - **Cách 2:** Tra cứu trên bảng danh sách: Tìm theo **Mã Booking**, **Số hiệu Flight** (ví dụ `FL026000001`), hoặc **Tên khách hàng**.  
     *Lưu ý:* Những nhóm đã đánh xong sẽ có dấu hiệu màu xanh lá **"Sẵn sàng thanh toán" (`Ready for Checkout`)**.
4. Bấm nút **"Thanh toán" (Check-out)** ở cuối dòng để mở hộp thoại quyết toán.

---

### BƯỚC 2: ĐỐI SOÁT BẢNG KÊ CHI PHÍ & THÊM DỊCH VỤ PHÁT SINH

1. Kiểm tra các dòng chi phí mặc định của vòng chơi:
   - **Tiền sân (`GREEN_FEE`):** Đúng số lỗ khách chơi thực tế (9 hố hoặc 18 hố)?
   - **Phí Caddie (`CADDY`):** Số lượng caddie phục vụ.
   - **Tiền xe Buggy (`CART`):** Số lượng xe điện sử dụng.
   - **Dịch vụ đặt trước (`ADDON`):** Các gói thuê gậy, bóng, suất ăn đã chọn lúc booking.
   - **Tiền cọc đã trả (`Paid Amount`):** Hệ thống tự động hiển thị số tiền đã cọc để trừ lùi vào tổng bill.
2. **Thêm phụ phí phát sinh tại sân (nếu có):**
   - Nếu golfer có ăn uống tại nhà hàng Clubhouse hoặc mua nước uống, bóng golf tại các Kiosk giữa sân chưa ghi nhận:
     1. Bấm nút **"Thêm phụ phí" (Add Charge Line)**.
     2. Chọn loại phụ phí: **Nhà hàng (`RESTAURANT`)**, **Kiosk (`POS`)**, **Tủ đồ (`LOCKER`)**, hoặc **Thủ công (`MANUAL`)**.
     3. Nhập tên dịch vụ (ví dụ: *"02 lon bia Heineken + 01 đĩa hoa quả Kiosk hố 10"*).
     4. Nhập số tiền (VND).
     5. Bấm **Lưu**. Số tiền này sẽ tự động cộng vào tổng bill của nhóm.

---

### BƯỚC 3: PHÂN BỔ HÓA ĐƠN (SPLIT BILLING / REASSIGN PAYER)

Hệ thống AloGolf hỗ trợ xử lý linh hoạt mọi nhu cầu chia tiền của golfer:
- **Trường hợp A: Một người đứng ra thanh toán toàn bộ cho cả nhóm (Bao trọn gói):**
  1. Bấm vào nút **"Gán tất cả cho một người" (Reassign All)**.
  2. Chọn tên golfer đứng ra thanh toán (ví dụ: Golfer Nguyễn Văn A).
  3. Hệ thống sẽ chuyển toàn bộ số tiền của các thành viên khác về tài khoản của Golfer A. Các thành viên còn lại có số dư cần trả = 0 VND.
- **Trường hợp B: Từng người tự thanh toán phần chi phí của mình (Tiền ai nấy trả):**
  - Mặc định hệ thống đã phân bổ chi phí riêng cho từng golfer.
  - Thu ngân thực hiện thu tiền tuần tự cho từng người một.
- **Trường hợp C: Chia sẻ một khoản chi phí cụ thể (Tùy chỉnh phân bổ):**
  - Bấm vào biểu tượng bút chì bên cạnh dòng chi phí muốn đổi (ví dụ: Tiền xe điện Buggy hoặc Tiền bữa ăn trưa chung).
  - Chọn lại **"Người thanh toán" (`Payer`)** là người nhận trả khoản chi phí đó.

---

### BƯỚC 4: THỰC HIỆN THU TIỀN (CASH HOẶC VIETQR PAYOS)

Sau khi đã chốt số tiền cần thu (`Amount Due`), bấm nút **"Thu tiền" (Checkout Player)**:

#### 1. Thanh toán bằng Tiền mặt (Cash):
1. Đếm đủ số tiền mặt khách trao.
2. Chọn phương thức: **"Tiền mặt" (Cash)**.
3. Bấm **"Xác nhận đã thu tiền mặt"**.
4. Hệ thống gạch nợ tức thì, chuyển trạng thái khoản chi phí sang `PAID` (`settledAt = now`).

#### 2. Thanh toán bằng Chuyển khoản QR Động (PayOS / VietQR):
1. Chọn phương thức: **"Chuyển khoản QR" (PayOS QR)**.
2. Màn hình máy tính hoặc màn hình phụ hướng về phía khách sẽ hiển thị **Mã VietQR động**:
   - Chứa chính xác số tiền cần thanh toán từng đồng (không cần khách phải tự gõ số tiền).
   - Chứa mã nội dung chuyển khoản tự động (ví dụ: `ALG 123456`).
3. Khách mở ứng dụng ngân hàng bất kỳ (Vietcombank, Techcombank, MB, BIDV, VPBank...) hoặc ví điện tử, quét mã QR và bấm chuyển khoản.
4. **Xử lý tự động:** Trong vòng 2 - 3 giây sau khi khách chuyển tiền thành công, cổng PayOS gửi tín hiệu Webhook về hệ thống. Màn hình Thu ngân tự động nhảy thông báo xanh **"Thanh toán thành công"** mà Thu ngân không cần thao tác bấm gạch nợ thủ công!

---

### BƯỚC 5: THU HỒI CHÌA KHÓA TỦ, ĐÓNG HỒ SƠ & IN HÓA ĐƠN

1. Sau khi tất cả các thành viên trong nhóm đã thanh toán hết nợ (`Amount Due = 0 VND`):
2. Thu ngân nhận lại toàn bộ thẻ chìa khóa tủ đồ RFID Locker từ khách.
3. Bấm nút **"Hoàn tất Check-out" (Complete Visit Check-out)**.
4. **Hệ thống tự động thực hiện:**
   - Giải phóng số tủ Locker của khách về trạng thái sẵn sàng (`AVAILABLE`) cho ca sau.
   - Hủy kích hoạt mã thẻ từ RFID (`REVOKED`).
   - Đóng hồ sơ lượt khách (`completedAt = now`).
5. **In hóa đơn:**
   - Bấm nút **"In hóa đơn" (Print Invoice)**.
   - Máy in nhiệt hoặc máy in laser in phiếu thanh toán chi tiết.
   - Thu ngân kẹp phiếu vào bìa kẹp hóa đơn, cảm ơn và chào tiễn khách ra về:
     > *"Dạ em đã nhận đủ thanh toán và nhận lại chìa khóa tủ đồ của đoàn mình ạ. Hóa đơn chi tiết của các anh/chị đây ạ. Cảm ơn các anh/chị đã đến với sân golf AloGolf. Hẹn gặp lại các anh/chị trong các buổi chơi tiếp theo ạ!"*

---

## 3. XỬ LÝ CÁC TÌNH HUỐNG LỖI & SỰ CỐ TÀI CHÍNH

### 1. Khách chuyển khoản thành công nhưng màn hình chưa báo gạch nợ
- **Nguyên nhân:** Do mạng viễn thông của ngân hàng phía người gửi phản hồi chậm hoặc nghẽn mạng cuối tuần.
- **Cách xử lý:**
  1. Yêu cầu khách cho xem màn hình thông báo "Chuyển tiền thành công" trên ứng dụng ngân hàng của khách (kiểm tra đúng tên tài khoản thụ hưởng của sân golf và đúng số tiền).
  2. Mở cổng quản trị PayOS của sân để kiểm tra dòng tiền đã vào tài khoản chưa.
  3. Nếu tiền đã vào tài khoản: Bấm hủy mã QR đang chờ (`Cancel Pending PayOS`) ➔ Chọn phương thức **"Xác nhận đã nhận chuyển khoản thủ công"** để gạch nợ ngay, không bắt khách phải đứng chờ tại quầy.

### 2. Khách đổi ý từ chuyển khoản sang trả tiền mặt khi mã QR đang hiện
1. Thu ngân bấm nút **"Hủy mã QR"** trên modal thanh toán.
2. Hệ thống gọi API giải phóng khóa nợ tạm thời.
3. Chọn lại phương thức **"Tiền mặt"** và thực hiện thu tiền bình thường.

### 3. Khách yêu cầu xuất Hóa đơn Giá trị Gia tăng (VAT Invoice)
1. Trên form thanh toán, tích chọn ô **"Yêu cầu xuất hóa đơn VAT"**.
2. Nhập đầy đủ thông tin: Tên công ty, Mã số thuế (MST), Địa chỉ doanh nghiệp và Email nhận hóa đơn điện tử.
3. Lưu thông tin để bộ phận Kế toán xuất hóa đơn điện tử gửi về email cho khách theo định kỳ trong ngày.
