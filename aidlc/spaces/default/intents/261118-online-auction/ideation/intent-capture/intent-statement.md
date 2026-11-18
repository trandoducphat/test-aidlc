# Intent Statement — Nền tảng đấu giá online cơ bản

## Problem Statement

Cần một nền tảng web nơi người dùng đăng một món đồ bất kỳ lên đấu giá trong một khoảng thời gian đếm ngược cố định; khi hết giờ, món đồ thuộc về người trả giá cao nhất cuối cùng. [desc]

Sản phẩm là một bản demo mẫu chạy ở máy local, chưa cần triển khai, nhưng phải thể hiện đầy đủ các chức năng cơ bản của một sàn đấu giá. [Q1]

## Target Customer

- Người dùng cá nhân đóng hai vai trò: đăng thông tin bán và mở phiên đấu giá, đồng thời tham gia trả giá cho các sản phẩm người khác đăng trên nền tảng. [Q2]
- Admin của nền tảng duyệt bài đăng trước khi bài được hiển thị công khai. [Q2] [desc]
- Lợi ích cho người dùng: mua bán qua hình thức đấu giá minh bạch, ai trả cao nhất khi hết giờ thì thắng, và sau đó hai bên nhận được thông tin liên hệ của nhau để tự giao dịch. [desc]

## Success Metrics

Bản đầu tiên được coi là thành công khi đạt cả ba tiêu chí sau: [Q3]

| # | Tiêu chí | Cách kiểm chứng | Source |
|---|----------|-----------------|--------|
| SM1 | Chạy trọn vẹn một luồng demo: đăng món → admin duyệt → nhiều người trả giá → hết giờ → xác định người thắng và hiển thị liên hệ hai bên | Chạy luồng demo từ đầu đến cuối trên môi trường local, mọi bước hoàn tất không cần thao tác thủ công ngoài ứng dụng | [Q3] [desc] |
| SM2 | Khi nhiều người trả giá cùng lúc, chỉ đúng một lượt hợp lệ được nhận và không bao giờ có hai người cùng thắng một mức giá | Test tự động gửi đồng thời nhiều lượt trả giá cho cùng một phiên; kết quả có đúng 1 lượt được chấp nhận ở mỗi mức giá | [Q3] |
| SM3 | Giá hiện tại và đồng hồ đếm ngược cập nhật trên trình duyệt của mọi người đang xem trong vòng 1 giây sau mỗi lượt trả giá | Mở cùng một phiên trên nhiều trình duyệt, đo thời gian từ lúc lượt trả giá được chấp nhận đến lúc các trình duyệt khác hiển thị giá mới: ≤ 1 giây | [Q3] |

## Initiative Trigger

Anh/chị muốn học và thực hành một công nghệ hoặc quy trình phát triển mới thông qua việc xây dựng sản phẩm này. [Q4]

## Initial Scope Signal

- Workflow-selected scope: `mvp` (workflow-selected). [scope]

### Phạm vi sản phẩm đã xác nhận cho bản đầu tiên

- Đấu giá có đồng hồ đếm ngược; khi hết giờ người trả giá cao nhất cuối cùng thắng. [desc]
- Mọi user đã đăng ký được đăng món, nhưng admin phải duyệt trước khi hiện. [desc]
- Bước giá tính theo phần trăm giá hiện tại, có mức cơ bản ban đầu và cơ chế làm tròn, mệnh giá nhỏ nhất là 50.000đ. [desc]
- Chống trả giá phút chót: lượt trả giá trong những giây cuối sẽ gia hạn phiên, có giới hạn tổng thời gian hoặc số lần gia hạn. [desc]
- Chỉ trả giá thủ công. [desc]
- Sau khi chốt, hệ thống xác định người thắng, hiển thị liên hệ hai bên và trạng thái "đã giao dịch". [desc]
- Nhắn tin giữa người mua và người bán. [Q5]
- Đánh giá, chấm điểm uy tín của người bán. [Q5]
- Gửi email cho cả người mua và người bán khi phiên đấu giá được chốt. [Q5]
- Tìm kiếm theo tên hoặc mã sản phẩm qua thanh tìm kiếm cơ bản, và lọc theo thuộc tính sản phẩm như khoảng giá khởi điểm, danh mục. [Q5]
- Danh sách theo dõi (watchlist) các phiên quan tâm. [Q9]
- Thông báo trong ứng dụng (popup và mục thông báo) khi bị người khác trả giá cao hơn hoặc khi phiên đang theo dõi sắp kết thúc. [Q9]
- Lịch sử trả giá công khai của từng phiên (mức giá, thời điểm, tên người trả được che bớt). [Q9]
- Chỉ là ứng dụng web, chạy local hoặc demo, quy mô dưới 100 người dùng online cùng lúc. [desc]

### Ngoài phạm vi bản đầu tiên

- Thanh toán online (hai bên tự giao dịch sau khi có thông tin liên hệ). [desc] [Q5]
- Giá sàn (reserve price) và mua ngay (buy-now). [desc] [Q5]
- Đặt giá tự động (proxy bid). [desc] [Q5]
- Ứng dụng mobile. [desc] [Q5]
- Triển khai lên môi trường production. [desc] [Q1] [Q5]

## Assumptions & Open Questions

None.
