# DAY 1 — Flashcards (Foundation)

Mix MCQ-style + fill-in-blank-style. ~50 thẻ.

---

## Flashcard 1
**Q:** Phân biệt **program** và **software** theo Lecture 1?
**A:** Program = chỉ là code chạy được trên máy. Software = computer programs + procedures + (associated) documentation + data dùng để vận hành computer system.

## Flashcard 2
**Q:** Software có 4 core components nào?
**A:** (1) Computer programs (the "code"), (2) Procedures, (3) Documentation, (4) Data.

## Flashcard 3
**Q:** Điền vào chỗ trống: Software Error là lỗi do _____ gây ra; Fault là phần lỗi tồn tại trong _____; Failure xảy ra khi fault bị _____.
**A:** programmer; software (code); activated.

## Flashcard 4
**Q:** Có bao nhiêu causes of software errors theo Lecture 1? Liệt kê.
**A:** 8 causes: (1) Faulty requirements definition, (2) Client–Developer communication failures, (3) Deliberate deviations from requirements, (4) Logical design errors, (5) Coding errors, (6) Non-compliance with instructions, (7) Shortcomings of testing process, (8) Procedure & documentation errors.

## Flashcard 5
**Q:** Software quality định nghĩa theo **Pressman (2000)** gồm 3 yêu cầu nào?
**A:** (1) Explicit Requirements (functional + performance goals), (2) Documented Standards (quality standards trong contract), (3) Implicit Characteristics (Good Software Engineering Practices — GSEP).

## Flashcard 6
**Q:** SQA viết tắt là gì? SQA tập trung vào việc gì so với SQC?
**A:** Software Quality Assurance. SQA tập trung **prevention** (phòng ngừa) gốc lỗi trong toàn process; SQC tập trung **detection** (phát hiện) lỗi trong sản phẩm. QC là một phần con của QA.

## Flashcard 7
**Q:** SQA bao trùm mấy processes trong lifecycle?
**A:** 2: Development process + Maintenance process.

## Flashcard 8
**Q:** SQA Standards được chia làm mấy loại? Cho ví dụ.
**A:** 2 loại: (1) **Quality Management Standards** ("WHAT") — ISO 9001, ISO 9000-3, SEI CMM. (2) **Project Process Standards** ("HOW") — IEEE 1012 (V&V), ISO/IEC 12207.

## Flashcard 9
**Q:** ISO 9000-3 thuộc loại standard nào?
**A:** Quality Management Standard (focus "WHAT").

## Flashcard 10
**Q:** IEEE 1012 đề cập đến lĩnh vực nào?
**A:** V&V — Verification and Validation (Project Process Standard).

## Flashcard 11
**Q:** McCall's quality model có bao nhiêu factors và chia làm mấy categories?
**A:** **11 factors**, chia **3 categories**: Product Operation (5), Product Revision (3), Product Transition (3).

## Flashcard 12
**Q:** 5 Product Operation factors của McCall là gì?
**A:** Correctness, Reliability, Efficiency, Integrity, Usability.

## Flashcard 13
**Q:** 3 Product Revision factors của McCall là gì?
**A:** Maintainability, Flexibility, Testability.

## Flashcard 14
**Q:** 3 Product Transition factors của McCall là gì?
**A:** Portability, Reusability, Interoperability.

## Flashcard 15
**Q:** Điền: McCall's Product Operation factors trả lời câu hỏi "_____"; Product Revision trả lời "_____"; Product Transition trả lời "_____".
**A:** How well it runs; How well it can be changed, tested, and redeployed; How well it can be moved to different platforms and interface with other systems.

## Flashcard 16
**Q:** Correctness có 5 dimensions nào?
**A:** Output Mission, Accuracy & Completeness, Up-to-dateness, Availability (response time), Standards Compliance.

## Flashcard 17
**Q:** Reliability requirement liên quan tới khía cạnh gì? Cho ví dụ spec.
**A:** Failures to provide service. Ví dụ: heart monitoring failure rate < 1 per million cases; downtime ≤ 10 min/month.

## Flashcard 18
**Q:** Efficiency factor đo bằng đơn vị gì?
**A:** Hardware resources: MIPS, MHz, MB/TB, KBPS/MBPS/GBPS, battery life (thời gian giữa các lần recharge).

## Flashcard 19
**Q:** Integrity factor đề cập tới khía cạnh gì?
**A:** Software system **security** (cyber security, internet security, network security).

## Flashcard 20
**Q:** Usability factor đo bằng gì?
**A:** Scope of **staff resources** cần để train nhân viên mới và operate hệ thống.

## Flashcard 21
**Q:** Spec ví dụ cho Maintainability factor?
**A:** Size of module ≤ 30 statements.

## Flashcard 22
**Q:** Evans & Marciniak Model có mấy factors / categories?
**A:** 12 factors / 3 categories (1987).

## Flashcard 23
**Q:** Deutsch & Willis Model có mấy factors / categories?
**A:** 15 factors / 4 categories (1988).

## Flashcard 24
**Q:** 5 "new" factors mà alternative models thêm vào so với McCall là gì?
**A:** Verifiability, Expandability, Safety, Manageability, Survivability.

## Flashcard 25
**Q:** Factor nào bị **exclude** khỏi cả Evans–Marciniak và Deutsch–Willis?
**A:** **Testability** (được coi như sub-element của Maintainability).

## Flashcard 26
**Q:** Tương đương: Expandability ≈ _____ ; Survivability ≈ _____.
**A:** Flexibility (McCall) ; Reliability (McCall).

## Flashcard 27
**Q:** Safety và Manageability là 2 factors riêng của mô hình nào?
**A:** Deutsch & Willis (1988).

## Flashcard 28
**Q:** Verifiability có trong (những) mô hình nào?
**A:** Cả Evans & Marciniak và Deutsch & Willis.

## Flashcard 29
**Q:** SQA system components được chia làm mấy classes?
**A:** **6 classes**: (1) Pre-project, (2) Project life cycle activities assessment, (3) Infrastructure error prevention & improvement, (4) Software quality management, (5) Standardization/certification/SQA assessment, (6) Organizing for SQA — human components.

## Flashcard 30
**Q:** Pre-project SQA components gồm 2 thành phần nào?
**A:** (1) Contract reviews (proposal draft + contract draft), (2) Development and Quality plans.

## Flashcard 31
**Q:** Liệt kê 6 components của Infrastructure error prevention & improvement.
**A:** (1) Procedures and work instructions, (2) Templates and checklists, (3) Staff training/retraining/certification, (4) Preventive and corrective actions, (5) Configuration management, (6) Documentation control.

## Flashcard 32
**Q:** Phân biệt **Procedures** và **Work Instructions**?
**A:** Procedures = generally applicable definitions cho toàn organization. Work Instructions = highly detailed directions cho specific methods, thường dùng bởi specialized teams.

## Flashcard 33
**Q:** Phân biệt **Formal Design Reviews (DRs)** và **Peer Reviews**?
**A:** DRs: formal approval; committee gồm senior professionals + project leader; cho documents quan trọng. Peer Reviews (Inspections, Walkthroughs): reviewers là peers; review documents ngắn; mục tiêu phát hiện càng nhiều faults càng tốt.

## Flashcard 34
**Q:** Configuration Management gồm 2 hoạt động chính nào?
**A:** **Change Control** (approve & record modifications) + **Version Control** (computerized tools quản lý versions).

## Flashcard 35
**Q:** Công thức Total Quality Cost?
**A:** Total Quality Cost = Costs of Control + Costs of Failure. (Control = Prevention + Appraisal + Managerial control; Failure = Internal + External + Managerial failure costs.)

## Flashcard 36
**Q:** 3 Management SQA components là gì?
**A:** (1) Project progress control, (2) Software quality metrics, (3) Software quality costs.

## Flashcard 37
**Q:** Contract review tham chiếu (những) standard nào?
**A:** **ISO 9001 & ISO 9000-3**.

## Flashcard 38
**Q:** 2 stages của contract review là gì?
**A:** Stage 1: **Proposal Draft Review** (trước khi gửi proposal). Stage 2: **Contract Draft Review** (trước khi ký contract).

## Flashcard 39
**Q:** Proposal Draft Review có bao nhiêu objectives?
**A:** **9 objectives** (clarify requirements, alternative approaches, formal aspects, risks, resource estimation, company capacity, customer capacity, partner/subcontractor conditions, proprietary rights).

## Flashcard 40
**Q:** Contract Draft Review có bao nhiêu objectives? Liệt kê.
**A:** **3 objectives**: (1) No unclarified issues remain, (2) All understandings từ negotiations được documented đúng, (3) No "new" changes/additions/omissions slipped in without discussion.

## Flashcard 41
**Q:** 4 yếu tố ảnh hưởng extent of contract review?
**A:** (1) Project magnitude, (2) Project technical complexity, (3) Staff acquaintance & experience trong project area, (4) Project organizational complexity.

## Flashcard 42
**Q:** Ai thực hiện contract review theo project size?
**A:** Simple: Proposal Team Leader hoặc 1 member. Medium: cả proposal team (đôi khi outside professional). Major: **team of outside experts**.

## Flashcard 43
**Q:** 3 khó khăn khi review major proposals?
**A:** Time Pressures, Workload, Availability (of senior experts).

## Flashcard 44
**Q:** Trong Case Study CFV, công ty lỗ bao nhiêu và lý do?
**A:** Lỗ **$90,000**. Lý do: bỏ sót clause trong RFP rằng "personnel ở các CFV branches sẽ được supplier huấn luyện". Bài học: Technical success ≠ Business success.

## Flashcard 45
**Q:** 5 lý do cần Development & Quality plans?
**A:** (1) Scheduling, (2) Recruiting, (3) Risk Management, (4) SQA Implementation, (5) Project Control.

## Flashcard 46
**Q:** Liệt kê 5 elements của Quality Plan.
**A:** (1) Quality Goals (quantitative), (2) Planned Reviews, (3) Planned Tests (unit/integration/system), (4) Acceptance Tests for external software, (5) Configuration Management.

## Flashcard 47
**Q:** Development Plan dùng công cụ scheduling phổ biến nào?
**A:** **GANTT Charts**.

## Flashcard 48
**Q:** Quality goals nên định nghĩa kiểu Quantitative hay Qualitative? Tại sao?
**A:** **Quantitative** (objective, đo được, kiểm chứng được).

## Flashcard 49
**Q:** TDD viết tắt là gì? Vòng lặp 3 bước?
**A:** Test-Driven Development. 3 bước: **Red** (viết test fail) → **Green** (viết code vừa đủ pass) → **Refactor** (dọn code, giữ test pass).

## Flashcard 50
**Q:** F.I.R.S.T trong unit testing là gì?
**A:** **F**ast, **I**solated, **R**epeatable, **S**elf-Validating, **T**imely.

## Flashcard 51
**Q:** 3 Representation Forms của Use Case?
**A:** (1) Narrative text (user stories), (2) Template-based descriptions (written use cases), (3) Diagrammatic representations (activity diagrams, use case diagrams).

## Flashcard 52
**Q:** Tutorial 4 sử dụng tool nào để thiết kế UI?
**A:** **Figma** (https://www.figma.com).

## Flashcard 53
**Q:** Điền: 4 nguyên tắc chính của TDD là _____, _____, _____, _____.
**A:** Test First; KISS (Keep It Simple, Stupid); Baby Steps; F.I.R.S.T.

## Flashcard 54
**Q:** SQA organizational base gồm những thành phần nhân sự nào?
**A:** Managers, testing personnel, SQA unit, practitioners (trustees, committee, forum members).
