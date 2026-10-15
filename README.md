Sửa lỗi:
 - Vì điều kiện sub.daysOverdue >= 3 nghĩa là số ngày nợ lớn hơn hoặc bằng 3, khiến hệ thống hạ thuê bao ngay từ ngày t3 trong khi khách hàng vẫn còn ngày âm hạn
 --> Thay điều kiện sub.daysOverdue >= 3 thành sub.daysOverdue > 3. Khi KH nợ từ 1 đến 3 ngày, trạng thái sẽ là GRACE_PERIOD và vẫn giữ nguyên gói thuê bao. Nếu nợ từ ngày thứ 4 trở đi, hệ thống sẽ chuyển gói thành FREE, giảm giới hạn thiết bị xuống 1 và cập nhật trạng thái EXPIRED.

Kiểm thử:
1. Khách hàng nợ 3 ngày (daysOverdue: 3). Chương trình cũ hạ cấp xuống FREE, giới hạn 1 thiết bị và chuyển trạng thái EXPIRED. Kết quả đúng là giữ gói FAMILY, 5 thiết bị và trạng thái GRACE_PERIOD.
2. Khách hàng nợ 4 ngày (daysOverdue: 4). Chương trình cũ chuyển sang FREE, giới hạn 1 thiết bị và trạng thái EXPIRED. Đây cũng là kết quả đúng mong đợi.