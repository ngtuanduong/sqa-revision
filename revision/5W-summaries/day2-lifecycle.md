# Day 2 – Lifecycle, Reviews & UI – Easy-to-Absorb Edition

Tổng hợp 4 lectures (5–8) + 3 tutorials (5–7). Mỗi concept gồm:
- **Hook/Ẩn dụ**: gợi nhớ trong 1–2 dòng (chỉ khi giúp ghi nhớ)
- **Core**: nội dung cốt lõi gọn
- **Bảng/Diagram**: visual hoá khi cần so sánh / có quy trình
- **Mnemonic**: chữ cái đầu hoặc vần
- **Bẫy / Self-check**: câu hỏi tự kiểm hay vào đề
- **Dẫn chứng**: trích slide gốc (giữ nguyên 100%)

---

## Bản đồ Day 2 — đọc 30 giây trước khi vào chi tiết

```
LECTURE 5 ── "Vòng đời phần mềm chạy thế nào?"
              SDLC Models: Waterfall (thác nước) / Prototyping (lặp)
                           / Spiral (vòng xoáy rủi ro) / Agile (ngược Waterfall)
              Scrum: 3 Roles + 5 Events + 3 Artifacts + 5 Values
              SQA trong lifecycle: Development stage + Operation–maintenance stage

LECTURE 6 ── "Lồng ghép QA vào dev — bao nhiêu là vừa?"
              QA intensity = Project factors + Team factors
              10 Testing principles / 4 Testing levels (Unit→Integration→System→Acceptance)
              Test process 4 phases / Prioritization C = kA + mB
              5 Termination criteria / 4 docs (STP-STD-STR-TSR)
              Defect Removal Model / Rule of 10x-110x

LECTURE 7 ── "Review là rào chắn lỗi"
              3 nhóm methodologies: Formal DR / Peer Review (Inspection+Walkthrough) / Expert
              DR = authority gate (cần approval) — 13 DRs, 3-5 members, max 2h
              Peer Review = detect-only (không approve) — 5–15% docs
              Fagan 6 steps: Plan→Overview→Prep→Meeting→Rework→Follow-up

LECTURE 8 ── "UI Review — đo bằng mắt user"
              Mental Model > Implementation Model
              Excise (việc thừa của tool) phải eliminate
              Safe Exploration / Smart Software / Affordance / Visual Hierarchy
              Icon: metaphor + label + 4 states

TUTORIALS ── T5 Authentication / T6 CRUD / T7 Test Planning (STP-STD-STR-TSR)
```

**Mnemonic cả ngày**: `LIFECYCLE - INTEGRATE - REVIEW - UI` (L-I-R-U) → mỗi lecture trả lời 1 câu: vòng đời thế nào, lồng QA ra sao, review thế nào, UI review ra sao.

---

## LECTURE 5 — Software Development Life Cycle

### 1. Waterfall Model

> **Ẩn dụ**: "Thác nước chảy 1 chiều" — nước rơi xuống rồi không quay lên được. Phase sau chỉ bắt đầu khi phase trước đã kết thúc và được approve.

**Core**: Mô hình SDLC cổ điển, mô tả **7 phases tuần tự**.

```
Requirements ──▶ Analysis ──▶ Design ──▶ Coding ──▶ System Tests
                                                          │
                                                          ▼
                            Operation & Maintenance ◀── Installation & Conversion
```

**End-of-Phase Review** — mỗi phase kết thúc bằng review, có 3 outcomes:
1. **Approve** → tiếp tục phase sau
2. **Request correction** → sửa rồi review lại
3. **Return to earlier phases** → quay về phase trước

**Where/When dùng**: requirements ổn định, công nghệ quen thuộc, rủi ro thấp.

**Bẫy**: "Waterfall không cho quay lại phase trước" → **SAI**. Có thể return to earlier phases nếu review phát hiện lỗi gốc.

- **Dẫn chứng**: Phase 4 Coding bao gồm inspection, unit tests, integration tests; Phase 7 Maintenance gồm Corrective, Adaptive, Perfective.

---

### 2. Prototyping Model

> **Ẩn dụ**: "Vẽ phác thảo trước, vẽ tranh sau". Xây bản mẫu nhanh, để user sờ thử, rồi chỉnh.

**Core**: Mô hình **tiến hoá**, dùng application generators để xây prototype nhanh, lặp lại đến khi đạt mục tiêu.

```
   ┌──────────────────────────────────────────┐
   │  Build Prototype → User examines → Feedback │
   │           ↑                            ↓        │
   │           └──────── Refine ◀───────────┘        │
   └──────────────────────────────────────────┘
              Lặp đến khi đạt prototyping goal
```

**Where/When**: dự án **small- to medium-sized**, requirements chưa rõ, cần giao tiếp trực quan giữa dev và user.

**Why (lợi ích)**:
- Rút ngắn development
- Tiết kiệm man-days
- Fit customer requirements tốt hơn
- Giảm rủi ro thất bại

**Bẫy**: "Prototyping luôn cho chất lượng cao" → **SAI**. Có thể neglect long-term maintainability.

- **Dẫn chứng**: Nhược điểm: có thể neglect software quality và long-term maintainability.

---

### 3. Spiral Model

> **Ẩn dụ**: "Vòng xoáy đo rủi ro" — mỗi vòng spiral phình to thêm, qua 4 ô (plan → risk → engineer → evaluate).

**Core**: Kết hợp **iterative nature** của prototyping + **controlled/systematic** aspects của waterfall.

**Boehm 1998 advanced spiral** — mỗi vòng spiral có 4 khu:

```
       ┌──────────────┐         ┌──────────────┐
       │  PLANNING    │ ─────▶  │ RISK ANALYSIS│
       │ (mục tiêu)   │         │ (đánh giá)   │
       └──────────────┘         └──────┬───────┘
              ▲                        │
              │                        ▼
       ┌──────┴───────┐         ┌──────────────┐
       │  EVALUATION  │ ◀────── │  ENGINEERING │
       │ (validate)   │         │ (build+test) │
       └──────────────┘         └──────────────┘
```

**Where/When**: dự án **lớn, phức tạp, rủi ro cao**; requirements có thể thay đổi muộn.

**Pros**: cho phép áp dụng prototyping ở bất kỳ stage; cho phép thay đổi requirements muộn.

**Cons**: khó quản lý thời gian, dễ thất bại nếu không xét rủi ro, time-consuming.

- **Dẫn chứng**: Cons: khó quản lý thời gian, dễ thất bại nếu không xét rủi ro, time-consuming.

---

### 4. So sánh nhanh 3 mô hình "cổ điển"

|              | **Waterfall**         | **Prototyping**         | **Spiral**                |
|--------------|-----------------------|-------------------------|---------------------------|
| Bản chất     | Tuần tự 1 chiều       | Lặp evolutionary        | Lặp + risk-driven         |
| Requirements | Phải rõ từ đầu        | Chưa rõ                 | Có thể thay đổi muộn      |
| Quy mô       | Mọi size              | Small–medium            | Lớn, phức tạp             |
| Rủi ro       | Thấp                  | Trung bình              | Cao                       |
| Điểm yếu     | Cứng nhắc             | Bỏ quên maintainability | Time-consuming            |

---

### 5. Agile Manifesto

> **Ẩn dụ**: "Ngược lại Waterfall" — thay vì plan tất cả rồi mới làm, thì làm nhỏ, thích ứng nhanh.

**Core**: 4 cặp value statements — **left-side được coi trọng hơn nhưng right-side vẫn có giá trị**:

| Coi trọng hơn (left)                | Hơn là (right)                    |
|-------------------------------------|------------------------------------|
| Individuals & interactions          | processes & tools                  |
| Working software                    | comprehensive documentation        |
| Customer collaboration              | contract negotiation               |
| Responding to change                | following a plan                   |

**Mnemonic**: **I-W-C-R** (Individuals - Working - Collaboration - Responding) → 4 thứ Agile ưu tiên.

**How implement**: qua các frameworks — **XP, Scrum, Kanban, Crystal, DSDM, FDD**.

**Bẫy**: "Agile = không cần documentation" → **SAI**. Documentation vẫn có giá trị, chỉ là working software được coi trọng hơn.

- **Dẫn chứng**: 4 cặp value statements – left-side được coi trọng hơn nhưng right-side vẫn có giá trị.

---

### 6. Scrum Framework — Tổng quan

> **Ẩn dụ**: "Đội rugby scrum" — cả team chụm đầu, cùng đẩy về 1 hướng, lightweight, không có thứ bậc cứng nhắc.

**Core**: Lightweight framework giúp teams/orgs tạo value qua **adaptive solutions** cho **complex problems**; **purposefully incomplete** (cố tình chưa đầy đủ — bạn ráp thêm tuỳ context).

**3 trụ cột (Pillars) — T-I-A**:
- **T**ransparency
- **I**nspection
- **A**daptation

**Cấu trúc Scrum**: **3 Roles + 5 Events + 3 Artifacts + 5 Values**

**5 Values — C-F-O-R-C** ("Cá Fọc Ốc Rượu Cay"):
- **C**ommitment
- **F**ocus
- **O**penness
- **R**espect
- **C**ourage

- **Dẫn chứng**: Team ≤ 10 người, cross-functional, self-managing, không sub-teams.

---

### 7. Scrum Roles (3 Accountabilities)

> **Mnemonic**: **PO-SM-Dev** (Product Owner / Scrum Master / Developers).

| Role             | Trách nhiệm chính                                                  |
|------------------|--------------------------------------------------------------------|
| **Product Owner**| Quản lý **Product Backlog** — maximize value of product            |
| **Scrum Master** | Thiết lập Scrum, **remove impediments** — "true leader who serves" |
| **Developers**   | Tạo **Increment** + **Sprint Backlog** + adhere to **Definition of Done** |

**Bẫy (cực hay vào đề)**:

| Câu hỏi                                    | Đáp án                                  |
|--------------------------------------------|-----------------------------------------|
| PO là 1 committee?                         | **SAI** — PO is **ONE person**          |
| SM là người ra lệnh cho team?              | **SAI** — SM là **leader who serves**   |
| PO tạo ra Increment?                       | **SAI** — **Developers** tạo Increment  |
| Scrum có sub-teams?                        | **SAI** — không sub-teams, ≤ 10 người   |

- **Dẫn chứng**: PO is ONE person, NOT a committee; SM is a "true leader who serves".

---

### 8. Scrum Events (5 events)

> **Mnemonic**: **S-P-D-R-R** ("Sprint Plans Daily Reviews Retro"):
> **S**print (container) / **P**lanning / **D**aily / **R**eview / **R**etrospective.

```
┌──────────────────────────────────────────────────────────────────┐
│                    THE SPRINT (≤ 1 month container)              │
│                                                                  │
│  Sprint Planning  ──▶  Daily Scrum (15')  ──▶  Sprint Review    │
│  (đầu Sprint)         (mỗi ngày)              (cuối Sprint)     │
│        │                                            │           │
│        └──────────────────────────────────────▶  Retrospective  │
│                                                  (concludes)    │
└──────────────────────────────────────────────────────────────────┘
```

**Sprint Planning trả lời 3 câu**:
1. **Why** is this Sprint valuable?
2. **What** can be Done this Sprint?
3. **How** will the chosen work get done?

**Timeboxes**:
- Sprint: **≤ 1 tháng**
- Daily Scrum: **15 phút** mỗi ngày

**Why (lợi ích)**: tạo regularity, giảm các meeting khác, đảm bảo transparency–inspection–adaptation.

- **Dẫn chứng**: Daily Scrum cho Developers inspect progress; Retrospective concludes Sprint.

---

### 9. Scrum Artifacts (3 + 3 Commitments)

> **Hook**: Mỗi artifact đi kèm 1 commitment — như "lời thề" để giữ transparency.

| Artifact            | Cấp        | Commitment đi kèm        |
|---------------------|------------|--------------------------|
| **Product Backlog** | Product    | **Product Goal**         |
| **Sprint Backlog**  | Sprint     | **Sprint Goal**          |
| **Increment**       | Sprint output | **Definition of Done** |

**Mnemonic**: **PB-SB-Inc** → **PG-SG-DoD**.

**Bẫy**: "Không có Definition of Done có release được không?"
→ **KHÔNG** — *No Definition of Done = No release.*

**Why**: Maximize **transparency** of key information.

- **Dẫn chứng**: No Definition of Done = No release.

---

### 10. SQA Components in Project Life Cycle

> **Hook**: SQA chia đôi vòng đời — trước/sau khi release.

**Core**: SQA chia 2 stages:

```
┌─────────────────────────────────────┬────────────────────────────────────┐
│ DEVELOPMENT LIFE CYCLE STAGE        │ OPERATION-MAINTENANCE STAGE        │
│  → detect design/programming errors │  → corrective + improvements       │
├─────────────────────────────────────┼────────────────────────────────────┤
│ 4 sub-classes:                      │ - Corrective: specialized components│
│  1. Formal design reviews           │ - Improvements: reuse dev components│
│  2. Peer reviews                    │ - External participants             │
│  3. Expert opinions                 │   (subcontractors → reduce risk)    │
│  4. Software testing                │                                    │
└─────────────────────────────────────┴────────────────────────────────────┘
```

- **Dẫn chứng**: Operation Stage – Corrective dùng specialized components; Improvements reuse development components; External participants (subcontractors) để giảm risk outsourcing.

---

## LECTURE 6 — Integrating Quality Activities

### 1. Factors Affecting QA Intensity

> **Hook**: "Liều thuốc QA" — dự án càng to/lạ/người mới càng nhiều → tăng liều.

**Core**: 2 nhóm yếu tố quyết định mức tập trung QA:

| **Project Factors**                       | **Team Factors**                          |
|-------------------------------------------|-------------------------------------------|
| Project **Magnitude**                     | Professional **qualifications**           |
| **Technical complexity**                  | Team **acquaintance** (kinh nghiệm cùng nhau) |
| Extent of **reusable components**         | Availability of **supporting staff**      |
| **Severity of failure outcomes** ⚠ essential! | **% new staff** members              |

**Mnemonic** — Project: **M-T-R-S** / Team: **Q-A-A-N**.

**Bẫy**: Yếu tố nào "essential" theo slide gốc?
→ **Severity of failure outcomes** (mức nghiêm trọng nếu lỗi xảy ra).

- **Dẫn chứng**: Severity of failure outcomes is "essential!"; % new staff – nhiều người mới cần QA chặt hơn.

---

### 2. 10 Testing Principles

> **Hook**: "10 điều răn của tester" — đa số xoay quanh 1 ý: tester phải khách quan + paranoid.

**Core** (đánh số theo slide gốc):

1. **Programmers không test code của chính họ** (over-familiarity)
2. **Tester độc lập**
3. **Positive Pessimism mindset** — luôn nghĩ "ở đâu cũng có bug"
4. **Probability of more errors** — nơi đã có lỗi thì khả năng có thêm cao
5. **Intellectually Challenging** — test là việc trí tuệ
6. **Mandatory: Expected Output** — phải có expected output trước
7. **Beyond the Happy Path** — test cả trường hợp xấu
8. **Verify what it should NOT do** — kiểm cả việc *không được làm*
9. **Meticulous result checking** — soi kỹ kết quả
10. **Design for Regression** — thiết kế test để chạy lại được

**Bẫy**: "Tester chỉ cần test happy path" → **SAI** — vi phạm nguyên tắc 7.

- **Dẫn chứng**: Programmers không thể tự test code mình do over-familiarity.

---

### 3. Testing Levels (4)

> **Mnemonic**: **U-I-S-A** ("Unit Integration System Acceptance") — đi từ nhỏ → to → user.

```
   Unit ──▶ Integration ──▶ System ──▶ Acceptance
  (module) (ghép modules)   (toàn bộ)   (user/customer)
```

| Level           | Phạm vi                | Khi nào                       |
|-----------------|------------------------|-------------------------------|
| **Unit**        | 1 module               | Khi code module xong          |
| **Integration** | Ghép modules           | Khi ghép modules              |
| **System**      | Toàn bộ system + UI    | Khi có toàn bộ system         |
| **Acceptance**  | Black-box, real data   | Trước release cho customer    |

**Unit Test — 4 phases**: **Set up → Exercise → Verify → Teardown**.

**Bẫy (CỰC HAY vào đề)**: "Acceptance test do development team làm phải không?"
→ **SAI** — Acceptance: development team should **NOT** be responsible.

- **Dẫn chứng**: Acceptance – development team should NOT be responsible.

---

### 4. Integration Testing Strategies — Top-down vs Bottom-up

|                  | **Top-down**                | **Bottom-up**                  |
|------------------|-----------------------------|--------------------------------|
| Hướng đi         | Từ **main module** xuống    | Từ **lowest-level** components lên |
| Cần viết         | **Stubs** (giả module dưới) | **Drivers** (giả module trên)  |
| Sub-strategy     | Depth-first / Breadth-first | (lên dần theo level)           |

**Mnemonic**: **Top → Stub**, **Bottom → Driver** (T-S / B-D).

- **Dẫn chứng**: Top-down cần stubs; Bottom-up cần drivers.

---

### 5. Testing Process — 4 Phases

```
1. Determining Test Methodology ──▶ 2. Planning the Tests
                                              │
                                              ▼
4. Test Implementation     ◀──────── 3. Test Design
```

**Methodology** gồm: chuẩn chất lượng + chiến lược (**Big Bang vs Incremental**, **Top-down vs Bottom-up**, **White Box**, **Automated**).

**Planning trả lời 5 câu (5W)**:
1. **What** to test
2. **Sources** (test data sources)
3. **Who** thực hiện
4. **Where** thực hiện
5. **When** to terminate

**Bẫy**: "Methodology cho medical software giống internal training không?"
→ **KHÔNG** — Medical cần chuẩn cao nhất; internal training chỉ cần medium.

- **Dẫn chứng**: Medical software cần chuẩn cao nhất; internal training chỉ cần medium.

---

### 6. Prioritization Formula — C = kA + mB

> **Hook**: Không có resource test mọi thứ → ưu tiên module nào điểm C cao nhất.

```
   C  =  k · A  +  m · B
   ▲        ▲          ▲
   │        │          └─ Risk (probability of failure)
   │        │             = complexity + programmer experience
   │        └──────────── Severity (damage)
   │                      = life / finance / essential functions
   └─────────────────── Priority score
        k, m = weights
```

**Rule**: A cao + B cao → C cao → test trước.

- **Dẫn chứng**: Modules có A và B cao → C cao → test trước.

---

### 7. Test Termination Criteria (5)

> **Hook**: Khi nào nói "test đủ rồi"? — 5 cách:

| #  | Criterion                | Nghĩa                                                |
|----|--------------------------|------------------------------------------------------|
| 1  | **Completed Implementation** | All tests clean (không còn lỗi nào)              |
| 2  | **Mathematical Models**  | Error detection rate giảm đến mức chấp nhận          |
| 3  | **Error Seeding**        | Chèn lỗi nhân tạo → tìm đủ % seed → dừng             |
| 4  | **Dual Teams**           | So sánh 2 team độc lập                               |
| 5  | **Resource Limit**       | Hết budget/time                                      |

**Mnemonic**: **C-M-E-D-R** ("Complete-Math-Errseed-Dual-Resource").

- **Dẫn chứng**: Error seeding – chèn lỗi nhân tạo, đánh giá tỷ lệ phát hiện.

---

### 8. Testing Documentation (4 docs)

> **Mnemonic**: **STP - STD - STR - TSR** (Plan → Description → Report → Summary).

| Doc     | Tên đầy đủ                | Khi nào                       |
|---------|---------------------------|-------------------------------|
| **STP** | Software **Test Plan**    | Đầu (Planning phase)          |
| **STD** | Software **Test Description** | Trong Design phase        |
| **STR** | Software **Test Report**  | Sau mỗi test/re-test          |
| **TSR** | **Test Summary Report**   | Cuối cùng                     |

**Bẫy**: STD chứa gì? → test **procedures + test cases** (không phải overall plan).

- **Dẫn chứng**: STD documents test procedures + test cases; TSR summarizes toàn bộ testing project.

---

### 9. Defect Removal Model

> **Hook**: "Mô hình kế toán lỗi" — đo Total Effectiveness + Total Cost của SQA plan.

**Công thức cốt lõi**:

```
Input Defects   = New Defects + Passed Defects (từ phase trước)
Removed         = Input × % Effectiveness
Passed Defects  = Input - Removed (đi sang phase sau)
TRC (Total Removal Cost) = Removed × Cost Unit
```

**Where**: áp dụng cho **linear (waterfall)** development process.

**Why**: chứng minh giá trị kinh tế của **early SQA investment**.

- **Dẫn chứng**: Dựa trên data lịch sử của IBM, TRW, Boehm.

---

### 10. Cost of Defect Removal — Rule of 10x / 110x

> **Hook**: "Bug càng già càng đắt" — như răng sâu để lâu phải nhổ.

```
   Requirements ──▶ Design ──▶ Coding ──▶ Testing ──▶ RELEASE
       1x            ~5x        ~10x      ~20x        110x
                            (chi phí sửa lỗi)
```

**Insight**: Fixing a bug after release ≈ **110× more expensive** than fixing during requirements.

**Bẫy**: "Lỗi chỉ phát sinh ở coding" → **SAI**. Defects origin phân bố khắp lifecycle.

- **Dẫn chứng**: Defects origin phân bố khắp lifecycle, không chỉ coding.

---

## LECTURE 7 — Reviews

### 1. Review Objectives

> **Hook**: "Hai con mắt khác sáng hơn một" — review = mời người khác soi việc mình.

**Core**: Process/meeting trình bày work product cho personnel để **comment hoặc approve**.

**Why** (2 trục lớn): **Early Detection** + **Cost Reduction** (phát hiện sớm rẻ hơn nhiều — liên kết Rule of 110x).

**Direct objectives** (4):
1. **Error Detection**
2. **Risk Identification**
3. **Standardization**
4. **Approval**

**Indirect objectives** (2):
5. **Knowledge Exchange**
6. **Process Improvement**

**Strategy**: "**Double or triple net**" — kết hợp nhiều methodologies.

- **Dẫn chứng**: "Double or triple net" strategy – kết hợp nhiều methodologies.

---

### 2. Review Methodologies — 3 nhóm

```
┌─────────────────────────────────────────────────────────┐
│ 1. FORMAL DESIGN REVIEWS (DRs)  → cần approval         │
│ 2. PEER REVIEWS (2 forms)                              │
│    ├─ Inspection (formal hơn)                          │
│    └─ Walkthrough (informal hơn)                       │
│ 3. EXPERT OPINIONS              → mời chuyên gia       │
└─────────────────────────────────────────────────────────┘
```

**Who tham gia**: peers, superiors, external experts, customer reps.

**Why**: tận dụng external viewpoints; **author không tự thấy lỗi mình**.

- **Dẫn chứng**: Peers, superiors, external experts, customer reps đều có thể tham gia.

---

### 3. Principles for Effective Reviews

> **Hook**: Review không phải "buổi tán phét" — phải có cấu trúc.

**3 thành phần**:
1. **Structured approach** (theo agenda)
2. **Key roles**: **Coordinator** (giữ on-track) + **Scribe** (record defects chi tiết)
3. **Golden Rule**: **Detect errors only, DO NOT design solutions on the spot.**

**Bẫy**: "Trong review tìm được lỗi xong sửa luôn cho nhanh" → **SAI** — vi phạm Golden Rule.

- **Dẫn chứng**: Procedural order, not haphazard.

---

### 4. Formal Design Reviews (DRs / FTR)

> **Hook**: "Cửa khẩu" giữa các phases — không có DR approval, không qua được cửa.

**Core**: Còn gọi **Formal Technical Reviews**. **Without DR approval, dev team CANNOT continue.**

**Khi nào**: Khi document phase hoàn thành (Requirement Specification, Installation Plan…).

**13 common DRs** (đánh số trong slide gốc):

| #  | Viết tắt | Tên                                     |
|----|----------|-----------------------------------------|
| 1  | DPR      | Development Plan Review                 |
| 2  | SRSR     | Software Requirement Specification Review |
| 3  | PDR      | **Preliminary Design Review**           |
| 4  | DDR      | Detailed Design Review                  |
| 5  | DBDR     | Database Design Review                  |
| 6  | TPR      | Test Plan Review                        |
| 7  | STPR     | Software Test Procedure Review          |
| 8  | VDR      | Version Description Review              |
| 9  | OMR      | Operations Manual Review                |
| 10 | SMR      | Software Manual Review                  |
| 11 | TRR      | Test Readiness Review                   |
| 12 | PRR      | **Product Release Review**              |
| 13 | IPR      | Installation Plan Review                |

- **Dẫn chứng**: PDR = Preliminary Design Review; PRR = Product Release Review.

---

### 5. Review Leader (DR)

> **Hook**: "Trọng tài chuyên môn" — phải khách quan, ngoài team, đủ senior.

**4 yêu cầu — K-S-P-R**:

| Yêu cầu          | Nội dung                                                 |
|------------------|----------------------------------------------------------|
| **K**nowledge    | Kinh nghiệm dự án cùng loại                              |
| **S**eniority    | Ngang/trên Project Leader                                |
| **P**osition     | **Ngoài project team** (ví dụ QA Manager, Chief SE)      |
| **R**elationship | Rapport tốt với team                                     |

- **Dẫn chứng**: QA Manager hoặc Chief Software Engineer.

---

### 6. DR Team & Size

**Composition**:
- Senior team members
- Senior pros từ projects khác
- Customer/User reps
- **Non-project staff nên là majority**

**Optimal size**: **3–5 members** (Pressman).

**Bẫy**: "Càng đông review càng kỹ" → **SAI** — quá lớn → waste time + coordination problem.

- **Dẫn chứng**: Pressman: Limit team size 3-5 members.

---

### 7. DR Session Agenda — 4 Steps

```
1. Presentation  ──▶  2. Discussion  ──▶  3. Verification  ──▶  4. Decision
   (short overview)    (review team       (mỗi comment xét      (quyết định
                       comments)           corrections cần)      progress)
```

**Bẫy**: "Presentation là phần general project description" → **SAI** — là **short overview**, không phải mô tả dự án tổng quát.

**Max duration**: **2 hours** (hard limit).

- **Dẫn chứng**: Presentation là short overview, KHÔNG phải general project description.

---

### 8. DR Decision Outputs (3)

| #  | Outcome                     | Hành động                                  |
|----|-----------------------------|--------------------------------------------|
| 1  | **Full Approval**           | Minor corrections OK → tiếp tục            |
| 2  | **Partial Approval**        | Approved parts proceed; non-approved phải **re-review** |
| 3  | **Denial of Approval**      | **Repeat DR** (nhiều major/critical defects) |

- **Dẫn chứng**: Denial khi có nhiều major/critical defects.

---

### 9. Pressman Golden Guidelines

> **Hook**: "10 điều răn của Pressman" — chia 2 cấp (hạ tầng + buổi họp).

**Infrastructure** (chuẩn bị):
- Develop **checklists**
- Train **senior pros**
- Schedule DRs **in project plan**

**Session** (trong buổi):
- **3-5 members**
- Professional tone (**no personal attacks**)
- Stick to agenda
- **MAX 2 HOURS**
- **Focus on detecting defects, NOT solutions** (Golden Rule lặp lại)

- **Dẫn chứng**: Max duration 2 hours là hard limit.

---

### 10. Peer Reviews — Inspection vs Walkthrough

> **Hook**: Cùng là peer review, khác mức "formality".

**Bảng so sánh cực hay vào đề**:

|                    | **Inspection**                          | **Walkthrough**                       |
|--------------------|------------------------------------------|---------------------------------------|
| Formality          | **Cao hơn**                              | Thấp hơn                              |
| Mục tiêu phụ       | Corrective action + **process improvement** | (chỉ detect)                       |
| Author present?    | **KHÔNG** present (Presenter thường là Coder) | **CÓ** — author IS presenter      |
| Leader             | **Moderator**                            | **Coordinator**                       |
| Scribe records     | **Critical / Major / Minor** severity    | Findings report đơn giản              |
| Overview meeting?  | **CÓ**                                   | **KHÔNG**                             |

**Coverage**: 5–15% of documents (focus on high-risk sections).

**Bẫy LỚN**: "Peer review có thể approve document như DR không?"
→ **KHÔNG** — Peer reviews **NOT authorized to approve** document.

- **Dẫn chứng**: Peer reviews NOT authorized to approve document (unlike DR).

---

### 11. Inspection Process — Fagan 6 Steps

> **Mnemonic**: **P-O-P-M-R-F** ("Plan Overview Prep Meeting Rework Follow") — nhớ theo thứ tự.

```
1. Planning   ──▶ 2. Overview  ──▶ 3. Preparation
   (chọn material   (đào tạo team)    (đọc + checklist)
    + team)
                                            │
                                            ▼
6. Follow-up  ◀── 5. Rework    ◀── 4. Meeting/Inspection
   (verify fix)     (sửa)            (find defects)
```

**Bẫy phân biệt**: Inspection có **Overview meeting** cho team trước session — **Walkthrough thì không cần**.

- **Dẫn chứng**: Inspection có Overview meeting cho team trước session – Walkthrough thì không cần.

---

### 12. Peer Review Participants

**Optimal size**: **3–5**.

**Common roles**:
- **Leader**: Moderator (Inspection) / Coordinator (Walkthrough) — **từ ngoài project team**
- **Author**: **always participates**

**Specific roles**:

| Inspection         | Walkthrough             |
|--------------------|-------------------------|
| Designer           | Standards Enforcer      |
| **Coder** (presenter) | Maintenance Expert   |
| Tester             | User Representative     |

**Bẫy**: "Author là người present trong Inspection?" → **SAI** — Presenter trong Inspection thường là **Coder**, không phải Author.

- **Dẫn chứng**: Presenter trong Inspection thường là Coder, không phải Author.

---

### 13. Coverage & Efficiency Metrics

| Metric                       | Ý nghĩa                                        |
|------------------------------|------------------------------------------------|
| **Coverage**                 | **5–15%** documents (focus high-risk/complex/defect-prone) |
| **Hours per defect**         | Effort cost                                    |
| **Defect density**           | defects / page                                 |
| **Internal effectiveness**   | % defects by review vs testing                 |

**Reports gửi đâu**: **Corrective Action Board (CAB)** để analyze trends.

- **Dẫn chứng**: Reports gửi Corrective Action Board (CAB) để analyze trends.

---

## LECTURE 8 — UI Review

### 1. Why Review UI

> **Hook**: "UI tốt = vô hình" — user không nghĩ về tool, chỉ nghĩ về task.

**4 mục tiêu cốt lõi**:
1. **Reduce Excise** (việc thừa không phục vụ user)
2. **Improve User Efficiency**
3. **Prevent Cognitive Friction**
4. **Ensure Goal-Directed Design**

**4 hoạt động**:
- Evaluate Interaction Methods
- Standardize UI Elements
- Apply Core UI Principles
- Assess Icon Usage & Visuals

- **Dẫn chứng**: Excise = unnecessary effort that satisfies the tool not the user.

---

### 2. Direct Manipulation

> **Hook**: "Sờ trực tiếp" — kéo file vào folder, không phải mở dialog "Move to".

**Core**: Users tương tác **trực tiếp** với objects thay vì menus phức tạp.

**Where/When**: action có thể map sang gesture trực quan.

**Why**: giảm cognitive load, tăng speed.

- **Dẫn chứng**: Drag file to folder là ví dụ kinh điển.

---

### 3. Mouse Interaction & Selection

| Action                      | Hành vi mong đợi                  |
|-----------------------------|-----------------------------------|
| **Hover**                   | **Pliancy signal** (clickable)    |
| **Single click**            | Select / toggle                   |
| **Double click**            | Open (use sparingly **on web**)   |
| **Click**                   | Select **One**                    |
| **Ctrl+Click**              | Select **Multiple**               |
| **Shift+Click**             | Select **Range**                  |

**Bẫy**: "Double click dùng nhiều trên web" → **SAI** — hiếm dùng trên web.

- **Dẫn chứng**: Double click hiếm dùng trên web.

---

### 4. Feedback & Responsiveness

> **Hook**: "Bấm vào phải có cảm giác" — như công tắc đèn.

**Latency Rule**: phản hồi **< 0.1s** = ngưỡng "tức thì".

**Visual feedback patterns**:
- Buttons look **"pressed"**
- Drag shows **"ghost" image**

- **Dẫn chứng**: 0.1s là ngưỡng phản hồi tức thì.

---

### 5. Undo vs Confirmation

> **Hook**: "Are you sure?" làm gián đoạn — Undo cho phép thám hiểm an toàn.

| Approach              | Trải nghiệm                                |
|-----------------------|--------------------------------------------|
| **Confirmation dialog** | Interrupt flow                           |
| **Infinite Undo**     | Encourage **Safe Exploration** (trial & error) |

**Pattern điển hình**: **Trash Can** — soft-delete (Gmail, macOS).

- **Dẫn chứng**: Trash Can là pattern soft-delete.

---

### 6. Keyboard Accessibility

**3 cơ chế**:

| Cơ chế              | Ví dụ                                  |
|---------------------|----------------------------------------|
| **Accelerators**    | Ctrl+S, Ctrl+C                         |
| **Focus Ring**      | Visible khi Tab                        |
| **Mnemonics**       | Underlined letters (<u>F</u>ile)       |

**Why**: accelerators tăng speed cho power users; focus ring cho **a11y** (accessibility).

- **Dẫn chứng**: Focus ring phải visible.

---

### 7. UI Elements — 6 Categories

| Category             | Ví dụ                                              |
|----------------------|----------------------------------------------------|
| **Text Inputs**      | Text field, text area                              |
| **Buttons**          | Text / icon / text+icon, social                    |
| **Checkboxes & Radio** | Checkbox (nhiều), Radio (chọn 1)                 |
| **Dropdown & List boxes** |                                               |
| **Toggles**          | 2+ states                                          |
| **Navigational**     | Breadcrumb, Pagination, Carousel                   |
| **Informational**    | Badge, Tooltip, Message box                        |

**Bẫy**: "Toggle giống Radio button?" → **KHÔNG** — khác ở **số lượng state**.

- **Dẫn chứng**: Toggle khác từ radio button ở số lượng state.

---

### 8. Mental Model vs Implementation Model (CỰC HAY vào đề)

> **Hook**: User chỉ quan tâm "tôi muốn gì", không quan tâm "máy chạy thế nào".

|                     | **Mental Model (User)**   | **Implementation Model (Machine)** |
|---------------------|---------------------------|------------------------------------|
| Tính chất           | **Simple + fluid**        | **Complex + rigid**                |
| Ai hiểu             | User                      | Developer / OS                     |
| UI nên reflect      | ✅ Cái này                | ❌ Không phải cái này              |

**Rule**: UI phải reflect **User's Mental Model**, KHÔNG phải Implementation Model.

**How**: **Mask complexity**, đừng bắt user hiểu file system/database.

- **Dẫn chứng**: User không cần biết về schema database.

---

### 9. Safe Exploration Principle

> **Hook**: "Cho user nghịch — ai cũng học bằng cách thử sai."

**Core**: Users learn by **exploring, not reading manuals**.

**3 cơ chế**:
1. **Infinite Undo** (+ Redo)
2. **Avoid "Are you sure?"**
3. **Trash Can** cho soft deletes

- **Dẫn chứng**: Trash Can pattern phổ biến trong Gmail, macOS.

---

### 10. Eliminate Excise

> **Hook**: "Excise" = việc làm cho công cụ chứ không phục vụ task của user.

**Excise examples**:
- Resizing windows
- Dismissing pop-ups
- **Re-entering data**

**Rule**: Minimize navigation tasks → **zero**.

- **Dẫn chứng**: Re-entering data là excise điển hình.

---

### 11. Smart Software (Memory)

> **Hook**: "App đừng amnesia" — khởi động lại như chưa từng gặp user là tội lỗi.

**Core**: Software phải nhớ user preferences/state. Treat restart as **continuation**, không phải reset.

**Cần nhớ**:
- Window position/size
- Last opened file/view
- Toggle states
- Settings

**Slogan**: *"Do what I did last time."*

- **Dẫn chứng**: Restore last session pattern.

---

### 12. Visual Hierarchy

> **Hook**: "Users **scan**, không **read**" — mắt lướt theo trọng lực thị giác.

**3 đòn bẩy**:

| Đòn bẩy        | Nghĩa                                |
|----------------|--------------------------------------|
| **Size**       | Important = larger                   |
| **Contrast**   | Primary actions stand out            |
| **Position**   | **F-Pattern** hoặc center            |

- **Dẫn chứng**: F-Pattern reading layout.

---

### 13. Affordance

> **Hook**: "Form follows function" — nhìn vào biết cách dùng.

**Core**: Visual properties chỉ ra cách dùng object.

| Visual cue              | Affordance ngầm  |
|-------------------------|------------------|
| **Raised (3D)**         | "Click me"       |
| **Recessed (inset)**    | "Fill me"        |
| **Grab handles**        | "Drag me"        |

**Bẫy**: "Flat design luôn đẹp hơn" → cẩn thận — Flat ambiguous graphics **hide functionality**, nên tránh.

- **Dẫn chứng**: Flat ambiguous graphics hide functionality – avoid.

---

### 14. Responsiveness, Consistency, Visual Design (3 nguyên tắc bổ sung)

| Principle           | Yêu cầu                                                |
|---------------------|--------------------------------------------------------|
| **Responsiveness**  | Adapt to devices; touch targets usable on mobile; elements resized properly |
| **Consistency**     | Components / naming / styling đồng nhất                |
| **Visual Design**   | Sufficient contrast; readable + consistent font; intuitive icons |

- **Dẫn chứng**: Touch target minimum size cho mobile.

---

### 15. Icon Guidelines — Design Strategy

> **Hook**: "Icon = thông điệp 16px" — phải đọc được ở size nhỏ.

**3 nguyên tắc design**:
1. Use **real-world metaphors** (Trash, Folder, Gear)
2. **Readability at 16px / 24px** is priority
3. **Avoid excessive gradients/shadows** that blur at small scales

**Metaphor examples**: Gear = Settings, Trash = Delete.

- **Dẫn chứng**: Gear = Settings, Trash = Delete.

---

### 16. Icon Usability & Ambiguity

> **Hook**: "Star = Favorite? Rating? New?" — icon vốn dĩ mơ hồ.

**2 nguyên tắc**:
1. **Distinct silhouettes** (silhouette riêng biệt)
2. **Golden Rule of Labeling**: always use **text labels or tooltips**

**Rule**: Tooltip **mandatory** cho icon-only buttons.

- **Dẫn chứng**: Tooltip mandatory cho icon-only buttons.

---

### 17. Icon States & Feedback — 4 States

| State                | Visual                                       |
|----------------------|----------------------------------------------|
| **Normal**           | Standard, high contrast                      |
| **Hover**            | Glow, brighten, slight **lift** (pliancy)    |
| **Active/Pressed**   | Darker, inset, size reduction                |
| **Disabled**         | Greyscale/ghosted, reduced opacity           |

**Bẫy**: "Disabled icon vẫn click được không?" → **KHÔNG** — reduced opacity = non-interactive.

- **Dẫn chứng**: Hover lift = pliancy signal.

---

## TUTORIALS 5–7

### Tutorial 5 — Authentication Implementation

> **Hook**: "Cổng vào nhà" — không có khoá thì ai cũng vào được.

**Core**: Implement **register, login, logout** cho topic đã chọn ở Tutorial 4 - Activity 3.

**Where**: Project code base.

**When**: Sau khi có database design + tech stack.

**Why**: Authentication là **foundation** cho mọi user-based feature.

**How — 3 forms**:

| Form         | Việc cần làm                                          |
|--------------|--------------------------------------------------------|
| **Register** | Validation, **hash password**, store user             |
| **Login**    | Verify credential, create **session/JWT**             |
| **Logout**   | Destroy session/token                                  |

- **Dẫn chứng**: Common patterns: bcrypt hash, session cookies, JWT bearer tokens.

---

### Tutorial 6 — CRUD Implementation

> **Hook**: "4 chữ cái cầm trịch business app" — Create, Read, Update, Delete.

**Core**: Implement remaining features — **CRUD operations** cho domain entities.

**How — REST mapping**:

| Operation     | HTTP method            | Status codes        |
|---------------|------------------------|---------------------|
| **C**reate    | POST + form validation | 201                 |
| **R**ead      | GET list / GET detail (pagination) | 200, 404 |
| **U**pdate    | PUT / PATCH            | 200                 |
| **D**elete    | DELETE (confirmation / soft delete) | 200, 404 |

**Common status codes**: 200, 201, 400, 401, 404, 500.

- **Dẫn chứng**: REST conventions + status codes (200, 201, 400, 401, 404, 500).

---

### Tutorial 7 — Test Planning & Reporting

> **Hook**: "Đo trước, sửa sau" — viết plan trước khi test, viết report sau khi test.

**Core**: Create **test plan, test design (from template), implement test, make test report**.

**Flow** (liên kết với Lecture 6):

```
Test Plan (STP) ──▶ Test Design (STD) ──▶ Implementation ──▶ Test Report (STR/TSR)
```

**IEEE 829 template** — 11 sections:
1. Introduction
2. Test Items
3. Features to be Tested
4. Features **NOT** to be Tested
5. Approach
6. Pass/Fail Criteria
7. Suspension Criteria
8. Test Deliverables
9. Schedule
10. Staffing
11. Risks

- **Dẫn chứng**: Liên kết với Lecture 6 testing process (4 phases).

---

## Quick Reference — Tổng kết Day 2 trong 1 trang

### "Câu thần chú" cho mỗi lecture

| Lecture | Một câu tóm gọn                                                         |
|---------|--------------------------------------------------------------------------|
| **L5**  | SDLC = Waterfall (1 chiều) / Prototyping (lặp) / Spiral (rủi ro) / Agile-Scrum (3 Roles + 5 Events + 3 Artifacts + 5 Values) |
| **L6**  | QA intensity = Project + Team factors; Testing = 4 levels, 4-phase process, C = kA + mB, 5 termination criteria, 4 docs (STP-STD-STR-TSR); cost grows 1x→110x |
| **L7**  | Review = DR (cần approval, 3-5 ng, max 2h, 13 DRs) vs Peer (Inspection/Walkthrough, 5–15% docs, KHÔNG approve); Fagan 6 steps |
| **L8**  | UI Review = Mental Model > Implementation Model; eliminate Excise; Safe Exploration; Affordance; Icon = metaphor + label + 4 states |

### Top 10 bẫy hay vào đề

1. **PO là 1 người, KHÔNG phải committee** (Scrum Roles)
2. **Developers tạo Increment, KHÔNG phải PO** (Scrum Roles)
3. **No Definition of Done = No release** (Scrum Artifacts)
4. **Acceptance test, development team should NOT be responsible** (Testing Levels)
5. **DR cần approval (authority gate); Peer Review KHÔNG được approve document** (Review Methodologies)
6. **Inspection có Overview meeting; Walkthrough thì KHÔNG** (Peer Review)
7. **Inspection: Author KHÔNG present (Coder làm presenter); Walkthrough: Author IS presenter** (Peer Review)
8. **Golden Rule of Review: Detect errors only, DO NOT design solutions on the spot** (Reviews)
9. **UI phải reflect User Mental Model, KHÔNG phải Implementation Model** (UI Review)
10. **Severity of failure outcomes là factor "essential!" của QA intensity** (Lecture 6)
