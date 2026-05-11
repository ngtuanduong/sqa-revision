# Day 2 – Lifecycle, Reviews & UI – 5W Summaries

## Lecture 5 – Software Development Life Cycle

### Waterfall Model
- **What**: Mô hình SDLC cổ điển, mô tả 7 phases tuần tự (Requirements → Analysis → Design → Coding → System Tests → Installation & Conversion → Operation & Maintenance).
- **Where**: Dự án có requirements ổn định, rõ ràng từ đầu; công nghệ quen thuộc; rủi ro thấp.
- **When**: Khi có thể xác định đầy đủ specs trước khi code; áp dụng trong giai đoạn lập kế hoạch toàn dự án.
- **Why**: Cung cấp mô tả toàn diện nhất, dễ quản lý milestone, dễ review End-of-Phase.
- **How**: Mỗi phase kết thúc bằng End-of-Phase Review; outputs phải được developer và customer kiểm tra; có thể (1) Approve, (2) Request correction, (3) Return to earlier phases.
- **Dẫn chứng**: Phase 4 Coding bao gồm inspection, unit tests, integration tests; Phase 7 Maintenance gồm Corrective, Adaptive, Perfective.

### Prototyping Model
- **What**: Mô hình tiến hóa, dùng application generators để xây prototype nhanh, lặp lại đến khi đạt mục tiêu.
- **Where**: Dự án small- to medium-sized; có customer/user tích cực tham gia.
- **When**: Khi requirements chưa rõ; cần giao tiếp trực quan giữa developer và user.
- **Why**: Rút ngắn development; tiết kiệm man-days; fit customer requirements tốt hơn; giảm rủi ro thất bại.
- **How**: Xây prototype → user examines → feedback → refine → repeat đến khi đạt prototyping goal.
- **Dẫn chứng**: Nhược điểm: có thể neglect software quality và long-term maintainability.

### Spiral Model
- **What**: Mô hình kết hợp iterative nature của prototyping + controlled/systematic aspects của waterfall.
- **Where**: Dự án lớn, phức tạp, rủi ro cao.
- **When**: Khi cần đánh giá rủi ro ở mỗi iteration; requirements có thể thay đổi ở phase sau.
- **Why**: Cho phép áp dụng prototyping ở bất kỳ stage; cho phép thay đổi requirements muộn.
- **How**: Boehm 1998 advanced spiral – mỗi vòng spiral có planning, risk analysis, engineering, evaluation.
- **Dẫn chứng**: Cons: khó quản lý thời gian, dễ thất bại nếu không xét rủi ro, time-consuming.

### Agile Manifesto
- **What**: Tập values/principles: Individuals & interactions > processes & tools; Working software > comprehensive documentation; Customer collaboration > contract negotiation; Responding to change > following a plan.
- **Where**: Dự án có requirements thay đổi nhanh, cần customer collaboration cao.
- **When**: Khi giá trị business cần phát hành nhanh và liên tục.
- **Why**: Tôn vinh con người, sản phẩm hoạt động, hợp tác và thích ứng thay đổi.
- **How**: Implement qua các frameworks: XP, Scrum, Kanban, Crystal, DSDM, FDD.
- **Dẫn chứng**: 4 cặp value statements – left-side được coi trọng hơn nhưng right-side vẫn có giá trị.

### Scrum Framework
- **What**: Lightweight framework giúp teams/organizations tạo value qua adaptive solutions cho complex problems; purposefully incomplete.
- **Where**: Complex product development, environments cần thích ứng nhanh.
- **When**: Bất kỳ dự án nào áp dụng được empiricism (kinh nghiệm thực tiễn) và lean thinking.
- **Why**: Dựa trên 3 trụ cột: Transparency, Inspection, Adaptation.
- **How**: 3 Roles + 5 Events + 3 Artifacts + 5 Values (Commitment, Focus, Openness, Respect, Courage).
- **Dẫn chứng**: Team ≤ 10 người, cross-functional, self-managing, không sub-teams.

### Scrum Roles (Accountabilities)
- **What**: Product Owner (PO), Scrum Master (SM), Developers.
- **Where**: Scrum Team – đơn vị nhỏ nhất.
- **When**: Cố định xuyên suốt mọi Sprint.
- **Why**: Mỗi role chịu trách nhiệm riêng biệt nhằm tối đa hóa value và effectiveness.
- **How**: PO quản lý Product Backlog; SM thiết lập Scrum và remove impediments; Developers tạo Increment + Sprint Backlog + adhering to Definition of Done.
- **Dẫn chứng**: PO is ONE person, NOT a committee; SM is a "true leader who serves".

### Scrum Events
- **What**: 5 events – The Sprint (container), Sprint Planning, Daily Scrum, Sprint Review, Sprint Retrospective.
- **Where**: Trong mỗi Sprint cycle.
- **When**: Sprint ≤ 1 tháng; Daily Scrum = 15 phút mỗi ngày; Planning/Review/Retro vào đầu và cuối Sprint.
- **Why**: Tạo regularity, giảm các meeting khác, đảm bảo transparency, inspection, adaptation.
- **How**: Sprint Planning trả lời 3 câu: Why valuable? What can be Done? How will work get done?
- **Dẫn chứng**: Daily Scrum cho Developers inspect progress; Retrospective concludes Sprint.

### Scrum Artifacts
- **What**: Product Backlog, Sprint Backlog, Increment.
- **Where**: Product Backlog cấp product; Sprint Backlog cấp Sprint; Increment là output của Sprint.
- **When**: Product Backlog refined liên tục; Sprint Backlog tạo trong Sprint Planning; Increment phải usable mỗi Sprint.
- **Why**: Maximize transparency of key information.
- **How**: Mỗi artifact gắn 1 commitment: Product Backlog → Product Goal; Sprint Backlog → Sprint Goal; Increment → Definition of Done.
- **Dẫn chứng**: No Definition of Done = No release.

### SQA Components in Project Life Cycle
- **What**: SQA chia 2 stages: Development life cycle stage + Operation–maintenance stage.
- **Where**: Áp dụng xuyên suốt project.
- **When**: Development → detect design/programming errors; Operation → corrective + improvements.
- **Why**: Đảm bảo chất lượng ở mọi phase.
- **How**: 4 sub-classes của Development SQA: Formal design reviews, Peer reviews, Expert opinions, Software testing.
- **Dẫn chứng**: Operation Stage – Corrective dùng specialized components; Improvements reuse development components; External participants (subcontractors) để giảm risk outsourcing.

## Lecture 6 – Integrating Quality Activities

### Factors Affecting QA Intensity
- **What**: Các yếu tố quyết định mức độ tập trung QA – Project Factors + Team Factors.
- **Where**: Áp dụng khi lập SQA plan.
- **When**: Quyết định trước khi bắt đầu development.
- **Why**: Tránh over-/under-invest vào QA; phù hợp với mức rủi ro.
- **How**: Project Factors: Magnitude, Technical complexity, Extent of reusable components, Severity of failure outcomes. Team Factors: Professional qualifications, Team acquaintance, Availability of supporting staff, % new staff members.
- **Dẫn chứng**: Severity of failure outcomes is "essential!"; % new staff – nhiều người mới cần QA chặt hơn.

### Testing Principles (10)
- **What**: 10 nguyên tắc nền tảng của testing.
- **Where**: Bất kỳ testing activity.
- **When**: Khi lập kế hoạch và thực hiện test.
- **Why**: Đảm bảo testing hiệu quả, khách quan, đầy đủ.
- **How**: (1) Programmers không test code của chính họ; (2) Tester độc lập; (3) Positive Pessimism mindset; (4) Probability of more errors; (5) Intellectually Challenging; (6) Mandatory: Expected Output; (7) Beyond the Happy Path; (8) Verify what it should NOT do; (9) Meticulous result checking; (10) Design for Regression.
- **Dẫn chứng**: Programmers không thể tự test code mình do over-familiarity.

### Testing Levels (4)
- **What**: Unit, Integration, System, Acceptance.
- **Where**: Áp dụng trong giai đoạn coding → release.
- **When**: Unit → khi code module xong; Integration → khi ghép modules; System → khi có toàn bộ system; Acceptance → trước khi release cho customer.
- **Why**: Mỗi level kiểm tra một aspect khác nhau.
- **How**: Unit (4 phases: Set up → Exercise → Verify → Teardown); Integration (Top-down hoặc Bottom-up); System (verify tích hợp + UI); Acceptance (black-box, real/customer data).
- **Dẫn chứng**: Acceptance – development team should NOT be responsible.

### Integration Testing Strategies
- **What**: Top-down vs Bottom-up integration.
- **Where**: Khi ghép modules.
- **When**: Phase Integration testing.
- **Why**: Lựa chọn strategy ảnh hưởng tới stub/driver cần viết và khi nào lỗi được phát hiện.
- **How**: Top-down: từ main module xuống, depth-first hoặc breadth-first. Bottom-up: bắt đầu từ lowest-level components.
- **Dẫn chứng**: Top-down cần stubs; Bottom-up cần drivers.

### Testing Process (4 phases)
- **What**: Determining test methodology → Planning the tests → Test design → Test implementation.
- **Where**: Toàn bộ testing project.
- **When**: Trước, trong và sau development.
- **Why**: Hệ thống hóa testing, tránh sót.
- **How**: Methodology gồm chuẩn chất lượng + chiến lược (Big Bang vs Incremental, Top-down vs Bottom-up, White Box, Automated). Planning gồm 5 câu: What, Sources, Who, Where, When-to-terminate.
- **Dẫn chứng**: Medical software cần chuẩn cao nhất; internal training chỉ cần medium.

### Prioritization Formula (C = kA + mB)
- **What**: Công thức xếp hạng modules để test theo độ quan trọng.
- **Where**: Khi lập kế hoạch test với resource hạn chế.
- **When**: Phase Planning của testing process.
- **Why**: Không thể test mọi thứ, phải ưu tiên.
- **How**: C = k·A + m·B với A = Severity (damage to life/finance/essential functions), B = Risk (probability of failure based on complexity + programmer experience), k và m là weights.
- **Dẫn chứng**: Modules có A và B cao → C cao → test trước.

### Test Termination Criteria (5)
- **What**: 5 cách để quyết định dừng test.
- **Where**: Test execution phase.
- **When**: Khi cần quyết định "đủ chưa".
- **Why**: Không thể test vô hạn.
- **How**: (1) Completed Implementation – all tests clean; (2) Mathematical Models – error detection rate giảm đến mức chấp nhận; (3) Error Seeding – tìm đủ % lỗi đã seed; (4) Dual Teams – so sánh 2 team độc lập; (5) Resource Limit – hết budget/time.
- **Dẫn chứng**: Error seeding – chèn lỗi nhân tạo, đánh giá tỷ lệ phát hiện.

### Testing Documentation (4)
- **What**: 4 tài liệu chính – STP, STD, STR, TSR.
- **Where**: Mỗi stage testing.
- **When**: STP đầu (Planning); STD trong Design; STR sau mỗi test/re-test; TSR cuối cùng.
- **Why**: Đảm bảo traceability + accountability.
- **How**: STP (Software Test Plan), STD (Software Test Description), STR (Software Test Report), TSR (Test Summary Report).
- **Dẫn chứng**: STD documents test procedures + test cases; TSR summarizes toàn bộ testing project.

### Defect Removal Model
- **What**: Mô hình định lượng đánh giá SQA plan theo 2 chỉ tiêu: Total Effectiveness + Total Cost.
- **Where**: Áp dụng cho linear (waterfall) development process.
- **When**: Khi evaluate hoặc compare các SQA plans.
- **Why**: Chứng minh giá trị kinh tế của early SQA investment.
- **How**: Input Defects = New Defects + Passed Defects; Removed = Input × % Effectiveness; Passed = Input - Removed; TRC = Removed × Cost Unit.
- **Dẫn chứng**: Dựa trên data lịch sử của IBM, TRW, Boehm.

### Cost of Defect Removal (Rule of 10x / 110x)
- **What**: Chi phí sửa lỗi tăng exponentially theo phase.
- **Where**: Mọi project software.
- **When**: Khi đánh giá ROI của early QA.
- **Why**: Lỗi phát hiện càng muộn càng đắt.
- **How**: Fixing a bug after release ≈ 110× more expensive than fixing during requirements.
- **Dẫn chứng**: Defects origin phân bố khắp lifecycle, không chỉ coding.

## Lecture 7 – Reviews

### Review Objectives
- **What**: Process/meeting trình bày work product cho personnel để comment hoặc approve.
- **Where**: Mọi development milestone.
- **When**: Sau khi hoàn thành analysis/design document.
- **Why**: Early Detection + Cost Reduction (phát hiện sớm rẻ hơn nhiều).
- **How**: Direct objectives = Error Detection, Risk Identification, Standardization, Approval. Indirect objectives = Knowledge Exchange, Process Improvement.
- **Dẫn chứng**: "Double or triple net" strategy – kết hợp nhiều methodologies.

### Review Methodologies
- **What**: 3 nhóm chính – Formal Design Reviews (DRs), Peer Reviews (Inspections + Walkthroughs), Expert Opinions.
- **Where**: Mọi document quan trọng.
- **When**: Khi cần authority approval (DR) hoặc detect lỗi (Peer Review).
- **Why**: Tận dụng external viewpoints; author không tự thấy lỗi mình.
- **How**: Áp dụng "double or triple net" – chồng nhiều layers review.
- **Dẫn chứng**: Peers, superiors, external experts, customer reps đều có thể tham gia.

### Principles for Effective Reviews
- **What**: Structured approach + Key roles (Coordinator, Scribe) + Golden Rule.
- **Where**: Mọi review session.
- **When**: Trong quá trình review.
- **Why**: Tránh review thành discussion ngẫu hứng.
- **How**: Coordinator giữ meeting on-track; Scribe record defects chi tiết. Golden Rule: Detect errors only, DO NOT design solutions on the spot.
- **Dẫn chứng**: Procedural order, not haphazard.

### Formal Design Reviews (DRs / FTR)
- **What**: Còn gọi Formal Technical Reviews; without DR approval, dev team CANNOT continue.
- **Where**: Mọi development milestone.
- **When**: Khi document phase hoàn thành (Requirement Specification, Installation Plan…).
- **Why**: Authority gate giữa các phases.
- **How**: 13 common DRs: DPR, SRSR, PDR, DDR, DBDR, TPR, STPR, VDR, OMR, SMR, TRR, PRR, IPR.
- **Dẫn chứng**: PDR = Preliminary Design Review; PRR = Product Release Review.

### Review Leader (DR)
- **What**: Người dẫn dắt DR, quyết định lớn cho success.
- **Where**: External to project team.
- **When**: Được appoint trước session.
- **Why**: Cần objective + senior để guide.
- **How**: Yêu cầu: Knowledge (kinh nghiệm dự án cùng loại), Seniority (ngang/trên Project Leader), Position (ngoài project team – ví dụ QA Manager, Chief SE), Relationship (rapport tốt với team).
- **Dẫn chứng**: QA Manager hoặc Chief Software Engineer.

### DR Team & Size
- **What**: Composition + Optimal size.
- **Where**: Trong DR session.
- **When**: Appoint trước session.
- **Why**: Quá lớn → waste time + coordination problem.
- **How**: Optimal 3–5 members; gồm Senior team members, Senior pros từ projects khác, Customer/User reps. Non-project staff nên là majority.
- **Dẫn chứng**: Pressman: Limit team size 3-5 members.

### DR Session Agenda (4 steps)
- **What**: 4 bước trong session.
- **Where**: Trong DR meeting (max 2h).
- **When**: Tiến hành theo thứ tự.
- **Why**: Đảm bảo focus + output rõ ràng.
- **How**: (1) Presentation – short overview; (2) Discussion – review team comments; (3) Verification – mỗi comment xét corrections cần; (4) Decision – quyết định progress.
- **Dẫn chứng**: Presentation là short overview, KHÔNG phải general project description.

### DR Decision Outputs (3)
- **What**: 3 quyết định khả dĩ.
- **Where**: Kết thúc DR session.
- **When**: Sau khi verification xong.
- **Why**: Quyết định phase tiếp.
- **How**: (1) Full Approval – minor corrections OK; (2) Partial Approval – approved parts proceed, non-approved phải re-review; (3) Denial of Approval – repeat DR.
- **Dẫn chứng**: Denial khi có nhiều major/critical defects.

### Pressman Golden Guidelines
- **What**: Hướng dẫn vàng cho DR.
- **Where**: Infrastructure + Session.
- **When**: Trước, trong session.
- **Why**: Đảm bảo professional + hiệu quả.
- **How**: Infrastructure: develop checklists, train senior pros, schedule DRs in project plan. Session: 3-5 members, professional tone (no personal attacks), stick to agenda, MAX 2 HOURS, focus on detecting defects NOT solutions.
- **Dẫn chứng**: Max duration 2 hours là hard limit.

### Peer Reviews – Inspection vs Walkthrough
- **What**: 2 forms của peer reviews.
- **Where**: 5–15% of documents.
- **When**: Trong development, focus on high-risk sections.
- **Why**: Highly efficient for SQA.
- **How**: Inspection – higher formality, corrective action + process improvement, author KHÔNG present (thường Coder), Moderator dẫn dắt, scribe records Critical/Major/Minor severity. Walkthrough – lower formality, author IS presenter, Coordinator dẫn dắt, findings report đơn giản.
- **Dẫn chứng**: Peer reviews NOT authorized to approve document (unlike DR).

### Inspection Process (Fagan 6 Steps – Implied)
- **What**: 6 phases của Fagan inspection: Planning → Overview → Preparation → Meeting/Inspection → Rework → Follow-up.
- **Where**: Mọi formal inspection.
- **When**: Theo thứ tự cố định.
- **Why**: Đảm bảo systematic + thorough.
- **How**: Planning (chọn material, team); Overview (đào tạo team); Preparation (đọc + chuẩn bị checklist); Meeting (find defects); Rework (sửa); Follow-up (verify fix).
- **Dẫn chứng**: Inspection có Overview meeting cho team trước session – Walkthrough thì không cần.

### Peer Review Participants
- **What**: Team structure cho Inspection/Walkthrough.
- **Where**: Trong peer review session.
- **When**: Appoint trước.
- **Why**: Specialized roles tăng coverage.
- **How**: Optimal 3-5. Leader: Moderator (Inspection) / Coordinator (Walkthrough), từ ngoài project team. Author always participates. Inspection: Designer, Coder, Tester. Walkthrough: Standards Enforcer, Maintenance Expert, User Representative.
- **Dẫn chứng**: Presenter trong Inspection thường là Coder, không phải Author.

### Coverage & Efficiency Metrics
- **What**: Phạm vi và chỉ số đo lường peer review.
- **Where**: SQA reporting.
- **When**: Sau peer review activities.
- **Why**: Đánh giá ROI.
- **How**: Coverage 5–15% documents (focus high-risk/complex/defect-prone). Metrics: hours per defect, defect density (defects/page), internal effectiveness (% defects by review vs testing).
- **Dẫn chứng**: Reports gửi Corrective Action Board (CAB) để analyze trends.

## Lecture 8 – UI Review

### Why Review UI
- **What**: Mục tiêu của UI review.
- **Where**: Mọi product có UI.
- **When**: Sau khi có UI mockup/prototype/implementation.
- **Why**: Reduce Excise, Improve User Efficiency, Prevent Cognitive Friction, Ensure Goal-Directed Design.
- **How**: Evaluate Interaction Methods, Standardize UI Elements, Apply Core UI Principles, Assess Icon Usage & Visuals.
- **Dẫn chứng**: Excise = unnecessary effort that satisfies the tool not the user.

### Direct Manipulation
- **What**: Users tương tác trực tiếp với objects thay vì menus phức tạp.
- **Where**: Desktop, mobile, web UI.
- **When**: Khi action có thể map sang gesture trực quan.
- **Why**: Giảm cognitive load, tăng speed.
- **How**: Drag-and-drop file vào folder thay vì dialog "Move to".
- **Dẫn chứng**: Drag file to folder là ví dụ kinh điển.

### Mouse Interaction & Selection
- **What**: Quy tắc hover/click/select.
- **Where**: Desktop UI.
- **When**: Mọi mouse interaction.
- **Why**: Tạo consistent expectation.
- **How**: Hover = pliancy signal (clickable); Single click = select/toggle; Double click = open (use sparingly on web). Selection: Click = One; Ctrl+Click = Multiple; Shift+Click = Range.
- **Dẫn chứng**: Double click hiếm dùng trên web.

### Feedback & Responsiveness
- **What**: Phản hồi visual + thời gian.
- **Where**: Mọi UI element.
- **When**: Ngay sau user action.
- **Why**: Interface feel solid + responsive.
- **How**: Latency Rule < 0.1s; buttons look "pressed"; drag shows "ghost" image.
- **Dẫn chứng**: 0.1s là ngưỡng phản hồi tức thì.

### Undo vs Confirmation
- **What**: Lựa chọn giữa Undo và "Are you sure?".
- **Where**: Bất kỳ destructive action.
- **When**: Khi user thực hiện action có rủi ro.
- **Why**: Confirmation dialogs interrupt flow.
- **How**: Support Infinite Undo → encourage Safe Exploration (trial & error).
- **Dẫn chứng**: Trash Can là pattern soft-delete.

### Keyboard Accessibility
- **What**: Hỗ trợ keyboard cho power users + accessibility.
- **Where**: Mọi UI.
- **When**: Mặc định.
- **Why**: Accelerators tăng speed; focus ring cho a11y.
- **How**: Accelerators (Ctrl+S, Ctrl+C), visible Focus Ring khi Tab, Mnemonics (underlined letters – e.g., <u>F</u>ile).
- **Dẫn chứng**: Focus ring phải visible.

### UI Elements (Categories)
- **What**: 6 nhóm UI elements.
- **Where**: Web/mobile UI.
- **When**: Khi design forms/navigation.
- **Why**: Standardize elements để user nhận biết.
- **How**: Text Inputs (text field, text area); Buttons (text/icon/text+icon, social); Checkboxes & Radio buttons; Dropdown & List boxes; Toggles (2+ states); Navigational (Breadcrumb, Pagination, Carousel); Informational (Badge, Tooltip, Message box).
- **Dẫn chứng**: Toggle khác từ radio button ở số lượng state.

### Mental Models Principle
- **What**: UI phải reflect User's Mental Model, không phải Implementation Model.
- **Where**: Mọi product design.
- **When**: Từ design phase.
- **Why**: Implementation Model phức tạp + rigid; Mental Model simple + fluid.
- **How**: Mask complexity, đừng bắt user hiểu file system/database.
- **Dẫn chứng**: User không cần biết về schema database.

### Safe Exploration Principle
- **What**: Cho phép user "trial and error" mà không bị punish.
- **Where**: Mọi UI.
- **When**: Mọi destructive/reversible action.
- **Why**: Users learn by exploring, not reading manuals.
- **How**: Infinite Undo (+ Redo); avoid "Are you sure?"; Trash Can cho soft deletes.
- **Dẫn chứng**: Trash Can pattern phổ biến trong Gmail, macOS.

### Eliminate Excise
- **What**: Loại bỏ extra work cho tool, không cho user.
- **Where**: UI navigation & dialogs.
- **When**: Throughout design.
- **Why**: UI nên transparent.
- **How**: Examples: resizing windows, dismissing pop-ups, re-entering data. Minimize navigation tasks → zero.
- **Dẫn chứng**: Re-entering data là excise điển hình.

### Smart Software (Memory)
- **What**: Software phải nhớ user preferences/state.
- **Where**: Apps có state.
- **When**: Mọi restart.
- **Why**: Tránh "amnesia" – treat restart as continuation.
- **How**: Remember window position/size, last opened file/view, toggle states, settings. "Do what I did last time."
- **Dẫn chứng**: Restore last session pattern.

### Visual Hierarchy
- **What**: Guide user's eye qua visual weight.
- **Where**: Mọi screen layout.
- **When**: Design phase.
- **Why**: Users scan, không read.
- **How**: Size (important = larger), Contrast (primary actions stand out), Position (F-Pattern hoặc center).
- **Dẫn chứng**: F-Pattern reading layout.

### Affordance
- **What**: Visual properties chỉ ra cách dùng object.
- **Where**: UI components.
- **When**: Design phase.
- **Why**: Form follows function.
- **How**: Raised (3D) = "Click me"; Recessed (inset) = "Fill me"; Grab handles = "Drag me".
- **Dẫn chứng**: Flat ambiguous graphics hide functionality – avoid.

### Responsiveness, Consistency, Visual Design
- **What**: 3 nguyên tắc bổ sung.
- **Where**: Mọi UI.
- **When**: Throughout design + review.
- **Why**: Đảm bảo experience đồng đều trên devices.
- **How**: Responsive: adapt to devices, touch targets usable on mobile, elements properly resized. Consistency: components/naming/styling consistent. Visual Design: sufficient contrast, readable+consistent font, intuitive icons.
- **Dẫn chứng**: Touch target minimum size cho mobile.

### Icon Guidelines – Design Strategy
- **What**: Rapid recognition + space saving qua metaphors.
- **Where**: Toolbars, navigation.
- **When**: Mỗi icon design.
- **Why**: Icons faster than text khi đã quen.
- **How**: Use real-world metaphors (Trash, Folder, Gear). Readability at 16px/24px is priority. Avoid excessive gradients/shadows that blur at small scales.
- **Dẫn chứng**: Gear = Settings, Trash = Delete.

### Icon Usability & Ambiguity
- **What**: Distinctiveness + Golden Rule of Labeling.
- **Where**: Icon-only UIs.
- **When**: Khi thiết kế icon.
- **Why**: Icons inherently ambiguous.
- **How**: Distinct silhouettes; always use text labels or tooltips. Star = Favorite? Rating? New?
- **Dẫn chứng**: Tooltip mandatory cho icon-only buttons.

### Icon States & Feedback
- **What**: 4 states của icon.
- **Where**: Mọi interactive icon.
- **When**: User hover/click.
- **Why**: Signals pliancy + state.
- **How**: Normal (standard, high contrast); Hover (glow, brighten, slight lift); Active/Pressed (darker, inset, size reduction); Disabled (greyscale/ghosted, reduced opacity).
- **Dẫn chứng**: Hover lift = pliancy signal.

## Tutorial 5-7

### Tutorial 5 – Authentication Implementation
- **What**: Implement register, login, logout cho topic đã chọn ở Tutorial 4 - Activity 3.
- **Where**: Project code base.
- **When**: Sau khi có database design + tech stack.
- **Why**: Authentication là foundation cho mọi user-based feature.
- **How**: Build register form (validation, hash password, store user); login form (verify credential, create session/JWT); logout (destroy session/token).
- **Dẫn chứng**: Common patterns: bcrypt hash, session cookies, JWT bearer tokens.

### Tutorial 6 – CRUD Implementation
- **What**: Implement remaining features – CRUD operations cho domain entities.
- **Where**: Project code base.
- **When**: Sau authentication setup.
- **Why**: CRUD là core của hầu hết business apps.
- **How**: Create (POST + form validation); Read (GET list + GET detail with pagination); Update (PUT/PATCH); Delete (DELETE with confirmation/soft delete).
- **Dẫn chứng**: REST conventions + status codes (200, 201, 400, 401, 404, 500).

### Tutorial 7 – Test Planning & Reporting
- **What**: Create test plan, test design (from template), implement test, make test report.
- **Where**: Áp dụng cho topic đã chọn.
- **When**: Sau khi feature đã code xong.
- **Why**: Đảm bảo quality + documentation.
- **How**: Test Plan (STP) → Test Design (STD) → Implementation → Test Report (STR/TSR). Áp dụng IEEE 829 template với sections: Introduction, Test Items, Features to be Tested, Features NOT to be Tested, Approach, Pass/Fail Criteria, Suspension Criteria, Test Deliverables, Schedule, Staffing, Risks.
- **Dẫn chứng**: Liên kết với Lecture 6 testing process (4 phases).
