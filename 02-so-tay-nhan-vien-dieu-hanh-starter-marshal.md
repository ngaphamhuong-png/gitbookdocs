# SỔ TAY HƯỚNG DẪN VẬN HÀNH DÀNH CHO ĐIỀU HÀNH SÂN & GIÁM SÁT (STARTER & MARSHAL SOP)

> **Tài liệu Hướng dẫn Thao tác Chuẩn (SOP - Standard Operating Procedure)**  
> **Đối tượng áp dụng:** Nhân viên Điều hành bến xuất phát (Starter) & Giám sát nhịp độ sân (Marshal)  
> **Hệ thống áp dụng:** AloGolf Management System - Phân hệ Starter Desk & Pace Monitor  
> **Phiên bản:** 1.0 | **Ngày ban hành:** 2026-10-23

---

## 1. MỤC TIÊU & NHIỆM VỤ CỦA BỘ PHẬN ĐIỀU HÀNH SÂN

Bộ phận Điều hành sân (Starter & Marshal) chịu trách nhiệm kiểm soát toàn bộ dòng di chuyển trên sân cỏ, đảm bảo an toàn, đúng giờ và tối ưu hóa năng lực phục vụ của từng đường golf:
1. **Quản lý bến phát bóng (Tee-off Staging):** Tiếp nhận danh sách khách đã check-in từ quầy lễ tân, tổ chức thứ tự xuất phát theo đúng lịch trình.
2. **Điều phối Caddie & Xe điện Buggy:** Ghép cặp Caddie và thẻ túi gậy (Bag Tag), gán xe điện khả dụng, kiểm tra trang thiết bị trước khi xe lăn bánh.
3. **Quản lý Vòng đời Flight:** Khởi động vòng chơi (bấm "Bắt đầu Flight"), kiểm soát thời gian thi đấu, và bấm "Hoàn tất Flight" khi khách về bến.
4. **Giám sát Nhịp độ Chơi (Pace of Play):** Theo dõi bản đồ thời gian thực, kịp thời can thiệp nhắc nhở các nhóm đánh chậm, hạn chế tối đa tình trạng dồn ứ tắc nghẽn sân.

---

## 2. QUY TRÌNH CHUẨN 5 BƯỚC ĐIỀU HÀNH BẾN PHÁT BÓNG (STARTER SOP)

```
[BƯỚC 1: TIẾP NHẬN FLIGHT] ➔ [BƯỚC 2: ĐIỀU PHỐI CADDIE & BUGGY] ➔ [BƯỚC 3: XUẤT PHÁT START FLIGHT] ➔ [BƯỚC 4: THEO DÕI PACE] ➔ [BƯỚC 5: HOÀN TẤT COMPLETE FLIGHT]
   Flight chờ (IN_WAITING)       Ghép Caddie ↔ Bag Tag               Gọi tên Golfer & Phổ biến luật      Giám sát GPS Checkpoints       Khách về bến hố 18
   Từ Lễ tân chuyển sang         Gán xe điện chưa bận                Bấm "Bắt đầu Flight"                Xử lý cảnh báo Vàng/Đỏ         Bấm "Hoàn tất Flight" -> Chuyển Thu ngân
```

---

### BƯỚC 1: TIẾP NHẬN DANH SÁCH CHỜ PHÁT BÓNG (STAGING QUEUE)

1. Mở màn hình Điều hành trên máy tính bàn hoặc máy tính bảng iPad tại bến phát bóng:
   - Vào menu: **Vận hành (Operations)** ➔ **Quản lý Flight (Flight Management)**.  
     *(Đường dẫn giao diện: `apps/webapp/src/app/(admin)/business/operations/flight-management/page.tsx`)*.
2. Màn hình chia làm 2 cột rõ ràng:
   - **Cột trái:** Bảng chuẩn bị Caddie ↔ Bag Tag (Dispatch Panel).
   - **Cột phải:** Bảng danh sách Flight theo các tab:
     - **Chờ xuất phát (`IN_WAITING`):** Chứa các Flight vừa được Lễ tân check-in xong hoặc Flight do Starter chuẩn bị sẵn.
     - **Đang trên sân (`IN_COURSE`):** Các nhóm đang thi đấu trên các hố.
     - **Hoàn thành (`TIME_OUT`):** Các nhóm đã đánh xong đang chờ thanh toán.
3. Kiểm tra thông tin nhóm chuẩn bị phát bóng tiếp theo: Số hiệu Flight (ví dụ: `FL026000001`), Giờ Tee Time dự kiến, Đường chơi (Sân A hay B), Số lượng khách trong đoàn.

---

### BƯỚC 2: ĐIỀU PHỐI CADDIE & GÁN XE ĐIỆN BUGGY (DISPATCHING)

1. **Ghép cặp Caddie ↔ Túi gậy (Bag Tag):**
   - Tại cột trái **Dispatch Panel**, hệ thống liệt kê danh sách Caddie đã điểm danh vào ca trực và các thẻ Bag Tag tương ứng.
   - Tích chọn các cặp Caddie ↔ Bag Tag đã sẵn sàng phục vụ cho nhóm chơi này.
   - Bấm nút **"Gán vào Flight"** hoặc dùng tính năng **"Tạo Flight nhanh 1-Click" (Quick Create)**.
2. **Gán Xe điện Buggy:**
   - Tại form chi tiết Flight, chọn số hiệu xe Buggy (ví dụ: Buggy 01, Buggy 02).
   - *Lưu ý:* Hệ thống tự động lọc và chỉ cho phép chọn những xe đang ở trạng thái sẵn sàng (`AVAILABLE`), không bị trùng với các flight đang thi đấu trên sân.
3. **Kiểm tra lộ trình hố (Hole Itinerary):**
   - Xác nhận hành trình: 9 hố đường A + 9 hố đường B (Tiêu chuẩn 18 hố) hoặc 9 hố tùy chọn.
   - Nếu có điều chỉnh luân chuyển đường hố để giãn sân, bấm vào **"Chọn lộ trình hố" (Itinerary Picker)** để đổi thứ tự xuất phát (ví dụ: xuất phát từ Hố 10 thay vì Hố 1).

---

### BƯỚC 3: GỌI TÊN XUẤT PHÁT & BẮT ĐẦU VÒNG CHƠI (START FLIGHT)

1. Trước giờ phát bóng 5 phút:
   - Nhân viên Starter gọi tên trưởng nhóm và các golfer thành viên ra khu vực Tee box phát bóng.
   - Giới thiệu Caddie phục vụ cho từng khách (đối chiếu đúng tên khách và mã Bag Tag trên túi gậy).
   - Phổ biến ngắn gọn các lưu ý an toàn của sân và điều kiện mặt cỏ trong ngày.
2. Đúng giờ phát bóng:
   - Trên dòng của Flight tương ứng, Starter bấm nút **"Bắt đầu Flight" (Start Flight)**.
   - Hệ thống hiển thị hộp thoại xác nhận ➔ Bấm **Xác nhận**.
3. **Hiệu ứng hệ thống ngay khi bấm Bắt đầu:**
   - Trạng thái Flight chuyển từ `IN_WAITING` sang `IN_COURSE`.
   - Giờ phát bóng thực tế được ghi nhận chính xác từng giây vào `FlightHoleProgress.startedAt`.
   - Trạng thái của Caddie chuyển thành `ON_ROUND` (Khóa ca, không thể phân công sang flight khác).
   - Tín hiệu được đồng bộ tức thì lên bản đồ điều hành toàn sân.

---

### BƯỚC 4: GIÁM SÁT TIẾN ĐỘ CHƠI (PACE OF PLAY MONITORING)

Trong suốt thời gian Flight di chuyển trên sân, bộ phận Marshal theo dõi màn hình **Pace Monitor**:
1. Hệ thống IoT GPS tự động bắt tọa độ xe điện và cập nhật tiến trình qua từng hố (Tee-box ➔ Fairway ➔ Green).
2. **Nhận diện cảnh báo màu sắc trên màn hình:**
   - **Xanh lá (On Pace):** Nhóm chơi đánh đúng hoặc nhanh hơn thời gian định mức quy định cho từng hố (Par 3: 12-14 phút, Par 4: 14-16 phút, Par 5: 16-18 phút). Không cần can thiệp.
   - **Màu Vàng (Slightly Slow):** Nhóm chơi trễ từ 3 - 8 phút so với định mức. Starter/Marshal gửi tin nhắn nhắc nhở qua màn hình iPad gắn trên xe Buggy hoặc bộ đàm nhắc Caddie giục khách đánh nhanh hơn.
   - **Màu Đỏ (Very Slow):** Nhóm chơi trễ trên 15 phút, gây nguy cơ tắc nghẽn toàn bộ các flight phía sau.
3. **Quy trình xử lý hiện trường khi có Cảnh báo Đỏ:**
   - Marshal lái xe chuyên dụng tiếp cận Flight bị cảnh báo đỏ.
   - Lịch sự nhắc nhở nhóm tăng tốc độ gạt bóng (Putt) hoặc nhặt bóng nếu đã vượt quá số gậy tối đa (Double Par).
   - Nếu nhóm chơi liên tục không theo kịp tiến độ, Marshal có quyền yêu cầu nhóm nhường đường cho flight phía sau vượt lên (Call through) hoặc bỏ qua hố đang đánh dở để tiến sang hố tiếp theo (`SKIP HOLE`).

---

### BƯỚC 5: ĐÓN KHÁCH VỀ BẾN & HOÀN TẤT VÒNG CHƠI (COMPLETE FLIGHT)

1. Khi nhóm chơi đánh xong hố cuối cùng và xe Buggy di chuyển về lại khu vực bãi trả xe:
   - Caddie bàn giao túi gậy cho bộ phận trả đồ tại sảnh hoặc đưa khách vào phòng thay đồ.
2. Starter kiểm tra Flight trên màn hình:
   - Bấm nút **"Hoàn tất Flight" (Complete Flight)**.
   - Hệ thống hiển thị popup xác nhận hoàn thành vòng đấu.
3. **Hiệu ứng hệ thống sau khi bấm Hoàn tất:**
   - Trạng thái Flight chuyển sang `TIME_OUT` và lưu giờ kết thúc `checkedOutAt = now()`.
   - Toàn bộ hố trên lộ trình được đánh dấu `COMPLETED`.
   - Caddie được giải phóng về trạng thái hoàn thành vòng đấu, tích lũy số lỗ phục vụ trong ngày.
   - Thẻ Bag Tag được nhả ra kho khả dụng để sẵn sàng phục vụ cho ngày tiếp theo.
   - **Đặc biệt:** Hệ thống tự động kích hoạt trường `readyForCheckoutAt = now()` trên đơn tiếp đón của Lễ tân/Thu ngân. Lúc này hóa đơn thanh toán của nhóm sẽ ngay lập tức xuất hiện tại quầy Thu ngân để làm thủ tục thanh toán.

---

## 3. CÁC TÌNH HUỐNG THAO TÁC NÂNG CAO

### 1. Khách vãng lai (Walk-in) ra thẳng bến phát bóng
Nếu khách không qua quầy lễ tân mà muốn đánh ngay:
1. Starter bấm nút **"Tạo Flight Vãng lai" (Create Walk-in Flight)** góc trên màn hình.
2. Nhập tên các golfer, chọn số hố (9 hoặc 18 hố), chọn xe điện và caddie.
3. Bấm **Lưu & Bắt đầu**. Hệ thống tự động tạo mã Flight mới (ví dụ `FL026000088`) cho nhóm xuất phát ngay.

### 2. Điều chuyển Golfer giữa các Flight (Transfer Golfer)
- Khi Golfer A muốn đổi sang nhóm khác:
  1. Mở Flight chứa Golfer A ➔ Bấm **"Chuyển khách" (Transfer Guest)**.
  2. Chọn Flight đích muốn chuyển đến.
  3. Bấm xác nhận. Toàn bộ thông tin gậy, caddie và tiền dịch vụ của Golfer A sẽ tự động chuyển sang Flight mới.

### 3. Nhập dữ liệu hàng loạt từ file Excel (Import Starter Flights)
Trong trường hợp đầu ngày hoặc khi mất mạng Internet phải ghi chép sổ tay:
1. Bấm nút **"Xuất file mẫu" (Export Template XLSX)** để lấy file mẫu Excel chuẩn của AloGolf.
2. Điền danh sách Flight, giờ xuất phát, tên khách, số xe, số caddie vào file Excel.
3. Bấm nút **"Nhập file Excel" (Import Flights)**, chọn file vừa điền và tải lên.
4. Hệ thống sẽ tự động khởi tạo hàng loạt Flight trên phần mềm chỉ trong vài giây.

---

## 4. HÌNH ẢNH MINH HỌA THAO TÁC THỰC TẾ TRÊN PHẦN MỀM

Dưới đây là các ảnh chụp màn hình ghi nhận trực tiếp từ hệ thống thực tế AloGolf:

### 4.1. Giao diện Tạo Flight trên Máy tính để bàn (Desktop Starter Interface)
Giao diện phân bổ người chơi, lộ trình hố và kiểm tra sẵn sàng xuất phát:
![Tạo Flight trên máy tính](file:///d:/Projects/alogolf/docs/screenshots/shot-timing/2026-04-29/starter-02-create-flight.png)
*Hình 1: Màn hình tạo mới Flight trên máy tính bàn - Nhập thông tin khách, caddie và xe Buggy.*

![Điền thông tin Golfer](file:///d:/Projects/alogolf/docs/screenshots/shot-timing/2026-04-29/starter-05-fill-guest1.png)
*Hình 2: Thao tác điền thông tin Golfer 1, chọn Bag Tag và gán Caddie phục vụ.*

![Flight sẵn sàng xuất phát](file:///d:/Projects/alogolf/docs/screenshots/shot-timing/2026-04-29/starter-06-ready-submit.png)
*Hình 3: Kiểm tra các chỉ số trước khi bấm Bắt đầu xuất phát.*

![Flight tạo thành công](file:///d:/Projects/alogolf/docs/screenshots/shot-timing/2026-04-29/starter-07-flight-created.png)
*Hình 4: Flight hiển thị trên bảng danh sách quản lý bến Starter.*

---

### 4.2. Giao diện Thao tác trên Máy tính bảng iPad / Di động (Mobile Starter Interface)
Giao diện tối ưu hóa cho màn hình cảm ứng để nhân viên Starter thao tác linh hoạt ngay tại mặt sân:
![Tạo Flight trên Mobile 1](file:///d:/Projects/alogolf/docs/screenshots/shot-timing/2026-04-29/starter-mobile-02-create-flight.png)
*Hình 5: Giao diện Starter tối ưu trên thiết bị di động / iPad bến phát bóng.*

![Nhập thông tin trên Mobile](file:///d:/Projects/alogolf/docs/screenshots/shot-timing/2026-04-29/starter-mobile-05-fill-guest1.png)
*Hình 6: Nhập mã Bag Tag và chọn Caddie trên giao diện cảm ứng di động.*

![Xác nhận xuất phát trên Mobile](file:///d:/Projects/alogolf/docs/screenshots/shot-timing/2026-04-29/starter-mobile-06-ready-submit.png)
*Hình 7: Thao tác 1 chạm bấm khởi động vòng chơi trên iPad.*
