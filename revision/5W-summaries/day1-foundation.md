# DAY 1 — Foundation (Easy-to-Absorb Edition)

Tổng hợp 4 lectures + 4 tutorials đầu tiên. Mỗi concept gồm:
- **Hook**: ẩn dụ/scenario gợi nhớ (chỉ khi cần)
- **Core**: nội dung cốt lõi
- **Visual**: bảng/diagram khi có list dài
- **Bẫy** / **Self-check**: câu hỏi tự kiểm thường gặp trong đề thi
- **Page**: dẫn chứng slide gốc

---

## Bản đồ Day 1 — đọc 30 giây trước khi vào chi tiết

```
LECTURE 1 ── "Software có lỗi → cần SQA"
              Software (4 phần) → Error/Fault/Failure → 8 causes
              → SQA = phòng ngừa, QC = phát hiện → Standards giúp gì

LECTURE 2 ── "Chất lượng đo bằng gì?"
              Functional req = WHAT it does
              Quality factors = HOW WELL it does
              McCall: 11 factors / 3 nhóm (Operation, Revision, Transition)
              Evans-Marciniak & Deutsch-Willis = biến thể (+Safety, +Verifiability...)

LECTURE 3 ── "Cách lắp ráp SQA System"
              6 lớp components: Pre-project → Lifecycle → Infrastructure
              → Management → Standards → Human

LECTURE 4 ── "Đo trước cắt sau"
              Pre-project = Contract Review (Proposal+Contract draft)
                          + Plans (Development + Quality)
              Bài học: Carnegie Fruits lỗ $90k vì bỏ sót 1 clause

TUTORIALS ── TDD (Red-Green-Refactor) + Use Case + ER/Class + Figma UI
```

**Mnemonic cả ngày**: `SOFTWARE-FACTORS-SYSTEM-PREPROJECT` (S-F-S-P) → mỗi lecture trả lời 1 câu: software là gì, đo chất lượng ra sao, ráp hệ thống thế nào, chuẩn bị trước khi code ra sao.

---

## LECTURE 1 — Introduction to SQA

### 1. Software (định nghĩa)

> **Ẩn dụ**: "Program" chỉ là *động cơ* xe. "Software" là cả *chiếc xe + sách hướng dẫn + lịch bảo dưỡng + danh bạ khách hàng*.

**Core**: "Software = Computer programs + procedures + documentation + data pertaining to operation of a computer system."

**4 thành phần lõi** (nhớ mnemonic **P-P-D-D**: Programs - Procedures - Documentation - Data):

| Thành phần    | Là gì                     |
|---------------|---------------------------|
| Programs      | Code chạy được            |
| Procedures    | Quy trình vận hành        |
| Documentation | Tài liệu (user/dev/admin) |
| Data          | Dữ liệu hệ thống          |

**Bẫy**: "Program = Software" → **SAI**. SQA quan tâm cả 4 phần, không chỉ code.

**Page**: Lecture 1, page 5–6.

---

### 2. Error → Fault → Failure

> **Ẩn dụ "quả mìn"**:
> - **Error** = tay run, gài sai dây kíp (dev gõ nhầm logic).
> - **Fault** = quả mìn đã chôn dưới đất, im lìm (code lỗi trong source).
> - **Failure** = ai đó dẫm phải → BOOM (user trigger code lỗi lúc runtime).

```
   [DEV gõ sai]      [Trong code]      [Runtime nổ]
      ERROR    ──▶     FAULT     ──▶    FAILURE
   (nguyên nhân)    (tiềm ẩn)        (bùng nổ ra user)
```

**Bẫy thường gặp** (đề hay hỏi):

| Câu hỏi                                | Đáp án                                                    |
|----------------------------------------|-----------------------------------------------------------|
| Mọi error đều thành fault?             | SAI — nếu đoạn code đó không tồn tại trong bản build cuối |
| Mọi fault đều thành failure?           | SAI — fault chỉ "nổ" khi được *activated* (chạy đến)      |
| Dev sửa bug trước commit → là gì?      | Error (chưa lên code base → không có fault)               |
| Bug trong dead-code không bao giờ chạy | Fault có, Failure không                                   |

**Page**: Lecture 1, page 7–8.

---

### 3. 8 Causes of Software Errors

> **Story**: Hãy hỏi *"Lỗi này sinh ra từ pha nào?"* — câu trả lời rơi vào 1 trong 8 ô dưới đây. Đề thi hay cho 1 tình huống và bắt phân loại nguyên nhân.

**Mnemonic** — chia theo pha SDLC:

```
REQUIREMENT pha:  (1) Faulty requirements definition
                  (2) Client-Developer communication failures
                  (3) Deliberate deviations from requirements
DESIGN pha:       (4) Logical design errors
CODING pha:       (5) Coding errors
                  (6) Non-compliance with instructions
TESTING pha:      (7) Shortcomings of the testing process
DOCS pha:         (8) Procedure and documentation errors
```

**Self-check**: Khách bảo "tôi muốn X" nhưng dev hiểu thành "Y" và làm Y → nguyên nhân số mấy?
→ **(2) Communication failure** (không phải (1) Faulty requirements vì requirements bản thân không sai, dev hiểu sai).

**Page**: Lecture 1, page 9–16.

---

### 4. Software Quality — 3 định nghĩa

> **Câu chuyện 3 góc nhìn**: cùng một chiếc bánh pizza:
> - **Crosby**: "Đúng công thức ghi trong thực đơn không?" (so với spec)
> - **Juran**: "Khách có hài lòng không?" (so với expectation)
> - **Pressman**: "Đúng spec + đúng chuẩn + có ngon theo good practices không?" (cả 3)

| Tác giả      | Năm  | Nội dung định nghĩa                                                  |
|--------------|------|----------------------------------------------------------------------|
| Crosby       | 1979 | meets **specified requirements**                                     |
| Juran        | —    | meets **customer needs/expectations**                                |
| **Pressman** | 2000 | conformance to explicit reqs + documented standards + implicit chars |

**Pressman = chuẩn nhất** vì gồm 3 lớp:
1. **Explicit Requirements** (functional + performance)
2. **Documented Standards** (chuẩn chất lượng trong hợp đồng)
3. **Implicit Characteristics** = GSEP (Good Software Engineering Practices: maintainability, readability…)

**Bẫy**: Nếu đề chỉ trích Crosby ("meets specified requirements"), nhớ rằng đây mới chỉ là 1 trong 3 góc nhìn — không phải định nghĩa "đầy đủ".

**Page**: Lecture 1, page 18–20.

---

### 5. SQA — Software Quality Assurance (định nghĩa)

> **Hook**: SQA = "kế hoạch toàn diện" để **đảm bảo** chất lượng, không phải mỗi việc testing cuối kỳ.

**Core**: *"A planned and systematic pattern of all actions necessary to provide **adequate confidence** that an item or product conforms to established technical requirements."*

**Mở rộng (rất hay hỏi)**: SQA còn cover:
- ✅ **Schedule** & **Budget** (không chỉ technical)
- ✅ Cả **Development** lẫn **Maintenance**

**Bẫy**: "SQA = Testing" → **SAI**. Testing chỉ là một phần. SQA = kế hoạch + tất cả activities + phòng ngừa.

**Page**: Lecture 1, page 21–22.

---

### 6. SQA vs SQC — phân biệt PROCESS vs PRODUCT

> **Ẩn dụ nhà máy bia**:
> - **SQC** = nhân viên nếm thử *từng chai bia* xuất xưởng (kiểm sản phẩm).
> - **SQA** = thiết kế cả *dây chuyền sản xuất* để bia ra lò luôn ngon (kiểm quy trình).

|                | **SQA** (Quality Assurance)       | **SQC** (Quality Control)       |
|----------------|-----------------------------------|---------------------------------|
| Đối tượng      | **Process** (quy trình)           | **Product** (sản phẩm)          |
| Mục tiêu       | **PREVENT** (phòng ngừa)          | **DETECT** (phát hiện)          |
| Thời điểm      | Xuyên suốt lifecycle              | Cuối phase / trước deploy       |
| Quan hệ        | QA ⊃ QC (QC là một phần của QA)   | QC chỉ là 1 phần của QA         |

**Self-check**: "Code review ở pha design" → SQA hay SQC?
→ **SQA** (kiểm process trước khi có code), **trừ khi** review để bắt lỗi sản phẩm cụ thể → khi đó tính SQC.

**Page**: Lecture 1, page 23–24.

---

### 7. Objectives of SQA Activities

**2 nhóm objectives** (chia theo pha vòng đời):

```
DEVELOPMENT (process-oriented):     MAINTENANCE (product-oriented):
 1. Conform technical reqs           1. Conform technical reqs
 2. Conform schedule + budget        2. Conform schedule + budget
 3. Initiate & manage improvement    3. Initiate & manage improvement
```

**Mnemonic**: Cả 2 nhóm cùng 3 mục tiêu: **Technical / Managerial / Improvement** — chỉ khác đối tượng (process vs product).

**Page**: Lecture 1, page 25–26.

---

### 8. SQA Standards — Vai trò & Phân loại

> **Hook**: Standards = "công cụ ngoại" để mượn kinh nghiệm của thế giới, không phải tự phát minh lại bánh xe.

**3 lợi ích** (mnemonic **U-C-O**):
- **U**tilization — tận dụng knowledge toàn cầu
- **C**oordination — đồng bộ với đối tác
- **O**bjective Evaluation — khung đo lường độc lập

**Phân loại 2 nhóm** — đây là bảng cực hay vào đề:

|                  | **Quality Management Standards**     | **Project Process Standards**          |
|------------------|--------------------------------------|----------------------------------------|
| Focus            | **WHAT** is required                 | **HOW** to perform                     |
| Cấp áp dụng      | Tổ chức (organization-level)         | Dự án (project-level)                  |
| Mục đích         | Xin **certification**                | Hướng dẫn **methodological**           |
| Ví dụ            | **ISO 9001, ISO 9000-3, SEI CMM**    | **IEEE 1012 (V&V), ISO/IEC 12207**     |

**Bẫy**: "ISO 9001 hướng dẫn cách viết test cases" → **SAI**. ISO 9001 là management standard (WHAT), nói cần có quy trình test chứ không nói cách viết test. Cách viết test là IEEE 1012.

**Page**: Lecture 1, page 27–29.

---

## LECTURE 2 — Software Quality Factors

### Mental model — Functional vs Non-functional

```
SRS (Software Requirements Spec) chia 2 loại requirements:
  ┌─────────────────────────────────────────┐
  │  FUNCTIONAL: "WHAT the system does"    │ ← Use Case Diagrams
  │  e.g. "Đặt vé, thanh toán, in vé"      │
  ├─────────────────────────────────────────┤
  │  NON-FUNCTIONAL: "HOW WELL it does it" │ ← Quality Factors
  │  e.g. "Phải chạy 24/7, response < 2s"  │
  └─────────────────────────────────────────┘
```

> **Hook**: 2 ứng dụng cùng đặt vé máy bay (functional giống nhau) nhưng 1 cái crash 10 lần/ngày, 1 cái mượt như nhung — *quality factors* mới là yếu tố differentiator.

**Trọng số factors khác nhau theo domain**:
- Medical/Banking → **Reliability** & **Integrity** cao
- Game/Social → **Usability** cao
- Mobile/IoT → **Efficiency** cao

**Page**: Lecture 2, page 5–7.

---

### McCall's Model — 11 Factors / 3 Categories

> **Mnemonic CIEIU - MFT - PRI** (5+3+3):

```
┌─────────────────────────────────────────────────────────────┐
│  PRODUCT OPERATION (5)  — "Phần mềm chạy NHƯ THẾ NÀO?"     │
│    Correctness, Integrity, Efficiency, Reliability, Usability│
├─────────────────────────────────────────────────────────────┤
│  PRODUCT REVISION (3)   — "Sửa đổi NHƯ THẾ NÀO?"           │
│    Maintainability, Flexibility, Testability                │
├─────────────────────────────────────────────────────────────┤
│  PRODUCT TRANSITION (3) — "Chuyển sang môi trường khác?"   │
│    Portability, Reusability, Interoperability               │
└─────────────────────────────────────────────────────────────┘
```

**Cách nhớ 3 nhóm**: Operation (đang chạy) → Revision (sửa đổi) → Transition (mang đi nơi khác). Đây là 3 pha của sản phẩm trong đời.

**Page**: Lecture 2, page 10.

---

### 5 Factors nhóm Product Operation

| Factor          | Hỏi gì                                          | Spec mẫu (lượng hoá)                          |
|-----------------|-------------------------------------------------|------------------------------------------------|
| **Correctness** | Output có đúng mission không?                   | Mission, accuracy, up-to-date, response time   |
| **Reliability** | Bao lâu thì lỗi 1 lần?                          | Failure rate < 1 / triệu cases; downtime ≤ 10 min/tháng |
| **Efficiency**  | Tốn bao nhiêu tài nguyên?                       | MIPS, MHz, MB, KBPS, battery life              |
| **Integrity**   | Có bảo mật không?                               | Cyber/network/internet security                |
| **Usability**   | Train nhân viên mới mất bao lâu?                | Số giờ training để vận hành thành thạo         |

**Bẫy phân biệt**:
- **Correctness vs Reliability**: Correctness = "kết quả đúng" (đúng tính toán). Reliability = "không sập" (không crash). App tính sai nhưng không crash → Correctness yếu, Reliability tốt.
- **Integrity ≠ Reliability**: Integrity = chống attack/data leak. Reliability = chống crash random.

**Page**: Lecture 2, page 10–14.

---

### 3 Factors nhóm Product Revision (M-F-T)

> **Story**: Sau khi release, sản phẩm phải *sửa*:
> - **M**aintainability — sửa bug dễ không? (module ≤ 30 statements là chuẩn)
> - **F**lexibility — thêm tính năng mới dễ không? (perfective evolution)
> - **T**estability — có log files, kết quả trung gian để debug không?

**Mnemonic**: M-F-T → **Mèo Fix Tech-debt**

**Page**: Lecture 2, page 15–18.

---

### 3 Factors nhóm Product Transition (P-R-I)

> **Story**: Sản phẩm phải "đi xa":
> - **P**ortability — chạy được trên OS/hardware khác?
> - **R**eusability — module dùng lại cho project sau?
> - **I**nteroperability — nói chuyện được với system khác? (API, REST)

**Mnemonic**: P-R-I → **Phim Reuse Interop**

**Bẫy**: Reusability ≠ Portability:
- Portability = chuyển *toàn bộ app* sang môi trường khác
- Reusability = lấy *từng module* dùng cho app khác

**Page**: Lecture 2, page 19–22.

---

### Alternative Models — Evans-Marciniak & Deutsch-Willis

> **Hook**: 2 mô hình "đối thủ" của McCall, nội dung 80% giống, chỉ khác nhau cấu trúc nhóm + thêm vài factor mới.

**Bảng so sánh cốt lõi** (cực hay vào đề):

|                   | McCall      | Evans-Marciniak | Deutsch-Willis |
|-------------------|-------------|-----------------|----------------|
| Năm               | 1977        | 1987            | 1988           |
| Số factors        | **11**      | **12**          | **15**         |
| Số categories     | **3**       | **3**           | **4**          |
| Có Testability?   | ✅          | ❌              | ❌             |

**5 factor "mới"** (cả 2 mô hình thay thế đều bỏ Testability, thêm):

| Factor mới        | Ai có?              | Tương đương McCall    |
|-------------------|---------------------|-----------------------|
| **Verifiability** | Cả 2                | (mới)                 |
| **Expandability** | Cả 2                | ≈ Flexibility         |
| **Safety**        | Chỉ Deutsch-Willis  | (mới)                 |
| **Manageability** | Chỉ Deutsch-Willis  | (mới)                 |
| **Survivability** | Chỉ Deutsch-Willis  | ≈ Reliability         |

**Self-check**: Factor nào *thật sự mới* (không có analog ở McCall)?
→ **Verifiability, Safety, Manageability** (3 factor mới hoàn toàn).
→ Expandability ≈ Flexibility, Survivability ≈ Reliability nên chỉ là *rebrand*.

**Page**: Lecture 2, page 24–29.

---

## LECTURE 3 — SQA System

### SQA System — định nghĩa

> **Ẩn dụ**: SQA System = "khung sắt" lắp ráp các thành phần (components) lại thành 1 hệ thống chống lỗi toàn diện. Như Iron Man's suit — nhiều mảnh ghép, vận hành như 1.

**Core**: *"An integrated framework that combines a wide range of SQA components, designed to challenge the multitude of sources of software errors and to achieve an acceptable level of software quality."*

**Page**: Lecture 3, page 5.

---

### 6 Classes of SQA Components — bộ khung của cả lecture

```
┌─────────────────────────────────────────────────────────────┐
│ 1. PRE-PROJECT          ─→ Contract review, Plans           │
│ 2. LIFECYCLE ASSESSMENT ─→ Reviews, Expert opinions, Tests  │
│ 3. INFRASTRUCTURE       ─→ Procedures, Templates, Training, │
│                            Preventive/corrective actions,   │
│                            Config mgmt, Doc control         │
│ 4. MANAGEMENT           ─→ Progress control, Metrics, Costs │
│ 5. STANDARDS/CERT       ─→ Mgmt standards + Process stds    │
│ 6. HUMAN COMPONENTS     ─→ Managers, Testers, SQA unit...   │
└─────────────────────────────────────────────────────────────┘
```

**Mnemonic** — **P-L-I-M-S-H** ("Please Let It Manage Standards Humanely"):
**P**re-project / **L**ifecycle / **I**nfrastructure / **M**anagement / **S**tandards / **H**uman.

**Page**: Lecture 3, page 6.

---

### Class 1 — Pre-project Components (2 items)

| Component                     | Khi nào                  | Mục tiêu                              |
|-------------------------------|--------------------------|---------------------------------------|
| **Contract reviews**          | Trước nộp proposal & ký  | Tránh unrealistic commitments         |
| **Development + Quality Plans** | Ngay sau ký contract   | Identify risk + xây roadmap           |

**Page**: Lecture 3, page 8–10.

---

### Development Plan — Issues chính

> **Mnemonic SMHROS**: Schedule / Manpower-Hardware / Risk / Organization / Methodology / Software-reuse.

- **S**chedules
- **M**anpower & **H**ardware resources
- **R**isk evaluations
- **O**rganizational issues (team, subcontractors)
- **M**ethodology & dev tools
- **S**oftware reuse plans

**Page**: Lecture 3, page 9.

---

### Quality Plan — Issues chính

- **Quality goals** (phải MEASURABLE — quantitative)
- **Criteria** start/end mỗi stage
- **List** of reviews, tests, V&V activities

**Self-check**: "Goal: phần mềm phải dễ dùng" → **SAI** (qualitative). Phải là: "User mới train trong 4 giờ vận hành được module A" → **OK** (quantitative).

**Page**: Lecture 3, page 10.

---

### Class 2 — Software Life Cycle Components

**5 components** trong lifecycle:
1. **Reviews** (formal DRs + peer reviews)
2. **Expert opinions**
3. **Software testing**
4. **Software maintenance components**
5. **Assurance of quality of subcontractors & customer-supplied parts**

**Page**: Lecture 3, page 11.

---

### Review — Formal DR vs Peer Review

|              | **Formal Design Review (DR)**         | **Peer Review** (Inspection, Walkthrough) |
|--------------|---------------------------------------|-------------------------------------------|
| Approval     | Cần formal professional approval      | Không cần                                 |
| Committee    | Senior pros + project leader          | Peers (đồng cấp)                          |
| Tài liệu     | Documents quan trọng                  | Documents ngắn                            |
| Mục tiêu     | Approve design                        | Phát hiện càng nhiều fault càng tốt       |

**Bẫy**: "Peer review = code review giữa các dev" → đúng. "Formal DR = code review giữa các dev" → SAI (cần approval formal, thường có management).

**Page**: Lecture 3, page 12.

---

### Expert Opinions — khi nào dùng

3 trường hợp gọi expert ngoài:
1. **Bổ sung** capabilities thiếu trong tổ chức
2. **Thay thế** DR khi không tổ chức được
3. **Xử lý bất đồng** giữa các senior nội bộ

**Page**: Lecture 3, page 13.

---

### Class 3 — Infrastructure Components (6 items, org-wide)

> **Hook**: Đây là "đường ray" mà mọi dự án trong tổ chức chạy trên đó — KHÔNG phải per-project.

**Mnemonic P-T-T-P-C-D** ("Please Train The People Carefully Daily"):

| #  | Component                                  | Mục đích                          |
|----|--------------------------------------------|-----------------------------------|
| 1  | **P**rocedures and work instructions       | Chuẩn hoá cách làm                |
| 2  | **T**emplates and checklists               | Khung tài liệu thống nhất         |
| 3  | **T**raining, retraining, certification    | Kỹ năng staff                     |
| 4  | **P**reventive and corrective actions      | Học từ lỗi cũ                     |
| 5  | **C**onfiguration management               | Version + Change control          |
| 6  | **D**ocumentation control                  | Quản lý phiên bản docs            |

**Page**: Lecture 3, page 16.

---

### Procedures vs Work Instructions

|                    | **Procedures**       | **Work Instructions**         |
|--------------------|----------------------|-------------------------------|
| Phạm vi            | Toàn tổ chức         | Specialized teams             |
| Mức độ chi tiết    | General              | Cực chi tiết                  |
| Loại tri thức      | Organizational rules | Specific methods              |

**Page**: Lecture 3, page 17.

---

### Configuration Management

> **Ẩn dụ**: Như Git nhưng cho cả tài liệu, không chỉ code. Gồm 2 chân:

- **Change Control** = procedures (con người approve)
- **Version Control** = computerized tools (máy ghi lại)

**Mục tiêu**: tránh modifications "lậu" + đồng bộ versions giữa nhiều site.

**Page**: Lecture 3, page 21.

---

### Class 4 — Management Components (3 items)

| Component                  | Đo cái gì                                      |
|----------------------------|------------------------------------------------|
| Project progress control   | Resource, schedule, risk, budget               |
| Software quality metrics   | Đo định lượng chất lượng                       |
| Software quality costs     | Cost of control vs cost of failure             |

**Page**: Lecture 3, page 23–26.

---

### Total Quality Cost — công thức kinh điển

```
                  ┌──────────────────────┐
TOTAL QUALITY  =  │  Costs of CONTROL   │  +  ┌──────────────────────┐
COST              │  (Prevention +      │     │  Costs of FAILURE   │
                  │   Appraisal +       │     │  (Internal +        │
                  │   Managerial ctrl)  │     │   External +        │
                  └──────────────────────┘     │   Managerial)       │
                                               └──────────────────────┘
                  ↑ TĂNG cái này  →  GIẢM cái kia nhiều hơn  →  Tổng GIẢM
```

**Insight**: Đầu tư SQA *trông* tốn nhưng tổng cost giảm vì failure cost cao hơn rất nhiều.

**Page**: Lecture 3, page 26.

---

### Class 5 — Standards & Certification (đã nói ở Lecture 1)

- **Quality management standards**: SEI CMM, ISO 9001
- **Project process standards**: IEEE 1012, ISO/IEC 12207

**Page**: Lecture 3, page 27.

---

### Class 6 — Human Components

**Organizational base** gồm:
- Managers
- Testing personnel
- SQA unit
- Practitioners (trustees, committee, forum members)

**3 mục tiêu chính**: develop/support SQA / detect deviations / suggest improvements.

**Page**: Lecture 3, page 28.

---

### Considerations for SQA System Construction

> **Insight**: Không có SQA system "one-size-fits-all". Mỗi tổ chức phải custom-fit.

**2 quyết định chính** khi build SQA system:
1. **Organizational base** (ai làm gì, cấu trúc nhân sự)
2. **Components & extent of use** (chọn components nào, dùng đến đâu)

**3 yếu tố ảnh hưởng** lựa chọn:
- Organization (size, văn hoá)
- Projects & services (loại, độ phức tạp)
- Professional staff (kinh nghiệm)

**Page**: Lecture 3, page 29–30.

---

## LECTURE 4 — Pre-project SQA Components

### Carnegie Fruits & Vegetables (CFV) — case mở màn

> **Story đáng nhớ**: CFV dự án **đúng hạn, team được thưởng**, ai cũng vui — nhưng công ty **lỗ $90,000** vì bỏ sót 1 clause: "personnel sẽ được supplier huấn luyện free". Không ai đọc kỹ RFP, không tính chi phí training vào proposal.

**Bài học**:
> **Technical success ≠ Business success**.
> Một dòng trong RFP có thể chôn vùi cả lợi nhuận.

**Page**: Lecture 4, page 5–6.

---

### Contract Review — 2 stages

> **Ẩn dụ**: Đo 2 lần, cắt 1 lần. Đọc RFP kỹ trước khi *gửi proposal* + trước khi *ký contract*.

```
Stage 1: Proposal Draft Review  ──→ Trước nộp proposal cho client
Stage 2: Contract Draft Review  ──→ Trước ký hợp đồng cuối
```

**Standards tham chiếu**: ISO 9001 & ISO 9000-3.

**Page**: Lecture 4, page 7–8.

---

### Stage 1 — 9 Objectives of Proposal Draft Review

> **Cách nhớ**: chia thành 3 cụm:

**Cụm A — Hiểu yêu cầu (3)**:
1. Customer requirements được clarify & document
2. Alternative approaches xét (reuse, off-the-shelf, subcontractor)
3. Formal aspects of relationship (channels, deliverables, acceptance criteria…)

**Cụm B — Đánh giá năng lực (4)**:
4. Identification of development **risks**
5. Adequate estimation of **resources & timetable**
6. Examination of **company's capacity** (staff, facilities)
7. Examination of **customer's capacity** (financial, personnel, hardware commitments)

**Cụm C — Hợp tác & sở hữu (2)**:
8. Definition of partner/subcontractor participation conditions
9. Definition & protection of **proprietary rights**

**Page**: Lecture 4, page 9–11.

---

### Stage 2 — 3 Objectives of Contract Draft Review

> **Hook**: Chỉ 3 mục, đều quy về 1 ý: *"Đảm bảo contract = đúng những gì đã đàm phán, không hơn không kém"*.

1. No **unclarified** issues remain
2. All understandings from negotiations are **correctly documented**
3. No **"new"** changes/additions/omissions slipped in without discussion

**Self-check**: Nếu trong contract xuất hiện 1 clause chưa từng bàn → vi phạm objective số mấy?
→ **(3)** — slipped in without discussion.

**Page**: Lecture 4, page 12.

---

### 4 Factors ảnh hưởng Contract Review Extent

> **Hook**: Dự án càng to/lạ/lạc/loạn → review càng kỹ.

| Yếu tố                                       | Tác động                              |
|----------------------------------------------|---------------------------------------|
| **Project magnitude** (budget/man-month)     | Càng to → review càng kỹ              |
| **Project technical complexity**             | Càng phức tạp → review càng sâu       |
| **Staff acquaintance** với area              | Càng quen → review giảm bớt           |
| **Organizational complexity** (số partner)   | Càng nhiều bên → review càng rộng     |

**Page**: Lecture 4, page 13.

---

### Who Performs Contract Review?

| Project size  | Ai review                                         |
|---------------|---------------------------------------------------|
| **Simple**    | Proposal Team Leader hoặc 1 thành viên            |
| **Medium**    | Cả proposal team, đôi khi 1 outside professional  |
| **Major**     | **Team** of outside experts                       |

**Page**: Lecture 4, page 14.

---

### Difficulties for Major Proposals

3 khó khăn (mnemonic **T-W-A**):
- **T**ime Pressures — deadline bid gấp
- **W**orkload — cần nhiều expertise cùng lúc
- **A**vailability — senior experts đang bận

**Page**: Lecture 4, page 15.

---

### Internal Projects (In-house) — bẫy lớn

> **Story Toyware**: Internal project (1 phòng làm cho 1 phòng khác trong cùng công ty) tưởng "dễ", bỏ qua review/plan → kết quả: ngân sách $240k, thực chi $385k, **lỡ mùa Christmas** (mất doanh thu lớn nhất năm).

**Bài học**: Internal projects vẫn cần full-scale plans như external projects.

**4 risks thường gặp ở internal projects**:
1. Inadequate definition of requirements
2. Poor resource estimation
3. Unrealistic timetables
4. Low awareness of development risks

**Page**: Lecture 4, page 17–20, 32–33.

---

### Why need Development & Quality Plans — 5 reasons

> **Mnemonic S-R-R-S-P**:

1. **S**cheduling — estimate time, budget, manpower
2. **R**ecruiting — allocate resources
3. **R**isk Management — resolve dev risks sớm
4. **S**QA Implementation — implement quality activities
5. **P**roject Control — data cho manager kiểm soát

**Insight**: Planning = **foundations** của cả project management lẫn SQA.

**Page**: Lecture 4, page 22.

---

### 11 Development Plan Elements

> **Cách nhớ** — chia 3 nhóm:

**Nhóm WHAT (sản phẩm & boundary)** — 4 items:
1. Project **products** (design docs, software, training, dates)
2. Project **interfaces** (existing packages, hardware, other teams)
3. **Methodology** & development tools
4. Software development **standards & procedures**

**Nhóm HOW (cách triển khai)** — 4 items:
5. **Map** of development process (GANTT charts!)
6. **Milestones**
7. Project **staff organization**
8. **Development facilities** (hardware, software, office)

**Nhóm CONTROL (rủi ro & giám sát)** — 3 items:
9. Development **risks** (technological gaps, staff shortages, interdependence)
10. **Control methods** (progress reports, status meetings, gantt tracking)
11. **Cost estimates**

**Page**: Lecture 4, page 23–26.

---

### 5 Quality Plan Elements

> **Mnemonic Q-R-T-A-C** ("Quality Reviews Tests Acceptance Config"):

1. **Q**uality Goals (quantitative)
2. **R**eviews planned (scope, type, schedule, person in charge)
3. **T**ests planned (unit, integration, system)
4. **A**cceptance Tests for external software (purchased, subcontracted, customer-supplied)
5. **C**onfiguration Management (tools, procedures)

**Page**: Lecture 4, page 27–28.

---

### Quality Goals — Quantitative vs Qualitative

> **Ví dụ HDS** (Help Desk System):
> - ❌ "Phần mềm phải reliable" (qualitative — không đo được)
> - ✅ "HDS chạy 100 giờ/tuần" (quantitative — đo được)

**Rule**: Luôn ưu tiên quantitative → mới verify được, mới audit được.

**Page**: Lecture 4, page 29–30.

---

### Small Projects — có cần plan không?

**Câu trả lời**: Không apply nguyên plan của large project, nhưng VẪN cần plan nếu:
- ⚠️ **High risk** identified, hoặc
- ⚠️ **Heavy penalty** for delay

**Lợi ích kể cả với small project**:
- Hiểu task rõ hơn
- Trách nhiệm rõ ràng
- Dễ control hơn

**Page**: Lecture 4, page 31.

---

## TUTORIALS 1–4

### Tutorial 1 — TDD (Test-Driven Development)

> **Ẩn dụ**: Bình thường viết code rồi mới test ("đi rồi vẽ đường"). TDD = **vẽ đường rồi mới đi**: viết test trước, viết code sau.

**Flow ngược**:
```
TRUYỀN THỐNG:  Write Code → Write Test → Fix Bugs
TDD:           Write Test → Write Code → Fix Code
```

**Vòng lặp Red-Green-Refactor**:
```
   ┌─────────────────────────────────────────┐
   │   RED   →   Viết test thất bại         │
   │ (logic chưa tồn tại nên fail là đúng)  │
   ├─────────────────────────────────────────┤
   │   GREEN →   Viết code vừa đủ để pass   │
   │ (KISS: không thừa 1 dòng)              │
   ├─────────────────────────────────────────┤
   │   REFACTOR → Dọn code, test vẫn pass   │
   └─────────────────────────────────────────┘
                   ↻ Lặp lại
```

**Môi trường thực hành**: Java + JUnit + Maven + JDK 21.

**Page**: Tutorial 1.

---

### TDD — 4 Key Principles

| Principle           | Nghĩa                                                       |
|---------------------|-------------------------------------------------------------|
| **Test First**      | KHÔNG viết production logic trước khi có test fail          |
| **KISS**            | Code chỉ vừa đủ pass test hiện tại (không tối ưu sớm)       |
| **Baby Steps**      | Chia nhỏ vấn đề thành nhiều test nhỏ                        |
| **F.I.R.S.T**       | Unit test phải đạt 5 tính chất (xem dưới)                   |

**Page**: Tutorial 1.

---

### F.I.R.S.T — 5 tính chất unit test

> **Mnemonic**: **F.I.R.S.T** — đọc thẳng tên đã là mnemonic.

| Chữ | Property         | Nghĩa                                           |
|-----|------------------|-------------------------------------------------|
| F   | **Fast**         | Chạy nhanh                                      |
| I   | **Isolated**     | Không phụ thuộc test khác                       |
| R   | **Repeatable**   | Luôn cho cùng kết quả                           |
| S   | **Self-Validating** | Pass/fail tự động — không cần đọc log         |
| T   | **Timely**       | Viết NGAY TRƯỚC code (đúng tinh thần TDD)       |

**Bẫy**: Test mà phải đọc log mới biết pass/fail → vi phạm **S** (Self-Validating).

**Page**: Tutorial 1.

---

### Tutorial 2 — Use Case Diagram

> **Hook**: Use Case = **high-level map** of what the system does, từ góc nhìn user. Trả lời câu "**WHAT** the system does" (functional requirements), bổ trợ cho quality factors trong SRS.

**3 forms biểu diễn use case** — chọn theo audience:

| Form                          | Khi nào dùng                    |
|-------------------------------|---------------------------------|
| **Narrative text**            | User stories (cho stakeholder)  |
| **Template-based**            | Written use cases (detail)      |
| **Diagrammatic**              | Activity / use case diagrams    |

**Tool gợi ý**: StarUML 7.0.0 (preferred), diagrams.net, Lucidchart, Visual Paradigm.

**Ví dụ áp dụng**: e-commerce, hospital, ATM systems.

**Page**: Tutorial 2.

---

### Tutorial 3 — ER Diagram & Class Diagram

> **Hook**: Cùng mô hình hoá data, khác paradigm:
> - **ER** = data-centric (cho database design)
> - **Class** = object-centric (cho OO design)

| Aspect      | **ER Diagram**                  | **Class Diagram**                                   |
|-------------|----------------------------------|-----------------------------------------------------|
| Paradigm    | Data modeling                    | OO design                                           |
| Phần tử     | Entities, attributes, relationships | Classes, attributes, methods, relationships      |
| Quan hệ     | Multiplicity (1:1, 1:N, N:M)     | Association, aggregation, composition, inheritance  |
| Output      | Database schema                  | Source code structure                               |

**Ví dụ**: School schedule system, photo sharing site.

**Page**: Tutorial 3.

---

### Tutorial 4 — UI Design with Figma

> **Hook**: "Đo 2 lần, cắt 1 lần" — thiết kế UI trước khi code → giảm rework.

**Yêu cầu thực hành**:
- Tool: Figma (https://www.figma.com)
- Phải có: form, report window, GUI hoàn chỉnh
- Tính năng: register / login / logout / CRUD + lưu DB (MySQL, MongoDB…)
- Topics gợi ý: university control, house monitor, mobile selling, streaming, technical share forum

**Page**: Tutorial 4.

---

## Quick Reference — Tổng kết Day 1 trong 1 trang

### "Câu thần chú" cho mỗi lecture

| Lecture | Một câu tóm gọn                                                          |
|---------|--------------------------------------------------------------------------|
| **L1**  | Software có lỗi → SQA = process-level prevention, QC = product-level detection |
| **L2**  | Quality = HOW WELL phần mềm chạy → McCall 11 factors / 3 nhóm (CIEIU-MFT-PRI) |
| **L3**  | SQA System = 6 lớp (P-L-I-M-S-H) ráp lại thành "Iron Man suit" chống lỗi |
| **L4**  | Pre-project = Contract Review (2 stages) + Plans (Dev 11 elements + Quality 5 elements) |

### Top 10 bẫy hay vào đề

1. Program ≠ Software (program chỉ là 1 trong 4 thành phần)
2. Error có thể không thành Fault; Fault có thể không thành Failure
3. SQA ≠ Testing (testing chỉ là 1 phần)
4. SQA = process-oriented (prevent); SQC = product-oriented (detect)
5. ISO 9001 = management standard (WHAT); IEEE 1012 = process standard (HOW)
6. Correctness ≠ Reliability (đúng kết quả ≠ không crash)
7. Portability ≠ Reusability (cả app vs từng module)
8. Evans-Marciniak & Deutsch-Willis BỎ Testability, THÊM Verifiability
9. Quality goals phải QUANTITATIVE, không qualitative
10. Internal projects VẪN cần full contract review + plans (case Toyware)
