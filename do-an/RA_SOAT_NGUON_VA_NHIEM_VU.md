# Rà soát nguồn và nhiệm vụ đồ án — Nhóm 7

Ngày đối chiếu: 28/11/2026. Mục đích: kết nối các nguồn đã có với công việc đồ án, không tự thay đổi kết quả hoặc trạng thái của thành viên.

## Nguồn đã kiểm tra

1. Chat **Đồ án**: yêu cầu đồ án, mẫu UEH, hạn nhóm 06/12/2026, luồng task, review và lưu trữ.
2. Chat **Bài tập**: kế hoạch SQA đã được nhóm trưởng xác nhận hoàn thành; bản chuẩn bị Walkthrough tạo đơn; bài tập kiểm soát chất lượng chức năng kho. Hai yêu cầu bài tập khác nhau; không gộp việc hoàn thành bài tập vào kết quả toàn đồ án.
3. `Bản sao của Nhom6-BranchFlow_Tuan1.docx.pdf` (14 trang): đề xuất BranchFlow, bối cảnh cửa hàng, vai trò, phân hệ và Project Charter. Đây là phạm vi đề xuất, cần đối chiếu phiên bản mã và phạm vi MVP trước khi xem chức năng đã triển khai.
4. `Chuong2_LenKeHoach.pdf` (45 trang): mục tiêu chất lượng, kế hoạch, review, kiểm thử, mẫu và checklist; dùng làm cơ sở xác định hoạt động QA/QC và đầu ra.
5. `03-CacThanhphan-Chatluong-Phanmem.pdf` (29 trang), nhất là trang 25–29: chuẩn bị, tiến hành, theo dõi peer review/Walkthrough; không coi quan sát cá nhân là biên bản họp.
6. `2025-HuongDanThucHienDeAn.pdf` (37 trang): hướng dẫn trích dẫn, tài liệu tham khảo và hình thức. Đây là hướng dẫn đề án thạc sĩ; vận dụng hình thức phù hợp, ưu tiên yêu cầu học phần và mẫu UEH.
7. `MAU_DO_AN_HOC_PHAN_SQA_QC_UEH.docx`: xác nhận năm chương: tổng quan; yêu cầu chất lượng và kế hoạch QA/QC; phân tích và đánh giá; kiểm soát chất lượng và quản lý lỗi; cải tiến và kế hoạch triển khai; có tài liệu tham khảo và phụ lục. Một số câu mô tả mẫu có nội dung quản lý dự án chung, cần ưu tiên yêu cầu SQA/QC cụ thể khi soạn.
8. Nội dung bài tập kho trong `Pasted text.txt`: yêu cầu quy trình, biểu mẫu, checklist, CASE tools, test cases và phân tích tĩnh. Báo cáo `Nhom_07_KiemSoatChatLuongKho.docx` là đầu vào cần rà soát, không tự xem là sản phẩm đồ án cuối.
9. `stock-result.trx`: tại 28/11/2026 có 1 lần chạy và 1 bài Pass, tên bài kiểm thử `WriteStockAsync_ValidatesStockQuantityRowVersionAndConcurrency`. Đây là một kết quả tổng hợp, không tách thành 5 Pass độc lập. Báo cáo nêu bốn trường hợp khác chưa chạy. `stock_static_analysis.log` ghi build `BranchFlow.Application` thành công với 0 cảnh báo, 0 lỗi ở cấu hình đã chạy; không chứng minh toàn bộ mã không có vấn đề. Checkout `BranchFlow_source` có HEAD `8f56909`; cần xác nhận mã và môi trường tại thời điểm chạy trước khi tái sử dụng.

## Đối chiếu nhiệm vụ hiện có

| Nhiệm vụ trên site | Điều chỉnh hoặc nội dung cần kiểm tra |
|---|---|
| Xác nhận phạm vi và đối tượng kiểm thử | Đối chiếu Charter với `docs/mvp-scope.md`, mã và môi trường hiện hành. Ghi rõ phần triển khai, phần hoãn và phạm vi kiểm thử được nhóm xác nhận. |
| Thu thập yêu cầu và tiêu chí chất lượng | Lập mã yêu cầu, nguồn, điều kiện chấp nhận, phương pháp đo; tham khảo kế hoạch SQA, bổ sung kiểm soát tồn kho âm, đồng thời và phân quyền khi có căn cứ. |
| Lập kế hoạch QA/QC | Kế thừa kế hoạch SQA đã hoàn thành, cập nhật phiên bản, người thực hiện, rủi ro, phạm vi QC, tiêu chí vào/ra và minh chứng phù hợp đồ án. |
| Thiết kế bộ test case | Truy vết yêu cầu, tiền điều kiện, dữ liệu, bước chạy, dự kiến/thực tế và trạng thái. Xem lại ca kiểm thử kho trong bài tập và bổ sung ca chưa chạy hoặc các luồng thuộc phạm vi đã duyệt. |
| Chuẩn bị môi trường và dữ liệu thử | Ghi commit, cấu hình, cơ sở dữ liệu thử, tài khoản, dữ liệu giả lập, điều kiện tái lập và giới hạn; không dùng dữ liệu thật. |
| Thực hiện kiểm thử và ghi minh chứng | Task đã được bổ sung hướng dẫn tái sử dụng kết quả kho; kiểm chứng từng kết quả và giữ riêng các ca chưa chạy. |
| Lập và theo dõi Bug Report | Ghi lỗi có bước tái hiện, môi trường, kết quả, ảnh hưởng, mức độ, người xử lý và minh chứng; quan sát Walkthrough là câu hỏi cho đến khi được xác minh. |
| Đánh giá chất lượng | Tổng hợp số liệu theo phiên bản, phạm vi và mẫu số rõ ràng; phân biệt một bài test tích hợp với từng kiểm tra bên trong; không suy ra chất lượng toàn hệ thống từ một bài Pass. |
| Đề xuất cải tiến chất lượng | Liên kết nguyên nhân với bằng chứng, ưu tiên theo tác động và khả thi; ghi đề xuất, đã thực hiện và đã xác minh riêng. |
| Tạo dashboard kết quả kiểm thử | Trình bày Pass/Fail/Chưa chạy, lỗi và phạm vi theo nguồn thực tế; ghi thời điểm, mẫu số và hạn chế. |
| Viết Chương 1–5 | Thực hiện sau kiểm thử, đánh giá và cải tiến theo phụ thuộc trên site; dùng đúng tên chương trong mẫu, không đưa nhận định chưa xác nhận thành kết quả. |
| Tổng hợp báo cáo và phụ lục | Đối chiếu đủ 30–80 trang, năm chương, tài liệu tham khảo và phụ lục; gắn checklist, test case, kết quả, bug report, minh chứng phù hợp. |
| Hoàn thiện slide và tập thuyết trình | 15–25 slide, tập trung quy trình, kết quả, đánh giá và cải tiến; sau các hoạt động thực tế. |
| Rà soát và nộp sản phẩm | Kiểm tra báo cáo, slide, test case, bug report, bảng chất lượng, minh chứng và dashboard; đối chiếu ngày thi và điều kiện nộp trước ít nhất 7 ngày. |

Hạn 06/12/2026 là mốc nhóm đặt; ngày thi và hạn nộp chính thức chưa được xác nhận. Tại thời điểm kiểm tra site ngày 28/11, 18 task đồ án vẫn ở Cần làm và một số hạn nội bộ đã qua. Không tự đổi trạng thái hoặc ngày để phản ánh giả định.

## Hạn chế và việc còn làm

- Chưa đối chiếu đầy đủ từng task trực tiếp với báo cáo/review mới nhất và từng file đính kèm trong Drive; không khẳng định toàn bộ task đã được cập nhật.
- Chưa tạo các thư mục riêng cho từng task trên Drive và chưa thiết lập quyền bất kỳ ai có liên kết được chỉnh sửa. Quyền trên thư mục cha có thể được kế thừa; cần kiểm tra thực tế từng thư mục.
- Nguồn Site qua trình duyệt có thể sửa task; lần trước công cụ cấp quyền ghi kho nguồn Site trả lỗi không tìm thấy project. Không triển khai thay đổi mã Site khi chưa xác minh đúng quyền sở hữu và nguồn.
- Các tệp minh chứng đang ở máy cục bộ; cần chuyển đến kho chung phù hợp, kiểm tra quyền truy cập, rồi liên kết tới task. Không đưa thông tin kết nối, mật khẩu, token hay dữ liệu thật vào kho công khai.
