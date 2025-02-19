# CDN

## CDN là gì?
- CDN (Content Delivery Network) là một mạng lưới các máy chủ phân tán trên toàn cầu, được thiết kế để phân phối nội dung trực tuyến nhanh hơn, hiệu quả hơn và đáng tin cậy hơn. CDN hoạt động bằng cách lưu trữ (cache) nội dung tĩnh, như hình ảnh, video, CSS, JavaScript và tài liệu, trên các máy chủ gần người dùng cuối.
- Các bạn có thể hiểu một cách nôm na như sau, các content dạng tĩnh (static) trên website của bạn sẽ được lưu trữ thêm dưới dạng cache ở các server gần vị trí hiện tại của người xem. Server của bạn có thể host ở Việt Nam, tuy nhiên nếu dùng CDN, người dùng ở Mỹ khi truy cập vào website của bạn sẽ load ảnh ở các server CDN ở mỹ thay vì load từ server host ở Việt Nam.

## Cách hoạt động của CDN
1. **Lưu trữ nội dung tại các máy chủ biên (edge servers)**: Khi nội dung được lưu trữ trên các máy chủ gần vị trí địa lý của người dùng, thời gian truyền tải (latency) sẽ giảm đáng kể.
2. **Chuyển hướng người dùng**: Khi người dùng yêu cầu nội dung từ một trang web, CDN sẽ tự động chuyển hướng yêu cầu đó đến máy chủ gần nhất có nội dung được lưu trữ.
3. **Phân phối tải**: CDN phân phối tải truy cập giữa nhiều máy chủ, giúp giảm áp lực lên máy chủ gốc (origin server).

## Tác dụng của CDN
1. **Tăng tốc độ tải trang**: CDN giảm độ trễ bằng cách phục vụ nội dung từ máy chủ gần người dùng nhất. Nội dung tĩnh được tải nhanh hơn, cải thiện trải nghiệm người dùng.
2. **Giảm tải cho máy chủ gốc**: CDN giảm số lượng yêu cầu trực tiếp đến máy chủ gốc, giúp giảm tải và tiết kiệm tài nguyên.
3. **Cải thiện khả năng mở rộng**: Với mạng lưới máy chủ toàn cầu, CDN có thể xử lý lưu lượng lớn từ nhiều người dùng mà không bị quá tải.
4. **Tăng độ tin cậy và giảm thời gian chết**: Nếu một máy chủ CDN gặp sự cố, yêu cầu sẽ được tự động chuyển sang máy chủ khác trong mạng lưới.
5. **Bảo mật tốt hơn**: CDN cung cấp các dịch vụ như bảo vệ DDoS, tường lửa ứng dụng web (WAF), và mã hóa SSL để bảo vệ nội dung và người dùng.
6. **Cải thiện SEO và tối ưu hóa hiệu suất**: Tốc độ tải trang nhanh hơn giúp tăng điểm SEO và giảm tỷ lệ thoát trang.

## Ví dụ về CDN
- **Cloudflare**: Một trong những nhà cung cấp CDN phổ biến với các dịch vụ bảo mật tích hợp.
- **AWS CloudFront**: Dịch vụ CDN của Amazon Web Services.
- **Akamai**: Một trong những CDN lớn nhất và lâu đời nhất trên thế giới.
- **Google Cloud CDN**: Giải pháp CDN từ Google.

**Note**: Nếu bạn nào muốn trải nghiệm CDN, các bạn có thể thử nó ngay với Cloudflare, hoàn toàn miễn phí và tác dụng mang lại cực kỳ hiệu quả. Các bạn sẽ tiết kiệm được một lượng bandwidth đáng kể và đồng thời cải thiện tốc độ website.