# Báo cáo trải nghiệm người dùng Chrome

Báo cáo trải nghiệm người dùng Chrome cung cấp chỉ số trải nghiệm người dùng cho cách người dùng Chrome trong thế giới thực trải nghiệm các điểm đến phổ biến trên web.

## Methodology
Báo cáo trải nghiệm người dùng Chrome được hỗ trợ bởi việc đo lường số liệu trải nghiệm người dùng chính trên web công cộng, được tổng hợp từ những người dùng đã chọn tham gia đồng bộ hóa lịch sử duyệt web của họ, chưa thiết lập cụm mật khẩu đồng bộ hóa và đã bật báo cáo thống kê sử dụng. Dữ liệu kết quả được cung cấp qua:

1. PageSpeed Insights, cung cấp chỉ số trải nghiệm người dùng cấp URL cho các URL phổ biến được trình thu thập dữ liệu web của Google biết đến.
2. Dự án Public Google BigQuery  tổng hợp các chỉ số trải nghiệm người dùng theo nguồn gốc, cho tất cả các nguồn gốc được trình thu thập thông tin web của Google biết và chia nhỏ trên nhiều khía cạnh được nêu bên dưới.

## Số liệu
Số liệu cung cấp bởi Báo cáo trải nghiệm người dùng Chrome công khai được lưu trữ trên được lưu trữ trên Google BigQuery Metrics đđược cung cấp bởi các API nền tảng web chuẩn được trình duyệt hiện đại hiển thị và được tổng hợp theo độ phân giải gốc. Chủ sở hữu trang web muốn phân tích chi tiết hơn (phân tích cấp độ URL) và hiểu rõ hơn về hiệu suất trang web của họ và có thể sử dụng cùng một API để thu thập dữ liệu đo lường thực tế chi tiết (RUM) cho nguồn của chính họ.

Lưu ý: Hiện tại, Báo cáo trải nghiệm người dùng Chrome tập trung vào việc tải hiệu suất. Thời gian tới,  chúng tôi hy vọng sẽ thêm nhiều chỉ số và nhiều khía cạnh hơn, cả hai đều cung cấp thông tin chi tiết hơn về tải và các yếu tố quan trọng khác ảnh hưởng nhiều nhất đến trải nghiệm người dùng.

Để được hướng dẫn về số liệu nào cần theo dõi và tối ưu hóa và các phương pháp hay nhất về cách diễn giải dữ liệu đo lường người dùng thực, hãy tham khảo tài liệu hiệu suất tập trung vào người dùng của chúng tôi.

## First Paint
Được định nghĩa bằng Paint Timing API và khả dụng trên Chrome M60+:

“First Paint báo cáo thời gian khi trình duyệt xuất hiện lần đầu tiên sau khi điều hướng. Điều này loại trừ background paint mặc định, nhưng bao gồm background paint không mặc định. Đây là thời điểm quan trọng đầu tiên mà các nhà phát triển quan tâm đến khi tải trang - khi trình duyệt bắt đầu hiển thị trang. "

##  First Contentful Paint
Được định nghĩa bằng Paint Timing API và khả dụng trên Chrome M60+:

“First Contentful Paint báo cáo thời gian khi trình duyệt hiển thị bất kỳ văn bản, hình ảnh nào (bao gồm hình nền), canvas không phải màu trắng hoặc SVG. Điều này bao gồm văn bản với webfonts đang chờ xử lý. Đây là lần đầu tiên người dùng có thể bắt đầu thấy nội dung trang. ”

## DOMContentLoaded
Định nghĩa bởi đặc tả HTML:

“DOMContentLoaded báo cáo thời gian khi tài liệu HTML ban đầu đã được tải và phân tích cú pháp hoàn toàn, mà không cần đợi các stylesheet, hình ảnh và các khung phụ để kết thúc tải.” - MDN.

### onload
Định nghĩa bởi đặc tả HTML:

“ Sự kiện tải được kích hoạt khi trang và các tài nguyên phụ thuộc của nó tải xong." -MDN

##  Những khía cạnh

Hiệu suất của nội dung web có thể thay đổi đáng kể dựa trên loại thiết bị, thuộc tính của mạng và các biến khác. Để giúp phân đoạn và hiểu trải nghiệm người dùng trên các phân đoạn chính như vậy, Báo cáo trải nghiệm người dùng Chrome cung cấp các khía cạnh sau.


##### Loại kết nối hiệu quả
Định nghĩa bởi Network Information API và khả dụng trên Chrome M62+:

“Cung cấp loại kết nối hiệu quả (“chậm-2g”, “2g”, “3g”, “4g” hoặc “ngoại tuyến”) được xác định theo giá trị vòng lặp và băng thông dựa trên các quan sát đo lường thực tế của người dùng thực”

##### Loại thiết bị
Phân loại thiết bị thô (“điện thoại”, “máy tính bảng” hoặc “máy tính để bàn”), được kết nối thông qua User-Agent.

##### Quốc gia
Vị trí địa lý của người dùng ở cấp quốc gia, được suy ra theo địa chỉ IP của họ. Các quốc gia được xác định theo các code ISO 3166-1 alpha-2 tương ứng.

##### Định dạng dữ liệu
Báo cáo được cung cấp qua Google BigQuery dưới dạng tập hợp các tập dữ liệu chứa các chỉ số trải nghiệm người dùng được tổng hợp thành độ phân giải gốc. Mỗi tập dữ liệu đại diện cho một quốc gia, quốc gia nắm bắt dữ liệu trải nghiệm người dùng cho người dùng ở Serbia (rs là mã ISO 31611-1 cho Serbia). Ngoài ra, có một tập dữ liệu tổng hợp toàn cầu (tất cả) thu thập trải nghiệm trên toàn thế giới. Mỗi hàng trong tập dữ liệu chứa bản ghi trải nghiệm người dùng lồng nhau cho một nguồn gốc cụ thể, được chia cho các khía cạnh chính.

Ví dụ, bảng bên trên hiển thị 1 mẫu bản ghi từ báo cáo trải nghiệm người dùng Chrome, chỉ ra rằng 12.3% lượt tải trạng có 1 độ đo "first paint time" nằm trong khoảng 1000-1200 milli giây khi tải "http://example.com" trên thiết bị điện thoại qua kết nối dạng "4g". Để đạt các  các giá trị tổng hợp trải nghiệm người dùng  lần đầu dưới 1200 mili giây, bạn có thể thêm tất cả các bản ghi có giá trị "kết thúc" của biểu đồ nhỏ hơn hoặc bằng 1200.

Lưu ý: Báo cáo trải nghiệm người dùng Chrome không cung cấp giá trị định lượng (ví dụ: trung tuyến). Các giá trị như vậy có thể xấp xỉ từ dữ liệu được cung cấp, nhưng không được báo cáo tiếp xúc trực tiếp.

## Bắt đầu
Báo cáo trải nghiệm người dùng Chrome được cung cấp như 1 dự án công khai trên Google BigQuery. Để truy cập vào dự án, bạn sẽ cần 1 tài khoản Google và dự án google Cloud: tham khảo hướng dẫn từng bước của chúng tôi và hướng dẫn về cách truy vấn dự án.

## Các mẹo khi phân tích và các phương pháp hay nhất
#### Xem xét sự khác biệt về lượng truy cập trên mỗi nguồn
Các số liệu được cung cấp bởi Báo cáo trải nghiệm người dùng Chrome được cung cấp bởi dữ liệu đo lường người dùng thực. Kết quả là, dữ liệu phản ánh cách người dùng thực sự trải nghiệm nguồn trang truy cập và không giống như thử nghiệm tổng hợp hoặc địa phương nơi thử nghiệm được thực hiện trong điều kiện cố định và mô phỏng, nắm bắt đầy đủ các yếu tố bên ngoài hình thành và đóng góp cho trải nghiệm người dùng cuối cùng.
Ví dụ: sự khác biệt về dân số người dùng truy cập nguồn cụ thể có thể đóng góp những khác biệt có ý nghĩa cho trải nghiệm người dùng. Nếu trang web thường xuyên được nhiều khách truy cập hơn với các thiết bị hiện đại hơn hoặc thông qua mạng nhanh hơn, kết quả có thể xuất hiện "nhanh" ngay cả khi trang web không được tối ưu hóa tốt. Ngược lại, một trang web được tối ưu hóa tốt thu hút một lượng người dùng rộng hơn hoặc truy cập có số lượng người dùng lớn hơn trên các thiết bị hoặc mạng chậm hơn, có thể xuất hiện "chậm".

Khi biểu hiện các so sánh trực tiếp giữa các trang nguồn, điều quan trọng là phải thống kê và kiểm soát lưu lượng người dùng khác nhau: phân chia từ những khía cạnh được cung cấp, ví dụ như là loại thiết bị và loại kết nối, cùng với đó cân nhắc những yếu tốt bên ngoài như là lượng kết nối, các quốc gia truy cập vào trang nguồn, vân vân.

### Xem xét sự khác biệt kích thước truy cập giữa các nguồn trang
Báo cáo trải nghiệm người dùng Chrome tổng hợp dữ liệu cho mỗi nguồn gốc, với các giá trị "mật độ" trên tất cả các biểu đồ khía cạnh-chỉ số tổng hợp với giá trị là "1.0". Điều này cung cấp thông tin chi tiết về phân phối trải nghiệm trên các khía cạnh chính cho một nguồn duy nhất.


Tuy nhiên, khi tổng hợp dữ liệu từ nhiều nguồn, ví dụ dọc theo 1 ngành công nghiệp hay 1 vùng địa lý, hãy cẩn thận với các loại tổng kết được vẽ ra: thêm  vào mật độ với cùng chỉ số cho các nguồn trang  không tính toán lưu lượng tương đối khác nhau qua các nguồn.

Ví dụ, trang A có thể có 10 triệu truy cập, trong khi trang B có 10 ngàn. Trong cả 2 trường hợp, biểu đồ mật độ với mỗi trang có tổng là 1, và tập dữ liệu không cung cấp bất kỳ số liệu tuyệt đối nào về kích thước lưu lượng của từng nguồn riêng biệt, hay kích thước lưu lượng tương đối khác nhau giữa các nguồn. Kết quả là, nếu bạn cộng các mật độ từ A và B, và trung bình của các kết quả, bạn sẽ coi chúng là bằng nhau mặc dù A có ba đơn vị lưu lượng truy cập lớn hơn.

### Cân nhắc sự khác biệt về truy cập của Chrome
Báo cáo trải nghiệm người dùng Chrome được hỗ trợ bởi đo lường người dùng thực được tổng hợp từ những người dùng Chrome đã chọn tham gia đồng bộ hóa lịch sử duyệt web của họ, chưa thiết lập cụm mật khẩu đồng bộ hóa và đã bật báo cáo thống kê sử dụng. Dân số này có thể không đại diện cho cơ sở người dùng rộng hơn cho một nguồn gốc cụ thể và nhiều nguồn gốc có thể có sự khác biệt về truy cập khác nhau. Hơn nữa, dữ liệu này không tính đến người dùng có trình duyệt khác nhau và sự khác biệt trong việc chấp nhận trình duyệt ở các khu vực địa lý khác nhau.

Do đó, hãy cẩn thận với các loại kết luận được rút ra khi nhìn vào mặt cắt ngang của nguồn và khi so sánh nguồn cá nhân: tránh sử dụng so sánh tuyệt đối và xem xét các yếu tố truy cập khác được nêu trong các phần ở trên.

## Phản hồi và đề xuất

Chúng tôi muốn nghe phản hồi, câu hỏi và đề xuất của bạn để giúp chúng tôi cải thiện Báo cáo trải nghiệm người dùng Chrome. Vui lòng tham gia cuộc trò chuyện trên Nhóm Google công khai của chúng tôi.
