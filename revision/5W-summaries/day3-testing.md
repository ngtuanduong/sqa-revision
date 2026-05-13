# DAY 3 — Testing Techniques, Security & Automation (Easy-to-Absorb Edition)

Đây là **phần dày nhất của môn**: 4 lectures (Black-box → White-box → Security → Automation) + 4 tutorials thực hành. Mỗi concept gồm:
- **Hook**: ẩn dụ/scenario gợi nhớ (chỉ khi cần)
- **Core**: nội dung cốt lõi
- **Visual**: bảng / ASCII diagram khi có list dài
- **Bẫy** / **Self-check**: câu hỏi tự kiểm thường gặp trong đề thi
- **Dẫn chứng**: nguồn slide gốc / ví dụ thực hành

---

## Bản đồ Day 3 — đọc 30 giây trước khi vào chi tiết

```
LECTURE 9  ── "Test như user, không xem code"  (Black-box)
              Definition → V&V&Q → 5 kỹ thuật:
              EP → BVA → Decision Table → State Transition → Pairwise

LECTURE 10 ── "Đọc code, soi từng đường đi"    (White-box)
              Coverage (Statement < Branch < Condition < Path)
              + CFG + Cyclomatic V(G) + Basis Path
              + Loop testing + Data Flow (d/r/u, 9 pairs, DU-pairs)

LECTURE 11 ── "Hacker mindset"                  (Security)
              Vulnerabilities (BO, SQLi, XSS, URL, Spoof)
              CIA triad + OWASP Top 10
              4 phương pháp: SAST → DAST → IAST → RASP
              + Pen-test + Fuzzing + 7 best practices

LECTURE 12 ── "Robot thay người bấm chuột"      (Automation)
              Selenium (IDE/RC/WebDriver/Grid) + 8 Locators + Waits
              JMeter (Thread Group, Sampler, Timer, Listener)
```

**Mnemonic cả ngày**: `BLACK-WHITE-SECURE-AUTO` (B-W-S-A) → 4 góc nhìn test một SP: không nhìn code, nhìn code, nhìn như hacker, để robot nhìn.

---

## LECTURE 9 — Black-box Testing

### 1. Software Testing — định nghĩa

> **Hook**: Testing = "chạy code để bắt lỗi", KHÔNG bao gồm code review (đó là static review). Là 1 *formal process*, không phải "thử nghịch".

**Core**: Tiến trình hình thức (formal process) thực thi chương trình bởi specialized testing team, áp dụng trên unit / nhóm unit tích hợp / toàn bộ package, dựa trên approved test procedures + approved test cases.

**Bẫy ngân sách rất hay vào đề**:

| Khoản                    | Plan         | Reality                  |
|--------------------------|--------------|--------------------------|
| Testing budget           | ~45%         | **~24% project budget**  |
| Testing time on schedule | ~45%         | **~27% schedule**        |

**Lý do gap**: Bị cắt do deadline gấp.

**Dẫn chứng**: Lecture 9 — budget testing ≈ 24% project budget, time ≈ 27% schedule.

---

### 2. Testing Objectives — Direct & Indirect

> **Mindset Myers (1979)**: *"If your goal is to show the absence of errors you won't discover many."* → mục tiêu testing là **TÌM BUG**, không phải chứng minh "không có bug".

| Loại         | Mục tiêu                                                              |
|--------------|-----------------------------------------------------------------------|
| **Direct**   | Tìm lỗi, đạt acceptable quality, hiệu quả trong budget/schedule       |
| **Indirect** | Ghi nhận lỗi (test record) → input cho corrective/preventive actions  |

**Dẫn chứng**: Test record dùng cho preventive actions (Lecture 5 — infrastructure components).

---

### 3. Verification vs Validation vs Qualification

> **Ẩn dụ 3 câu hỏi**:
> - **V**erification: "Tôi có *build đúng cách* không?" (đúng spec, đúng phase)
> - **V**alidation: "Tôi có *build đúng thứ* không?" (đúng nhu cầu khách hàng)
> - **Q**ualification: "Phần mềm có *sẵn sàng vận hành* không?" (đủ chuẩn để go-live)

| Loại              | Câu khẩu hiệu                  | So sánh                                    | Khi nào                |
|-------------------|--------------------------------|--------------------------------------------|------------------------|
| **Verification**  | "Build the product right"      | Phase-to-phase consistency                 | Giữa các pha           |
| **Validation**    | "Build the right product"      | Output vs customer needs                   | Cuối                   |
| **Qualification** | "Fit for operational use"      | Output vs operational/maintenance standard | Trước go-live          |

**Dẫn chứng**: Verification compare design output vs requirement document.

---

### 4. Black-box Testing — tổng quan

> **Hook hộp đen**: Bạn không nhìn được vào trong hộp, chỉ biết *cho input X → ra output Y*. Tester đứng ngoài như end-user.

**Core**: Behavioral / behavior-based technique — chỉ test input/output, KHÔNG xem internal code.

**Áp dụng**: Mọi level (Unit → Integration → System → Acceptance), đặc biệt mạnh ở **System / Acceptance**.

**5 kỹ thuật chính** — mnemonic **EP-BVA-DT-ST-PW**:

```
1. Equivalence Partitioning (EP)
2. Boundary Value Analysis (BVA)
3. Decision Table
4. State Transition
5. Pairwise
```

**Pros**: Hiệu quả resource, broad scope, có thể test load/availability.

**Cons (Disadvantages — hay vào đề)**:
- **Masked errors**: 2 lỗi triệt tiêu nhau, output nhìn đúng
- **No coverage control** (không biết test bao phủ bao nhiêu code)
- **Không check coding quality** (chuẩn code, độ sạch)

---

### 5. Equivalence Partitioning (EP)

> **Ẩn dụ**: "Chia lớp học thành nhóm, mỗi nhóm cử 1 đại diện đi thi". Nếu đại diện đúng/sai → cả nhóm coi như đúng/sai.

**Core**: Chia input domain thành các **partition (equivalence class — EC)** mà program xử lý GIỐNG NHAU → mỗi EC chỉ cần test 1 đại diện.

**Số test case tối thiểu theo loại input**:

| Loại input              | Valid class | Invalid class | Tổng tối thiểu |
|-------------------------|-------------|---------------|----------------|
| **Range** (vd 1-100)    | 1           | **2** (<min, >max) | **3**          |
| **Specific value**      | 1           | 2             | 3              |
| **Set member** (in list)| 1           | 1             | 2              |
| **Boolean**             | 1           | 1             | 2              |

**Diagram trực quan cho Range**:

```
Invalid (<min)  │    Valid    │  Invalid (>max)
────────────────┼─────────────┼────────────────
  -∞ ... min-1  │  min ... max│  max+1 ... +∞
       ↑              ↑              ↑
    1 TC          1 TC          1 TC      → tổng 3 TC
```

**Rule**: Mỗi EC ít nhất 1 TC; **Tổng TC ≥ số EC**.

**Dẫn chứng**: 
- Input age 0-120 → valid [0,120], invalid (<0), invalid (>120) → 3 TC.
- Range: 1 valid + 2 invalid class.
- Specific value: 1 valid + 2 invalid.
- Set member: 1 valid + 1 invalid.
- Boolean: 1 valid + 1 invalid.

---

### 6. Boundary Value Analysis (BVA)

> **Hook**: *"Lỗi rình ở biên giới"*. Programmer hay viết nhầm `>` thành `>=`, `<` thành `<=` — off-by-one. BVA cố tình ném giá trị ngay sát biên để bắt loại lỗi này.

**Core**: Mở rộng EP — chọn giá trị **TẠI** và **GẦN** biên (errors xuất hiện nhiều ở edge).

**Với range [a, b]** test 6 điểm:

```
       ┌──────────── valid range ────────────┐
... ──┬──┬──┬─────────────────────────┬──┬──┬── ...
     a-1 a  a+1                    b-1  b  b+1
      ↑       ↑                       ↑      ↑
    invalid  just                   just   invalid
            above a                 below b
```

**Hai biến thể**:
- **2-value**: `{a-1, a, b, b+1}` *hoặc* `{a, a+1, b-1, b}`
- **3-value**: thêm cả `{min, min+1, max-1, max, +ngoài biên}`

**So sánh EP vs BVA**:

| Tiêu chí       | EP                          | BVA                                |
|----------------|-----------------------------|------------------------------------|
| Mục tiêu       | Giảm redundancy             | Bắt off-by-one ở edge              |
| Cách chọn      | 1 đại diện / class          | Tại biên + sát biên                |
| Bước trong process | Trước                   | Sau (mở rộng EP)                   |
| Quan hệ        | Tiền đề                     | Bổ sung — thường dùng CHUNG        |

**Dẫn chứng**: 
- Input 1-100 → BVA test: **0, 1, 2, 99, 100, 101**.
- Tutorial 9 Exercise 3 Triangle với sides 1-200 inclusive → boundary: **0, 1, 2, 199, 200, 201**.

---

### 7. Decision Table Testing

> **Ẩn dụ**: "Ma trận if-then". Mỗi cột là một rule = 1 combination of conditions → action tương ứng.

**Core**: Bảng mô hình hóa business logic dạng *rule = combination của conditions → actions*. Hữu ích khi logic phức tạp ("if X and Y but not Z").

**4 bước**:
1. List **conditions** (T/F).
2. List **actions**.
3. Tạo **rule** (column) = mọi combination.
4. **Loại** rule không thể xảy ra.

**Ví dụ Car Insurance**:

| Condition           | R1   | R2   | R3   | R4   | R5   | R6   |
|---------------------|------|------|------|------|------|------|
| Gender = Male       | T    | T    | T    | F    | F    | F    |
| Age < 25            | T    | F    | F    | T    | F    | F    |
| Age 25-65           | F    | T    | F    | F    | T    | F    |
| Age ≥ 65            | F    | F    | T    | F    | F    | T    |
| → Fee               | high | mid  | mid+ | high | low  | mid  |

**Dẫn chứng**: Tutorial 9 Exercise 3 Triangle dùng Decision Table + BVA.

---

### 8. State Transition Testing

> **Ẩn dụ**: "Máy trạng thái như ATM". Idle → Card inserted → PIN OK → Menu → Withdraw → ... Hệ thống nhớ *mình đang ở trạng thái nào*.

**Core**: Model hành vi hệ thống qua các **State** và **Transition**. Áp dụng khi behavior phụ thuộc lịch sử (stateful) — ATM, login flow, order workflow.

**5 bước**:
1. Define **perspective** (user view vs system view).
2. Identify **states**.
3. Map **transitions** (event, guard, action).
4. Model bằng **graph/table**.
5. **Verify**.

**Mục đích**: Phát hiện *invalid transitions* + *defect masking*.

---

### 9. State Transition Coverage Criteria

| Tiêu chí                  | Nghĩa                                              | Mạnh hơn?              |
|---------------------------|----------------------------------------------------|------------------------|
| **All-states coverage**   | Exercise mọi state                                 | (mức 1)                |
| **All-transitions coverage** | Exercise mọi valid transition + thử invalid    | **Mạnh hơn all-states** |

**Quy tắc bao hàm**: **All-transitions ⇒ All-states** (đạt all-transitions thì tự khắc đạt all-states).

**Self-check**: All-states có ⇒ All-transitions không? → **KHÔNG**. Đi đủ thành phố nhưng chưa chắc đi đủ con đường.

**Dẫn chứng**: ATM machine — All-states coverage: **2 paths** đủ; All-transitions coverage: **4 paths**. All-transitions giúp tránh defect masking.

---

### 10. Pairwise Testing

> **Ẩn dụ**: "Không test toàn bộ, chỉ test từng cặp". Statistically 70-90% defect đến từ *2-way interaction* giữa parameters.

**Core**: Kỹ thuật combinatorial — mỗi **cặp** giá trị của **2 parameter bất kỳ** được test cùng nhau ít nhất 1 lần.

**Áp dụng**: Nhiều input parameter, không thể test exhaustive.

**Số TC giảm dramatic**:

| Cách test           | Số TC (3 param × 3 value) |
|---------------------|---------------------------|
| **1-wise**          | 3                         |
| **Pairwise (2-wise)** | **9**                   |
| **Exhaustive**      | 27                        |

**How**: Dùng *all-pairs algorithm* hoặc *Classification Tree*.

**Dẫn chứng**: 3 class × 3 value: 1-wise = 3 TC; pairwise = 9 TC (thay vì 27 exhaustive).

---

## LECTURE 10 — White-box Testing

### 11. Code Coverage — tổng quan

> **Hook**: White-box mở nắp hộp. *"Đường đi nào trong code đã được test, đường nào chưa?"*

**Core**: Ratio = **components tested / total components**. Higher coverage → higher reliability.

**4 criterion chính** — xếp theo độ mạnh:

```
Statement < Branch/Decision < Condition < Multiple Condition < Path (MC/DC)
   yếu                                                          mạnh
```

**Công thức chung**:

```
Coverage = (executed / total) × 100%
```

---

### 12. Statement Coverage (SC)

> **Hook**: "Mỗi dòng code phải được chạy ít nhất 1 lần". Mức coverage **cơ bản nhất**.

**Core**: % câu lệnh (line) được thực thi.

**Công thức**:

```
SC = (executed statements / total statements) × 100%
```

**Phát hiện**: Unused statements, dead code, missing statements.

**Limitation**: Không phát hiện lỗi trong **complex logical expression** hoặc **empty branch**.

**Dẫn chứng (lecture example)**:
- TC1: `a=-1, b=0` → **80%**.
- TC2: `a=5, b=0` → **100%**.

---

### 13. Decision / Branch Coverage (DC)

> **Hook**: "Mỗi nhánh true/false của decision phải được chạy". Mạnh hơn statement vì có decision không có statement bên trong (empty branch).

**Core**: % branch (T/F outcome của decision) được thực thi.

**Công thức**:

```
DC = (executed branches / total branches) × 100%
```

**Quy tắc bao hàm cực hay vào đề**: **100% Branch ⇒ 100% Statement** (luôn đúng).

**Dẫn chứng**: `if (a>0 && b>0)` → cần 2 TC (true, false). TC1 `a=5, b=0` (false toàn bộ); TC2 `a=1, b=0` (vẫn false thôi — đề hay đánh lừa) → cần thực sự 1 TC pass cả 2 condition.

---

### 14. Condition Coverage (CC)

> **Hook**: "Mỗi sub-condition phải nhận cả T và F". Soi sâu hơn branch — branch chỉ nhìn kết quả tổng hợp, condition coverage nhìn từng atomic.

**Core**: Mỗi condition đơn (Boolean atomic) phải nhận cả T và F ít nhất 1 lần.

**Công thức**:

```
CC = (tested boolean outcomes / total) × 100%
```

**BẪY CỰC LỚN**: Condition coverage **KHÔNG đảm bảo** decision/branch coverage. Có thể 100% condition mà chỉ test 1 nhánh của decision.

**Dẫn chứng**: `if (a==5 && b>0)`:
- TC1 `a=5, b=1` → (T, T) → branch = T.
- TC2 `a=0, b=0` → (F, F) → branch = F.
- Branch coverage = 100% nhưng `b>0` chưa được test thành T với `a≠5` → cần thêm TC3 `a=0, b=1` để `b>0=T`.

---

### 15. Coverage Hierarchy

> **Hook**: "Mỗi cấp coverage là tập con của cấp cao hơn — KHÔNG phải lúc nào cũng".

**Bảng quan hệ — hay vào đề CỰC NHIỀU**:

| Quan hệ                              | Đúng?         |
|--------------------------------------|---------------|
| 100% Branch ⇒ 100% Statement         | ✅ Luôn       |
| 100% Condition ⇒ 100% Branch         | ❌ KHÔNG      |
| 100% Path ⇒ 100% Branch ⇒ 100% Stmt  | ✅            |
| 100% Statement ⇒ 100% Branch         | ❌ KHÔNG      |

**Diagram**:

```
┌─ Path / MC/DC ───────────────────┐
│  ┌─ Multiple Condition ────────┐ │
│  │  ┌─ Condition ─┐ Branch ┐  │ │     Condition KHÔNG ⊂ Branch
│  │  └─────────────┘─────────┘  │ │     (đường thẳng đứt)
│  └─────────────────────────────┘ │
│  ┌─ Branch / Decision ──────────┐│
│  │  ┌─ Statement ───┐           ││
│  │  └───────────────┘           ││
│  └──────────────────────────────┘│
└──────────────────────────────────┘
```

**Dẫn chứng**: MC/DC dùng cho safety-critical (**DO-178B avionics** — chuẩn của FAA cho phần mềm hàng không).

---

### 16. White-box Testing — tổng quan

> **Hook**: Mở "hộp kính" (glass-box), thấy mọi cấu trúc bên trong. Tester biết code, biết design.

**Core**: Structural / glass-box — dựa trên design, internal logic, code structure.

**Áp dụng**: Unit level, modules high-risk.

**2 strategy chính**:
1. **Control Flow** (basis path, loop testing)
2. **Data Flow**

**Cons (đề hay hỏi)**:
- Tốn resource
- **KHÔNG test non-functional** (availability, load) — phải kết hợp black-box

---

### 17. Control Flow Graph (CFG)

> **Hook**: "Bản đồ đường đi của code". Mỗi ngã rẽ là 1 decision node, mỗi đoạn thẳng là 1 sequence.

**Core**: Đồ thị biểu diễn control structure:
- **Node** = statement(s)
- **Edge** = control flow
- **Decision node**: > 1 outgoing arrow
- **Junction node**: > 1 incoming arrow
- **Region**: bounded area (vùng kín)

**ASCII sample CFG cho `if-else`**:

```
        ┌───┐
        │ 1 │  start
        └─┬─┘
          │
        ┌─▼─┐
        │ 2 │  decision (if cond)
        └┬─┬┘
        T│ │F
     ┌───▼┐│ ┌▼───┐
     │ 3  ││ │ 4  │  branches
     └─┬──┘│ └──┬─┘
       │   └─┐  │
       │     │  │
     ┌─▼─────▼──▼─┐
     │      5     │  junction
     └────────────┘
```

**Patterns**:
- Sequence → 1 node thẳng.
- `if` → 2 edges.
- `loop` → cycle (vòng lặp).

---

### 18. Cyclomatic Complexity — V(G)

> **Hook**: "Số đường đi độc lập qua program". McCabe metric — upper bound số test case để cover mọi independent path.

**Core**: 3 công thức (kết quả GIỐNG NHAU — đây là điểm vàng vào đề):

```
┌───────────────────────────────────────┐
│  V(G) = E − N + 2                     │   (Edges − Nodes + 2)
│  V(G) = P + 1                         │   (Predicate/decision + 1)
│  V(G) = R                             │   (Regions, đếm cả vùng ngoài)
└───────────────────────────────────────┘
```

**Khi nào dùng công thức nào**:
- **E−N+2**: khi có sẵn CFG đếm edge và node.
- **P+1**: khi đếm được số decision (nhanh nhất với code).
- **R**: khi vẽ planar CFG (đẹp visualization).

**Dẫn chứng (Tutorial 10)**:
- Sequential code: **V(G) = 1**.
- 1 `if`: **V(G) = 2**.
- 2 nested `if`: **V(G) = 3**.
- Graph 2 decision node → V(G) = **2 + 1 = 3**.

**Self-check**: Một CFG có 8 edges, 7 nodes, 2 decision → V(G) = ?
→ Cách 1: 8 − 7 + 2 = **3**. Cách 2: 2 + 1 = **3**. Cách 3: đếm regions ra 3. → Cùng kết quả.

---

### 19. Basis Path Testing

> **Hook**: "Bộ test case tối thiểu phủ mọi đường đi độc lập" — McCabe's technique.

**4 bước**:
1. Draw **CFG**.
2. Tính **V(G)**.
3. Identify **basis set** = V(G) linearly independent path.
4. **Test case** force mỗi path.

**Guarantee**: Mỗi statement được execute ≥ 1 lần (= 100% statement coverage tối thiểu).

**Dẫn chứng**: V(G) = 3 → cần **3 test case** cho 3 path độc lập.

---

### 20. Loop Testing — Simple Loops

> **Hook**: "Test mép vòng lặp" — off-by-one, infinite loop hay xảy ra ở loop boundary.

**Core**: Với max iterations n, test các case:

| Case          | Mục đích                              |
|---------------|---------------------------------------|
| **Skip loop** (0 iter) | Loop có bị skip đúng không?  |
| **1 iteration**        | Entry/exit đơn giản          |
| **2 iterations**       | Tăng dần check               |
| **m iterations** (k<n) | "Typical" case               |
| **n−1, n, n+1**        | Boundary của max             |

**Dẫn chứng (lecture)**: input=0→0 pass, input=5→5 pass, input=6→5 pass (capped).

---

### 21. Loop Testing — Nested Loops

> **Hook**: "Inside-out để tránh bùng nổ tổ hợp" — n×m×k tăng theo cấp số nhân, không test exhaustive được.

**4 bước (inside-out)**:
1. Start innermost, set outer = min.
2. Apply **simple loop test** cho innermost.
3. Work outward, giữ inner ở "typical", outer khác ở min.
4. Continue cho đến outer cùng.

**Dẫn chứng**: 2 nested `for(n)(m)` — KHÔNG test n×m combination.

---

### 22. Loop Testing — Concatenated & Unstructured

| Loại                  | Đặc điểm                                       | Cách test                                    |
|-----------------------|------------------------------------------------|----------------------------------------------|
| **Concat independent**| 2 loop nối tiếp, không phụ thuộc                | Simple loop test mỗi cái                     |
| **Concat dependent**  | Loop1 counter feed Loop2 (final → init)         | Nested approach                              |
| **Unstructured**      | Goto-like, jumbled                              | **Redesign** nếu có thể                      |

**Dẫn chứng**: Loop2 dùng loop1's final counter làm init → dependent → test giống nested.

---

### 23. Data Flow Testing

> **Hook**: "Đời 1 biến gồm 3 giai đoạn: sinh, sống, chết". Bug data thường là dùng trước khi định nghĩa, hoặc gán mà chưa dùng đã xóa.

**Core**: White-box focus vào **variable definition** và **reference**.

**Life cycle 3 actions** — mnemonic **d-r-u**:

```
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│  d (define)  │ ──▶│ r (reference)│ ──▶│ u (undefine) │
│  assigns     │    │ uses value   │    │ kills/clears │
│  value/input │    │              │    │              │
└──────────────┘    └──────────────┘    └──────────────┘
   "Created"            "Used"             "Deleted"
```

**Phát hiện**: Initialization bug, assignment bug, sequence bug.

---

### 24. Data Flow — 9 Pairs of Operations

> **Hook**: "9 cặp action liên tiếp = 9 tình huống đời 1 biến". Cần phân loại đúng để biết cái nào lỗi, cái nào ổn.

**Bảng 9 pairs phân loại — CỰC HAY VÀO ĐỀ**:

| Cặp     | Ý nghĩa                                          | Phân loại                       |
|---------|--------------------------------------------------|---------------------------------|
| **dr**  | define → reference (gán rồi dùng)                | ✅ Valid / Normal               |
| **rd**  | reference → redefine (dùng rồi gán lại)          | ✅ Valid / Normal               |
| **rr**  | reference → reference (dùng nhiều lần)           | ✅ Valid / Normal               |
| **ru**  | reference → undefine (dùng rồi xóa)              | ✅ Valid / Normal               |
| **ud**  | undefine → redefine (xóa rồi gán mới)            | ✅ Valid / Normal               |
| **dd**  | define → define lại (overwrite không dùng)       | ⚠️ Suspicious (useless)         |
| **du**  | define → undefine (gán chưa dùng đã xóa)         | ⚠️ Suspicious                   |
| **ur**  | undefine → reference (dùng khi đã xóa)           | ❌ **Definite Error (SEVERE)**  |
| **uu**  | undefine → undefine (xóa hoài)                   | ❌ Definite Error               |

**Initial state `~` (trạng thái đầu)**:

| Cặp     | Ý nghĩa                                | Phân loại               |
|---------|----------------------------------------|-------------------------|
| **~d**  | start → define (gán đầu tiên)          | ✅ Normal               |
| **~r**  | start → reference (use before define)  | ❌ **Error**            |
| **~u**  | start → undefine (xóa biến chưa có)    | ⚠️ Abnormal             |

**Dẫn chứng**: Lecture scenario `~dduk` có abnormal pair `dd` → cần check.

---

### 25. Data Flow Testing Process

**4 bước**:
1. Build **DFG** từ CFG (label d/r/u trên node/edge).
2. Tính **V(G)**.
3. Tạo **paths** theo V(G).
4. **Test variable life cycle** trên mỗi path → tìm abnormal pair.

**Dẫn chứng**: V(G) = 3 → 3 scenarios per variable; check 5 vars × 3 scenarios.

---

### 26. Def-Use Pairs (DU pairs)

> **Hook**: "Mỗi định nghĩa phải có người dùng — không thì lãng phí (hoặc bug)".

**Core**: Cặp **(definition, use)** của cùng biến — definition tại node d, use tại node u, có path từ d→u **không re-define**.

**3 criterion bao hàm**:

```
All-defs ⊂ All-uses ⊂ All-du-paths
 yếu                       mạnh nhất
```

| Criterion          | Yêu cầu                                              |
|--------------------|------------------------------------------------------|
| **All-defs**       | Mỗi def reach ít nhất 1 use                          |
| **All-uses**       | Mỗi (def, use) pair được cover                       |
| **All-du-paths**   | Mỗi đường def→use loop-free được cover (mạnh nhất)   |

---

## LECTURE 11 — Security Testing

### 27. Quality vs Security

> **Hook**: "Security không phải lớp áo khoác ngoài". Phải design-in, không retrofit.

**Core**: High-quality SW phải **INHERENTLY** include security — đứng ngang performance, functionality, maintainability.

**Bài học**: Security retrofit thường thất bại; phải design-in từ **specification phase**.

---

### 28. Vulnerability — định nghĩa

> **Hook**: "Khe hở mà attacker chui vào được". Weakness/flaw trong architecture, code, configuration mà attacker exploit được.

**6 loại common vulnerabilities**:

| #  | Vulnerability                | Tóm tắt                                          |
|----|------------------------------|--------------------------------------------------|
| 1  | **Buffer Overflow**          | Ghi data vượt allocated memory (C/C++)           |
| 2  | **SQL Injection**            | Inject SQL malicious → manipulate/steal DB       |
| 3  | **XSS (Cross-Site Scripting)** | Inject script → hijack session                 |
| 4  | **URL Manipulation**         | Sửa URL param → bypass auth                      |
| 5  | **Spoofing**                 | Giả mạo IP/identity = trusted source             |
| 6  | **Weak Auth**                | Password yếu, không lockout                      |

---

### 29. Common Vulnerabilities — Memory & Data

| Vulnerability        | Cơ chế                                       | Hậu quả          | Prevent                   |
|----------------------|----------------------------------------------|------------------|---------------------------|
| **Buffer Overflow**  | Ghi data vượt allocated memory (C/C++)       | Crash, **RCE**   | Bounds check              |
| **SQL Injection**    | Inject SQL malicious vào input field          | Manipulate/steal DB | **Prepared Statements** |

---

### 30. Common Vulnerabilities — Web & Network

| Vulnerability         | Cơ chế                                          | Prevent                            |
|-----------------------|-------------------------------------------------|------------------------------------|
| **XSS**               | Inject malicious script vào trusted website → hijack session, execute trong browser khác | Output encoding |
| **URL Manipulation**  | Sửa URL parameter để bypass auth, access hidden data | Authorization check         |
| **Spoofing**          | Giả mạo IP/identity là trusted source           | Mutual TLS                         |

---

### 31. CIA Triad — Foundational Security

> **Mnemonic CIA** — 3 pillar bảo mật:

```
┌─────────────────────────────────────────────────┐
│  C — Confidentiality (giữ bí mật)              │
│       → Encryption, access control              │
├─────────────────────────────────────────────────┤
│  I — Integrity (giữ nguyên vẹn)                │
│       → Hash, signature, checksum               │
├─────────────────────────────────────────────────┤
│  A — Availability (giữ sẵn sàng)               │
│       → Redundancy, anti-DDoS                   │
└─────────────────────────────────────────────────┘
```

**Áp dụng**: Threat modeling, requirement definition. Security testing bảo vệ sensitive data → CIA.

---

### 32. OWASP Top 10

> **Hook**: "Bộ tiêu chuẩn ngành" cho web vulnerability. Open Web Application Security Project — industry benchmark.

**10 vulnerability nguy hiểm nhất**:
1. Injection
2. Broken Auth
3. XSS
4. IDOR (Insecure Direct Object Reference)
5. Security Misconfig
6. Sensitive Data Exposure
7. XXE (XML External Entity)
8. Broken Access Control
9. Insecure Deserialization
10. Components with Known Vulnerabilities

**Dẫn chứng**: DAST tool (ZAP, Burp) test theo OWASP Top 10.

---

### 33. Penetration Testing

> **Hook**: "Hacker mũ trắng đập cửa thử khóa". Manual exploratory testing simulating real-world attacks.

**Core**: Áp dụng ở **production-like environment**; trước go-live + định kỳ. Mục tiêu: discover & exploit vulnerability, assess resilience.

**2 loại pen-test — hay so sánh trong đề**:

| Loại                       | Knowledge của tester  | Kỹ thuật                              |
|----------------------------|-----------------------|---------------------------------------|
| **Black-box pen-test**     | Zero knowledge        | Phishing, **social engineering**      |
| **White-box pen-test**     | Full code access      | Tìm internal flaw (SQLi)              |

**Dẫn chứng**: Tutorial 11 dùng **pentest-tools.com** light scan.

---

### 34. Fuzzing (Fuzz Testing)

> **Hook**: "Bơm rác vào input xem app có chết không". Tự động bơm invalid/semi-valid data để trigger crash/exception.

**Áp dụng**: Input parser, API, file format. Trong CI hoặc lab security.

**3 loại fuzzing**:

| Loại                       | Cách hoạt động                                       |
|----------------------------|------------------------------------------------------|
| **Black-box random**       | Random data lớn                                      |
| **Grammar-based**          | Mutate valid format                                  |
| **White-box fuzzing**      | Dùng source + solver → force path                    |

**Dẫn chứng**: **Microsoft OneFuzz**; **Google ClusterFuzz** → tìm **27k Chrome bug** + **28k OSS bug**.

---

### 35. SAST (Static Application Security Testing)

> **Ẩn dụ**: "Đọc bản thiết kế tìm lỗi". Đọc code khi nó đang nằm im, không cần chạy.

**Core**: "White-box" analysis source code/binary **at rest**, KHÔNG execute.

**Áp dụng**: IDE plugin, code commit, **CI pipeline**. **Early SDLC**.

**Pros vs Cons**:
- ✅ Early/cheap → tìm hardcoded credentials, weak logic, SQLi sớm
- ❌ No runtime view, **false positive** nhiều

**Tools**: **SonarQube, Checkmarx, Fortify, Veracode**.

---

### 36. DAST (Dynamic Application Security Testing)

> **Ẩn dụ**: "Đập cửa thử khóa". Tấn công app đang chạy từ ngoài vào.

**Core**: "Black-box" test running app từ **outside-in**, simulating attack.

**Áp dụng**: Staging, QA, **Production**. **Later SDLC**.

**Pros vs Cons**:
- ✅ Real attack simulation, detect runtime issues (XSS, auth bypass, server misconfig)
- ❌ No source access → khó pinpoint vị trí code lỗi

**Tools**: **OWASP ZAP, Burp Suite, Invicti, Acunetix**.

---

### 37. IAST (Interactive Application Security Testing)

> **Ẩn dụ**: "Camera trong nhà". Agent nằm bên trong app runtime, monitor liên tục.

**Core**: **Hybrid** — agent in JVM/.NET, observe data flow.

**Áp dụng**: QA env trong automated UI / functional test. Active during **testing phase**.

**Pros vs Cons**:
- ✅ Accurate, deep, earlier than DAST, pinpoint vulnerable code, verify exploitability, scan 3rd party
- ❌ **KHÔNG replace DAST/pen-test**

**Tools**: **Contrast Security, Synopsys Seeker, Checkmarx IAST, HCL AppScan**.

---

### 38. RASP (Runtime Application Self-Protection)

> **Ẩn dụ**: "Vệ sĩ chặn kẻ trộm". Đứng trong production, không phải test mà **BLOCK** attack.

**Core**: Defense tool integrated vào app server, monitor traffic & behavior, **BLOCK attack**.

**Áp dụng**: **Production live**. After deployment.

**Bẫy quan trọng**: RASP là **DEFENSE**, không phải testing tool. 3 cái kia (SAST/DAST/IAST) là test; RASP block.

**Pros vs Cons**:
- ✅ Deeper than WAF, virtual patching
- ❌ KHÔNG silver bullet

**Tools**: **Imperva RASP, Contrast Protect, OpenRASP, Datadog**.

---

### 39. SAST vs DAST vs IAST vs RASP — bảng so sánh

| Tiêu chí        | **SAST**           | **DAST**             | **IAST**             | **RASP**             |
|-----------------|--------------------|----------------------|----------------------|----------------------|
| Approach        | White-box          | Black-box            | Hybrid               | Production defense   |
| Object          | Code **at rest**   | Running app          | Runtime (in-app)     | Runtime (in-app)     |
| Phase           | **Early SDLC**     | **Late SDLC**        | Testing phase        | **Production**       |
| Execute code?   | ❌ NO              | ✅ YES               | ✅ YES (agent)       | ✅ YES (agent)       |
| Mục đích        | Find vulns         | Simulate attack      | Find + verify        | **BLOCK** attack     |
| Tools           | SonarQube, Checkmarx, Fortify, Veracode | OWASP ZAP, Burp, Invicti, Acunetix | Contrast, Seeker, Checkmarx IAST, HCL AppScan | Imperva, Contrast Protect, OpenRASP, Datadog |

**Self-check**: 
- SAST hay DAST tìm **hardcoded credentials** tốt hơn? → **SAST** (đọc source).
- IAST hay DAST detect **runtime XSS** tốt hơn? → IAST chính xác hơn nhưng DAST broader.
- RASP có phải testing không? → **KHÔNG**, là defense.

---

### 40. Security Best Practices — Error & Logging

| Item                                  | Lý do                                              |
|---------------------------------------|----------------------------------------------------|
| Display **generic error**             | Error message reveal internal state → attacker enumerate |
| **Handle all exceptions**             | Tránh stack trace leak                             |
| Log user activities **NOT password**  | Log bị leak = lộ password                          |

**Dẫn chứng**: troyhunt.com — error message leak source code.

---

### 41. Security Best Practices — Network & Permissions

| Item                                | Cách                                       |
|-------------------------------------|--------------------------------------------|
| **HTTPS everywhere (TLS)**          | Force HTTPS, không HTTP                    |
| Proper file permission              | chown, chmod — least privilege             |

**Why**: HTTP capture lộ password.

---

### 42. Security Best Practices — Credentials & Passwords

> **Hook**: "Convenience = security flaw". Hard-coded credentials, password yếu = mở cửa.

**Rules**:
- **KHÔNG hard-code credentials**
- Enforce **strong password policy**
- Store **salted hash** (Bcrypt, Argon2i)
- **Password reset, không restore**
- **Tokenization** với encrypted session token

**Bảng hash function — từ tệ đến tốt**:

```
MD5  <  SHA-1  <  SHA-256 (unsalted)  <  Bcrypt (salted)  <  Argon2i
 ❌      ❌          ⚠️                       ✅                  ✅ OWASP khuyến nghị
```

**Dẫn chứng**: Bcrypt (salted) > SHA-256 (unsalted) > SHA-1 > MD5. Argon2i là khuyến nghị OWASP hiện đại.

---

### 43. Security Best Practices — Access Control

| Item                              | Mục đích                            |
|-----------------------------------|-------------------------------------|
| **Account lockout** (after N failed) | Defend brute-force                |
| **Least privilege**               | Limit blast radius                  |
| **Expire cookies/sessions**       | Counter session hijack              |

**How**: Counter failed attempts, set cookie TTL, principle of least privilege.

---

### 44. Security Best Practices — Input Validation

> **Hook**: "KHÔNG trust client" — client-side validation bypass dễ.

**Rules**:
- **Validate ALL input** (file, field, source)
- **Safe defaults**
- **Whitelist > Blacklist** (whitelist block unknown)
- **Server-side validation**, không chỉ client
- **Prepared statements**
- **Context-aware encoding**

---

### 45. Preventing Injection / Bots / DDoS

| Attack       | Defense                                       |
|--------------|-----------------------------------------------|
| **SQLi**     | **Prepared Statements** (ORM/parameterized)   |
| **XSS**      | **Context encoding** (HTML encoding)          |
| **Bots**     | **CAPTCHA**                                   |
| **DDoS**     | **Throttle login** (rate-limit middleware)    |

---

## LECTURE 12 — Testing Tools (Automation)

### 46. Automated Testing — tổng quan

> **Hook**: "Robot thay người bấm chuột". Tích hợp tool vào testing process — đặc biệt cho regression và volume lớn.

**Áp dụng**: Mọi level test, test lặp lại (regression), volume lớn.

**Quy trình**: Plan → design → prepare cases → **execute (auto)** → report → regression.

**5 types of test automation**:
1. **Code Auditing** (white-box)
2. **Coverage Monitoring** (white-box)
3. **Functional Tests** (black-box)
4. **Load Tests**
5. **Test Management**

---

### 47. Automated Testing — Adv / Disadv

| Advantage                          | Disadvantage                              |
|------------------------------------|-------------------------------------------|
| Accuracy                           | High package & training cost              |
| Completeness                       | High development cost                     |
| Comprehensive info                 | High prep manpower                        |
| Fewer manpower (execution)         | Considerable area uncovered               |
| Shorter cycle                      |                                           |
| Full regression                    |                                           |
| Beyond manual scope (load)         |                                           |

---

### 48. Selenium — tổng quan

> **Hook**: "Open-source automation suite cho web app". Free, multi-language, huge community.

**Áp dụng**: Web browser (Chrome, Firefox, Edge, Safari). UI regression, smoke test, E2E.

**Languages**: Java, C#, Python, Ruby, PHP, Perl, JS, Kotlin.

**4 components**:

| Component             | Vai trò                                             |
|-----------------------|-----------------------------------------------------|
| **Selenium IDE**      | Record-and-playback, đơn giản                       |
| **Selenium RC**       | Legacy remote control (merged into WebDriver)       |
| **Selenium WebDriver**| **Industry standard**, full control, CI/CD friendly |
| **Selenium Grid**     | Parallel execution across machines/browsers         |

---

### 49. Selenium Suite Components — chi tiết

| Component       | Mạnh                              | Yếu                                                |
|-----------------|-----------------------------------|----------------------------------------------------|
| **IDE**         | Record-playback nhanh             | **No loop/if**, hard maintain, **NO CI/CD**        |
| **RC**          | Legacy                            | Đã merged → không còn dùng riêng                    |
| **WebDriver**   | Full control, fast, CI/CD friendly | Phải code                                          |
| **Grid**        | Parallel exec                     | Cần infrastructure                                  |

**Bẫy**: Selenium IDE record-and-playback **KHÔNG support CI/CD** → không dùng cho production automation.

---

### 50. WebDriver Architecture — 4 layers

```
┌─────────────────────────────────────────────────────────────┐
│ Layer 1: Language Bindings (Java/Python/JS/C#... script)   │
│           ↓                                                 │
│ Layer 2: W3C WebDriver Protocol (JSON commands over HTTP)  │
│           ↓                                                 │
│ Layer 3: Browser Drivers (ChromeDriver, GeckoDriver, ...)  │
│           ↓                                                 │
│ Layer 4: Real Browser thực thi action                      │
└─────────────────────────────────────────────────────────────┘
```

**Dẫn chứng**: ChromeDriver intermediate giữa script & Chrome.

---

### 51. Selenium Locators — 8 loại

> **Hook**: "Cách định danh element trong DOM". WebDriver phải biết chính xác element trước khi click/type.

**Bảng 8 locators — theo priority best practice**:

| #  | Locator                | Tốc độ / Reliability        |
|----|------------------------|------------------------------|
| 1  | `By.id()`              | **Nhanh nhất, reliable nhất** |
| 2  | `By.name()`            | Alternate khi không có id    |
| 3  | `By.className()`       | Theo CSS class               |
| 4  | `By.tagName()`         | Theo HTML tag                |
| 5  | `By.linkText()`        | `<a>` theo exact visible text |
| 6  | `By.partialLinkText()` | `<a>` theo portion text      |
| 7  | `By.cssSelector()`     | Flexible & fast              |
| 8  | `By.xpath()`           | Mạnh nhất DOM phức tạp, **SLOWEST** |

**Best practice priority**: **id > name > css > xpath**.

**Self-check**: `By.id` hay `By.xpath` nhanh hơn? → **By.id** (xpath chậm nhất).

---

### 52. Browser & Navigation Commands

```java
driver.get("url")                  // open static page, wait full load
driver.getTitle()                  // title tab hiện tại
driver.getCurrentUrl()             // URL thực tế (test redirect)
driver.close()                     // close TAB hiện tại
driver.quit()                      // QUIT toàn bộ browser session (best practice end of test)
driver.navigate().to("url")        // like get nhưng RETAIN HISTORY
driver.navigate().back()           // click Back
driver.navigate().refresh()        // reload
```

**Bẫy CỰC HAY**: `driver.close()` vs `driver.quit()`:
- **close()** → đóng **1 tab hiện tại**.
- **quit()** → đóng **toàn bộ browser session** (best practice end of test).

---

### 53. Web Element Interaction Commands

| Nhóm           | Commands                                               |
|----------------|--------------------------------------------------------|
| **Action**     | `click()`, `sendKeys("text")`, `clear()`, `submit()`   |
| **Validation** | `getText()`, `getAttribute("href")`                    |
| **State**      | `isDisplayed()`, `isEnabled()`, `isSelected()`         |

**Dẫn chứng**: `submit()` press Enter trong form.

---

### 54. Handling Dropdowns — Select class

> **Hook**: Dropdown `<select>` đặc biệt — KHÔNG dùng `click/sendKeys` được, phải dùng class `Select`.

```java
WebElement dd = driver.findElement(By.id("countryDropdown"));
Select s = new Select(dd);
s.selectByVisibleText("Vietnam");
// s.selectByValue("VN");
// s.selectByIndex(1);
```

**3 strategies**:

| Method                       | Khi nào dùng                      |
|------------------------------|-----------------------------------|
| `selectByIndex(int)`         | Biết vị trí option                |
| `selectByValue("VN")`        | Có `value` attribute              |
| `selectByVisibleText("VN")`  | Match text hiển thị               |

---

### 55. JUnit 5 Assertions với Selenium

> **Hook**: Selenium *không quyết định pass/fail* — cần JUnit assertion để check.

| Assertion         | Dùng cho                              |
|-------------------|---------------------------------------|
| `assertEquals`    | Verify title, text, URL               |
| `assertTrue`      | Check element visible                 |
| `assertFalse`     | Verify loading spinner gone           |
| `assertNotNull`   | Verify element located                |

**Dẫn chứng**:

```java
assertEquals("https://example.com/dashboard", driver.getCurrentUrl(), "Login failed!");
```

---

### 56. Selenium Waits — Synchronization

> **Hook**: "Modern page = dynamic". DOM render chậm hơn script → cần wait, tránh `NoSuchElementException`.

**3 loại wait — bảng so sánh CỰC HAY VÀO ĐỀ**:

| Loại             | Scope             | Cách hoạt động                          | Best practice?      |
|------------------|-------------------|-----------------------------------------|---------------------|
| **Implicit Wait**| **Global**, set 1 lần per session | Wait up to X giây cho mọi missing element | OK nhưng generic |
| **Explicit Wait**| **Targeted**, per element/condition | Wait condition cụ thể, stop ngay khi true | ✅ **Industry best practice** |
| **Fluent Wait**  | Customizable polling interval | Ignore exception types | Advanced            |

**Syntax**:

```java
// Implicit Wait
driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));

// Explicit Wait
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
wait.until(ExpectedConditions.elementToBeClickable(...));
```

**Bẫy CỰC LỚN**: `Thread.sleep(2000)` chỉ để **visual demo**, **KHÔNG dùng production** (cứng nhắc, lãng phí thời gian).

**Self-check**: Explicit Wait hay Implicit Wait là industry best practice? → **Explicit Wait** (targeted, save time).

---

### 57. JMeter — tổng quan

> **Hook**: "Mô phỏng cả ngàn user cùng lúc". Java open-source app cho load test & performance.

**Multi-protocol**: HTTP/HTTPS, JDBC, REST/SOAP, FTP, JMS, …

**Khả năng**: Simulate concurrent user, browser-like (cookie/cache/header), record-playback.

**3 main use cases**:
1. **Performance Testing**
2. **Load Testing**
3. **Stress Testing**

---

### 58. JMeter — Performance Test Types

| Loại                | Mục tiêu                                          | Khi nào                  |
|---------------------|---------------------------------------------------|--------------------------|
| **Load Testing**    | Simulate **expected** user traffic, ensure handle | Test capacity normal     |
| **Stress Testing**  | Push **beyond normal** → find breaking point      | Test extreme             |
| **Performance**     | Tổng quát, analyze under various loads            | General                  |
| **Spike Testing**   | **Sudden surge** of traffic                       | Test elastic scaling     |
| **Endurance/Soak**  | **Long duration** (hours/days)                    | Test memory leak         |
| **Volume Testing**  | **Large data** volume                             | Test DB scale            |

**Self-check**: Load vs Stress?
- **Load** = test **expected** traffic (normal capacity).
- **Stress** = test **beyond normal** (find breaking point).

---

### 59. JMeter Test Plan — Anatomy

```
Test Plan (root)
  ├── Thread Group (users)
  │     ├── Number of Threads
  │     ├── Ramp-Up Period
  │     └── Loop Count
  │
  ├── Config Elements
  │     ├── HTTP Cookie Manager
  │     ├── HTTP Cache Manager
  │     ├── HTTP Header Manager
  │     ├── CSV Data Set Config
  │     └── HTTP Request Defaults
  │
  ├── Samplers (actions)
  │     ├── HTTP Request
  │     └── JDBC Request
  │
  ├── Logic Controllers
  │     ├── If Controller
  │     ├── Loop Controller
  │     ├── Once Only Controller
  │     └── Transaction Controller
  │
  ├── Timers (think time)
  │     └── Constant Timer 2000ms
  │
  ├── Pre/Post Processors
  │     ├── BeanShell PreProcessor
  │     └── JSON Extractor (Post)
  │
  ├── Assertions
  │     ├── Response Assertion
  │     └── Duration Assertion
  │
  └── Listeners (results)
        ├── View Results Tree
        ├── View Results in Table
        ├── Summary Report
        └── Aggregate Report
```

| Element              | Vai trò                                                |
|----------------------|--------------------------------------------------------|
| **Test Plan**        | Root node chứa mọi element                             |
| **Thread Group**     | Pool virtual user                                      |
| **Samplers**         | Send request (HTTP, JDBC)                              |
| **Timers**           | Delay simulate user reading                            |
| **Listeners**        | Validate response (Response Assertion, Duration)        |
| **Assertions**       | Validate response                                       |
| **Config Elements**  | Cookie/Cache/Header manager, CSV, defaults             |
| **Logic Controllers**| If, Loop, Once Only, Transaction                       |
| **Pre/Post Processors** | BeanShell, JSON Extractor                           |

---

### 60. JMeter — Handling Web Forms

- **Parameters**: HTTP Request → Parameters tab → Name-Value pair (`fromPort=Boston`, `toPort=London`).
- **HTTP Cookie Manager**: maintain session/login.
- **HTTP Cache Manager**: simulate browser cache (static asset load realistically).

---

### 61. JMeter — Script Creation

| Cách                       | Khi nào dùng                              |
|----------------------------|-------------------------------------------|
| **Manual Creation**        | Simple API — add Thread Group, Sampler, URL manually |
| **Recording** (Industry)   | Workflow phức tạp — dùng **proxy** hoặc **BlazeMeter Chrome Extension** |

**Recording workflow**:
1. Click through workflow → tool record HTTP/S.
2. Export `.jmx`.
3. Import vào JMeter.

**Lợi**: Capture hidden request, dynamic param, header tự động.

---

## TUTORIALS 9-12 — Worked Examples

### 62. Tutorial 9 — BadMoney (BVA Practice)

**Target**: 3 methods — `calculateDiscount`, `times100`, `calculateSavings`.

**Approach**: BVA 100% boundary coverage + JUnit 5 parameterized test.

**Rounding boundary** (RẤT TINH TẾ):
- 3rd decimal **0-4** → **round down** (0.0649 → 0.06).
- 3rd decimal **5-9** → **round up** (0.0650 → 0.07).
- BVA boundary tại 0.0050, 0.0049, 0.0050, 0.0051 (just above/below half).
- `times100`: **truncate** (4.35 → 435, but 4.34999 → 434).

---

### 63. Tutorial 9 — Fahrenheit Converter (EP + BVA)

**Formula**:

```
C = (F − 32) * 5/9
F = C * 9/5 + 32
```

**Rounding**: 1 decimal half-up (30.5499 → 30.5; 30.55 → 30.6).

**EP**: Valid range, invalid (vd dưới absolute zero -273.15°C / -459.67°F).

**BVA**: Tại boundary rounding: `...x9` vs `...x4`.

---

### 64. Tutorial 9 — Triangle (Decision Table + BVA)

**Inputs**: a, b, c ∈ [1, 200].

**Outputs**:

| Code | Tên             | Điều kiện                                       |
|------|-----------------|-------------------------------------------------|
| **-2** | OUT_OF_RANGE  | Any side out of [1, 200]                        |
| **-1** | INVALID       | Violate triangle inequality (a < b+c, b < a+c, c < a+b) |
| **2**  | EQUILATERAL   | a == b == c                                     |
| **1**  | ISOSCELES     | Exactly 2 sides equal                           |
| **0**  | SCALENE       | All different                                   |

**BVA boundary**: 0, 1, 2, 199, 200, 201.

**Decision Table example rules**: (range OK, triangle ineq OK, eq?, iso?, scalene?) → return code.

---

### 65. Tutorial 10 — HandleStr & Cyclomatic Complexity

**Bài toán**: Capitalize first letter của word bắt đầu bằng **u/v/t/k**, ghi mỗi sentence (kết thúc bằng `.?!`) trên 1 dòng vào file.

**Approach**: Draw Activity diagram → Flow Graph → tính V(G).

**Task 2**: Tạo TC đạt **100% Condition Coverage** cho HandleStr (stronger than Branch).

**Dẫn chứng**: Condition coverage requires test mỗi sub-condition T/F (u/v/t/k là OR chain → **4 condition**).

---

### 66. Tutorial 11 — pentest-tools.com (DAST)

**Target**: `http://testaspnet.vulnweb.com:80/`

**Workflow**:
1. Web scanner online → light scan website.
2. Run light scan **≥ 2 lần** → export report.
3. So sánh → list top 3 critical vulnerability.

---

### 67. Tutorial 11 — Nmap Flags

> **Hook**: Network mapper — phát hiện host, port, service, OS từ ngoài.

| Flag                  | Ý nghĩa                                              |
|-----------------------|------------------------------------------------------|
| `nmap -sn [IP]`       | **Ping scan** (host discovery, không scan port)      |
| `nmap -O [IP]`        | **OS detection**                                     |
| `nmap -p [port] [IP]` | Scan port cụ thể; range: `-p 1-1000`                 |
| `nmap -sT [IP]`       | **TCP connect scan** (full handshake, không cần root) |
| `nmap -sU [IP]`       | **UDP scan**                                         |
| `nmap -sS [IP]`       | (Bonus) **TCP SYN stealth scan** (need root, không complete handshake) |
| `nmap -A [IP]`        | (Bonus) **Aggressive scan** (OS + version + script + traceroute) |

**Port states**: open, closed, filtered, unfiltered, open|filtered, closed|filtered.

---

### 68. Tutorial 12 — Selenium WebDriver E2E (BlazeDemo)

**Target**: `https://blazedemo.com/`

**Workflow 8 bước**:
1. Init WebDriver + navigate URL.
2. **Implicit wait** (global).
3. **Verify title** (assertEquals).
4. **Find Flights** — Select dropdown departure/destination.
5. **Choose Flights** — **Explicit Wait** → click "Choose This Flight".
6. **Purchase** — fill form + click "Purchase Flight".
7. **Final validation** — locate success message.
8. `driver.quit()`.

**Dẫn chứng**: `Thread.sleep(2000)` chỉ để **visual demo**, KHÔNG dùng production.

---

### 69. Tutorial 12 — JMeter Test Plan (BlazeDemo)

**7 bước**:

| Step | Element                                | Detail                                              |
|------|----------------------------------------|-----------------------------------------------------|
| 1    | **Thread Group**                       | 10 threads, ramp-up 5s                              |
| 2    | **HTTP Request Sampler** (homepage)    | Protocol https, Server blazedemo.com                |
| 3    | **HTTP Request Sampler** (reserve)     | POST `/reserve.php`                                 |
| 4    | **Parameters tab**                     | `fromPort=Boston`, `toPort=London`                  |
| 5    | **Constant Timer**                     | 2000ms ("think time")                               |
| 6    | **Listener**                           | View Results Tree or View Results in Table          |
| 7    | Save `.jmx`, run, inspect response     |                                                     |

---

### 70. Maven `pom.xml` cho Tutorial 12

**Setup**: Java 21, Maven build.

**Dependencies** (exact version):

```xml
<dependency>
  <groupId>org.seleniumhq.selenium</groupId>
  <artifactId>selenium-java</artifactId>
  <version>4.41.0</version>
  <!-- compile scope -->
</dependency>

<dependency>
  <groupId>org.junit.jupiter</groupId>
  <artifactId>junit-jupiter-api</artifactId>
  <version>5.8.2</version>
  <scope>test</scope>
</dependency>
```

---

## Quick Reference — Tổng kết Day 3 trong 1 trang

### "Câu thần chú" cho mỗi lecture

| Lecture  | Một câu tóm gọn                                                                                       |
|----------|-------------------------------------------------------------------------------------------------------|
| **L9**   | Black-box = test input/output không xem code → 5 kỹ thuật **EP-BVA-DT-ST-PW**                         |
| **L10**  | White-box = soi code → Coverage (Stmt < Branch < Cond < Path) + V(G) + Data Flow (d/r/u, 9 pairs)     |
| **L11**  | Security = CIA triad + 4 phương pháp **SAST → DAST → IAST → RASP** (3 test + 1 defense)               |
| **L12**  | Automation = Selenium (WebDriver + 8 locator + Explicit Wait) + JMeter (Thread Group + Sampler + Listener) |

### 4 Security Testing Methods — bảng tổng hợp

| Method   | Approach    | Object         | Phase           | Block attack? | Tools                                              |
|----------|-------------|----------------|-----------------|---------------|----------------------------------------------------|
| **SAST** | White-box   | Code at rest   | Early SDLC      | ❌            | SonarQube, Checkmarx, Fortify, Veracode            |
| **DAST** | Black-box   | Running app    | Late SDLC       | ❌            | OWASP ZAP, Burp, Invicti, Acunetix                 |
| **IAST** | Hybrid agent| Runtime        | Testing         | ❌            | Contrast, Seeker, Checkmarx IAST, HCL AppScan      |
| **RASP** | Defense agent| Production    | Production      | ✅ **YES**    | Imperva, Contrast Protect, OpenRASP, Datadog       |

### 9 Data Flow Pairs — bảng tổng hợp

| Pair   | Phân loại               | Pair   | Phân loại                       |
|--------|-------------------------|--------|---------------------------------|
| **dr** | ✅ Valid                | **dd** | ⚠️ Suspicious                   |
| **rd** | ✅ Valid                | **du** | ⚠️ Suspicious                   |
| **rr** | ✅ Valid                | **ur** | ❌ Definite Error (SEVERE)      |
| **ru** | ✅ Valid                | **uu** | ❌ Definite Error               |
| **ud** | ✅ Valid                | **~r** | ❌ Error (use before define)    |

### Coverage Hierarchy — quy tắc bao hàm

```
100% Path     ⇒ 100% Branch ⇒ 100% Statement   ✅
100% Branch   ⇒ 100% Statement                  ✅
100% Condition ⇒ 100% Branch                    ❌ KHÔNG!
100% Statement ⇒ 100% Branch                    ❌ KHÔNG!
```

### Cyclomatic Complexity — 3 công thức cùng kết quả

```
V(G) = E − N + 2  (edges − nodes + 2)
V(G) = P + 1      (predicate + 1)
V(G) = R          (regions, gồm cả vùng ngoài)
```

---

## Top 15+ bẫy hay vào đề Day 3

1. **EP cho range** cần **3 TC tối thiểu** (1 valid + 2 invalid), không phải 2.
2. **BVA boundary "just above/below"** — với [1,100] phải test 0, 1, 2, 99, 100, 101 (6 điểm).
3. **100% Branch ⇒ 100% Statement** ✅ nhưng **100% Condition KHÔNG ⇒ 100% Branch** ❌.
4. **All-transitions ⇒ All-states** ✅ nhưng KHÔNG ngược lại.
5. **3 công thức V(G)** ra cùng kết quả: `E−N+2 = P+1 = R`.
6. **9 data flow pairs** phân loại: dr/rd/rr/ru/ud = Valid; dd/du = Suspicious; **ur/uu = Definite Error**.
7. **~r là error** (use before define); **~d là normal**; **~u là abnormal**.
8. **SAST = source code at rest** (early, white-box); **DAST = running app** (late, black-box).
9. **IAST = agent in runtime** during testing; **RASP = production defense** (BLOCKS attack — không phải testing!).
10. **Selenium IDE record-and-playback KHÔNG support CI/CD** → chỉ dùng cho demo.
11. **Locator priority**: `By.id > By.name > By.css > By.xpath` (xpath SLOWEST).
12. **Explicit Wait > Implicit Wait** — industry best practice (targeted, save time).
13. **`Thread.sleep` KHÔNG dùng production** — chỉ để visual demo.
14. **`driver.close()` đóng 1 tab; `driver.quit()` đóng toàn bộ session** (best practice end of test).
15. **JMeter Load vs Stress**: Load = expected traffic; Stress = beyond normal (breaking point); Spike = sudden surge; Endurance/Soak = long duration; Volume = large data.
16. **Testing budget thực tế ≈ 24% (plan 45%), time ≈ 27%** — bị cắt do deadline.
17. **Pen-test Black-box = zero knowledge** (phishing, social engineering); **White-box = full code access** (find internal SQLi).
18. **Bcrypt (salted) > SHA-256 (unsalted) > SHA-1 > MD5**; **Argon2i** là khuyến nghị OWASP hiện đại.
19. **Whitelist > Blacklist** trong input validation (whitelist block unknown).
20. **CIA triad**: Confidentiality (encryption) / Integrity (hash) / Availability (anti-DDoS).
