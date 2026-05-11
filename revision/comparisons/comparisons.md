# Bảng So Sánh Các Khái Niệm Dễ Nhầm — SQA

> Đây là tài liệu **cứu mạng** trong kỳ thi MCQ + fill-in-blank. Các cặp/nhóm khái niệm dưới đây là điểm "bẫy" thường gặp. Học thuộc cột so sánh — tránh nhầm khi áp lực thời gian.

---

## 1. Error vs Fault vs Failure (Lecture 1)

| Tiêu chí | **Error** | **Fault** | **Failure** |
|---|---|---|---|
| **Định nghĩa** | Lỗi do con người (programmer) | Phần code chứa error | Hành vi sai khi system chạy |
| **Khi nào xuất hiện** | Lúc viết/thiết kế | Sau khi code | Lúc runtime |
| **Có cần execution không?** | Không | Không | Có — phải activated |
| **Tính nhân quả** | Cause | Manifestation | Effect |
| **Ví dụ** | Lập trình viên gõ `+` thay vì `*` | Dòng code sai trong file | Output trả về 5 thay vì 6 |

**Mnemonic:** Error → Fault → Failure (chuỗi nhân quả, theo thứ tự thời gian).

---

## 2. Quality Assurance (QA) vs Quality Control (QC) vs Testing

| Tiêu chí | **QA** | **QC** | **Testing** |
|---|---|---|---|
| **Mục tiêu** | Prevent defects | Detect defects | Find defects in product |
| **Tập trung** | Process | Product | Product (execution) |
| **Hoạt động** | Lập plan, standard, training, review | Inspection, audit | Run test cases |
| **Thời điểm** | Toàn bộ lifecycle | Trong & sau development | Sau coding |
| **Scope** | Bao trùm QC + Testing | Subset của QA | Subset của QC |
| **Người làm** | QA Manager, team | QC Inspector | Tester |

**Nhớ:** QA ⊇ QC ⊇ Testing. "QA = how things are done; QC = whether things were done right."

---

## 3. Verification vs Validation

| Tiêu chí | **Verification** | **Validation** |
|---|---|---|
| **Câu hỏi** | "Are we building the product RIGHT?" | "Are we building the RIGHT product?" |
| **So với cái gì** | Specifications, documents | Real user needs, customer expectations |
| **Hoạt động** | Reviews, inspections, walkthroughs (static) | Testing — unit/integration/system (dynamic) |
| **Loại** | Static (không chạy code) | Dynamic (chạy code) |
| **Khi thực hiện** | Sớm trong SDLC | Sau khi có code |

---

## 4. McCall vs ISO 9126 vs ISO/IEC 25010

| Tiêu chí | **McCall (1977)** | **ISO 9126 (1991)** | **ISO/IEC 25010 (2011)** |
|---|---|---|---|
| **Số factors/characteristics** | 11 factors | 6 characteristics | 8 characteristics |
| **Số nhóm** | 3 (Operation, Revision, Transition) | Không nhóm | Không nhóm |
| **Operation/Run-time** | Correctness, Reliability, Efficiency, Integrity, Usability | Functionality, Reliability, Usability, Efficiency | Functional suitability, Performance efficiency, Compatibility, Usability, Reliability, Security |
| **Revision/Change** | Maintainability, Flexibility, Testability | Maintainability | Maintainability |
| **Transition/Adapt** | Portability, Reusability, Interoperability | Portability | Portability |
| **Bổ sung trong 25010** | — | — | Compatibility, Security (tách riêng) |

**Mnemonic McCall 11 factors:** C-R-E-I-U (operation 5) | M-F-T (revision 3) | P-R-I (transition 3)

---

## 5. McCall's 11 Quality Factors — Phân nhóm chi tiết

| Nhóm | Factor | What |
|---|---|---|
| **Product Operation** (5) | Correctness | Đáp ứng đúng spec, output đúng |
| | Reliability | Tỉ lệ failure thấp, ổn định |
| | Efficiency | Dùng ít tài nguyên (CPU, mem, network) |
| | Integrity | Security, kiểm soát truy cập |
| | Usability | Dễ học, dễ dùng |
| **Product Revision** (3) | Maintainability | Dễ sửa lỗi, modular |
| | Flexibility | Dễ thay đổi để đáp ứng requirement mới |
| | Testability | Dễ test, có log, intermediate output |
| **Product Transition** (3) | Portability | Chuyển sang platform khác dễ |
| | Reusability | Module dùng lại cho project khác |
| | Interoperability | Tương tác với system khác (API, REST) |

---

## 6. Reliability vs Correctness vs Robustness

| | **Correctness** | **Reliability** | **Robustness** |
|---|---|---|---|
| **What** | Đúng theo spec | Hoạt động liên tục, ít failure | Xử lý input bất thường tốt |
| **Đo bằng** | Spec compliance | MTBF, failure rate | Tỉ lệ crash khi input lỗi |
| **Ví dụ** | Output đúng cho input hợp lệ | Server uptime 99.9% | Không crash khi user nhập rác |

---

## 7. Maintainability vs Flexibility vs Testability

| | **Maintainability** | **Flexibility** | **Testability** |
|---|---|---|---|
| **Mục đích** | Sửa lỗi | Thêm/đổi feature | Test dễ |
| **Trigger** | Bug fix | New requirement, customization | Verify behavior |
| **Cần** | Modular, documented code | Plug-in architecture | Log, hook, predefined data |

---

## 8. SDLC Models: Waterfall vs V-Model vs Iterative vs Spiral vs Agile

| Tiêu chí | **Waterfall** | **V-Model** | **Iterative** | **Spiral** | **Agile** |
|---|---|---|---|---|---|
| **Cấu trúc** | Linear, sequential | Linear với testing song song | Lặp nhiều phase | Lặp + risk analysis | Sprint ngắn |
| **Khi nào dùng** | Requirement rõ, ổn định | Critical system | Requirement có thay đổi | High-risk project | Requirement không rõ, thay đổi liên tục |
| **Feedback** | Cuối project | Mỗi giai đoạn có test tương ứng | Cuối mỗi iteration | Sau mỗi vòng spiral | Cuối mỗi sprint |
| **Quay lại phase trước** | Khó | Có thể | Có | Có | Liên tục |
| **Risk handling** | Yếu | Trung bình | Tốt hơn | Mạnh nhất (built-in) | Phân tán qua sprint |
| **Documentation** | Nặng | Nặng | Vừa | Vừa | Nhẹ |

---

## 9. Scrum: 3 Roles + 5 Events + 3 Artifacts

| Loại | Thành phần | Mô tả |
|---|---|---|
| **Roles (3)** | Product Owner | Quản lý Product Backlog, ưu tiên |
| | Scrum Master | Coach team, remove blocker, không quản lý người |
| | Dev Team | Build increment, self-organizing |
| **Events (5)** | Sprint | Thời gian box (thường 2-4 tuần) |
| | Sprint Planning | Plan sprint sắp tới (≤ 8h cho sprint 1 tháng) |
| | Daily Scrum | 15 phút stand-up hằng ngày |
| | Sprint Review | Demo cho stakeholder (≤ 4h) |
| | Sprint Retrospective | Cải tiến process (≤ 3h) |
| **Artifacts (3)** | Product Backlog | Toàn bộ work cần làm |
| | Sprint Backlog | Subset cho sprint hiện tại |
| | Increment | Sản phẩm cuối sprint, "done" |

**Mnemonic:** 3-5-3 → "Three roles, Five events, Three artifacts."

---

## 10. Testing Levels: Unit vs Integration vs System vs Acceptance

| Tiêu chí | **Unit** | **Integration** | **System** | **Acceptance** |
|---|---|---|---|---|
| **What test** | 1 component nhỏ nhất | Tương tác giữa modules | Toàn bộ system | System với user thật |
| **Who tests** | Developer | Developer/Tester | Independent test team | Customer/User |
| **Where** | Dev's site | Dev's site | Dev's site | Customer's site |
| **Test type** | White-box | White + Black box | Mostly black-box | Black-box |
| **Data** | Synthetic | Synthetic | Realistic | Real data |
| **Strategy** | TDD, JUnit | Top-down, Bottom-up, Big Bang | End-to-end | UAT, Alpha, Beta |
| **Ai chịu trách nhiệm cuối** | Dev | Dev | QA team | **Customer** |

---

## 11. Integration Strategies: Top-down vs Bottom-up vs Big Bang vs Sandwich

| | **Top-down** | **Bottom-up** | **Big Bang** | **Sandwich** |
|---|---|---|---|---|
| **Hướng** | Trên xuống | Dưới lên | Tất cả cùng lúc | Trên + Dưới đồng thời |
| **Cần stub/driver?** | Cần **stubs** | Cần **drivers** | Không | Cả 2 |
| **Phát hiện lỗi early** | Major control flow | Low-level utils | Khó isolate | Cả hai đầu |
| **Khi dùng** | Top-level critical | Low-level reused | System nhỏ | System lớn |

---

## 12. Review Types: Formal Design Review vs Inspection vs Walkthrough vs Expert Opinion

| Tiêu chí | **Formal DR** | **Inspection** | **Walkthrough** | **Expert opinion** |
|---|---|---|---|---|
| **Formality** | Cao nhất | Cao | Thấp | Thấp |
| **Authority** | Có quyền approve cho next phase | Không có quyền approve | Không | Không |
| **Presenter** | — | KHÔNG phải author (thường là Coder) | LÀ author | — |
| **Leader** | Review Leader (external) | Moderator | Coordinator | — |
| **Đầu ra** | Approve/Partial/Deny + Action items | Defect list + corrective action | Comments | Recommendation |
| **Roles đặc thù** | — | Designer, Coder, Tester | Standards Enforcer, Maintenance Expert, User Rep | — |
| **Team size** | 3-5 | 3-5 | 3-5 | 1+ |
| **Max thời gian** | 2 tiếng | — | — | — |

**Nhớ:** Inspection > Walkthrough về formality. Author là presenter trong Walkthrough, KHÔNG phải trong Inspection.

---

## 13. Fagan Inspection 6 Steps

| # | Step | Mục đích |
|---|---|---|
| 1 | **Planning** | Chọn material, tập hợp team |
| 2 | **Overview** | Author giới thiệu material |
| 3 | **Preparation** | Reviewers nghiên cứu riêng |
| 4 | **Meeting** | Inspection meeting, list defects |
| 5 | **Rework** | Author sửa defects |
| 6 | **Follow-up** | Verify defects đã sửa |

**Mnemonic:** "**P**eople **O**ften **P**repare **M**uch **R**eview **F**ollowing"

---

## 14. Black-box vs White-box vs Gray-box

| Tiêu chí | **Black-box** | **White-box** | **Gray-box** |
|---|---|---|---|
| **Nội bộ code** | Không biết | Biết hết | Biết một phần |
| **Dựa trên** | Specification | Code structure | Cả 2 |
| **Ai làm** | Tester, customer | Developer | Tester có hiểu biết code |
| **Techniques** | EP, BVA, Decision Table, State Transition, Pairwise | Statement, Branch, Condition, Path, Data flow | API testing, integration |
| **Mục tiêu** | Verify behavior | Verify implementation logic | Both |

---

## 15. Black-box Techniques: EP vs BVA vs Decision Table vs State Transition vs Pairwise

| Technique | **What** | **Khi dùng** | **Test case** |
|---|---|---|---|
| **EP (Equivalence Partitioning)** | Chia input thành valid/invalid classes | Input có range hoặc category | 1 rep / class |
| **BVA (Boundary Value Analysis)** | Test giá trị tại biên | Có boundary rõ (min, max) | min-1, min, max, max+1 (2-value) hoặc min-1, min, min+1, max-1, max, max+1 (3-value) |
| **Decision Table** | Combinations of conditions → actions | Logic phức tạp với nhiều condition | 2^N rules với N conditions |
| **State Transition** | Test transition giữa các state | System có state | 0-switch (all states), 1-switch (all pairs) |
| **Pairwise (All-pairs)** | Test mọi cặp giá trị | Nhiều parameter, giá trị nhiều | Ít hơn exhaustive nhiều |

**Cặp dễ nhầm:** EP "1 đại diện cho class", BVA "test biên". Thường dùng kết hợp EP + BVA.

---

## 16. EP vs BVA: Chi tiết

| | **EP** | **BVA** |
|---|---|---|
| **Hypothesis** | "Cùng class → cùng behavior" | "Lỗi tập trung ở biên" |
| **Số test case cho range [1,100]** | 3 (1 invalid <1, 1 valid, 1 invalid >100) | 6 (0, 1, 2, 99, 100, 101) hoặc 4 (0,1,100,101) |
| **Tốt cho** | Categorical input | Numeric range, age, length |
| **Yếu khi** | Lỗi ở biên | Lỗi giữa range |

---

## 17. Code Coverage Hierarchy (từ yếu đến mạnh)

```
Statement < Decision/Branch < Condition < Decision/Condition < Multiple Condition < MC/DC < Path
```

| Coverage | Required | Test case count cho `if (A && B)` |
|---|---|---|
| **Statement** | Execute mỗi statement ≥ 1 lần | 1 (A=T, B=T) |
| **Decision/Branch** | Mỗi branch (T/F của condition tổng) ≥ 1 | 2 (T-T, F-anything) |
| **Condition** | Mỗi sub-condition T và F | 2 (A=T,B=F + A=F,B=T) |
| **Decision/Condition** | Cả Decision + Condition | 2-4 |
| **Multiple Condition** | Mọi combination của sub-conditions | 2^N |
| **MC/DC** | Mỗi sub-condition ảnh hưởng độc lập đến decision | N+1 (xấp xỉ) |
| **Path** | Mỗi path qua code ≥ 1 lần | Có thể vô hạn (loop) |

**Bẫy:** Branch coverage 100% **không** đảm bảo Condition coverage 100%, và ngược lại.

---

## 18. Cyclomatic Complexity — 3 Công Thức

Cho Control Flow Graph (CFG):

| Cách | Công thức | Ký hiệu |
|---|---|---|
| **1. Edges - Nodes + 2** | V(G) = E - N + 2 | E = số edges, N = số nodes |
| **2. Predicates + 1** | V(G) = P + 1 | P = số predicate nodes (decision nodes) |
| **3. Regions** | V(G) = số regions (kể cả outer) trong planar graph | — |

**3 cách phải cho cùng kết quả.** Số test case tối thiểu cho basis path = V(G).

**Ý nghĩa:**
- V(G) ≤ 10: code dễ test
- V(G) > 10: code phức tạp, cần refactor

---

## 19. Data Flow Testing Coverage

| Coverage | Yêu cầu |
|---|---|
| **All-defs** | Với mỗi def của biến, đi qua ≥ 1 use |
| **All-uses** | Mỗi def-use pair phải được thực thi |
| **All-c-uses** | Mọi (def, computational-use) pair |
| **All-p-uses** | Mọi (def, predicate-use) pair |
| **All-du-paths** | Mọi path từ def đến use (nhiều nhất) |

**Strength:** all-defs < all-c-uses, all-p-uses < all-uses < all-du-paths

---

## 20. Security: CIA Triad

| | **Confidentiality** | **Integrity** | **Availability** |
|---|---|---|---|
| **What** | Data chỉ người được phép thấy | Data không bị sửa trái phép | System sẵn sàng khi cần |
| **Threat** | Eavesdropping, leak | Tampering, MITM | DoS, hardware failure |
| **Defense** | Encryption, access control | Hash, signature | Redundancy, backup |

---

## 21. Quality vs Security

| | **Quality** | **Security** |
|---|---|---|
| **Question** | "Does it do what it SHOULD?" | "Does it NOT do what it SHOULDN'T?" |
| **Goal** | Functional + non-functional correctness | Prevent unauthorized access |
| **Tester mindset** | Validate intended behavior | Adversarial — break the system |
| **Coverage** | Specification | Threat model |

---

## 22. Security Testing Types: SAST vs DAST vs IAST vs RASP vs Penetration

| | **SAST** | **DAST** | **IAST** | **RASP** | **Penetration testing** |
|---|---|---|---|---|---|
| **Full name** | Static App Sec Testing | Dynamic App Sec Testing | Interactive AST | Runtime App Self-Protection | Pen test |
| **Khi test** | Build time (code chưa chạy) | Runtime (running app) | Runtime + code analysis | Runtime (protect, not just test) | Manual, ad-hoc |
| **Cần source code?** | Có | Không | Có (agent in app) | Có | Không bắt buộc |
| **Tốc độ** | Nhanh | Chậm | Trung bình | Continuous | Chậm |
| **False positive** | Cao | Thấp | Trung bình | Thấp | Thấp (manual) |
| **Tool ví dụ** | SonarQube, Checkmarx | OWASP ZAP, Burp | Contrast, Seeker | Imperva RASP | Nmap + manual |

---

## 23. Performance Test Types: Load vs Stress vs Spike vs Endurance vs Volume

| Type | **Mục đích** | **Load pattern** |
|---|---|---|
| **Load** | Verify performance dưới expected load | Steady, normal level |
| **Stress** | Tìm breaking point | Tăng dần vượt capacity |
| **Spike** | Test phản ứng với sudden surge | Đột ngột tăng vọt → giảm |
| **Endurance (Soak)** | Tìm memory leak, degradation | Sustained over long time |
| **Volume** | Test với data size lớn | Lượng data tăng |

---

## 24. Selenium Locators (8 loại)

| Locator | Syntax (Java) | Khi dùng |
|---|---|---|
| **ID** | `By.id("username")` | Best — unique, fastest |
| **Name** | `By.name("user")` | Form fields |
| **Class Name** | `By.className("btn")` | CSS class |
| **Tag Name** | `By.tagName("input")` | Element type |
| **Link Text** | `By.linkText("Click here")` | Anchor exact text |
| **Partial Link Text** | `By.partialLinkText("Click")` | Anchor partial |
| **CSS Selector** | `By.cssSelector("#main .row")` | Phức tạp, fast |
| **XPath** | `By.xpath("//div[@id='x']")` | Most flexible, slow |

**Priority:** ID > Name > CSS Selector > XPath (XPath chậm nhất).

---

## 25. Selenium Waits: Implicit vs Explicit vs Fluent

| | **Implicit Wait** | **Explicit Wait** | **Fluent Wait** |
|---|---|---|---|
| **Scope** | Global (toàn driver) | Element/condition specific | Element/condition specific |
| **Polling** | Auto | Default 500ms | Custom interval |
| **Condition** | Element present | ExpectedCondition (clickable, visible...) | ExpectedCondition + ignore exceptions |
| **Code** | `driver.manage().timeouts().implicitlyWait(10, SEC)` | `new WebDriverWait(driver,10).until(...)` | `new FluentWait<>(driver).withTimeout(...).pollingEvery(...).ignoring(...)` |
| **Flexibility** | Thấp | Trung bình | Cao nhất |

**Bẫy:** KHÔNG nên trộn Implicit + Explicit wait → timing không lường được.

---

## 26. JMeter Element Hierarchy

| Element type | Mục đích | Ví dụ |
|---|---|---|
| **Thread Group** | Mô phỏng users | Number of threads, ramp-up, loop count |
| **Sampler** | Gửi request | HTTP Request, FTP, JDBC, SOAP |
| **Logic Controller** | Điều khiển flow | If Controller, Loop Controller, Transaction |
| **Listener** | Hiển thị result | View Results Tree, Aggregate Report, Summary Report |
| **Timer** | Tạo think time | Constant Timer, Gaussian Random Timer |
| **Assertion** | Verify response | Response Assertion, Duration Assertion |
| **Config Element** | Cấu hình | HTTP Header Manager, Cookie Manager, CSV Data Set |
| **Pre/Post Processor** | Trước/sau sampler | Regex Extractor (post), User Parameters (pre) |

---

## 27. Use Case Relationships: `<<include>>` vs `<<extend>>` vs Generalization

| | **`<<include>>`** | **`<<extend>>`** | **Generalization** |
|---|---|---|---|
| **Ý nghĩa** | Bắt buộc — luôn execute included UC | Optional — chỉ execute ở extension point | Kế thừa UC tổng |
| **Mũi tên** | Base ─→ Included | Extension ─→ Base | Specialized ─→ General |
| **Khi dùng** | Reuse common behavior | Optional/exceptional behavior | Specialized form |
| **Ví dụ** | Login `<<include>>` ValidateCredentials | Search `<<extend>>` SaveSearchHistory | Online Payment ─→ Payment |

**Mnemonic:** include = "**must** include", extend = "**may** extend".

---

## 28. ER Diagram Cardinality Notations

| | **Chen** | **Crow's Foot** |
|---|---|---|
| **1:1** | 1 — 1 | `─║`...`║─` |
| **1:N** | 1 — N | `─║`...`─<` |
| **N:M** | N — M | `>─`...`─<` |
| **Optional** | (0,1), (0,N) | Vòng tròn trên đường |
| **Mandatory** | (1,1), (1,N) | Vạch ngang trên đường |

---

## 29. F.I.R.S.T Principles (TDD)

| Chữ | Ý nghĩa | Mô tả |
|---|---|---|
| **F** | Fast | Test chạy nhanh — second's tier |
| **I** | Independent (Isolated) | Test không phụ thuộc nhau |
| **R** | Repeatable | Chạy bao nhiêu lần cũng cho kết quả như nhau |
| **S** | Self-validating | Pass/Fail rõ ràng, không cần manual check |
| **T** | Timely | Viết test ngay khi/trước khi viết code |

---

## 30. TDD Red-Green-Refactor Cycle

| Phase | Hành động | Mục tiêu |
|---|---|---|
| 🔴 **Red** | Viết test fail | Test code đúng — fail vì chưa implement |
| 🟢 **Green** | Viết code đơn giản nhất để pass | Make it work — chấp nhận code xấu tạm |
| 🔵 **Refactor** | Cải thiện code mà không thay đổi behavior | Make it clean — test vẫn pass |

---

## 31. HTTP Methods — Idempotency & Safety

| Method | **Safe** (không thay đổi data) | **Idempotent** (gọi N lần = 1 lần) | Mục đích |
|---|---|---|---|
| **GET** | ✅ | ✅ | Read |
| **HEAD** | ✅ | ✅ | Read metadata |
| **OPTIONS** | ✅ | ✅ | Check available methods |
| **POST** | ❌ | ❌ | Create |
| **PUT** | ❌ | ✅ | Update/Replace |
| **PATCH** | ❌ | ❌ (thường) | Partial update |
| **DELETE** | ❌ | ✅ | Delete |

**Bẫy:** POST không idempotent (gọi 2 lần tạo 2 record), PUT idempotent (gọi 2 lần update cùng giá trị).

---

## 32. HTTP Status Code Categories

| Range | Category | Ví dụ |
|---|---|---|
| **1xx** | Informational | 100 Continue, 101 Switching |
| **2xx** | Success | 200 OK, 201 Created, 204 No Content |
| **3xx** | Redirection | 301 Moved Permanently, 304 Not Modified |
| **4xx** | Client error | 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 409 Conflict |
| **5xx** | Server error | 500 Internal Error, 502 Bad Gateway, 503 Unavailable |

**Bẫy thường gặp:** 401 (chưa auth) vs 403 (auth rồi nhưng không có quyền) vs 404 (không tồn tại).

---

## 33. Nmap Common Flags

| Flag | Mục đích |
|---|---|
| `-sS` | SYN scan (stealthy) — half-open |
| `-sT` | TCP connect scan (full handshake) |
| `-sU` | UDP scan |
| `-sV` | Version detection |
| `-O` | OS detection |
| `-A` | Aggressive (OS + version + scripts + traceroute) |
| `-p <port>` | Specific port hoặc range (-p 1-1000) |
| `-Pn` | Skip ping (treat host as up) |
| `-T4` | Speed timing (0=slowest, 5=fastest) |

**Port states:** `open`, `closed`, `filtered` (firewall blocking), `unfiltered`, `open|filtered`.

---

## 34. OWASP Top 10 (2021)

| # | Risk | Mô tả ngắn |
|---|---|---|
| A01 | Broken Access Control | Quyền sai, IDOR |
| A02 | Cryptographic Failures | Plaintext, weak hash |
| A03 | Injection | SQL, NoSQL, command, LDAP injection |
| A04 | Insecure Design | Thiết kế thiếu security |
| A05 | Security Misconfiguration | Default password, exposed endpoint |
| A06 | Vulnerable & Outdated Components | Lib lỗi thời |
| A07 | Identification & Authentication Failures | Weak auth, session fixation |
| A08 | Software & Data Integrity Failures | Unsigned update, deserialization |
| A09 | Security Logging & Monitoring Failures | Không log, không alert |
| A10 | Server-Side Request Forgery (SSRF) | Server bị lừa gọi internal |

---

## 35. SQA Components (6 nhóm chính — Lecture 3)

| Nhóm | Components điển hình |
|---|---|
| **1. Pre-project** | Contract review, Development plan, Quality plan |
| **2. Project life cycle** | Reviews, Expert opinion, Testing, Maintenance |
| **3. Infrastructure** | Procedures, Templates, Checklists, Training, CASE tools, Configuration management |
| **4. Management** | Project progress control, Quality metrics, Costs of software quality |
| **5. Standardization & certification** | ISO 9001, IEEE standards, CMM/CMMI |
| **6. Organizing for SQA** | Managers, Testers, SQA committees, SQA forums |

---

## 36. Test Plan IEEE 829 Sections (16 sections)

1. Test plan identifier
2. Introduction
3. Test items
4. Features to be tested
5. Features not to be tested
6. Approach (strategy)
7. Item pass/fail criteria
8. Suspension criteria & resumption requirements
9. Test deliverables
10. Testing tasks
11. Environmental needs
12. Responsibilities
13. Staffing & training needs
14. Schedule
15. Risks & contingencies
16. Approvals

**Mnemonic:** "Test plan IEEE 829 = 16 sections"

---

## 37. Test Termination Criteria (5 routes — Lecture 6)

1. **Completed Implementation** — All tests run & clean
2. **Mathematical Models** — Error detection rate → acceptable
3. **Error Seeding** — % of seeded errors detected
4. **Dual Teams** — Compare 2 independent teams' results
5. **Resource Limit** — Budget/time exhausted

---

## 38. Unit Test Phases (4 phases — Lecture 6)

| # | Phase | Mô tả |
|---|---|---|
| 1 | **Set up** | Khởi tạo state, mock |
| 2 | **Exercise** | Gọi method being tested |
| 3 | **Verify** | Assert kết quả |
| 4 | **Teardown** | Dọn dẹp state |

**JUnit 5 mapping:** `@BeforeEach` (set up), `@Test` body (exercise + verify), `@AfterEach` (teardown).

---

## 39. UI Principles — Nielsen 10 Usability Heuristics

1. Visibility of system status
2. Match between system and real world
3. User control and freedom
4. Consistency and standards
5. Error prevention
6. Recognition rather than recall
7. Flexibility and efficiency of use
8. Aesthetic and minimalist design
9. Help users recognize, diagnose, recover from errors
10. Help and documentation

**Mnemonic:** "10 Nielsen heuristics" — số chính xác là **10**.

---

## 40. UML Class Diagram Multiplicity

| Notation | Ý nghĩa |
|---|---|
| `1` | Exactly one |
| `0..1` | Zero or one (optional) |
| `*` hoặc `0..*` | Zero or more |
| `1..*` | One or more |
| `n..m` | Between n and m |

---

## Sticker tổng kết — In ra để mang đi thi

> **McCall:** 11 / 3 nhóm (5-3-3)  
> **SQA components:** 6 nhóm  
> **Testing levels:** 4 (Unit → Integ → System → Accept)  
> **Scrum:** 3-5-3 (roles-events-artifacts)  
> **Black-box techniques:** 5 (EP, BVA, DT, ST, Pair)  
> **Coverage hierarchy:** Stmt → Branch → Cond → MC/DC → Path  
> **Cyclomatic:** V(G) = E - N + 2 = P + 1 = #regions  
> **F.I.R.S.T:** Fast / Independent / Repeatable / Self-validating / Timely  
> **TDD:** Red → Green → Refactor  
> **CIA:** Confidentiality / Integrity / Availability  
> **OWASP Top 10 (2021):** A01-A10  
> **Selenium 8 locators:** id, name, class, tag, link, partial link, css, xpath  
> **Selenium 3 waits:** Implicit / Explicit / Fluent  
> **Nielsen:** 10 heuristics  
> **IEEE 829:** 16 sections của test plan  
> **Fagan inspection:** 6 steps (Plan → Overview → Prep → Meeting → Rework → Follow-up)
