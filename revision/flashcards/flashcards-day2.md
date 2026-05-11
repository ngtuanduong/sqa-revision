# Day 2 – Flashcards (Lifecycle, Reviews, UI)

## Flashcard 1
**Q:** Waterfall Model có bao nhiêu phases và liệt kê chúng theo thứ tự?
**A:** 7 phases: (1) Requirements Definition, (2) Analysis, (3) Design, (4) Coding, (5) System Tests, (6) Installation and Conversion, (7) Regular Operation and Maintenance.

## Flashcard 2
**Q:** Ba loại maintenance services trong Waterfall phase 7?
**A:** Corrective (sửa faults), Adaptive (đáp ứng requirements mới), Perfective (thêm minor features cải thiện performance).

## Flashcard 3
**Q:** Three possible outcomes của End-of-Phase Review trong Waterfall?
**A:** (1) Approval và proceed to next phase; (2) Correction/Change demands for parts of last phase; (3) Return to earlier phases.

## Flashcard 4
**Q:** Prototyping Model phù hợp nhất với loại dự án nào?
**A:** Small- to medium-sized projects với customer/user tham gia tích cực để examine prototypes.

## Flashcard 5
**Q:** Spiral Model là sự kết hợp của những gì?
**A:** Kết hợp iterative nature của Prototyping + controlled/systematic aspects của Waterfall.

## Flashcard 6
**Q:** Điền vào chỗ trống: Agile Manifesto value "____ over comprehensive documentation".
**A:** Working software.

## Flashcard 7
**Q:** Bốn giá trị của Agile Manifesto?
**A:** (1) Individuals & interactions > processes & tools; (2) Working software > comprehensive documentation; (3) Customer collaboration > contract negotiation; (4) Responding to change > following a plan.

## Flashcard 8
**Q:** Scrum dựa trên những trụ cột nào của Empiricism?
**A:** Ba trụ cột: Transparency, Inspection, Adaptation.

## Flashcard 9
**Q:** Scrum có mấy roles, mấy events, mấy artifacts?
**A:** 3 roles (Product Owner, Scrum Master, Developers), 5 events (Sprint, Sprint Planning, Daily Scrum, Sprint Review, Sprint Retrospective), 3 artifacts (Product Backlog, Sprint Backlog, Increment).

## Flashcard 10
**Q:** Năm giá trị (Values) của Scrum?
**A:** Commitment, Focus, Openness, Respect, Courage.

## Flashcard 11
**Q:** Time-box của Sprint và Daily Scrum?
**A:** Sprint ≤ 1 tháng; Daily Scrum = 15 phút.

## Flashcard 12
**Q:** Sprint Planning addresses three topics nào?
**A:** (1) Why is this Sprint valuable? (2) What can be Done? (3) How will the chosen work get done?

## Flashcard 13
**Q:** Commitment gắn với mỗi Scrum artifact?
**A:** Product Backlog → Product Goal; Sprint Backlog → Sprint Goal; Increment → Definition of Done.

## Flashcard 14
**Q:** Đúng/Sai: Product Owner có thể là một committee.
**A:** SAI. Product Owner is ONE person, not a committee.

## Flashcard 15
**Q:** 4 sub-classes của Development life cycle SQA components?
**A:** Formal design reviews, Peer reviews, Expert opinions, Software testing.

## Flashcard 16
**Q:** Liệt kê Project Factors ảnh hưởng QA intensity?
**A:** (1) Magnitude of project; (2) Technical complexity & difficulty; (3) Extent of reusable software components; (4) Severity of failure outcomes.

## Flashcard 17
**Q:** Liệt kê Team Factors ảnh hưởng QA intensity?
**A:** (1) Professional qualifications của team members; (2) Team acquaintance với project + experience; (3) Availability of supporting staff; (4) Percentage of new staff members.

## Flashcard 18
**Q:** Bốn testing levels theo thứ tự?
**A:** Unit testing → Integration testing → System testing → Acceptance testing.

## Flashcard 19
**Q:** Bốn phases của unit test case?
**A:** Set up → Exercise → Verify → Teardown.

## Flashcard 20
**Q:** Hai chiến lược integration testing và đặc điểm?
**A:** Top-down (từ main control xuống, depth-first hoặc breadth-first, cần stubs); Bottom-up (từ lowest levels lên, cần drivers).

## Flashcard 21
**Q:** Ai chịu trách nhiệm acceptance testing?
**A:** KHÔNG phải development team. Thường là customer hoặc independent party; usually black-box testing với real/customer data.

## Flashcard 22
**Q:** Công thức prioritize modules để test?
**A:** C = k·A + m·B, trong đó A = Severity (damage to life/finance/essential functions), B = Risk (probability of failure based on complexity + programmer experience).

## Flashcard 23
**Q:** 5 cách terminate testing?
**A:** (1) Completed Implementation; (2) Mathematical Models (error detection rate giảm); (3) Error Seeding; (4) Dual Teams comparison; (5) Resource Limit (time/budget).

## Flashcard 24
**Q:** 4 tài liệu chính trong testing process?
**A:** STP (Software Test Plan), STD (Software Test Description), STR (Software Test Report), TSR (Test Summary Report).

## Flashcard 25
**Q:** Theo defect cost model, fix bug sau release đắt gấp bao nhiêu lần so với requirement phase?
**A:** Khoảng 110 lần (110×).

## Flashcard 26
**Q:** Công thức tính Removed Defects và Passed Defects?
**A:** Removed Defects = Input Defects × % Effectiveness; Passed Defects = Input Defects - Removed Defects.

## Flashcard 27
**Q:** Hai mục tiêu chính (objectives) của defect removal model?
**A:** (1) Total Effectiveness (khả năng remove defects); (2) Total Cost (resources required).

## Flashcard 28
**Q:** 4 direct objectives của reviews?
**A:** (1) Error Detection; (2) Risk Identification; (3) Standardization; (4) Approval.

## Flashcard 29
**Q:** 2 indirect objectives của reviews?
**A:** (1) Knowledge Exchange; (2) Process Improvement.

## Flashcard 30
**Q:** Golden Rule của review meeting?
**A:** Detect errors only – DO NOT design solutions on the spot.

## Flashcard 31
**Q:** Optimal size của review team?
**A:** 3 đến 5 members.

## Flashcard 32
**Q:** Max duration của một review session?
**A:** 2 hours.

## Flashcard 33
**Q:** 4 bước trong DR session agenda?
**A:** (1) Presentation; (2) Discussion; (3) Verification; (4) Decision.

## Flashcard 34
**Q:** 3 outcomes (decisions) khả dĩ của DR team?
**A:** (1) Full Approval; (2) Partial Approval; (3) Denial of Approval.

## Flashcard 35
**Q:** 4 yêu cầu (characteristics) của DR Review Leader?
**A:** Knowledge (kinh nghiệm dự án cùng loại), Seniority (ngang/cao hơn Project Leader), Position (ngoài project team), Relationship (rapport tốt).

## Flashcard 36
**Q:** Sự khác biệt cốt lõi giữa DR và Peer Review về authority?
**A:** DR có quyền approve để qua phase tiếp; Peer Review KHÔNG có authority approve.

## Flashcard 37
**Q:** Inspection vs Walkthrough – ai là presenter?
**A:** Inspection: presenter usually NOT the author (thường là Coder); Walkthrough: presenter usually IS the author.

## Flashcard 38
**Q:** Specialized roles trong Inspection và Walkthrough?
**A:** Inspection: Designer, Coder, Tester. Walkthrough: Standards Enforcer, Maintenance Expert, User Representative.

## Flashcard 39
**Q:** 6 steps của Fagan Inspection theo thứ tự?
**A:** Planning → Overview → Preparation → Meeting (Inspection) → Rework → Follow-up.

## Flashcard 40
**Q:** Severity classification cho defects trong Inspection?
**A:** Critical / Major / Minor.

## Flashcard 41
**Q:** Coverage typical của peer reviews?
**A:** 5–15% of documents (focus on high-risk, complex, defect-prone sections).

## Flashcard 42
**Q:** Reports từ Inspection gửi tới đâu để analyze trends?
**A:** Corrective Action Board (CAB).

## Flashcard 43
**Q:** Latency Rule của UI feedback?
**A:** System phải response trong < 0.1s (100ms).

## Flashcard 44
**Q:** Phân biệt Click, Ctrl+Click, Shift+Click trong selection?
**A:** Click = Select One; Ctrl+Click = Select Multiple (rời rạc); Shift+Click = Select Range (liên tục).

## Flashcard 45
**Q:** UI Principle "Mental Models" – UI nên reflect cái nào?
**A:** User's Mental Model (simple & fluid), KHÔNG phải Implementation Model (complex & rigid).

## Flashcard 46
**Q:** 3 thành phần của Visual Hierarchy?
**A:** Size (lớn hơn = quan trọng), Contrast (primary stand out), Position (F-Pattern hoặc center).

## Flashcard 47
**Q:** Affordance: Raised, Recessed, Grab handles biểu thị gì?
**A:** Raised (3D) = "Click me"; Recessed (inset) = "Fill me"; Grab handles = "Drag me".

## Flashcard 48
**Q:** 4 states của icon và cách thể hiện?
**A:** Normal (standard, high contrast); Hover (glow/brighten/lift); Active/Pressed (darker/inset/size reduced); Disabled (greyscale/ghosted/reduced opacity).

## Flashcard 49
**Q:** Golden Rule of Icon Labeling?
**A:** Always use text labels or tooltips vì icons inherently ambiguous (Star = Favorite? Rating? New?).

## Flashcard 50
**Q:** Sections chính của IEEE 829 Test Plan?
**A:** Introduction, Test Items, Features to be Tested, Features NOT to be Tested, Approach, Pass/Fail Criteria, Suspension Criteria & Resumption Requirements, Test Deliverables, Testing Tasks/Schedule, Environmental Needs, Staffing & Training, Responsibilities, Risks & Contingencies, Approvals.

## Flashcard 51
**Q:** Điền vào chỗ trống: "No ____ = No release" trong Scrum.
**A:** Definition of Done.

## Flashcard 52
**Q:** Pressman: tối đa team size cho DR và max duration?
**A:** 3-5 members; max 2 hours.

## Flashcard 53
**Q:** Tutorial 7 yêu cầu tạo những deliverables gì?
**A:** Test plan, test design (theo template), implementing the test, test report.

## Flashcard 54
**Q:** Eliminate Excise – examples?
**A:** Resizing/moving windows constantly; dismissing unnecessary pop-up dialogs; re-entering data đã provided.

## Flashcard 55
**Q:** Smart Software memory – cần nhớ những gì?
**A:** Window position/size; last opened file/view; toggle states; settings. "Do what I did last time."
