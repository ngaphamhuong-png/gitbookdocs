# HƯỚNG DẪN VẬN HÀNH & SỬ DỤNG KIOSK TỰ PHỤC VỤ (KIOSK USER GUIDE)

> **Tài liệu Hướng dẫn Thao tác Chuẩn (SOP - Standard Operating Procedure)**  
> **Đối tượng áp dụng:** Nhân viên Hỗ trợ sảnh (Lobby Host), Kỹ thuật viên & Khách chơi Golf (Golfer)  
> **Hệ thống áp dụng:** AloGolf Management System - Phân hệ Thiết bị Kiosk tự phục vụ (`apps/webapp/src/app/kiosk`)  
> **Phiên bản:** 1.0 | **Ngày ban hành:** 2026-10-23

---

## 1. TỔNG QUAN VỀ KIOSK TỰ PHỤC VỤ (SELF-SERVICE KIOSK)

Kiosk tự phục vụ của AloGolf là thiết bị cảm ứng thông minh được bố trí tại khu vực tiền sảnh câu lạc bộ (Clubhouse Lobby). Mục tiêu:
1. **Giảm thiểu thời gian chờ đợi:** Giúp golfer tự làm thủ tục Check-in và Check-out trong vòng dưới 30 giây vào các khung giờ cao điểm mà không cần xếp hàng tại quầy lễ tân.
2. **Trải nghiệm công nghệ cao:** Tích hợp camera quét mã QR đa năng (Dual QR Scanner), đầu đọc thẻ không tiếp xúc RFID cho chìa khóa Locker, và máy in phiếu nhiệt tự động.

---

## 2. QUY TRÌNH KÍCH HOẠT & GHÉP NỐI THIẾT BI KIOSK (KIOSK PAIRING)

Dành cho Nhân viên Kỹ thuật và Quản lý vận hành khi khởi động máy Kiosk đầu ngày:

```
[BẬT THIẾT BỊ KIOSK] ➔ [HIỂN THỊ MÃ PAIRING QR] ➔ [QUẢN LÝ DÙNG APP QUÉT CLAIM] ➔ [KIOSK SẴN SÀNG HOẠT ĐỘNG]
  Mở trình duyệt Kiosk      Mã thử thách 64 ký tự           Xác thực phân quyền OrgScope        Màn hình chuyển sang giao diện
  Truy cập /kiosk           Thời hạn hiệu lực 15 phút       Cấp Token phiên KioskSession        chào đón khách chơi (Welcome)
```

1. Bật nguồn máy Kiosk. Mở ứng dụng Kiosk AloGolf tại địa chỉ: `https://kiosk.[tên-miền-sân].alogolf.vn` hoặc truy cập route: `apps/webapp/src/app/kiosk`.
2. Khi chưa được đăng nhập, màn hình Kiosk sẽ hiển thị một **Mã QR Thử Thách Ghép Nối (Pairing Challenge QR)**.
3. Người quản lý (Manager) mở ứng dụng AloGolf trên điện thoại, đăng nhập tài khoản quản trị sân:
   - Vào menu: **Thiết bị (Devices)** ➔ **Ghép nối Kiosk (Pair Kiosk)**.
   - Quét mã QR hiển thị trên màn hình Kiosk.
4. **Hệ thống tự động kích hoạt:**
   - Tạo phiên làm việc [`KioskSession`](file:///d:/Projects/alogolf/libs/backend/database/prisma/models/course.prisma#L365-L389) với mã refresh token bảo mật.
   - Màn hình Kiosk chuyển sang giao diện chính: **"CHÀO MỪNG QUÝ KHÁCH ĐẾN VỚI SÂN GOLF ALOGOLF"** với 2 nút chức năng lớn: **"Tự Check-in"** và **"Tự Thanh toán"**.

<p align="center">
  <img src="../screenshots/kiosk/kiosk-home-screen-mockup.jpg" alt="Màn hình chính Kiosk tự phục vụ AloGolf" width="90%" />
  <br />
  <em>Hình 1: Giao diện màn hình chính Kiosk cảm ứng tự phục vụ AloGolf (Tỷ lệ 16:9) tích hợp đầu đọc QR và phím cảm ứng đa ngôn ngữ</em>
</p>

---

## 3. HƯỚNG DẪN 3 BƯỚC GOLFER TỰ CHECK-IN TẠI KIOSK

Quy trình cực kỳ đơn giản dành cho khách chơi golf:

```
[BƯỚC 1: QUÉT MÃ ĐẶT CHỖ]  ➔  [BƯỚC 2: XÁC NHẬN THÔNG TIN]  ➔  [BƯỚC 3: NHẬN TỦ ĐỒ & TÚI GẬY]
  Đưa mã QR trên ZNS/App         Kiểm tra tên, số lỗ (9/18)        Kiosk in phiếu số tủ Locker
  vào máy quét cảm ứng           Chọn vị trí người chơi            Chạm thẻ Bag Tag dán lên túi
```

### Bước 1: Quét mã QR đặt chỗ (Scan Booking QR)
1. Golfer chạm vào nút **"BẮT ĐẦU CHECK-IN"** trên màn hình cảm ứng.
2. Mở tin nhắn Zalo ZNS hoặc ứng dụng AloGolf trên điện thoại có chứa mã QR đặt chỗ.
3. Đưa màn hình điện thoại vào khu vực đầu đọc camera phía dưới màn hình Kiosk.
4. Kiosk phát tiếng bíp `Bíp!` và tự động hiển thị thông tin nhóm đặt chỗ của khách.

### Bước 2: Xác nhận danh tính người chơi (Player Confirmation)
1. Màn hình hiển thị danh sách các thành viên trong nhóm chơi.
2. Golfer bấm chọn vào tên của mình:
   - Xác nhận số điện thoại và tên hiển thị.
   - Xác nhận số lỗ chơi (18 lỗ hoặc 9 lỗ).
3. Bấm nút **"XÁC NHẬN ĐIỂM DANH"**.

### Bước 3: Nhận thẻ tủ Locker & Hoàn tất thủ tục
1. **Cấp tủ đồ Locker tự động:**
   - Kiosk tự động chọn một số tủ Locker đang trống trong khu vực tương ứng.
   - Máy in của Kiosk in ra một **Phiếu Check-in nhiệt** chứa:
     - Số tủ đồ Locker của khách (ví dụ: `Tủ Nam - Số 128`).
     - Mã vạch để mở khóa tủ đồ hoặc chỉ dẫn vị trí nhận vòng đeo tay RFID tại quầy phát thẻ tự động.
2. **Gắn thẻ Bag Tag:**
   - Khách lấy một thẻ Bag Tag tại khay đựng thẻ bên cạnh Kiosk, đưa mã vạch của thẻ vào đầu đọc để hệ thống liên kết mã túi gậy với tên của mình.
   - Gắn thẻ Bag Tag vào túi gậy và đặt túi gậy lên băng chuyền/khu vực bến xe điện.
3. Màn hình Kiosk hiển thị thông báo:
   > *"Quý khách đã hoàn tất thủ tục Check-in thành công! Giờ phát bóng dự kiến của quý khách là [Giờ:Phút] tại Sân [A/B]. Chúc quý khách có một ngày thi đấu tuyệt vời!"*

---

## 4. HƯỚNG DẪN TỰ THANH TOÁN TẠI KIOSK (KIOSK SELF-CHECKOUT)

Sau khi hoàn thành vòng chơi, golfer có thể tự quyết toán chi phí cá nhân tại Kiosk mà không cần đến quầy thu ngân:
1. Tại màn hình chính của Kiosk, bấm nút **"TỰ THANH TOÁN (CHECK-OUT)"**.
2. Đưa thẻ Bag Tag hoặc quét mã QR trên phiếu Check-in vào đầu đọc.
3. Màn hình Kiosk hiển thị chi tiết hóa đơn cá nhân của golfer:
   - Tiền sân Green fee.
   - Tiền caddie và xe Buggy.
   - Các dịch vụ ăn uống F&B hoặc thuê đồ đã sử dụng.
   - Khấu trừ tiền cọc đã thanh toán trước (nếu có).
   - Số tiền còn lại phải thanh toán (`Amount Due`).
4. Bấm nút **"THANH TOÁN QUA VIETQR"**:
   - Màn hình Kiosk hiển thị mã VietQR động PayOS.
   - Golfer mở ứng dụng ngân hàng quét mã chuyển khoản.
5. Ngay khi chuyển khoản thành công, Kiosk tự động in biên lai thanh toán và hiển thị hướng dẫn golfer thả lại thẻ chìa khóa Locker vào hòm thu hồi thẻ tự động để giải phóng tủ đồ.

---

## 5. HƯỚNG DẪN XỬ LÝ SỰ CỐ & BẢO TRÌ KIOSK (TROUBLESHOOTING)

Dành cho Nhân viên Hỗ trợ sảnh (Lobby Host) hoặc Kỹ thuật viên:

| Hiện tượng sự cố | Nguyên nhân khả dĩ | Hướng dẫn khắc phục nhanh |
| :--- | :--- | :--- |
| **Màn hình Kiosk quay lại trang Pairing QR** | Phiên đăng nhập `KioskSession` đã hết hạn (sau 30 ngày) hoặc bị Quản trị viên hủy bỏ từ xa. | Dùng điện thoại quản trị quét lại mã QR trên màn hình Kiosk để ghép nối lại trong 10 giây. |
| **Đầu đọc không nhận mã QR của khách** | Độ sáng màn hình điện thoại khách quá tối, hoặc khách để quá sát mắt đọc camera. | Hướng dẫn khách tăng độ sáng màn hình điện thoại lên 100%, giữ khoảng cách 10 - 15 cm vuông góc với mắt đọc. |
| **Máy in không ra phiếu số tủ Locker** | Kẹt giấy in nhiệt hoặc cuộn giấy in đã hết. | Mở nắp máy in phía dưới thân Kiosk, gỡ giấy kẹt hoặc thay cuộn giấy in nhiệt K80 mới. Bấm nút Feed để kiểm tra giấy ra đều. |
| **Báo lỗi "Không tìm thấy thông tin đơn đặt"** | Khách quét mã đơn đặt của ngày khác hoặc đơn đặt chưa được xác nhận (`PENDING`). | Hướng dẫn khách sang quầy Lễ tân số 1 để nhân viên kiểm tra tình trạng đơn trên máy chủ trung tâm. |
| **Mất kết nối mạng Internet (Offline)** | Mất sóng Wifi hoặc đứt dây mạng LAN cấp cho Kiosk. | Kiểm tra cáp mạng LAN phía sau thân máy Kiosk. Nếu sự cố kéo dài, đặt biển báo *"Quý khách vui lòng làm thủ tục tại quầy Tiếp tân"* và liên hệ phòng IT xử lý. |
