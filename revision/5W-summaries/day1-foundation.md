# DAY 1 — Foundation 5W Summaries

Tổng hợp các khái niệm nền tảng của 4 lectures + 4 tutorials đầu tiên, format 5W+H.

---

## Lecture 1 — Introduction to SQA

### Software (định nghĩa)
- **What**: "Software is: Computer programs, procedures, and possibly associated documentation and data pertaining to the operation of a computer system." Khác với "program" — một program chỉ là code chạy được trên máy.
- **Where**: Toàn bộ ngành CNTT; áp dụng trong cả sản phẩm cho khách riêng (custom) và sản phẩm thị trường chung (general market).
- **When**: Định nghĩa nền tảng dùng xuyên suốt SDLC.
- **Why**: Phân biệt rõ giữa "program" (chỉ code) và "software" (code + procedures + documentation + data) để hiểu đối tượng của SQA gồm nhiều thành phần.
- **How**: Khi nói "software", phải xét đầy đủ 4 core components: programs (code), procedures, documentation, data.
- **Dẫn chứng**: Lecture 1, page 5–6.

### Software Error, Fault, Failure
- **What**: 3 khái niệm phân biệt:
  - **Error**: lỗi do lập trình viên gây ra (syntax error hoặc logic error).
  - **Fault**: lỗi tồn tại trong code, nhưng có thể chưa bị kích hoạt (error có thể chưa tạo ra fault nếu phần code đó không chạy).
  - **Failure**: khi fault bị kích hoạt thì biến thành failure (hệ thống chạy sai).
- **Where**: Trong quá trình development & maintenance.
- **When**: Error xảy ra trước (lúc viết code), fault tồn tại trong code, failure xảy ra lúc runtime.
- **Why**: Hiểu chuỗi nhân–quả để biết nơi cần phòng ngừa/phát hiện lỗi.
- **How**: Error → Fault → Failure (failure chỉ xảy ra khi fault được activated).
- **Dẫn chứng**: Lecture 1, page 7–8.

### 8 Causes of Software Errors
- **What**: Các nguyên nhân gốc gây lỗi phần mềm: (1) Faulty requirements definition, (2) Client–Developer communication failures, (3) Deliberate deviations from requirements, (4) Logical design errors, (5) Coding errors, (6) Non-compliance with instructions, (7) Shortcomings of the testing process, (8) Procedure and documentation errors.
- **Where**: Bao trùm toàn bộ vòng đời phát triển (requirement → design → coding → testing → documentation).
- **When**: Cần ghi nhớ ngay từ giai đoạn requirements vì error có thể phát sinh ở mọi pha.
- **Why**: Để định hướng các SQA activities phù hợp với từng nguyên nhân (prevention).
- **How**: Áp dụng các SQA components (review, testing, training, procedures…) tương ứng với mỗi loại nguyên nhân.
- **Dẫn chứng**: Lecture 1, page 9–16.

### Software Quality (3 định nghĩa)
- **What**: 3 định nghĩa cổ điển:
  1. **Crosby (1979)**: "The degree to which a system, component, or process meets specified requirements."
  2. **Juran**: "The degree to which a system, component, or process meets customer needs or expectations."
  3. **Pressman (2000)**: "Conformance to explicit requirements, documented standards, and implicit characteristics."
- **Where**: Định nghĩa được trích dẫn ở mọi tài liệu về SQA.
- **When**: Là cơ sở lý luận để xây dựng SQA system.
- **Why**: 3 góc nhìn khác nhau (specification vs. customer expectation vs. conformance) giúp hiểu chất lượng toàn diện.
- **How**: Pressman's definition gồm 3 yêu cầu: Explicit Requirements (functional + performance), Documented Standards (quality standards trong contract), Implicit Characteristics (Good Software Engineering Practices — GSEP: maintainability, readability…).
- **Dẫn chứng**: Lecture 1, page 18–20.

### SQA (Software Quality Assurance) — định nghĩa
- **What**: "A planned and systematic pattern of all actions necessary to provide adequate confidence that an item or product conforms to established technical requirements." Mở rộng: bao gồm cả schedule và budget; covers cả development và maintenance processes.
- **Where**: Áp dụng xuyên suốt toàn bộ lifecycle (development + maintenance).
- **When**: Bắt đầu từ pre-project và kéo dài đến hết maintenance.
- **Why**: Để cung cấp "adequate confidence" rằng software đáp ứng technical, managerial, schedule, budget requirements.
- **How**: Bằng một tập các activities có hệ thống được lên kế hoạch trước — không phải chỉ là testing.
- **Dẫn chứng**: Lecture 1, page 21–22.

### SQA vs. SQC (Quality Control)
- **What**: QC = set of activities **đánh giá chất lượng** của sản phẩm đã được phát triển/sản xuất; QA = set of activities **đánh giá process** đã tạo ra sản phẩm.
- **Where**: QC inspections diễn ra trong/cuối development; QA trải khắp toàn lifecycle.
- **When**: QC ngay trước deployment; QA xuyên suốt mọi stage.
- **Why**: QA mục tiêu *prevent* (phòng ngừa) gốc lỗi; QC mục tiêu *detect* lỗi trong sản phẩm.
- **How**: QC chỉ là một phần trong tập rộng hơn của QA activities. QA giảm cost bằng phát hiện sớm lỗi.
- **Dẫn chứng**: Lecture 1, page 23–24.

### Objectives of SQA Activities
- **What**: Mục tiêu chia 2 nhóm:
  - **Development (process-oriented)**: (1) conform to functional technical requirements, (2) conform to managerial scheduling/budgetary requirements, (3) initiate & manage improvement activities.
  - **Maintenance (product-oriented)**: Tương tự 3 mục nhưng áp dụng cho maintenance activities.
- **Where**: Trong cả phát triển mới và bảo trì.
- **When**: Là kim chỉ nam khi thiết kế SQA system.
- **Why**: Đảm bảo software đáp ứng cả yêu cầu kỹ thuật lẫn quản lý (time + budget).
- **How**: Triển khai SQA components phù hợp với từng objective.
- **Dẫn chứng**: Lecture 1, page 25–26.

### SQA Standards — Vai trò
- **What**: Standards là **external tools** dùng để tích hợp chuyên môn quốc tế vào quality system của tổ chức.
- **Where**: Áp dụng tại tổ chức / dự án để tham chiếu best practice.
- **When**: Khi xây dựng hoặc đánh giá quality system.
- **Why**: 3 lợi ích: (1) Utilization — leverage global knowledge, (2) Coordination — align với partner, (3) Objective Evaluation — khung độc lập đo lường chất lượng.
- **How**: Áp dụng standard phù hợp với loại nhu cầu (quản lý hay quy trình).
- **Dẫn chứng**: Lecture 1, page 27.

### Classification of SQA Standards (Management vs Process)
- **What**: 2 loại:
  - **Quality Management Standards** (focus: "WHAT"): hướng dẫn quản lý phát triển/bảo trì. Ví dụ: **ISO 9001, ISO 9000-3, SEI CMM**.
  - **Project Process Standards** (focus: "HOW"): cung cấp hướng dẫn cụ thể về phương pháp/quy trình. Ví dụ: **IEEE 1012 (V&V), ISO/IEC 12207 (Software Life Cycle Processes)**.
- **Where**: Quản lý standards áp dụng cấp tổ chức; process standards áp dụng cấp dự án.
- **When**: Management → xin certification; Process → trong từng task của project.
- **Why**: Tách biệt "what is required" (management) khỏi "how to perform" (process).
- **How**: Tổ chức chọn theo nhu cầu certification (ISO 9001) hoặc methodological (IEEE 1012).
- **Dẫn chứng**: Lecture 1, page 28–29.

---

## Lecture 2 — Software Quality Factors

### Software Quality Factor — định nghĩa
- **What**: "A set of attributes grouped into content groups that define the operational, revision, and transition characteristics of software."
- **Where**: Trong Software Requirements Specification (SRS) — phần "How the system behaves" (non-functional).
- **When**: Định nghĩa khi đặc tả requirements.
- **Why**: Functional requirements (qua Use Cases) chỉ trả lời "what the system does"; quality factors trả lời "how it behaves" — là yếu tố differentiator.
- **How**: Mô hình SQA đề xuất 11–15 factors, được phân nhóm. Mỗi project chọn trọng số khác nhau (ví dụ: medical → reliability cao; game → usability cao).
- **Dẫn chứng**: Lecture 2, page 5–7.

### McCall's Factor Model — Tổng quan
- **What**: Mô hình của McCall (1977) gồm **11 factors** chia thành **3 categories**: Product Operation (5), Product Revision (3), Product Transition (3).
- **Where**: Tiêu chuẩn cổ điển nhất khi đánh giá chất lượng phần mềm.
- **When**: Khi soạn SRS hoặc đánh giá chất lượng.
- **Why**: Cung cấp khung phân loại có hệ thống các non-functional requirements.
- **How**: Áp dụng từng factor phù hợp với loại software cần đánh giá.
- **Dẫn chứng**: Lecture 2, page 10.

### Product Operation Factors (5)
- **What**: 5 factors: **Correctness, Reliability, Efficiency, Integrity, Usability** — đánh giá "how well it runs".
- **Where**: Liên quan đến vận hành/end-user.
- **When**: Đo lường khi software chạy thật.
- **Why**: Đảm bảo chương trình chạy đúng yêu cầu vận hành.
- **How**: Định nghĩa quantitative specs (ví dụ: failure rate < 1/million; downtime < 10 phút/tháng).
- **Dẫn chứng**: Lecture 2, page 10–14.

### Correctness (factor)
- **What**: Mức độ system thoả mãn specifications & fulfills its mission.
- **Where**: Output của hệ thống.
- **When**: Validation outputs.
- **Why**: Output sai là chất lượng zero.
- **How**: 5 dimensions: Output Mission, Accuracy & Completeness, Up-to-dateness, Availability (response time), Standards Compliance.
- **Dẫn chứng**: Lecture 2, page 11.

### Reliability (factor)
- **What**: Yêu cầu liên quan đến **failures to provide service**.
- **Where**: Hệ thống cần độ tin cậy cao (medical, financial).
- **When**: Trong vận hành dài hạn.
- **Why**: Failures gây thiệt hại lớn.
- **How**: Spec ví dụ: "failure rate < 1 per million cases"; "downtime ≤ 10 min/month".
- **Dẫn chứng**: Lecture 2, page 12.

### Efficiency (factor)
- **What**: Yêu cầu liên quan **hardware resources** cần để chạy chức năng.
- **Where**: Trên hardware, network, storage.
- **When**: Khi spec resource budget.
- **Why**: Giới hạn tài nguyên (mobile, embedded) cần tối ưu.
- **How**: Đo bằng MIPS, MHz, MB/TB, KBPS/MBPS/GBPS, battery life.
- **Dẫn chứng**: Lecture 2, page 13.

### Integrity (factor)
- **What**: Yêu cầu liên quan **security** của software.
- **Where**: Hệ thống có dữ liệu nhạy cảm, ngân hàng, IoT.
- **When**: Phân tích security threats.
- **Why**: Bảo vệ data + access.
- **How**: Cyber/Internet/network security — không cùng nghĩa với nhau.
- **Dẫn chứng**: Lecture 2, page 14.

### Usability (factor)
- **What**: Yêu cầu liên quan **staff resources** để train nhân viên mới và operate hệ thống.
- **Where**: End-user interfaces, training programs.
- **When**: Khi thiết kế UI/UX và training.
- **Why**: Giảm chi phí training, tăng productivity.
- **How**: Spec số giờ training để vận hành thành thạo.
- **Dẫn chứng**: Lecture 2, page 14.

### Product Revision Factors (3)
- **What**: **Maintainability, Flexibility, Testability** — "how well it can be changed, tested, redeployed."
- **Where**: Trong bảo trì sau release.
- **When**: Phase maintenance.
- **Why**: Software cần thay đổi liên tục.
- **How**:
  - **Maintainability**: nỗ lực sửa lỗi & verify (ví dụ: module ≤ 30 statements).
  - **Flexibility**: nỗ lực adapt cho customer/scale khác (perfective evolution).
  - **Testability**: log files, predefined intermediate results, automated diagnostics (Standard Test Data).
- **Dẫn chứng**: Lecture 2, page 15–18.

### Product Transition Factors (3)
- **What**: **Portability, Reusability, Interoperability** — "how well it can be moved to different platforms and interface with other systems."
- **Where**: Khi chạy đa nền tảng hoặc tích hợp.
- **When**: Khi planning architecture.
- **Why**: Tận dụng module và mở rộng tích hợp.
- **How**:
  - **Portability**: cross-platform transfer (adapt to hardware, OS).
  - **Reusability**: future-proofing modules (tái sử dụng module cũ → tiết kiệm).
  - **Interoperability**: API/REST, standardized data output (giao tiếp hệ thống khác).
- **Dẫn chứng**: Lecture 2, page 19–22.

### Alternative Models (Evans–Marciniak, Deutsch–Willis)
- **What**: Hai mô hình thay thế:
  - **Evans & Marciniak (1987)**: 12 factors / 3 categories.
  - **Deutsch & Willis (1988)**: 15 factors / 4 categories.
- **Where**: Tham khảo trong các bài toán mở rộng quality.
- **When**: Khi McCall không đủ phản ánh nhu cầu (safety-critical, large-scale evolution).
- **Why**: Cả 2 đều **exclude Testability** và **thêm 5 new factors**: Verifiability, Expandability, Safety, Manageability, Survivability.
- **How**:
  - Verifiability — cả 2 mô hình (modularity, simplicity).
  - Expandability — cả 2 (≈ Flexibility của McCall).
  - Safety — Deutsch & Willis (loại bỏ điều kiện nguy hiểm).
  - Manageability — Deutsch & Willis (configuration management, change procedures).
  - Survivability — Deutsch & Willis (≈ Reliability của McCall).
- **Dẫn chứng**: Lecture 2, page 24–28.

### McCall vs. Alternative — So sánh
- **What**: Khác biệt cốt lõi là **structural grouping**, không phải bản chất factors.
- **Where**: Khi chọn mô hình áp dụng.
- **When**: Khi review mô hình quality.
- **Why**: Tương đương: Expandability ≈ Flexibility; Survivability ≈ Reliability; Testability ⊂ Maintainability.
- **How**: Thực sự "mới": Verifiability (cả 2) + Safety, Manageability (chỉ Deutsch & Willis).
- **Dẫn chứng**: Lecture 2, page 29.

---

## Lecture 3 — SQA System

### SQA System — định nghĩa
- **What**: "An integrated framework that combines a wide range of SQA components, designed to challenge the multitude of sources of software errors and to achieve an acceptable level of software quality."
- **Where**: Toàn tổ chức software house.
- **When**: Thiết lập một lần và duy trì lâu dài.
- **Why**: Tích hợp tất cả components SQA thành 1 hệ thống nhất quán.
- **How**: Triển khai 6 classes SQA components.
- **Dẫn chứng**: Lecture 3, page 5.

### 6 Classes of SQA Components
- **What**: 6 lớp components:
  1. **Pre-project components**.
  2. **Components of project life cycle activities assessment**.
  3. **Components of infrastructure error prevention and improvement**.
  4. **Components of software quality management**.
  5. **Components of standardization, certification, and SQA system assessment**.
  6. **Organizing for SQA — the human components**.
- **Where**: Mỗi class áp dụng ở mức/giai đoạn khác nhau.
- **When**: Từ trước khi bắt đầu project tới hết maintenance + tổ chức toàn quy mô.
- **Why**: Cover toàn bộ nguồn lỗi.
- **How**: Chọn components phù hợp theo organization & project nature.
- **Dẫn chứng**: Lecture 3, page 6.

### Pre-project SQA Components
- **What**: 2 thành phần: (1) **Contract reviews** — review proposal & contract drafts, (2) **Development and quality plans** — soạn plan sau khi ký contract.
- **Where**: Trước khi bắt đầu coding.
- **When**: Giai đoạn proposal/contract & ngay sau ký.
- **Why**: Tránh "unrealistic commitments"; identify risk sớm.
- **How**: Tách 2 stage rõ ràng (proposal vs. contract draft review); plan riêng cho development + quality.
- **Dẫn chứng**: Lecture 3, page 8–10.

### Development Plan — Issues
- **What**: Main issues: Schedules; Required manpower & hardware resources; Risk evaluations; Organizational issues (team, subcontractors, partnerships); Project methodology & dev tools; Software reuse plans.
- **Where**: Trong project plan tổng.
- **When**: Sau khi ký contract.
- **Why**: Tránh trượt schedule và budget.
- **How**: Document hoá đầy đủ 6 issues trên.
- **Dẫn chứng**: Lecture 3, page 9.

### Quality Plan — Issues
- **What**: Main issues: Quality goals (measurable); Criteria for starting/ending each stage; List of reviews, tests, verification & validation activities.
- **Where**: Đi kèm Development Plan.
- **When**: Lập song song trước khi vào coding.
- **Why**: Tạo benchmark chất lượng để kiểm soát.
- **How**: Quantitative goals + lịch reviews/tests.
- **Dẫn chứng**: Lecture 3, page 10.

### Software Life Cycle Components
- **What**: Các components SQA trong lifecycle: **Reviews, Expert opinions, Software testing, Software maintenance components, Assurance of quality of subcontractors & customer-supplied parts**.
- **Where**: Suốt phases của project.
- **When**: Tại các điểm tương ứng (design, code, test, maintenance).
- **Why**: Bắt lỗi sớm + đảm bảo chất lượng các bên thứ ba.
- **How**: Áp dụng tại từng pha cụ thể.
- **Dẫn chứng**: Lecture 3, page 11.

### Review (loại)
- **What**: 2 loại review:
  - **Formal Design Reviews (DRs)**: Cần formal professional approval; committee gồm senior professionals + project leader; review documents quan trọng.
  - **Peer Reviews (Inspections, Walkthroughs)**: Review documents ngắn; reviewers là peers; mục tiêu phát hiện càng nhiều design/programming faults càng tốt.
- **Where**: Trên documents và code.
- **When**: Sau mỗi milestone.
- **Why**: Phát hiện faults sớm.
- **How**: Theo procedure formal/informal tương ứng.
- **Dẫn chứng**: Lecture 3, page 12.

### Expert Opinions
- **What**: Bổ sung external capabilities — outside experts có thể join DR committee, thay thế DR, hoặc xử lý bất đồng giữa senior professionals.
- **Where**: Khi tổ chức thiếu chuyên môn nội bộ.
- **When**: Lúc cần input độc lập.
- **Why**: Đảm bảo objectivity và bổ sung kiến thức chuyên sâu.
- **How**: Mời chuyên gia bên ngoài tham gia review.
- **Dẫn chứng**: Lecture 3, page 13.

### Infrastructure Components
- **What**: 6 components áp dụng toàn tổ chức:
  1. **Procedures and work instructions**
  2. **Templates and checklists**
  3. **Staff training, retraining, and certification**
  4. **Preventive and corrective actions**
  5. **Configuration management**
  6. **Documentation control**
- **Where**: Áp dụng cấp organization (không chỉ cấp project).
- **When**: Luôn duy trì.
- **Why**: Giảm/ loại bỏ tỉ lệ lỗi xuyên dự án.
- **How**: Chuẩn hoá process qua procedures + tools + training.
- **Dẫn chứng**: Lecture 3, page 16.

### Procedures vs. Work Instructions
- **What**: 
  - **Procedures**: định nghĩa generally applicable cho toàn organization.
  - **Work Instructions**: hướng dẫn cực chi tiết cho specific methods, thường cho teams chuyên môn.
- **Where**: Toàn tổ chức (procedures) vs. specialized teams (work instructions).
- **When**: Khi muốn chuẩn hoá kiến thức.
- **Why**: Chuyển organizational knowledge → standard routines.
- **How**: Procedures rộng, work instructions sâu chi tiết.
- **Dẫn chứng**: Lecture 3, page 17.

### Configuration Management
- **What**: Quản lý các modifications (versions/releases) qua thời gian.
- **Where**: Mọi software phát triển dài hạn.
- **When**: Khi có nhiều phiên bản tồn tại đồng thời.
- **Why**: Tránh modifications không được phê duyệt; đồng bộ versions giữa sites.
- **How**: **Change Control** (procedures để approve & record) + **Version Control** (computerized tools).
- **Dẫn chứng**: Lecture 3, page 21.

### Management SQA Components
- **What**: 3 control components: **Project progress control, Software quality metrics, Software quality costs**.
- **Where**: Quản lý project & maintenance.
- **When**: Liên tục trong project.
- **Why**: Phát hiện sớm tình huống không mong muốn.
- **How**: Theo dõi resource usage, schedule, risk, budget; đo metrics; tối ưu cost of control vs. cost of failure.
- **Dẫn chứng**: Lecture 3, page 23–26.

### Total Quality Cost
- **What**: **Total Quality Cost = Costs of Control + Costs of Failure**.
- **Where**: Trong quản lý quality budget.
- **When**: Đánh giá ROI của SQA activities.
- **Why**: Tối ưu hoá: thêm chi phí control sẽ giảm chi phí failure nhiều hơn → giảm tổng.
- **How**: Costs of Control = Prevention + Appraisal + Managerial control; Costs of Failure = Internal + External + Managerial.
- **Dẫn chứng**: Lecture 3, page 26.

### Standards/Certification Components — 2 sub-classes
- **What**: 
  - **Quality management standards**: SEI CMM, ISO 9001.
  - **Project process standards**: IEEE 1012, ISO/IEC 12207.
- **Where**: Cấp organization và project.
- **When**: Khi audit/cert.
- **Why**: International knowledge + coordination + objective measurement.
- **How**: Compliance để xin certification (quality mgmt) hoặc làm theo methodological guide (process).
- **Dẫn chứng**: Lecture 3, page 27.

### Organizing for SQA — Human Components
- **What**: SQA organizational base gồm: **managers, testing personnel, SQA unit, practitioners (trustees, committee, forum members)**.
- **Where**: Trong organization.
- **When**: Luôn tồn tại như cơ cấu.
- **Why**: Người là chìa khoá triển khai SQA components.
- **How**: 3 mục tiêu chính: develop/support SQA, detect deviations, suggest improvements.
- **Dẫn chứng**: Lecture 3, page 28.

### Considerations for SQA System Construction
- **What**: SQA system **không "one-size-fits-all"**; cần system flexibility.
- **Where**: Khi thiết kế SQA system cho 1 tổ chức cụ thể.
- **When**: Lúc construction.
- **Why**: Mỗi org/project/staff khác nhau → hệ thống khác nhau.
- **How**: 2 quyết định chính: (1) SQA organizational base, (2) SQA components & extent of use. Bị ảnh hưởng bởi: **organization, projects & services, professional staff**.
- **Dẫn chứng**: Lecture 3, page 29–30.

---

## Lecture 4 — Pre-project SQA Components

### CFV Case Study — Bài học
- **What**: Case Carnegie Fruits & Vegetables: dự án "thành công kỹ thuật" (đúng hạn, team thưởng) nhưng công ty lỗ $90,000 do bỏ sót clause "personnel sẽ được supplier huấn luyện".
- **Where**: Pre-project review.
- **When**: Trước khi gửi proposal.
- **Why**: **Technical success ≠ Business success**. Một clause trong RFP có thể gây lỗ lớn.
- **How**: Đọc kỹ requirement → review proposal → review contract.
- **Dẫn chứng**: Lecture 4, page 5–6.

### Contract Review — Định nghĩa
- **What**: Review proposal draft & contract draft. Standard tham chiếu: **ISO 9001 & ISO 9000-3**.
- **Where**: Pre-project stage.
- **When**: Trước nộp proposal + trước ký contract.
- **Why**: Verify feasibility (budget, schedule), identify risks sớm, prevent unrealistic commitments.
- **How**: 2 stages: Proposal Draft Review + Contract Draft Review.
- **Dẫn chứng**: Lecture 4, page 7.

### Stage 1 — Proposal Draft Review
- **What**: Review proposal trước khi gửi cho client.
- **Where**: Tại software house.
- **When**: Trước nộp proposal.
- **Why**: Kiểm tra requirements, costs, resources, partners, subcontractors.
- **How**: Đạt 9 mục tiêu (xem entry kế tiếp).
- **Dẫn chứng**: Lecture 4, page 8.

### Stage 2 — Contract Draft Review
- **What**: Review bản contract trước khi ký.
- **Where**: Cuối giai đoạn đàm phán.
- **When**: Trước ký contract.
- **Why**: Bảo đảm proposal + agreements trong negotiation được phản ánh đầy đủ.
- **How**: 3 objectives (xem entry kế tiếp).
- **Dẫn chứng**: Lecture 4, page 8.

### 9 Objectives of Proposal Draft Review
- **What**:
  1. Customer requirements được clarify & document.
  2. Alternative approaches đã xét (reuse, off-the-shelf, subcontractor).
  3. Formal aspects of relationship (channels, deliverables, acceptance criteria, phase approval, follow-up, change request).
  4. Identification of development risks (technological gaps, lack of know-how, tool availability).
  5. Adequate estimation of resources & timetable.
  6. Examination of company's capacity (staff & facilities availability).
  7. Examination of customer's capacity (commitments financial/personnel/hardware).
  8. Definition of partner & subcontractor participation conditions.
  9. Definition & protection of proprietary rights.
- **Where**: Proposal team.
- **When**: Trước nộp proposal.
- **Why**: Bảo đảm proposal khả thi & an toàn.
- **How**: Checklist 9 mục.
- **Dẫn chứng**: Lecture 4, page 9–11.

### 3 Objectives of Contract Draft Review
- **What**:
  1. No unclarified issues remain.
  2. All understandings from negotiations are correctly documented.
  3. No "new" changes, additions, or omissions slipped in without discussion.
- **Where**: Final contract draft.
- **When**: Trước khi ký.
- **Why**: Tránh tranh chấp sau ký.
- **How**: So sánh với proposal & meeting notes.
- **Dẫn chứng**: Lecture 4, page 12.

### Factors Affecting Contract Review Extent
- **What**: 4 yếu tố:
  1. **Project magnitude** (budget / man-months).
  2. **Project technical complexity** (higher → deeper review).
  3. **Degree of staff acquaintance with project area** (high familiarity/reuse → less review).
  4. **Project organizational complexity** (number of partners/stakeholders).
- **Where**: Khi planning review effort.
- **When**: Đầu giai đoạn proposal.
- **Why**: Để allocate review effort hợp lý.
- **How**: Đánh giá 4 yếu tố trên.
- **Dẫn chứng**: Lecture 4, page 13.

### Who Performs Contract Review
- **What**: Theo project size:
  - **Simple**: Proposal Team Leader hoặc 1 thành viên.
  - **Medium**: Cả proposal team, đôi khi outside professional.
  - **Major**: Team of outside experts.
- **Where**: Trong/ngoài tổ chức.
- **When**: Trước nộp proposal.
- **Why**: Match độ chuyên môn với độ phức tạp.
- **How**: Chọn reviewer theo size dự án.
- **Dẫn chứng**: Lecture 4, page 14.

### Difficulties for Major Proposals
- **What**: 3 khó khăn: **Time Pressures** (vội nộp bid), **Workload** (cần expertise nhiều), **Availability** (senior experts đang bận).
- **Where**: Major proposals.
- **When**: Lúc proposal deadline.
- **Why**: Để có chiến lược dự phòng review.
- **How**: Lập kế hoạch review sớm; thuê chuyên gia khi cần.
- **Dẫn chứng**: Lecture 4, page 15.

### Internal Projects (In-House)
- **What**: Một unit (Supplier) phát triển software cho unit khác (Customer) trong cùng organization.
- **Where**: Bên trong tổ chức.
- **When**: Khi 2 phòng ban khác làm việc với nhau.
- **Why**: Risk: relationships "loose"/goodwill, thiếu formal contract, ít/không có contract review.
- **How**: Vẫn nên prepare full-scale plans như external projects (case Toyware: lỗ $385k vs $240k ngân sách, lỡ Christmas).
- **Dẫn chứng**: Lecture 4, page 17–20, 32–33.

### Risks of Internal Projects (4 common problems)
- **What**: (1) Inadequate definition of requirements, (2) Poor resource estimation, (3) Unrealistic timetables, (4) Low awareness of development risks.
- **Where**: Internal projects.
- **When**: Bị bỏ qua review/plan.
- **Why**: Loose relationships → failure.
- **How**: Khắc phục bằng cách formalize plan + review.
- **Dẫn chứng**: Lecture 4, page 19.

### Why Need Development & Quality Plans (5 reasons)
- **What**: (1) **Scheduling** — estimate time, budget, manpower; (2) **Recruiting** — allocate resources; (3) **Risk Management** — resolve dev risks sớm; (4) **SQA Implementation** — implement quality activities; (5) **Project Control** — data cho manager kiểm soát.
- **Where**: Pre-project + early project.
- **When**: Ngay sau ký contract.
- **Why**: Planning là **foundations** của project mgmt & SQA.
- **How**: Document 2 plans riêng nhưng liên kết.
- **Dẫn chứng**: Lecture 4, page 22.

### 11 Development Plan Elements
- **What**:
  1. Project products (design docs, software, training tasks, completion dates).
  2. Project interfaces (existing packages, hardware, other teams).
  3. Project methodology & development tools.
  4. Software development standards & procedures.
  5. Map of development process (inputs/outputs/sequence; **GANTT charts** as scheduling tool).
  6. Project milestones.
  7. Project staff organization.
  8. Development facilities (hardware, software, office space).
  9. Development risks (technological gaps, staff shortages, interdependence).
  10. Control methods (progress reports, status meetings, gantt tracking).
  11. Project cost estimates.
- **Where**: Trong development plan tổng.
- **When**: Sau ký contract.
- **Why**: Đảm bảo project có roadmap chi tiết.
- **How**: Document hoá 11 elements.
- **Dẫn chứng**: Lecture 4, page 23–26.

### 5 Quality Plan Elements
- **What**:
  1. **Quality Goals** (quantitative).
  2. **Planned Reviews** (list, scope, type, schedule, person in charge).
  3. **Planned Tests** (unit, integration, system; type, schedule, person in charge).
  4. **Acceptance Tests for external software** (purchased, subcontracted, customer-supplied).
  5. **Configuration Management** (management tools, procedures).
- **Where**: Đi kèm development plan.
- **When**: Sau ký contract.
- **Why**: Tách rõ chất lượng để kiểm soát.
- **How**: Document hoá 5 elements; ưu tiên quantitative goals.
- **Dẫn chứng**: Lecture 4, page 27–28.

### Quality Goals — Quantitative vs Qualitative
- **What**: Preference: **Quantitative measures (Objective)** thay vì qualitative.
- **Where**: Trong Quality Plan.
- **When**: Khi đặt goals.
- **Why**: Quantitative đo lường được, kiểm chứng được.
- **How**: Ví dụ Help Desk System: HDS chạy 100 giờ/tuần — convert qualitative requirements thành quantitative specs.
- **Dẫn chứng**: Lecture 4, page 29–30.

### Small Projects — To Plan or Not
- **What**: Không tự động apply large-project plans cho small projects, nhưng plan vẫn cần nếu: **high risk identified** hoặc **heavy penalty for delay**.
- **Where**: Small projects.
- **When**: Đầu project.
- **Why**: Benefits: better task understanding, clearer responsibility, easier management control.
- **How**: Plan lite nhưng đầy đủ key elements.
- **Dẫn chứng**: Lecture 4, page 31.

---

## Tutorials 1–4

### TDD (Test-Driven Development) — Tutorial 1
- **What**: Software development process viết test cases TRƯỚC code thực. Reverse flow: Write Test → Write Code → Fix Code (thay vì Write Code → Write Test → Fix Bugs).
- **Where**: Trong unit testing, Java/JUnit (môi trường Maven, JDK 21).
- **When**: Áp dụng cho mỗi feature nhỏ.
- **Why**: Đảm bảo test coverage; bắt bug sớm; code refactor an toàn.
- **How**: Vòng lặp 3 bước:
  - **Red**: viết test thất bại (logic chưa tồn tại).
  - **Green**: viết code vừa đủ để test pass.
  - **Refactor**: dọn code, giữ test vẫn pass.
- **Dẫn chứng**: Tutorial 1.

### TDD Key Principles
- **What**: 4 nguyên tắc:
  1. **Test First**: không viết production logic trước test thất bại.
  2. **KISS** (Keep It Simple, Stupid): code chỉ vừa đủ pass test hiện tại.
  3. **Baby Steps**: chia nhỏ vấn đề thành nhiều tests nhỏ.
  4. **F.I.R.S.T**: Unit test phải Fast, Isolated, Repeatable, Self-Validating, Timely.
- **Where**: Khi viết unit tests.
- **When**: Mỗi feature mới.
- **Why**: Bảo đảm test chất lượng.
- **How**: Tuân thủ 4 nguyên tắc.
- **Dẫn chứng**: Tutorial 1.

### F.I.R.S.T (Unit Test Properties)
- **What**: 5 properties: **F**ast, **I**solated (test này không phụ thuộc test khác), **R**epeatable (luôn cho kết quả như nhau), **S**elf-Validating (pass/fail tự động, không cần đọc log), **T**imely (viết ngay trước code).
- **Where**: Unit tests trong TDD.
- **When**: Khi viết unit test.
- **Why**: Bảo đảm test có chất lượng cao.
- **How**: Refactor test khi thiếu thuộc tính.
- **Dẫn chứng**: Tutorial 1.

### Use Case Diagram — Tutorial 2
- **What**: Visual outline of tasks & interactions từ góc nhìn end-user. Cung cấp **high-level map** of system functionality.
- **Where**: Trong requirements engineering.
- **When**: Giai đoạn requirements/analysis.
- **Why**: Mô tả "what the system does" (functional) — bổ sung quality factors trong SRS.
- **How**: Vẽ actors, use cases, system boundary, relationships; có thể decompose use case lớn thành nhỏ; hỗ trợ multi-system & multi-actor.
- **Dẫn chứng**: Tutorial 2 (e-commerce, hospital, ATM examples).

### Use Case Representation Forms
- **What**: 3 forms:
  - **Narrative text** (user stories).
  - **Template-based descriptions** (written use cases).
  - **Diagrammatic representations** (activity diagrams, use case diagrams).
- **Where**: Tài liệu requirements.
- **When**: Khi capture requirements.
- **Why**: Mỗi form phù hợp một mục đích/audience.
- **How**: Có thể dùng StarUML (preferred 7.0.0), diagrams.net, Lucidchart, Visual Paradigm.
- **Dẫn chứng**: Tutorial 2.

### ER Diagram — Tutorial 3
- **What**: Entity-Relationship diagram — mô hình hoá data thông qua entities, attributes, relationships.
- **Where**: Phase analysis/design data layer.
- **When**: Sau khi requirements rõ ràng.
- **Why**: Mô hình hoá data domain → cơ sở schema database.
- **How**: Phân tích requirement → xác định entities, attributes, relationships, multiplicities.
- **Dẫn chứng**: Tutorial 3 (school schedule system, photo sharing site).

### Class Diagram (Data Modeling) — Tutorial 3
- **What**: UML class diagram — biểu diễn classes, attributes, methods, relationships (association, aggregation, composition, inheritance).
- **Where**: Object-oriented design.
- **When**: Sau ER hoặc song song.
- **Why**: Chuyển từ data model → OO design.
- **How**: Analyze requirement → identify classes & relationships → mô hình hoá.
- **Dẫn chứng**: Tutorial 3 Activity 2.

### UI Design with Figma — Tutorial 4
- **What**: Thiết kế GUI/UI mockup bằng Figma (https://www.figma.com).
- **Where**: Pha thiết kế UI/UX.
- **When**: Trước implementation.
- **Why**: Visualize giao diện trước khi code → giảm rework.
- **How**: Vẽ form, report window, GUI hoàn chỉnh có register/login/logout/CRUD + lưu DB (MySQL, MongoDB…). Suggested topics: university control, house monitor, mobile selling, streaming, technical share forum.
- **Dẫn chứng**: Tutorial 4.
