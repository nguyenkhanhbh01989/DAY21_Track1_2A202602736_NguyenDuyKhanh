# Lab 21 — Phân tích rủi ro AI qua case study thực tế
- Họ và tên: Nguyễn Duy Khánh
- MSSV / mã học viên: 2A202602736
- Lớp: Track 1 (AI Thực Chiến)
- Ngành đã chọn: HR / Tuyển dụng (Tuyển dụng và Quản lý Nguồn nhân lực)

---

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| **Những tác hại chính có thể xảy ra** | **Tước đoạt cơ hội việc làm và thu nhập (Opportunity Loss & Economic Harm):** Ứng viên bị thuật toán tự động từ chối hoặc hạ điểm hồ sơ một cách bất công mà không rõ lý do.<br>**Phân biệt đối xử mang tính hệ thống (Systemic Discrimination):** AI kế thừa hoặc vô tình học các định kiến xã hội, tạo ra sự bất bình đẳng dựa trên các đặc tính được pháp luật bảo vệ như giới tính, tuổi tác, chủng tộc, tình trạng khuyết tật.<br>**Tổn hại phẩm giá (Dignity Loss):** Con người bị đối xử như những tập dữ liệu vô cảm, không có cơ hội thể hiện năng lực thực tế hoặc bị tước quyền giải trình khi bị loại bỏ.<br>**Rủi ro pháp lý & danh tiếng doanh nghiệp:** Nhà tuyển dụng và nhà cung cấp phần mềm đối mặt với các vụ kiện tập thể, án phạt từ cơ quan quản lý lao động (như EEOC) và khủng hoảng truyền thông. |
| **Mức độ high-stakes** | **Cao (High):** Quyết định tuyển dụng ảnh hưởng trực tiếp đến sinh kế, mức sống, sự thăng tiến sự nghiệp và an sinh xã hội của cá nhân và gia đình họ. Việc một thuật toán AI đưa ra quyết định sai lệch ở giai đoạn lọc hồ sơ có thể tước đi cơ hội tiếp cận thị trường lao động của hàng trăm đến hàng nghìn người trong tích tắc mà nạn nhân hoàn toàn không hay biết. |
| **Dữ liệu nhạy cảm có thể được sử dụng** | **Thông tin định danh & nhân khẩu học:** Họ tên, giới tính, ngày tháng năm sinh/tuổi tác, chủng tộc/quốc tịch, tình trạng hôn nhân, địa chỉ cư trú.<br>**Dữ liệu hồ sơ năng lực & đời tư:** Lịch sử công tác, mức lương quá khứ, các trường đại học/tổ chức tham gia (dễ làm lộ giới tính, tôn giáo hoặc nguồn gốc xuất thân), tình trạng sức khỏe/khuyết tật.<br>**Dữ liệu sinh trắc học/hành vi (nếu có phỏng vấn AI):** Giọng nói, biểu cảm khuôn mặt, chuyển động ánh mắt, phong cách giao tiếp. *(Lưu ý: Báo cáo chỉ nêu loại dữ liệu phục vụ phân tích, không sử dụng dữ liệu thật của cá nhân).* |
| **Nhu cầu human review** | **Cao (High):** Bắt buộc phải có cơ chế Human-in-the-loop (chuyên viên nhân sự có chuyên môn) can thiệp ở các khâu trọng yếu, đặc biệt là **trước khi đưa ra quyết định từ chối/loại bỏ ứng viên (rejection)** hoặc khi chốt danh sách ứng viên rút gọn (shortlist). Không bao giờ được để hệ thống AI tự động hóa hoàn toàn việc sa thải hoặc từ chối mà không có sự kiểm tra, phê duyệt của con người và kênh tiếp nhận khiếu nại minh bạch cho ứng viên. |

---

### 2. Case study 1 — Amazon AI Recruiting Tool (Thiên vị giới tính trong sàng lọc CV)

#### Brief Case
- **Tổ chức / sản phẩm AI:** Amazon.com, Inc. — Dự án công cụ sàng lọc và chấm điểm hồ sơ ứng viên tự động bằng máy học (Machine Learning recruiting tool), phát triển bởi đội ngũ kỹ sư tại Edinburgh (Scotland).
- **Thời gian, địa điểm / bối cảnh:** Năm 2014 – 2017/2018; Seattle, Hoa Kỳ & Edinburgh, Scotland. Amazon mong muốn xây dựng một công cụ tự động hóa quy trình tuyển dụng kỹ sư phần mềm, biến việc tìm kiếm nhân tài hàng đầu thành quy trình nhanh chóng và hiệu quả.
- **AI được dùng để làm gì:** Tự động rà soát hàng nghìn hồ sơ ứng tuyển nộp vào Amazon, phân tích kỹ năng và xếp hạng ứng viên theo thang điểm từ 1 đến 5 sao (tương tự cách khách hàng chấm điểm sản phẩm trên sàn thương mại điện tử Amazon) để đề xuất những ứng viên sáng giá nhất cho người tuyển dụng.
- **Vấn đề hoặc sự kiện đáng chú ý:** Đến năm 2015, Amazon nhận thấy hệ thống không đánh giá ứng viên một cách trung lập về giới tính mà có xu hướng thiên vị nam giới và hạ điểm các ứng viên nữ. Nguyên nhân cốt lõi là dữ liệu huấn luyện được lấy từ các hồ sơ nộp vào Amazon trong vòng 10 năm trước đó — giai đoạn mà ngành công nghệ do nam giới áp đảo. Mô hình đã tự khái quát hóa rằng ứng viên nam là tiêu chuẩn ưu tiên và tự động hạ điểm các hồ sơ có từ khóa chứa từ "women's" (ví dụ: *"women's chess club captain"*) hoặc tên của các trường đại học chỉ dành cho nữ sinh. Dù các kỹ sư đã cố gắng tinh chỉnh để loại bỏ từ khóa nhạy cảm, họ nhận thấy AI vẫn có thể gián tiếp học được các biến đại diện (proxy variables) khác. Năm 2017, Amazon chính thức giải tán nhóm phát triển và khai tử dự án.
- **Số liệu có nguồn:**
  - Mô hình được huấn luyện trên tập dữ liệu hồ sơ ứng tuyển tích lũy trong **10 năm**.
  - Đội ngũ đã thử nghiệm khoảng **500 mô hình máy học** tập trung vào các chức danh và yêu cầu công việc cụ thể.
  - Hệ thống chấm điểm hồ sơ theo thang đo **1 đến 5 sao**.
  - Dự án bắt đầu năm **2014**, phát hiện thiên vị giới tính năm **2015**, và chính thức bị giải tán vào năm **2017** trước khi đưa vào vận hành diện rộng.
- **Nguồn:**
  - Báo cáo điều tra độc quyền của Reuters: Jeffrey Dastin, *"Amazon scraps secret AI recruiting tool that showed bias against women"*, Reuters, ngày 10/10/2018. URL: `https://www.reuters.com/article/world/insight-amazon-scraps-secret-ai-recruiting-tool-that-showed-bias-against-women-idUSKCN1MK08G/`
  - Báo cáo nghiên cứu của Viện Nghiên cứu Khoa học Xã hội (SSRC): *"Amazon’s AI Recruiting Tool: When Algorithms Learn Bias"*, Just Tech Platform, 2019.
- **Phân biệt bằng chứng và nhận định:**
  - *Điều nguồn xác nhận (Bằng chứng):* Reuters xác nhận dự án sử dụng dữ liệu 10 năm của Amazon, chia thành 500 mô hình máy học chấm điểm 1–5 sao, hệ thống thực tế đã phạt điểm các từ ngữ liên quan đến phụ nữ, và ban lãnh đạo Amazon đã quyết định giải tán đội ngũ vào năm 2017. Amazon khẳng định công cụ này chưa từng được sử dụng độc lập để đưa ra quyết định tuyển dụng chính thức.
  - *Điều tôi suy luận / Nhận định:* Nếu hệ thống này được triển khai độc lập trên thực tế mà không có kiểm toán thuật toán, nó sẽ gây ra sự loại trừ mang tính hệ thống đối với lao động nữ trong ngành công nghệ, làm trầm trọng thêm khoảng cách bất bình đẳng giới vốn đã tồn tại lâu năm tại Thung lũng Silicon.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| **High-risk moment** | Thời điểm hệ thống phân tích văn bản (NLP/text extraction) trên CV của ứng viên và gán điểm xếp hạng 1–5 sao để quyết định ứng viên nào được chuyển tiếp cho HR. |
| **Stakeholder bị ảnh hưởng** | Các ứng viên nữ nộp hồ sơ vào các vị trí kỹ thuật tại Amazon; bộ phận tuyển dụng của Amazon; cộng đồng phụ nữ làm việc trong lĩnh vực khoa học công nghệ (STEM). |
| **Failure mode** | **Bias / fairness:** Thiên lệch dữ liệu lịch sử (Historical bias) và thiên lệch biểu diễn (Representation bias) dẫn đến kết quả phân biệt giới tính. |
| **Layer bắt đầu lỗi** | **Grounding & Model (Data Layer):** Dữ liệu huấn luyện 10 năm phản ánh thực trạng áp đảo của nam giới trong ngành công nghệ. Mô hình học mối tương quan giả (spurious correlation) rằng từ ngữ chỉ nam giới tương đương với năng lực vượt trội. |
| **Harm xảy ra là gì?** | **Nguy cơ tước đoạt cơ hội việc làm (Potential Opportunity Loss):** Ứng viên nữ có nguy cơ bị loại bỏ ngay từ vòng duyệt hồ sơ chỉ vì các từ ngữ phản ánh giới tính trên CV. Thực tế đã gây tổn hại danh tiếng (Reputational harm) cho Amazon khi thông tin bị rò rỉ. |
| **Harm lens** | **Opportunity loss** (tước đoạt cơ hội cạnh tranh công bằng) và **Dignity loss** (tổn hại phẩm giá khi hồ sơ bị đánh giá thấp vì giới tính). |
| **Severity** | **High:** Tác động trực tiếp đến sự nghiệp và khả năng tiếp cận việc làm của người lao động nếu được đưa vào áp dụng thực tế. |
| **Scale** | **Medium:** Được phát hiện trong giai đoạn thử nghiệm nội bộ tại Amazon, chưa được triển khai chính thức cho toàn bộ ứng viên đại trà. |
| **Probability** | **Critical (Rất cao):** Trong phạm vi thử nghiệm của mô hình, xác suất các hồ sơ chứa từ khóa phụ nữ bị hạ điểm là gần như tuyệt đối do cơ chế chấm điểm của thuật toán. |
| **Frequency** | **High:** Lặp đi lặp lại một cách nhất quán trên mọi hồ sơ có chứa từ khóa liên quan đến nữ giới khi thuật toán quét qua. |
| **Vì sao?** | Thuật toán học máy phản ánh trung thực định kiến trong dữ liệu quá khứ. Việc Amazon chủ động dừng dự án khi phát hiện lỗi cho thấy tầm quan trọng của việc kiểm thử nội bộ trước khi thương mại hóa hoặc áp dụng AI tuyển dụng vào thực tế. |

---

### 3. Case study 2 — iTutorGroup (Phân biệt tuổi tác bằng thuật toán tự động)

#### Brief Case
- **Tổ chức / sản phẩm AI:** iTutorGroup, Inc. (cùng các công ty liên kết: Shanghai PingAn Intelligent Education Technology Co., Ltd. và Tutor Group).
- **Thời gian, địa điểm / bối cảnh:** Tháng 5/2022 (Ủy ban Cơ hội Việc làm Bình đẳng Hoa Kỳ - EEOC khởi kiện tại Tòa án Quận Đông New York) – Tháng 8/2023 (Tòa án phê chuẩn thỏa thuận giải quyết hòa giải Consent Decree).
- **AI được dùng để làm gì:** Phần mềm tuyển dụng và sàng lọc tự động hồ sơ ứng viên nộp vào vị trí giáo viên dạy kèm tiếng Anh trực tuyến cho học sinh tại Trung Quốc.
- **Vấn đề hoặc sự kiện đáng chú ý:** Hệ thống tuyển dụng tự động của iTutorGroup được lập trình để tự động loại bỏ hồ sơ của các ứng viên nữ từ 55 tuổi trở lên và ứng viên nam từ 60 tuổi trở lên ngay khi họ nộp đơn. Vụ việc bị phát hiện khi một nữ ứng viên trên 55 tuổi nộp hồ sơ bị hệ thống từ chối ngay lập tức, nhưng khi bà nộp lại một bộ hồ sơ hoàn toàn giống hệt nhưng khai năm sinh trẻ hơn thì lập tức nhận được lời mời phỏng vấn. EEOC đã điều tra và khởi kiện công ty vì hành vi phân biệt đối xử vì tuổi tác vi phạm Đạo luật Chống phân biệt đối xử trong việc làm theo tuổi tác (ADEA).
- **Số liệu có nguồn:**
  - iTutorGroup đồng ý chi trả **365.000 USD** tiền bồi thường cho các ứng viên bị ảnh hưởng để hòa giải vụ kiện.
  - Có hơn **200 ứng viên** có đầy đủ năng lực và phẩm chất bị hệ thống tự động từ chối chỉ vì tuổi tác.
  - Tiêu chí lọc tự động của thuật toán: Loại trừ phụ nữ từ **55 tuổi** trở lên và nam giới từ **60 tuổi** trở lên.
  - Thỏa thuận hòa giải có hiệu lực giám sát trong **5 năm**, buộc công ty ngừng hỏi ngày sinh của ứng viên trước khi tuyển dụng và đào tạo lại toàn bộ nhân sự tuyển dụng.
- **Nguồn:**
  - Thông cáo báo chí chính thức của EEOC: U.S. Equal Employment Opportunity Commission, *"iTutorGroup to Pay $365,000 to Settle EEOC Discriminatory Practice Lawsuit"*, Press Release, ngày 09/08/2023. URL: `https://www.eeoc.gov/newsroom/itutorgroup-to-pay-365000-settle-eeoc-discriminatory-practice-lawsuit`
  - Hồ sơ vụ án tại Tòa án Liên bang: *EEOC v. iTutorGroup, Inc., Shanghai PingAn Intelligent Education Technology Co., Ltd., and Tutor Group*, Case No. 1:22-cv-02565 (E.D.N.Y., Consent Decree approved August 9, 2023).
- **Phân biệt bằng chứng và nhận định:**
  - *Điều nguồn xác nhận (Bằng chứng):* Hồ sơ tòa án và thông cáo chính thức của cơ quan liên bang EEOC xác nhận thuật toán đã tự động từ chối hơn 200 ứng viên vì tuổi tác, số tiền bồi thường 365.000 USD, ngưỡng tuổi bị loại (nữ >= 55, nam >= 60) và lệnh giám sát 5 năm.
  - *Điều tôi suy luận / Nhận định:* Đây là bằng chứng rõ ràng cho thấy doanh nghiệp đã chủ động mã hóa định kiến bất hợp pháp vào phần mềm tuyển dụng để trốn tránh việc xem xét công bằng, biến công nghệ tự động hóa thành công cụ phân biệt đối xử có hệ thống.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| **High-risk moment** | Thời điểm ứng viên điền thông tin ngày sinh vào biểu mẫu ứng tuyển trực tuyến và hệ thống thực thi lệnh sàng lọc tự động (instant auto-rejection). |
| **Stakeholder bị ảnh hưởng** | Hơn 200 giáo viên lớn tuổi đủ tiêu chuẩn tại Hoa Kỳ; công ty iTutorGroup; cơ quan thực thi pháp luật lao động (EEOC). |
| **Failure mode** | **Algorithmic discrimination / Harmful rule (Bias / Fairness):** Hệ thống thực thi quy tắc phân biệt đối xử bất hợp pháp theo độ tuổi. |
| **Layer bắt đầu lỗi** | **Grounding & Safety (Business Logic Layer):** Doanh nghiệp chủ động nhúng logic loại trừ theo tuổi tác vào quy trình tiếp nhận hồ sơ mà không thiết lập bất kỳ cơ chế kiểm soát an toàn (safety guardrails) hay rà soát tuân thủ pháp luật lao động. |
| **Harm xảy ra là gì?** | **Hậu quả thực tế đã xảy ra (Confirmed Harm):** Hơn 200 ứng viên bị tước đoạt cơ hội việc làm và thu nhập thực tế; iTutorGroup phải bồi thường 365.000 USD và chịu sự giám sát tư pháp trong 5 năm. |
| **Harm lens** | **Opportunity loss** (mất cơ hội việc làm thực tế) và **Economic harm** (thiệt hại thu nhập cho ứng viên và tổn thất tài chính cho doanh nghiệp). |
| **Severity** | **High:** Vi phạm trực tiếp luật pháp liên bang Hoa Kỳ (ADEA), tước bỏ quyền làm việc chính đáng của hơn 200 người. |
| **Scale** | **Medium:** Tác động trực tiếp đến hơn 200 ứng viên đã được xác định danh tính trong hồ sơ điều tra của EEOC. |
| **Probability** | **Critical (100%):** Mọi ứng viên nộp hồ sơ thuộc ngưỡng tuổi trên đều bị hệ thống tự động từ chối ngay lập tức mà không có ngoại lệ. |
| **Frequency** | **High:** Diễn ra liên tục và tự động 24/7 trên toàn bộ các đơn ứng tuyển nộp qua cổng tuyển dụng trực tuyến của công ty. |
| **Vì sao?** | Sự thiếu vắng hoàn toàn của Human-in-the-loop và việc cố tình nhúng quy tắc phân biệt đối xử vào phần mềm đã biến công cụ tự động hóa thành hành vi phạm pháp rõ ràng, được chứng minh qua thỏa thuận xử phạt của EEOC. |

---

### 4. Case study 3 — Workday AI Hiring Discrimination Litigation (Mobley v. Workday, Inc.)

#### Brief Case
- **Tổ chức / sản phẩm AI:** Workday, Inc. — Tập đoàn công nghệ hàng đầu cung cấp phần mềm quản trị nguồn nhân lực đám mây (HCM) và hệ thống theo dõi ứng viên (ATS) tích hợp AI và Machine Learning để sàng lọc, xếp hạng ứng viên cho các doanh nghiệp lớn.
- **Thời gian, địa điểm / bối cảnh:** Tháng 2/2023 đến nay (Phán quyết quan trọng ngày 12/07/2024 tại Tòa án Liên bang Khu vực Bắc California - N.D. Cal.).
- **AI được dùng để làm gì:** Công cụ AI/ML của Workday được các doanh nghiệp sử dụng để tự động phân tích CV, chấm điểm mức độ phù hợp của ứng viên, xếp hạng và tự động loại bỏ các ứng viên không đạt tiêu chuẩn trước khi hồ sơ được chuyển tới chuyên viên tuyển dụng con người.
- **Vấn đề hoặc sự kiện đáng chú ý:** Nguyên đơn Derek Mobley (một người da đen, trên 40 tuổi và mắc chứng rối loạn lo âu/trầm cảm) đã nộp hồ sơ ứng tuyển vào hơn 100 vị trí công việc tại hàng chục công ty khác nhau sử dụng phần mềm tuyển dụng Workday nhưng đều bị từ chối tự động. Ông đã khởi xướng vụ kiện tập thể (putative class action) cáo buộc rằng các thuật toán AI của Workday tạo ra tác động bất lợi mang tính phân biệt đối xử (disparate impact) đối với người da đen, người lớn tuổi (trên 40 tuổi) và người khuyết tật, vi phạm Title VII, ADEA và ADA. Điểm bước ngoặt: Ngày 12/07/2024, Thẩm phán Liên bang Rita Lin đã ra phán quyết lịch sử công nhận Workday có thể bị khởi kiện trực tiếp với tư cách là "đại lý" (agent) của các nhà tuyển dụng nếu phần mềm AI thay mặt người sử dụng lao động thực hiện các chức năng tuyển dụng cốt lõi. Vụ kiện cũng nhận được sự ủng hộ từ bản đệ trình Amicus Brief của EEOC.
- **Số liệu có nguồn:**
  - Nguyên đơn Derek Mobley đã nộp đơn vào hơn **100 vị trí công việc** qua hệ thống Workday từ năm 2018 đến 2023 và đều bị từ chối hàng loạt.
  - Nền tảng Workday được sử dụng bởi hơn **50% các tập đoàn trong danh sách Fortune 500** và hàng nghìn doanh nghiệp toàn cầu.
  - Phán quyết ngày **12/07/2024** của Thẩm phán Rita Lin bác bỏ yêu cầu hủy vụ kiện của Workday, cho phép vụ kiện tiếp tục theo thuyết trách nhiệm đại lý ("Agent" theory of liability).
  - Đến tháng **05/2025**, tòa án đã phê duyệt sơ bộ việc mở rộng thành vụ kiện tập thể cấp quốc gia (nationwide collective action) đối với khiếu nại phân biệt tuổi tác theo ADEA.
- **Nguồn:**
  - Phán quyết của Tòa án Liên bang Hoa Kỳ: *Mobley v. Workday, Inc.*, No. 4:23-cv-00770-RFL (N.D. Cal. July 12, 2024).
  - Phân tích pháp lý của Seyfarth Shaw LLP: *"Court Allows Discrimination Claims Against AI Hiring Vendor To Proceed Under 'Agent' Theory"*, July 2024. URL: `https://www.seyfarth.com/news-insights/court-allows-discrimination-claims-against-ai-hiring-vendor-to-proceed-under-agent-theory.html`
  - Báo cáo của Đại học Stanford (Stanford Law Review): *"Regulating AI Vendors in Employment: Mobley v. Workday and the Agent Liability Doctrine"*, 2024/2025.
- **Phân biệt bằng chứng và nhận định:**
  - *Điều nguồn xác nhận (Bằng chứng):* Hồ sơ tòa án xác nhận nguyên đơn bị từ chối hơn 100 lần, phán quyết ngày 12/7/2024 của Thẩm phán Rita Lin xác lập cơ sở pháp lý truy cứu trách nhiệm nhà cung cấp AI theo thuyết đại lý, và EEOC đã chính thức gửi Amicus Brief ủng hộ việc quy trách nhiệm cho nhà cung cấp phần mềm tuyển dụng.
  - *Điều tôi suy luận / Nhận định:* Việc các doanh nghiệp ủy thác hoàn toàn việc lọc hồ sơ cho một hệ thống AI "hộp đen" của bên thứ ba mà không kiểm định độc lập đã tạo ra khoảng trống trách nhiệm giải trình (accountability vacuum), nơi nhà tuyển dụng đổ lỗi cho thuật toán, còn nhà cung cấp thuật toán lại tuyên bố mình chỉ cung cấp công cụ phần mềm trung tính.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| **High-risk moment** | Thời điểm hệ thống AI của Workday tự động quét, xếp hạng và lọc hàng loạt hồ sơ ứng tuyển (mass automated screening) trước khi con người can thiệp. |
| **Stakeholder bị ảnh hưởng** | Hàng chục nghìn ứng viên da đen, ứng viên trên 40 tuổi và người khuyết tật; các tập đoàn sử dụng Workday; công ty Workday. |
| **Failure mode** | **Proxy Discrimination & Disparate Impact (Bias / Fairness):** Thuật toán sử dụng các biến đại diện ẩn (proxy features) trong hồ sơ dẫn đến tỷ lệ loại trừ bất đối xứng đối với các nhóm yếu thế được pháp luật bảo vệ. |
| **Layer bắt đầu lỗi** | **Model & Safety / Compliance:** Thuật toán máy học phức tạp thiếu cơ chế kiểm định tác động phân biệt đối xử (disparate impact audit), không có lớp bảo vệ (safety guardrail) để kích hoạt cảnh báo khi tỷ lệ loại trừ vi phạm quy tắc 4/5 (Four-Fifths Rule) trong luật lao động. |
| **Harm xảy ra là gì?** | **Nguy cơ và cáo buộc tổn hại diện rộng (Alleged Systemic Harm):** Hàng nghìn ứng viên có nguy cơ bị tước bỏ cơ hội tiếp cận việc làm một cách có hệ thống tại các công ty lớn; tạo ra gánh nặng pháp lý và rủi ro kiện tụng tập thể khổng lồ cho nhà cung cấp AI. |
| **Harm lens** | **Opportunity loss** (mất cơ hội việc làm trên diện rộng) và **Dignity loss** (cảm giác bất lực và bị tước đoạt quyền cạnh tranh công bằng trước thuật toán hộp đen). |
| **Severity** | **Critical:** Quy mô ảnh hưởng có thể bao trùm thị trường lao động của hàng trăm tập đoàn Fortune 500, đe dọa trực tiếp các nguyên tắc công bằng của luật lao động liên bang. |
| **Scale** | **Critical / High:** Workday xử lý hàng chục triệu hồ sơ tuyển dụng trên toàn thế giới, do đó bất kỳ sai lệch thuật toán nào cũng có tác động ở quy mô quốc gia và quốc tế. |
| **Probability** | **High:** Được tòa án liên bang công nhận có đủ chứng cứ hợp lý để tiến hành xét xử và được EEOC chính thức can thiệp hỗ trợ pháp lý. |
| **Frequency** | **High:** Diễn ra liên tục mỗi ngày trên hàng triệu đơn ứng tuyển được xử lý qua hạ tầng của Workday. |
| **Vì sao?** | Sự kết hợp giữa quy mô sử dụng cực lớn của nền tảng và bản chất "hộp đen" của mô hình học máy khiến việc phát hiện sai lệch trở nên vô cùng khó khăn. Phán quyết vụ *Mobley v. Workday* là cột mốc lịch sử buộc các nhà cung cấp giải pháp AI phải chịu trách nhiệm pháp lý trực tiếp như một đại lý tuyển dụng, thay vì trốn tránh sau danh nghĩa cung cấp phần mềm. |
