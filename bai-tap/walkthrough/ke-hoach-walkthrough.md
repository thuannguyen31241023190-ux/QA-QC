# Kế hoạch Walkthrough luồng tạo đơn BranchFlow

## 1. Thông tin phiên

- **Đề tài:** Ứng dụng Walkthrough trong đảm bảo chất lượng phần mềm, Nhóm 7.
- **Đối tượng:** luồng Employee tạo đơn của hệ thống BranchFlow.
- **Thời gian dự kiến:** 08:00 ngày 17/12/2026 (giờ Việt Nam).
- **Hình thức:** trực tuyến, chia sẻ màn hình để trình bày tài liệu và mã nguồn.
- **Nền tảng họp và liên kết:** chưa xác định; nhóm trưởng bổ sung trước phiên.
- **Thời lượng dự kiến:** khoảng 45 phút; điều chỉnh theo thực tế.
- **Trạng thái:** kế hoạch chuẩn bị, chưa phải biên bản phiên đã diễn ra.

## 2. Mục tiêu

1. Cùng lần theo đường đi của yêu cầu tạo đơn từ API qua xử lý nghiệp vụ đến lưu dữ liệu.
2. Đối chiếu luồng và các giới hạn quan sát trong mã với phạm vi MVP, yêu cầu đã được nhóm xác nhận.
3. Đặt câu hỏi, ghi nhận vị trí và ảnh hưởng của vấn đề cần làm rõ; phân biệt quan sát cá nhân với kết luận được nhóm thống nhất trong phiên.
4. Chia sẻ hiểu biết để nhóm lập danh sách xử lý và kiểm chứng sau phiên.

Walkthrough là rà soát ngang hàng để phát hiện vấn đề và trao đổi kiến thức. Việc đọc mã tĩnh không thay thế việc chạy kiểm thử, không chứng minh toàn bộ hệ thống vận hành đúng và không tự tạo kết luận nghiệm thu.

## 3. Phạm vi và tài liệu đầu vào

**Phiên bản mã dùng để chuẩn bị:** candidate `05c6b165132809958c69929b95efac900925043b` của BranchFlow. Đối chiếu đến đầu nhánh `main` `a7f0115b3fd8ac862bf6bceaa0c6ee6f420d6e76` ngày 19/11/2026; so sánh commit xác nhận các thay đổi sau candidate chỉ nằm ở tài liệu phạm vi và hồ sơ kiểm thử, không có tệp mã ứng dụng thay đổi. Trước phiên vẫn cần xác nhận nhóm sẽ walkthrough đúng candidate này.

| Thành phần | Nội dung đưa vào Walkthrough |
|---|---|
| `docs/mvp-scope.md` | Quyền Employee, quy tắc giá, ghi chú và giới hạn MVP liên quan đến tạo đơn. |
| `src/BranchFlow.Api/Controllers/OrdersController.cs`, dòng 10–28 | Route `POST /api/orders`, vai trò `EMPLOYEE`, lấy user ID, gọi service và ánh xạ lỗi. |
| `src/BranchFlow.Application/DTOs/Sprint4/Contracts.cs`, dòng 26–37 | Request/response tạo đơn; không có trường giá trong request. |
| `src/BranchFlow.Application/Services/OrderMenuService.cs`, dòng 17–99 | Kiểm tra quyền chi nhánh trước khi đọc menu và dựng dữ liệu menu. |
| `src/BranchFlow.Application/Services/OrderService.cs`, dòng 13–72 và 77–127 | `PriceItems`, validation, lấy giá/snapshot, tính tổng, transaction, cấp mã, lưu và rollback. |
| `tests/BranchFlow.Tests/Backend/OrderPricingTests.cs` và `OrderServiceTests.cs` | Các test tham chiếu cho tính giá, validation, transaction và rollback; không thay thế kết quả walkthrough. |
| `tests/final/2026-11-19/README.md` | Kết quả tích hợp và kiểm tra public được ghi riêng theo môi trường. |
| [luong-tao-don.md](luong-tao-don.md) | Tài liệu dẫn luồng và kịch bản nói của người trình bày BT05. |

**Ngoài phạm vi phiên:** kiểm thử tải, nghiệm thu toàn hệ thống, thanh toán trực tuyến, tính lương, điều chuyển, kiểm kê/duyệt phiếu và xử lý đơn sai nhiều bước. Có thể ghi vấn đề liên quan để xem xét riêng nhưng không tự mở rộng kết luận của phiên.

## 4. Phân công

| Thành viên | Vai trò | Việc chuẩn bị và trách nhiệm trong phiên |
|---|---|---|
| Nguyễn Đặng Hòa Thuận | Người tổ chức, điều phối | Xác nhận lịch và tài liệu; gửi checklist; điều phối thời gian, kết luận và theo dõi vấn đề. |
| Nguyễn Phước Thuần | Người trình bày | Đọc trước luồng tạo đơn, chia sẻ màn hình và đi qua ba tình huống; giải thích các điểm cần làm rõ. |
| Nguyễn Công Thành | Người rà soát | Đối chiếu yêu cầu với mã, ghi câu hỏi, nêu vị trí và ảnh hưởng có căn cứ. |
| Bá Thành Chí Khang | Thư ký | Ghi người tham dự thực tế, nội dung, vị trí, ý kiến, vấn đề được nhóm chấp nhận và người theo dõi. |

Phân công này theo thông tin nhóm đã thống nhất. Người tham dự thực tế và kết quả tham gia sẽ được ghi tại thời điểm họp; không mặc định là bằng chứng đã hoàn thành nhiệm vụ.

## 5. Chuẩn bị trước phiên

- [ ] Nhóm trưởng xác nhận nền tảng, liên kết họp và khả năng chia sẻ màn hình cho phiên 08:00 ngày 17/12/2026.
- [ ] Đối chiếu phiên bản mã và phạm vi MVP đang áp dụng; ghi lại thay đổi so với phiên bản tham chiếu nếu có.
- [ ] Chia sẻ kế hoạch này, checklist, tài liệu phạm vi, các đoạn mã và bản dự thảo để bốn thành viên đọc trước.
- [ ] Người trình bày đọc và chuẩn bị theo [tài liệu dẫn luồng tạo đơn](luong-tao-don.md), đặc biệt các điểm cần nhóm xác nhận.
- [ ] Người rà soát đọc checklist, ghi câu hỏi và đánh dấu vị trí cần xem xét.
- [ ] Thư ký chuẩn bị bảng biên bản, sổ vấn đề và nơi lưu minh chứng; không đưa mật khẩu hoặc token vào tài liệu, ảnh hay bản ghi.

## 6. Kịch bản Walkthrough

Chi tiết thứ tự đọc mã, hợp đồng request/response, ánh xạ lỗi và kịch bản nói được chuẩn bị tại [Tài liệu dẫn luồng tạo đơn](luong-tao-don.md).

### Tình huống 1 — Tạo đơn hợp lệ

Bắt đầu từ request có chi nhánh và danh sách món phù hợp. Đi qua giới hạn vai trò tại controller, kiểm tra quyền chi nhánh và menu, kiểm tra món/size/topping/ghi chú, tính giá phía máy chủ, cấp mã, lưu dữ liệu và phản hồi. Câu hỏi: dữ liệu nào được lấy từ client, dữ liệu nào được lấy từ menu, trạng thái và thời điểm nghiệp vụ được xác định thế nào?

### Tình huống 2 — Không đủ quyền hoặc dữ liệu không hợp lệ

Đi qua các nhánh chi nhánh ngoài quyền, chi nhánh không khả dụng, giỏ rỗng, số lượng không hợp lệ, món/size không có trong menu, topping trùng hoặc quá giới hạn, ghi chú không hợp lệ. Xác định nơi kiểm tra, ngoại lệ và phản hồi dự kiến theo mã; đối chiếu yêu cầu đã xác nhận. Không dùng việc đọc mã làm kết quả chạy.

### Tình huống 3 — Lỗi trong khi lưu hoặc yêu cầu gửi lại

Lần theo thứ tự mở giao dịch, cấp mã, lưu, commit và rollback khi có ngoại lệ. Đặt câu hỏi khi kết nối gián đoạn sau khi gửi, người dùng gửi lại thì yêu cầu nghiệp vụ và cơ chế ngăn đơn trùng là gì. Đây là **câu hỏi cần làm rõ**, chưa phải kết luận có lỗi. Nếu cần kiểm chứng hành vi runtime, ghi thành hoạt động riêng với môi trường và bằng chứng.

## 7. Chương trình dự kiến

| Thời lượng | Người dẫn | Nội dung |
|---|---|---|
| 0–5 phút | Thuận | Xác nhận mục tiêu, phạm vi, thành viên tham dự và phiên bản được xem. |
| 5–15 phút | Thuần | Trình bày cấu trúc, đầu vào và tình huống đơn hợp lệ. |
| 15–25 phút | Thuần, Thành | Đi qua nhánh quyền và dữ liệu không hợp lệ; đối chiếu checklist. |
| 25–35 phút | Cả nhóm | Thảo luận giao dịch, lỗi lưu và câu hỏi về gửi lại. |
| 35–42 phút | Khang | Đọc lại danh sách vấn đề, vị trí, câu hỏi và người theo dõi để nhóm thống nhất. |
| 42–45 phút | Thuận | Tóm tắt nội dung cần xử lý, hạn theo dõi nếu được thống nhất và bước tiếp theo. |

Thời lượng chỉ là đề xuất; biên bản phải phản ánh diễn biến thực tế.

## 8. Đầu ra và theo dõi

- **Trước phiên:** kế hoạch, danh sách tài liệu, tài liệu dẫn luồng và checklist; tất cả mục checklist ở trạng thái chưa rà soát cho đến khi có kết quả.
- **Trong phiên:** biên bản và danh sách vấn đề có vị trí, mô tả, ảnh hưởng hoặc câu hỏi, ý kiến thống nhất và người theo dõi.
- **Sau phiên:** bản cập nhật danh sách vấn đề; quyết định xử lý hoặc lý do chưa xử lý; liên kết thay đổi và kết quả kiểm tra lại khi thực sự có.

Thư ký dùng các trường: mã; vị trí/phiên bản; mô tả và bằng chứng; phân loại; ảnh hưởng dự kiến; người theo dõi; hành động; hạn thống nhất; trạng thái; kết quả xác minh lại. Không tự điền kết quả phiên, số lỗi hoặc hiệu quả cải tiến trước khi có minh chứng.

## 9. Tiêu chí sẵn sàng và tài liệu cần bổ sung

Phiên sẵn sàng khi nhóm xác nhận lịch/hình thức, liên kết họp, phạm vi và phiên bản, tài liệu đã được chia sẻ, bốn vai trò được thông báo, checklist và mẫu ghi nhận đã chuẩn bị. Nếu thiếu điều kiện nào, người tổ chức ghi lại và thống nhất cách xử lý trước phiên.

Hồ sơ sau phiên cần xác nhận sự tham gia, nội dung đã xem, các kết luận và vấn đề; chưa thể hoàn tất khi chưa có phiên thực tế. Kế hoạch này không tự đặt hạn nộp học phần. Cần đối chiếu lịch phiên 17/12 với thời hạn bài tập được giảng viên xác nhận.
