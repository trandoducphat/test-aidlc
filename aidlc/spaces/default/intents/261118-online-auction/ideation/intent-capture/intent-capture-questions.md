# Intent Capture & Framing — Câu hỏi làm rõ

## Sources

- [desc] Initial description: "hiện tại t đang muốn build 1 phần mềm đấu giá online cơ bản để các user có thể vào 1 nền tảng và thực hiện đấu giá cho 1 món đồ bất kỳ được rao lên trong 1 khoảng thời gian countdown nhất định. Khi hết countdown thì món đồ sẽ thuộc về người trả giá cao nhất cuối cùng.\n\nCác lựa chọn đã chốt:\n1. Thanh toán: không thanh toán online; hệ thống xác định người thắng rồi hiển thị liên hệ hai bên và trạng thái \"đã giao dịch\".\n2. Đăng món: mọi user đã đăng ký được đăng, nhưng admin phải duyệt trước khi hiện.\n3. Bước giá: theo phần trăm giá hiện tại, tuy nhiên sẽ có base cơ bản ban đầu và cơ chế làm tròn (mệnh giá nhỏ nhất phải là 50k).\n4. Không có giá sàn (reserve price) và không có mua ngay (buy-now).\n5. Có anti-sniping (bid trong T giây cuối thì gia hạn), nhưng giới hạn tổng thời gian hoặc số lần gia hạn.\n6. Không có proxy bid, chỉ đặt giá thủ công.\n7. Quy mô: demo/học tập, dưới 100 người online cùng lúc.\n8. Tech stack: Node.js/TypeScript (NestJS) + React.\n9. Nền tảng: webapp từ đầu đến cuối.\n10. Triển khai: chỉ chạy local hoặc demo."
- [scope] Workflow-selected scope: `mvp`.

Các lựa chọn anh/chị đã chốt trong mô tả ban đầu (thanh toán, duyệt bài đăng, bước giá, không giá sàn/mua ngay, anti-sniping có giới hạn, không proxy bid, quy mô, tech stack, webapp, chạy local) được coi là đã quyết định và không hỏi lại ở đây.

## Q1. [Sản phẩm] Mục đích chính của dự án là gì?

Câu trả lời quyết định mức độ "thật" của sản phẩm (học tập hay đưa vào dùng) và cách đo thành công.

A. Dự án học tập / tự nâng cao kỹ năng (luyện xây hệ thống realtime, xử lý bid đồng thời)
B. Sản phẩm demo / portfolio để giới thiệu năng lực với khách hàng hoặc nhà tuyển dụng
C. Bước đầu của một nền tảng đấu giá thật cho một cộng đồng nhỏ
D. Not yet defined
X. Other (please specify)

[Answer]: B — "mục đích chính của dự án là build up được dự án demo mẫu chạy ở local, chưa cần deployment; nhưng vẫn thể hiện được đầy đủ các chức năng yêu cầu cơ bản. Chọn mục 2"

## Q2. [Sản phẩm] Ai là người dùng mục tiêu của nền tảng?

Giúp xác định các vai trò (persona) cần thiết kế màn hình và quyền hạn.

A. Người dùng cá nhân vừa đăng bán vừa đấu giá (mua bán giữa cá nhân với nhau), cộng thêm admin duyệt bài
B. Chỉ một nhóm người dùng thử nội bộ (bạn bè, đồng nghiệp, người chấm) để demo
C. Người bán là cửa hàng / doanh nghiệp nhỏ, người mua là cá nhân
D. Not yet defined
X. Other (please specify)

[Answer]: A — "người dùng vừa có thể là bên đăng tải thông tin bán / mở đấu giá; vừa có thể là người tiếp nhận và tham gia đấu giá của các sản phẩm được đăng tải trên nền tảng. Chọn mục 1"

## Q3. [Sản phẩm] Bản đầu tiên được coi là thành công khi nào? (select all that apply)

Các tiêu chí này sẽ trở thành điều kiện nghiệm thu đo được ở các bước sau.

A. Chạy trọn vẹn một luồng demo: đăng món → admin duyệt → nhiều người trả giá → hết giờ → xác định người thắng và hiển thị liên hệ hai bên
B. Khi nhiều người trả giá cùng lúc, chỉ đúng một lượt hợp lệ được nhận, không bao giờ có hai người cùng "thắng" một mức giá (kiểm chứng bằng test đồng thời)
C. Giá hiện tại và đồng hồ đếm ngược cập nhật trên trình duyệt của mọi người đang xem trong vòng 1 giây sau mỗi lượt trả giá
D. Đạt độ phủ test tự động (line coverage) từ 80% trở lên
E. Not yet defined
X. Other (please specify)

[Answer]: A, B, C

## Q4. [Sản phẩm] Điều gì khiến anh/chị bắt đầu dự án này lúc này?

A. Muốn học / thực hành một công nghệ hoặc quy trình mới (ví dụ thử quy trình phát triển có AI hỗ trợ)
B. Bài tập hoặc đồ án trong một khoá đào tạo
C. Có ý tưởng hoặc cơ hội kinh doanh cụ thể
D. Not identified
X. Other (please specify)

[Answer]: A

## Q5. [Sản phẩm] Ngoài những gì đã chốt, bản đầu tiên KHÔNG làm thêm những tính năng nào? (select all that apply)

Đã chốt là không có: thanh toán online, giá sàn, mua ngay, proxy bid, mobile app, triển khai production. Câu này hỏi thêm các tính năng hay gặp ở sàn đấu giá mà mô tả chưa nhắc tới.

A. Nhắn tin / chat giữa người mua và người bán trong ứng dụng
B. Đánh giá, chấm điểm uy tín người dùng sau giao dịch
C. Gửi thông báo qua email (chỉ thông báo ngay trong ứng dụng)
D. Tìm kiếm, lọc nâng cao theo danh mục và khoảng giá (chỉ có danh sách phiên đang diễn ra)
E. None (không loại thêm tính năng nào, để các bước sau quyết định)
X. Other (please specify)

[Answer]: X — "ở giai đoạn đầu (cần các tính năng đặc thù, cơ bản phải có đối với dự án này), sẽ không làm các tính năng mà bạn đã kể ở trên, ngoài ra các tính năng vẫn có sẽ là: nhắn tin giữa người mua và người bán. đánh giá chấm điểm uy tín của người bán, gửi thông báo thông qua email của người dùng (gửi về cả người mua và người bán khi cuộc đấu giá được chốt), tìm kiếm tên / mã sản phẩm thông qua search bar cơ bản và lọc sản phẩm theo thuộc tính của sản phẩm đó (có thể lọc theo: tầm giá khởi điểm, danh mục của sản phẩm là gì,...), bạn có thể đề xuất thêm"

## Q6. [Các bên liên quan] Những ai liên quan đến dự án và mỗi người quan tâm điều gì?

A. Chỉ một mình anh/chị: vừa là người làm, vừa là người dùng thử, vừa là người duyệt
B. Anh/chị cùng một mentor / giảng viên sẽ xem và đánh giá kết quả
C. Anh/chị cùng một nhóm nhỏ cùng phát triển
D. Not identified
X. Other (please specify)

[Answer]: A

## Q7. [Các bên liên quan] Ai quyết định phạm vi và thứ tự ưu tiên tính năng?

A. Anh/chị tự quyết định hoàn toàn
B. Mentor / giảng viên / khách hàng quyết định, anh/chị góp ý
C. Cả nhóm cùng thống nhất
D. Not yet defined
X. Other (please specify)

[Answer]: A

## Q8. [Các bên liên quan] Có yêu cầu báo cáo tiến độ hay mốc trình bày nào không?

A. None (không cần báo cáo)
B. Có buổi demo / trình bày kết quả vào một mốc cụ thể
C. Báo cáo tiến độ định kỳ (ví dụ hàng tuần) cho mentor hoặc nhóm
D. Not yet defined
X. Other (please specify)

[Answer]: A

## Q9. [Sản phẩm] Anh/chị muốn thêm những tính năng đề xuất nào vào bản đầu tiên? (select all that apply)

Câu hỏi bổ sung cho Q5: anh/chị đã chọn có nhắn tin, đánh giá uy tín người bán, email khi chốt phiên, tìm kiếm và lọc, và mời tôi đề xuất thêm. Đây là các tính năng nhỏ, hay gặp ở sàn đấu giá, khớp với quy mô demo.

A. Theo dõi (watchlist): lưu các phiên quan tâm để xem lại nhanh
B. Thông báo ngay trong ứng dụng khi bị người khác trả giá cao hơn, hoặc khi phiên đang theo dõi sắp kết thúc
C. Lịch sử trả giá công khai của từng phiên (mức giá, thời điểm, tên người trả được che bớt)
D. Báo cáo bài đăng vi phạm gửi tới admin
E. None (không thêm tính năng nào)
X. Other (please specify)

[Answer]: A, B, C — "1, 2 (popup trên phần mềm đồng thời thông báo trên phần mềm đó), 3"

## Consolidated Summary Confirmation

- Mục đích: dự án demo mẫu chạy ở local, chưa cần triển khai, nhưng thể hiện đầy đủ các chức năng cơ bản (Q1).
- Người dùng: cá nhân vừa đăng bán / mở đấu giá, vừa tham gia đấu giá các sản phẩm trên nền tảng; admin duyệt bài đăng (Q2).
- Thành công khi: (1) chạy trọn luồng đăng món → duyệt → nhiều người trả giá → hết giờ → xác định người thắng và hiển thị liên hệ hai bên; (2) trả giá đồng thời chỉ nhận đúng một lượt hợp lệ, không có hai người cùng thắng; (3) giá và đồng hồ đếm ngược cập nhật cho mọi người xem trong vòng 1 giây (Q3).
- Lý do bắt đầu: học / thực hành công nghệ hoặc quy trình mới (Q4).
- Không làm ở bản đầu: các mục đã chốt từ trước (thanh toán online, giá sàn, mua ngay, proxy bid, mobile app, triển khai production) (Q5).
- Có làm ở bản đầu: nhắn tin người mua - người bán; đánh giá, chấm điểm uy tín người bán; email cho cả người mua và người bán khi phiên chốt; tìm kiếm theo tên / mã sản phẩm và lọc theo thuộc tính (khoảng giá khởi điểm, danh mục...) (Q5).
- Thêm theo đề xuất: danh sách theo dõi (watchlist); thông báo trong ứng dụng dạng popup kèm mục thông báo khi bị trả giá vượt hoặc phiên theo dõi sắp kết thúc; lịch sử trả giá công khai của từng phiên (Q9).
- Các bên liên quan: chỉ một mình anh/chị; anh/chị tự quyết phạm vi và ưu tiên; không cần báo cáo tiến độ (Q6, Q7, Q8).

Does this all look correct before I generate the artifact?

- Looks correct
- Request changes

[Answer]: Looks correct
