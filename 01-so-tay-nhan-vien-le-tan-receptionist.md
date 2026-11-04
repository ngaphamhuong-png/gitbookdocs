# SỔ TAY HƯỚNG DẪN VẬN HÀNH DÀNH CHO NHÂN VIÊN LỄ TÂN (RECEPTIONIST SOP)

> **Tài liệu Hướng dẫn Thao tác Chuẩn (SOP - Standard Operating Procedure)**  
> **Đối tượng áp dụng:** Nhân viên Tiếp tân / Bộ phận Chăm sóc Khách hàng Sân Golf  
> **Hệ thống áp dụng:** AloGolf Management System - Phân hệ Lễ tân (Reception Desk)  
> **Phiên bản:** 1.0 | **Ngày ban hành:** 2026-10-23

---

## 1. MỤC TIÊU & NHIỆM VỤ CỦA NHÂN VIÊN LỄ TÂN

Nhân viên Lễ tân là điểm tiếp xúc trực tiếp đầu tiên (First Impression) của golfer khi đến trải nghiệm tại sân golf AloGolf. Nhiệm vụ trọng tâm bao gồm:
1. Tiếp nhận và quản lý danh sách đặt giờ chơi (Tee Time Booking).
2. Chào đón khách, thực hiện quy trình Check-in nhanh chóng và chuẩn xác.
3. Cấp phát thẻ tủ đồ cá nhân (Locker Card) và gắn thẻ định danh túi gậy golf (Bag Tag).
4. Xác nhận số lỗ chơi thực tế và các gói dịch vụ phụ trợ (thuê gậy, thuê giày, suất ăn).
5. Kích hoạt lượt khách trên hệ thống phần mềm để chuyển tiếp thông tin ra bến phát bóng (Starter Desk).

---

## 2. QUY TRÌNH CHUẨN 4 BƯỚC THAO TÁC TẠI QUẦY (STEP-BY-STEP SOP)

```
[BƯỚC 1: TRA CỨU ĐƠN]  ->  [BƯỚC 2: TIẾP ĐÓN & ĐIỂM DANH] -> [BƯỚC 3: CẤP LOCKER & BAG TAG] -> [BƯỚC 4: BÀN GIAO & TIỄN RA SÂN]
  Quét QR hoặc SĐT          Xác nhận số lượng khách            Chọn khu vực tủ đồ Nam/Nữ         Kiểm tra trạng thái READY
  Kiểm tra giờ Tee Time      Xác nhận số hố chơi (9/18)        Dán mã Bag Tag vào túi gậy        Hướng dẫn lối ra bến Starter
```

---

### BƯỚC 1: TRA CỨU VÀ XÁC THỰC ĐƠN ĐẶT CHỖ (BOOKING LOOKUP)

1. Đăng nhập vào hệ thống AloGolf bằng tài khoản Lễ tân được cấp.
2. Trên thanh điều hướng bên trái, chọn mục: **Vận hành (Operations)** ➔ **Tiếp đón (Check-in)**.  
   *(Đường dẫn giao diện: `apps/webapp/src/app/(admin)/business/operations/check-in/page.tsx`)*.
3. Khi khách tiến đến quầy:
   - **Cách 1 (Khuyên dùng - Nhanh nhất):** Bấm nút **"Quét mã QR"** góc trên bên phải màn hình. Yêu cầu khách xuất trình mã QR trên ứng dụng AloGolf hoặc tin nhắn Zalo ZNS. Đưa mã QR vào máy quét hoặc camera. Hệ thống sẽ tự động tìm đúng đơn đặt chỗ của khách trong vòng 1 giây.
   - **Cách 2:** Nhập **Số điện thoại** hoặc **Tên khách hàng** hoặc **Mã Booking** (ví dụ: `BK261023A01`) vào ô tìm kiếm ở thanh công cụ phía trên bảng danh sách.

---

### BƯỚC 2: TIẾP ĐÓN VÀ ĐIỂM DANH NGƯỜI CHƠI (GUEST ARRIVAL & CHECK-IN)

1. Kiểm tra thông tin hiển thị trên màn hình:
   - Khung giờ phát bóng (`TeeOffAt`): Có đúng khung giờ của ca trực hiện tại không?
   - Đường chơi (`GolfPath`): Sân A, Sân B hay Sân C?
   - Tổng số người trong đoàn (`PlayerCount`): 1, 2, 3 hay 4 người?
   - Số hố đăng ký: 9 hố hay 18 hố?
2. Điểm danh từng khách có mặt:
   - Nếu cả đoàn đến cùng lúc: Bấm nút **"Tiếp đón cả nhóm" (Check-in All)**.
   - Nếu khách đến rải rác: Bấm vào dòng của từng người chơi cụ thể để đánh dấu **"Đã đến" (Arrived)**.
3. **Xử lý thay đổi số lỗ chơi:**
   - Nếu khách muốn đổi từ 18 lỗ xuống 9 lỗ hoặc tăng lên 27 lỗ, bấm nút **"Chỉnh sửa" (Edit Check-in)**.
   - Tại ô "Số lỗ", chọn lại số lỗ mong muốn. Hệ thống sẽ tự động lưu vết và cập nhật giá tương ứng sang khâu thanh toán.

---

### BƯỚC 3: CẤP THẺ TỦ ĐỒ (LOCKER) VÀ GẮN THẺ TÚI GẬY (BAG TAG)

Đây là bước cực kỳ quan trọng để đảm bảo tài sản của khách không bị thất lạc hoặc nhầm lẫn:

1. **Cấp phát Thẻ Tủ Đồ Locker:**
   - Trên dòng thông tin của từng người chơi, chọn **Khu vực tủ đồ** (Khu Nam / Khu Nữ / VIP).
   - Chọn **Số tủ Locker** khả dụng (hệ thống chỉ hiển thị những tủ đang ở trạng thái `AVAILABLE`).
   - Lấy thẻ từ RFID tương ứng từ khay tủ, chạm thẻ vào đầu đọc RFID để hệ thống ghi nhận mã UID liên kết.
   - Trao thẻ chìa khóa tủ đồ cho khách. Nhắc khách cất đồ cá nhân và đeo thẻ cẩn thận.
2. **Gắn Thẻ Túi Gậy Golf (Bag Tag):**
   - Lấy thẻ Bag Tag của ngày hôm nay (Lưu ý kiểm tra ký tự tiền tố xoay vòng theo ngày, ví dụ: Thứ Hai là thẻ màu xanh tiền tố `A...`, Thứ Ba là tiền tố `B...`).
   - Nhập hoặc quét mã vạch Bag Tag vào ô **"Mã Bag Tag"** của người chơi (ví dụ: `A015`).
   - Gắn thẻ Bag Tag chắc chắn vào quai xách của túi gậy golf.
   - Nhắc nhân viên vận chuyển chuyển túi gậy ra khu vực tập kết bàn giao Caddie.

---

### BƯỚC 4: HOÀN TẤT CHECK-IN & HƯỚNG DẪN KHÁCH RA BẾN STARTER

1. Sau khi đã nhập đầy đủ số tủ Locker và mã Bag Tag cho toàn bộ người chơi trong đoàn, kiểm tra cột **Trạng thái**:
   - Nếu đã đủ khách: Hệ thống tự động chuyển sang trạng thái **"Sẵn sàng" (`READY`)**.
   - Nếu còn khách chưa đến: Hệ thống giữ trạng thái **"Đang chờ" (`ASSIGNED_FLIGHT`)**. Lễ tân có thể tiếp đón trước các khách đã có mặt để họ vào phòng thay đồ chuẩn bị.
2. Bấm nút **"Hoàn tất Check-in"**.
3. Hệ thống sẽ tự động khởi tạo một Flight vỏ trạng thái `IN_WAITING` và đẩy dữ liệu sang màn hình của nhân viên Điều hành sân (Starter Desk).
4. Lễ tân mỉm cười, gửi lời chào và hướng dẫn khách:
   > *"Dạ em đã hoàn tất thủ tục tiếp đón cho nhóm mình. Chìa khóa tủ đồ của các anh/chị đây ạ. Túi gậy của đoàn mình đã được gắn thẻ và đang được chuyển ra xe điện tại bến phát bóng sân [Tên sân]. Chúc các anh/chị có một buổi chơi golf vui vẻ và đạt nhiều điểm Birdie/Eagle ạ!"*

---

## 3. CÁC THAO TÁC BỔ TRỢ & TÌNH HUỐNG THƯỜNG GẶP

### 1. Tạo đặt chỗ mới trực tiếp tại quầy (Walk-in / Desk Booking)
Nếu khách đến sân trực tiếp mà chưa đặt chỗ trước:
1. Vào menu **Vận hành** ➔ **Đặt chỗ (Bookings)** ➔ Bấm nút **"Tạo đặt chỗ mới" (Create Booking)**.
2. Màn hình Wizard 3 bước hiển thị:
   - **Bước 1:** Chọn ngày chơi hôm nay, chọn đường chơi còn khung giờ trống (`OPEN`), chọn giờ Tee Time và số lượng khách.
   - **Bước 2:** Nhập họ tên và số điện thoại của người đại diện. Thêm các dịch vụ phụ trợ nếu khách yêu cầu (thuê xe Buggy, thuê gậy).
   - **Bước 3:** Tại mục hình thức thanh toán, chọn **"Thanh toán khi ra về" (`PAY_ON_CHECKOUT`)**.
3. Bấm **"Xác nhận tạo đơn"**. Sau khi tạo xong, hệ thống chuyển thẳng sang màn hình Check-in để làm thủ tục cấp thẻ tủ ngay.

### 2. Khách hủy giờ chơi ngay tại quầy
- Trường hợp khách đã check-in nhưng phải hủy vì việc gấp:
  1. Tìm dòng của nhóm khách trên bảng Check-in.
  2. Bấm vào biểu tượng ba chấm (...) ở cuối dòng ➔ Chọn **"Hủy Check-in" (Cancel Visit)**.
  3. Xác nhận thu lại thẻ chìa khóa Locker và thẻ Bag Tag.
  4. Hệ thống sẽ tự động giải phóng tủ đồ về kho và hủy thông báo flight tại bến xuất phát.

### 3. Khách làm mất thẻ chìa khóa tủ Locker
1. Báo cho Quản lý ca trực (Shift Supervisor) để sử dụng thẻ Master mở tủ lấy đồ cho khách.
2. Trên màn hình Check-in, tìm người chơi làm mất thẻ ➔ Bấm **"Thu hồi thẻ" (Revoke RFID)** để hủy mã thẻ cũ.
3. Cấp một thẻ mới nếu khách vẫn tiếp tục sử dụng tủ đồ.
4. Ghi chú lại sự việc để Thu ngân tính phí bồi thường mất thẻ (nếu có quy định).
