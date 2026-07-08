---
title: "Event 1"
date: 2026-05-23
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# Bài thu hoạch “FCAJ Community Day”

### Thông tin sự kiện

- **Tên sự kiện:** FCAJ Community Day
- **Thời gian:** 09:00 AM - 12:00 PM, ngày 23/05/2026
- **Địa điểm:** Floor 26, Bitexco Financial Tower
- **Vai trò trong sự kiện:** Người tham dự

### Mục Đích Của Sự Kiện

- Tạo cơ hội giao lưu, kết nối giữa các thành viên trong cộng đồng First Cloud AI Journey.
- Chia sẻ kiến thức thực tế về AWS, Generative AI, Amazon CloudFront, hệ thống multi-agent và các ứng dụng AI trong doanh nghiệp.
- Giúp người tham dự hiểu thêm cách các công nghệ AWS được áp dụng trong những bài toán thực tế.
- Truyền cảm hứng cho sinh viên và người mới bắt đầu xây dựng project cá nhân, tham gia hackathon và phát triển kỹ năng cloud/AI.
- Cung cấp góc nhìn thực tế từ các speaker đang làm việc trong lĩnh vực cloud, DevOps, AI, platform engineering và business systems.

### Danh Sách Diễn Giả

- **Tinh Truong** - Platform Engineer, GoTymeX
- **Pham Ng Hai Anh** - G-AsiaPacific Vietnam, AWS Community Builder
- **Nguyen Tuan Thinh** - DevOps Engineer, First Cloud AI Journey
- **Duc Dao** - Solution Architect, Cloud Kinetics
- **Vy Lam** - Senior Business Systems Analyst, VPBank
- **Team UTMorpho** - Chia sẻ hành trình xây dựng sản phẩm tại LotusHacks 2026

### Nội Dung Nổi Bật

#### Context Is Everything - GenAIOps Essential

Phần chia sẻ này tập trung vào vai trò của context khi làm việc với AI. Speaker nhấn mạnh rằng AI model hiện nay đã rất mạnh, nhưng kết quả đầu ra thường chưa tốt khi người dùng cung cấp context chưa đủ, chưa đúng hoặc chưa rõ mục tiêu.

Nội dung giúp em hiểu rằng một prompt hiệu quả cần có mục tiêu, tình huống, ràng buộc, thông tin liên quan và tiêu chí đánh giá kết quả. Nếu thiếu các yếu tố này, AI dễ trả lời chung chung, sai hướng hoặc bỏ sót yêu cầu quan trọng.

Bài chia sẻ cũng đề cập đến sự phát triển từ Prompt, Context đến Memory, cho thấy cách sử dụng AI đang dần chuyển từ hỏi đáp đơn lẻ sang các hệ thống có khả năng lưu trữ, truy xuất và sử dụng ngữ cảnh phù hợp theo thời gian.

#### Automate Any Business Process Using Amazon Quick Suite

Phần chia sẻ về Amazon Quick Suite tập trung vào bài toán tự động hóa quy trình nghiệp vụ trong doanh nghiệp. Speaker đưa ra vấn đề thực tế là business users thường phải thu thập, phân tích thông tin từ nhiều nguồn khác nhau và lặp lại nhiều tác vụ thủ công tốn thời gian.

Amazon Quick Suite được giới thiệu như một nền tảng hỗ trợ agentic AI, có khả năng kết nối dữ liệu doanh nghiệp, dữ liệu người dùng upload, database, data warehouse, web search và các ứng dụng bên thứ ba. Từ đó, hệ thống có thể hỗ trợ các tác vụ như chat, research, BI dashboard, automation flow và insight generation.

Một use case nổi bật là PM assistant, có thể tự động tạo meeting minutes, gửi email cho stakeholders và lên lịch cuộc họp tiếp theo. Qua phần này, em thấy rõ AI trong doanh nghiệp không chỉ là chatbot trả lời câu hỏi, mà có thể trở thành một assistant hỗ trợ vận hành và tự động hóa công việc thực tế.

#### CloudFront as Your Foundation

Phần chia sẻ về Amazon CloudFront giúp em có góc nhìn rộng hơn về dịch vụ CDN của AWS. Trước đây, em thường hiểu CloudFront chủ yếu là dịch vụ cache và phân phối nội dung, nhưng trong bài trình bày này, CloudFront được nhìn nhận như một lớp nền tảng cho cost optimization, security, resiliency và performance.

Speaker phân tích các thách thức khi sử dụng mô hình pay-as-you-go, đặc biệt trong trường hợp traffic tăng đột biến, nội dung trở nên viral hoặc ứng dụng bị tấn công DDoS. Từ đó, bài chia sẻ giới thiệu mô hình flat-rate pricing giúp chi phí CDN dễ dự đoán hơn.

Ngoài bài toán chi phí, CloudFront còn được trình bày ở nhiều khía cạnh khác như AWS Global Edge Network, AWS WAF, AWS Shield, DDoS mitigation, HTTPS/TLS, Mutual TLS, Origin Access Control, Signed URL, geographic restriction, origin failover, HTTP/3, compression và xử lý logic tại edge bằng CloudFront Function hoặc Lambda@Edge.

#### UTMorpho - Building from Idea to Reality

Phần chia sẻ về UTMorpho kể lại hành trình xây dựng sản phẩm tại LotusHacks 2026. Team bắt đầu từ việc chưa có ý tưởng rõ ràng, brainstorm nhiều hướng khác nhau, sau đó tìm ra vấn đề từ chính trải nghiệm làm việc hằng ngày.

UTMorpho xuất phát từ hạn chế của các AI UI generator: có thể tạo giao diện từ prompt, nhưng khi muốn chỉnh sửa chi tiết như màu sắc, spacing, text hoặc layout thì thường phải re-prompt, dẫn đến kết quả bị thay đổi ngoài ý muốn. Từ vấn đề đó, team xây dựng một agent có thể generate UI và cho phép chỉnh sửa trực tiếp trên canvas theo hướng WYSIWYG.

Qua câu chuyện này, em học được cách một ý tưởng sản phẩm có thể bắt đầu từ một pain point rất thật. Ngoài ra, phần chia sẻ cũng cho thấy khi build sản phẩm trong thời gian ngắn, team cần biết chia task, tập trung vào demo path, cắt bớt feature không cần thiết và kiểm soát token usage như một ràng buộc thiết kế.

#### Non-Determinism of “Deterministic” LLM Settings

Phần chia sẻ này giúp em hiểu sâu hơn về cách LLM sinh output. Speaker giải thích rằng LLM tạo văn bản theo từng token, mỗi bước model sinh ra logit, chuyển thành xác suất bằng softmax rồi chọn token tiếp theo.

Một điểm rất đáng chú ý là many người thường nghĩ temperature = 0 sẽ giúp output luôn giống nhau tuyệt đối. Tuy nhiên, bài trình bày cho thấy trong thực tế, output của LLM vẫn có thể khác nhau dù prompt, seed và setting giống nhau.

Nguyên nhân đến từ nhiều yếu tố như floating-point arithmetic trên GPU, thứ tự tính toán song song và inference batching trên các managed endpoint. Điều này đặc biệt quan trọng với các hệ thống production hoặc các lĩnh vực nhạy cảm như y tế, pháp lý, tài chính, nơi output cần độ ổn định và khả năng kiểm thử cao.

#### Enterprise-Grade Multi-Agent System

Phần chia sẻ cuối cùng nói về Enterprise-Grade Multi-Agent System thông qua case study chấm điểm tín dụng cho startup. Speaker chỉ ra rằng hệ thống credit scoring truyền thống thường phù hợp với doanh nghiệp đã hoạt động ổn định, nhưng lại gặp khó khi đánh giá startup vì startup có dữ liệu ngắn hạn, ít lịch sử tín dụng, tài sản phi truyền thống và nhiều dữ liệu phi cấu trúc.

Bài trình bày phân biệt khi nào nên dùng single-agent và khi nào nên dùng multi-agent. Với các bài toán nhiều domain, nhiều ràng buộc, cần audit và có độ rủi ro cao, multi-agent sẽ phù hợp hơn vì mỗi agent có thể đảm nhiệm một vai trò chuyên biệt như Financial Analyst, Market Analyst, Team Evaluator, Risk Assessor hoặc Compliance.

Nội dung này cũng nhấn mạnh rằng hệ thống AI cấp doanh nghiệp không chỉ cần chạy được demo, mà cần có bảo mật, data governance, network isolation, monitoring, incident response, compliance, guardrails và roadmap triển khai rõ ràng.

### Những Gì Học Được

#### Kiến thức về AI và cách sử dụng AI hiệu quả

- Hiểu rõ hơn vai trò của context khi làm việc với AI.
- Biết rằng kết quả AI phụ thuộc nhiều vào mục tiêu, ràng buộc, dữ liệu liên quan và tiêu chí đầu ra mà người dùng cung cấp.
- Nhận ra rằng không nên đưa quá nhiều tài liệu không liên quan vào AI, vì context nhiều nhưng nhiễu có thể làm giảm chất lượng output.
- Nắm được sự phát triển từ prompt đơn lẻ sang context system và memory trong các ứng dụng AI hiện đại.
- Biết thêm một số ý tưởng project phù hợp với sinh viên như AI Study Assistant, PDF Chat App, AI Code Reviewer và Personal Second Brain.

#### Kiến thức về AWS và kiến trúc cloud

- Hiểu rõ hơn vai trò của Amazon CloudFront trong kiến trúc ứng dụng hiện đại.
- Nhận ra CloudFront không chỉ là CDN mà còn hỗ trợ tối ưu chi phí, tăng bảo mật, cải thiện hiệu năng và nâng cao độ tin cậy.
- Biết thêm các cơ chế bảo mật như AWS WAF, AWS Shield, Signed URL, Origin Access Control, Mutual TLS và geographic restriction.
- Hiểu cách CloudFront giảm tải cho origin bằng caching, request collapsing, compression và persistent connection.
- Có thêm góc nhìn về việc thiết kế hệ thống chịu tải tốt hơn thông qua edge network, failover và custom error handling.

#### Kiến thức về automation và ứng dụng AI trong doanh nghiệp

- Hiểu thêm cách agentic AI có thể hỗ trợ tự động hóa quy trình nghiệp vụ.
- Biết được Amazon Quick Suite có thể kết nối nhiều nguồn dữ liệu và hỗ trợ người dùng doanh nghiệp trong các tác vụ như research, dashboard, automation flow và insight generation.
- Nhận ra AI trong doanh nghiệp không chỉ dừng ở việc trả lời câu hỏi, mà còn có thể thực hiện hành động và hỗ trợ vận hành quy trình làm việc.
- Có thêm ví dụ thực tế về PM assistant có thể tạo meeting minutes, gửi email và lên lịch cuộc họp.

#### Kiến thức về LLM trong production

- Hiểu cách LLM chọn token tiếp theo thông qua logit, softmax và temperature.
- Nhận ra rằng temperature = 0 không đảm bảo output luôn deterministic tuyệt đối.
- Biết một số nguyên nhân gây non-determinism như floating-point arithmetic, GPU parallelism và inference batching.
- Hiểu rằng khi xây dựng ứng dụng AI production, cần thiết kế hệ thống chấp nhận variance và có cơ chế kiểm thử kỹ.
- Biết thêm các hướng giảm rủi ro như majority voting, structured output, constrained output và testing lặp lại.

#### Kiến thức về multi-agent system

- Phân biệt được khi nào nên sử dụng single-agent và khi nào nên sử dụng multi-agent.
- Hiểu rằng multi-agent phù hợp với các bài toán nhiều domain, nhiều tiêu chí đánh giá và cần audit trail.
- Biết cách một hệ thống multi-agent có thể mô phỏng virtual credit committee với nhiều agent chuyên biệt.
- Nhận ra tầm quan trọng của guardrails, compliance, security, observability và operations khi đưa AI vào môi trường enterprise.
- Có thêm góc nhìn về việc dùng các AWS building blocks như Bedrock, ECR, API Gateway, IAM, Secrets Manager, CloudWatch và X-Ray trong triển khai hệ thống AI production-ready.

#### Bài học về tư duy sản phẩm và làm việc nhóm

- Hiểu rằng ý tưởng sản phẩm tốt có thể bắt đầu từ chính pain point thật trong công việc.
- Biết thêm cách một team hackathon xây dựng MVP trong thời gian ngắn bằng cách tập trung vào demo path và cắt bớt feature không cần thiết.
- Nhận ra token usage trong sản phẩm AI không chỉ là vấn đề chi phí mà còn ảnh hưởng đến thiết kế UX.
- Học được rằng team chemistry, khả năng chia việc và ra quyết định nhanh rất quan trọng khi build sản phẩm trong thời gian giới hạn.
- Có thêm động lực để tham gia các hoạt động cộng đồng, workshop hoặc hackathon nhằm học hỏi kinh nghiệm thực tế từ người đi trước.

### Ứng Dụng Vào Công Việc Và Học Tập

- Áp dụng cách chuẩn bị context rõ ràng hơn khi sử dụng AI trong học tập, viết báo cáo, debug code hoặc xây dựng project.
- Khi làm việc với AI, cần xác định trước mục tiêu, ràng buộc, dữ liệu liên quan và format đầu ra mong muốn.
- Khi thiết kế backend hoặc cloud architecture, cần quan tâm không chỉ đến việc hệ thống chạy được mà còn đến chi phí, bảo mật, hiệu năng và khả năng mở rộng.
- Có thể áp dụng kiến thức về CloudFront khi triển khai static website, API hoặc các ứng dụng cần tối ưu tốc độ truy cập.
- Có thể tham khảo mô hình AI assistant hoặc second brain để xây dựng project cá nhân phục vụ việc học.
- Khi xây dựng ứng dụng AI, cần có cơ chế kiểm thử, logging, guardrails và xử lý output không ổn định.
- Có thể áp dụng tư duy multi-agent cho các bài toán phức tạp cần nhiều góc nhìn hoặc nhiều vai trò xử lý khác nhau.
- Có thêm định hướng chọn đề tài project cuối kỳ liên quan đến AI assistant, cloud architecture, serverless application hoặc data/automation workflow.

### Trải nghiệm trong event

Tham gia **FCAJ Community Day** là một trải nghiệm rất bổ ích đối với em. Sự kiện không chỉ giúp em cập nhật thêm kiến thức về AWS và AI, mà còn giúp em có cơ hội lắng nghe các chia sẻ thực tế từ những anh/chị đang làm việc trong lĩnh vực cloud, DevOps, AI và enterprise system.

Điểm em ấn tượng nhất là các nội dung trong event không chỉ dừng lại ở lý thuyết, mà đều gắn với các vấn đề thực tế: làm sao dùng AI hiệu quả hơn, làm sao tối ưu CloudFront, làm sao xây dựng sản phẩm trong hackathon, làm sao hiểu đúng về LLM trong production và làm sao thiết kế hệ thống AI đạt chuẩn doanh nghiệp.

Thông qua các phần chia sẻ, em nhận ra rằng để làm tốt trong lĩnh vực cloud và AI, người học không chỉ cần biết sử dụng dịch vụ, mà còn cần tư duy hệ thống, khả năng đặt câu hỏi đúng, hiểu business problem, quan tâm đến bảo mật, chi phí, vận hành và khả năng mở rộng.

Sự kiện cũng giúp em có thêm động lực tiếp tục học AWS, tham gia cộng đồng và xây dựng project cá nhân có tính thực tế hơn. Đây là một hoạt động có giá trị trong quá trình thực tập vì giúp em kết nối kiến thức đã học trong các module với các tình huống ứng dụng thực tế.

#### Một số hình ảnh khi tham gia sự kiện

* Thêm các hình ảnh của em tại sự kiện vào phần này.

> Tổng thể, FCAJ Community Day giúp em mở rộng góc nhìn về AWS, Generative AI và cách các công nghệ cloud được ứng dụng trong thực tế. Sự kiện mang lại nhiều kiến thức hữu ích, đồng thời giúp em có thêm định hướng cho việc học tập, viết blog và phát triển project cuối kỳ.
