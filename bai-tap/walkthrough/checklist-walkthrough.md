# Checklist Walkthrough luồng tạo đơn BranchFlow

**Phiên dự kiến:** 08:00 ngày 17/12/2026, trực tuyến.  
**Phiên bản mã dùng để chuẩn bị:** candidate `05c6b165132809958c69929b95efac900925043b`; đối chiếu đầu `main` `a7f0115b3fd8ac862bf6bceaa0c6ee6f420d6e76` ngày 19/11/2026. Xác nhận lại phiên bản được dùng trong phiên.  
**Kết quả thực tế:** chưa thực hiện Walkthrough; toàn bộ mục dưới đây đang chờ rà soát.

Quy ước kết quả khi họp: **Đạt / Có vấn đề / Cần làm rõ / Không áp dụng**. Mỗi nhận xét cần có vị trí, căn cứ và người theo dõi nếu nhóm xác nhận; không coi trạng thái “chờ rà soát” là đạt.

| Mã | Câu hỏi/tiêu chí rà soát | Vị trí tham chiếu | Kết quả | Minh chứng / ghi chú |
|---|---|---|---|---|
| W01 | Phạm vi, mục tiêu và phiên bản mã đã được xác nhận trước phiên? | `docs/mvp-scope.md`; kế hoạch Mục 3 | Chờ rà soát | Chưa có |
| W02 | Endpoint tạo đơn giới hạn đúng vai trò Employee? | `OrdersController.cs:10–18` | Chờ rà soát | Chưa có |
| W03 | User ID được lấy từ claim và truyền xuống service nhất quán? | `OrdersController.cs:14,18–23` | Chờ rà soát | Chưa có |
| W04 | Request chỉ nhận dữ liệu được phép, không nhận giá do client quyết định? | `Contracts.cs:26–32`; `OrderService.cs:13–20` | Chờ rà soát | DTO request có `JsonUnmappedMemberHandling.Disallow`. |
| W05 | BranchId không hợp lệ bị từ chối trước khi mở transaction? | `OrderService.cs:77–83` | Chờ rà soát | Chưa có |
| W06 | Quyền chi nhánh được kiểm tra trước khi truy vấn menu? | `OrderMenuService.cs:17–35`; `OrderService.cs:89–90` | Chờ rà soát | Chưa có |
| W07 | Chi nhánh/menu không khả dụng được chuyển thành kết quả phù hợp? | `OrderMenuService.cs:33–39`; `OrderService.cs:89,118–121`; `OrdersController.cs:28` | Chờ rà soát | Chưa có |
| W08 | Số dòng, số ly, ProductSizeId và dữ liệu topping/ghi chú được kiểm tra? | `OrderService.cs:13–27` | Chờ rà soát | Chưa có |
| W09 | Topping không trùng, thuộc menu chi nhánh và không vượt giới hạn số phần? | `OrderService.cs:30–44` | Chờ rà soát | Chưa có |
| W10 | Ghi chú hợp lệ, không trùng và quy tắc chọn theo nhóm đã đúng yêu cầu? | `OrderService.cs:46–55` | Chờ rà soát | Cần xác nhận vì logic hiện tại chỉ cho một lựa chọn mỗi nhóm. |
| W11 | Giá, tên sản phẩm, size và topping được lấy từ menu server và lưu snapshot? | `OrderService.cs:24–44` | Chờ rà soát | Chưa có |
| W12 | Thành tiền, tổng đơn và trường hợp overflow được xử lý? | `OrderService.cs:57–72,93–94` | Chờ rà soát | Chưa có |
| W13 | BusinessDate theo UTC+07 và trạng thái ban đầu COMPLETED có khớp yêu cầu? | `OrderService.cs:85–86,99–109`; `docs/mvp-scope.md` | Chờ rà soát | Cần nhóm xác nhận trạng thái ngay khi tạo. |
| W14 | Mã đơn chỉ được cấp sau khi quyền, menu và dữ liệu hợp lệ? | `OrderService.cs:89–98` | Chờ rà soát | Chưa có |
| W15 | Header, dòng món và snapshot nằm trong transaction; lỗi lưu có rollback? | `OrderService.cs:82–84,99–127` | Chờ rà soát | Chưa có |
| W16 | API trả 201 khi thành công và ánh xạ exception đã bắt đúng? | `OrdersController.cs:18–28` | Chờ rà soát | Không suy ra status cho exception không được action bắt. |
| W17 | Hành vi khi client gửi lại request sau timeout đã được thống nhất? | `Contracts.cs:26–32`; `OrderService.cs:77–116` | Chờ rà soát | Chưa thấy idempotency key trong contract/phương thức đang rà soát; chưa kết luận có lỗi. |
| W18 | Mỗi vấn đề đã thống nhất có vị trí, mô tả, người theo dõi và bước tiếp theo? | Biên bản và danh sách vấn đề của phiên | Chờ rà soát | Chưa có |
| W19 | Nhóm có thống nhất rằng tạo đơn không tự trừ kho trong MVP? | `docs/mvp-scope.md` | Chờ rà soát | MVP mô tả kho nhập/xuất thủ công; bán hàng không tự trừ kho. |

## Mẫu ghi nhận trong phiên

| Mã | Vị trí và phiên bản | Mô tả / căn cứ | Loại / ảnh hưởng cần xác minh | Người theo dõi | Hành động / hạn thống nhất | Trạng thái |
|---|---|---|---|---|---|---|
| Chưa ghi | Chưa ghi | Chưa ghi | Chưa ghi | Chưa ghi | Chưa ghi | Chưa ghi |

## Ghi chú sau phiên

- Người tham dự thực tế và thời gian kết thúc: chưa có.
- Vấn đề được nhóm thống nhất: chưa có.
- Quyết định, nội dung cần làm rõ và người theo dõi: chưa có.
- Liên kết sửa đổi và kết quả kiểm tra lại: chưa có.

Các tệp test tham chiếu là đầu vào để nhóm xem xét, không phải kết quả kiểm thử đã chạy trong nhiệm vụ chuẩn bị này. Tài liệu dẫn luồng của người trình bày nằm tại [luong-tao-don.md](luong-tao-don.md).
