# DAY 3 — Testing Techniques, Security & Automation (5W Summaries)

> Trọng tâm: Black-box, White-box, Security testing, Selenium, JMeter — đây là phần dày nhất của môn.

---

## Lecture 9 — Black-box Testing

### 1. Software Testing (Định nghĩa)
- **What**: Tiến trình hình thức (formal process) thực thi chương trình bởi specialized testing team để tìm lỗi.
- **Where**: Áp dụng trên unit, nhóm unit tích hợp, hoặc toàn bộ package.
- **When**: Sau khi có approved test procedures và approved test cases.
- **Why**: Tìm càng nhiều lỗi càng tốt; đưa SW đến mức quality chấp nhận được.
- **How**: Chạy code trên máy tính theo test procedure đã duyệt (không bao gồm code review).
- **Dẫn chứng**: Budget testing ≈ 24% project budget, time ≈ 27% schedule (thực tế plan 45% nhưng bị cắt do deadline).

### 2. Testing Objectives (Direct & Indirect)
- **What**: Direct = tìm lỗi, đạt acceptable quality, hiệu quả trong budget/schedule. Indirect = ghi nhận lỗi cho corrective/preventive actions.
- **Where**: Toàn dự án.
- **When**: Suốt SDLC.
- **Why**: Myers (1979): "If your goal is to show the absence of errors you won't discover many." → mindset phải là tìm bug.
- **How**: Lập kế hoạch, thiết kế test, thực thi, theo dõi lỗi.
- **Dẫn chứng**: Test record dùng cho preventive actions (lecture 5).

### 3. Verification vs Validation vs Qualification
- **What**: Verification = "build the product right" (consistency); Validation = "build the right product" (customer needs); Qualification = suitable for operational use (maintenance, coding standards).
- **Where**: Trong V&V process suốt SDLC.
- **When**: Verification giữa các pha; Validation cuối; Qualification trước go-live.
- **Why**: 3 góc nhìn khác nhau về đảm bảo chất lượng.
- **How**: Verification check phase-to-phase; Validation check vs requirement; Qualification check operations.
- **Dẫn chứng**: Verification compare design output vs requirement document.

### 4. Black-box Testing (Tổng quan)
- **What**: Behavioral/behavior-based technique — chỉ test input/output, không xem internal code.
- **Where**: Mọi level (Unit → System), đặc biệt System/Acceptance.
- **When**: Khi không cần kiến thức code, hoặc khi test performance/load.
- **Why**: Hiệu quả về resource, broad scope, có thể test load/availability.
- **How**: 5 kỹ thuật chính: EP, BVA, Decision Table, State Transition, Pairwise.
- **Dẫn chứng**: Disadvantage: masked errors (lỗi triệt tiêu nhau), no coverage control, không check coding quality.

### 5. Equivalence Partitioning (EP)
- **What**: Chia input domain thành các partition (equivalence class) mà program xử lý giống nhau.
- **Where**: Khi input có range, set, boolean, array, string.
- **When**: Bước đầu thiết kế test để giảm redundancy.
- **Why**: Không cần test mọi giá trị; tin tưởng class đại diện.
- **How**: Mỗi EC ít nhất 1 test case. Total TC ≥ số EC.
- **Dẫn chứng**: 
  - Range: 1 valid + 2 invalid class.
  - Specific value: 1 valid + 2 invalid.
  - Set member: 1 valid + 1 invalid.
  - Boolean: 1 valid + 1 invalid.
  - VD: Input age 0-120 → valid [0,120], invalid (<0), invalid (>120).

### 6. Boundary Value Analysis (BVA)
- **What**: Mở rộng EP, chọn giá trị TẠI và GẦN biên (errors xuất hiện nhiều ở edge).
- **Where**: Khi input/output có range hoặc số lượng giá trị.
- **When**: Sau khi xác định EC.
- **Why**: Lỗi off-by-one (>=, >, =, ≤) thường xảy ra ở boundary.
- **How**: Với range [a,b]: test a, b, just above a, just below a, just above b, just below b. 2-value: {a-1, a, b, b+1} hoặc {a, a+1, b-1, b}; 3-value: thêm cả {min, min+1, max-1, max, +ngoài biên}.
- **Dẫn chứng**: 
  - Input 1-100 → BVA test: 0, 1, 2, 99, 100, 101.
  - Tutorial 9 Exercise 3: Triangle với sides 1-200 inclusive → boundary: 0, 1, 2, 199, 200, 201.

### 7. Decision Table Testing
- **What**: Bảng mô hình hóa business logic dạng rule = combination của conditions → actions.
- **Where**: Logic phức tạp ("if X and Y but not Z").
- **When**: Khi cần đảm bảo completeness (không miss combination).
- **Why**: Mỗi combination → defined outcome; tránh sót case.
- **How**: 
  1. List conditions (T/F).
  2. List actions.
  3. Tạo rule (column) = mọi combination.
  4. Loại rule không thể xảy ra.
- **Dẫn chứng**: Car insurance: Male/Female × Age range (<25, 25-65, ≥65) → fee. Tutorial 9 Exercise 3 Triangle dùng Decision Table + BVA.

### 8. State Transition Testing
- **What**: Model hành vi hệ thống qua các State và Transition.
- **Where**: Hệ thống có trạng thái rõ (ATM, login flow, order workflow).
- **When**: Khi behavior phụ thuộc vào lịch sử (stateful).
- **Why**: Phát hiện invalid transitions, defect masking.
- **How**: 5 bước — (1) Define perspective, (2) Identify states, (3) Map transitions (event, guard, action), (4) Model bằng graph/table, (5) Verify.
- **Dẫn chứng**: ATM machine. All-states coverage: 2 paths đủ. All-transitions coverage: 4 paths.

### 9. State Transition Coverage Criteria
- **What**: (1) All-states coverage = exercise mọi state. (2) All-transitions coverage = exercise mọi valid transition + thử invalid.
- **Where**: State diagram.
- **When**: Tuỳ rủi ro yêu cầu.
- **Why**: All-transitions mạnh hơn all-states (đạt all-transitions ⇒ đạt all-states).
- **How**: Đo (exercised / total) %.
- **Dẫn chứng**: All-transitions giúp tránh defect masking khi 1 lỗi che lỗi khác.

### 10. Pairwise Testing
- **What**: Kỹ thuật combinatorial: mỗi cặp giá trị của 2 parameter bất kỳ được test cùng nhau ít nhất 1 lần.
- **Where**: Nhiều input parameter, không thể test exhaustive.
- **When**: Số combination quá lớn (vd 3 param × 3 value = 27 cases).
- **Why**: Reduce drastically # test case mà vẫn cover phần lớn defect.
- **How**: Dùng all-pairs algorithm hoặc Classification Tree.
- **Dẫn chứng**: 3 class × 3 value: 1-wise = 3 TC; pairwise = 9 TC (thay vì 27 exhaustive).

---

## Lecture 10 — White-box Testing

### 11. Code Coverage (Tổng quan)
- **What**: Ratio components tested / total components.
- **Where**: White-box testing.
- **When**: Khi đo mức độ test sâu.
- **Why**: Higher coverage → higher reliability.
- **How**: 4 criterion: Statement, Decision/Branch, Condition, Path.
- **Dẫn chứng**: Mỗi criterion có công thức A/B với A = executed, B = total.

### 12. Statement Coverage
- **What**: % câu lệnh (line) được thực thi.
- **Where**: Granularity = line of code.
- **When**: Mức coverage cơ bản nhất.
- **Why**: Phát hiện unused statements, dead code, missing statements.
- **How**: SC = (executed statements / total statements) × 100%.
- **Dẫn chứng**: VD lecture: TC1 a=-1, b=0 → 80%; TC2 a=5, b=0 → 100%.
- **Limitation**: Không phát hiện lỗi trong complex logical expression, empty branch.

### 13. Decision/Branch Coverage
- **What**: % branch (T/F outcome của decision) được thực thi.
- **Where**: Mỗi if/else, switch, loop condition.
- **When**: Mạnh hơn statement coverage.
- **Why**: Đảm bảo cả nhánh true và false đều test.
- **How**: DC = (executed branches / total branches). 100% branch ⇒ 100% statement.
- **Dẫn chứng**: VD: if (a>0 && b>0) → cần 2 TC (true, false). TC1 a=5,b=0 (true); TC2 a=1,b=0 (false) → 100% branch.

### 14. Condition Coverage
- **What**: Mỗi condition đơn (Boolean atomic) phải nhận cả T và F ít nhất 1 lần.
- **Where**: Compound boolean expression.
- **When**: Khi có && / || trong condition.
- **Why**: Branch coverage có thể bỏ sót sub-condition; condition coverage cụ thể hơn.
- **How**: CC = (tested boolean outcomes / total). KHÔNG đảm bảo decision coverage.
- **Dẫn chứng**: `if (a==5 && b>0)`. TC1 a=5,b=1 (T,T); TC2 a=0,b=0 (F,F) → branch coverage 100% nhưng b>0 chỉ test F? Cần thêm TC3 a=0,b=1 để b>0=T.

### 15. Coverage Hierarchy
- **What**: Statement < Branch/Decision < Condition < Multiple Condition < Path (MC/DC).
- **Where**: White-box analysis.
- **When**: Chọn theo risk/criticality.
- **Why**: Stronger coverage → catch more bugs nhưng tốn resource.
- **How**: Branch ⇒ Statement (luôn). Condition KHÔNG ⇒ Branch.
- **Dẫn chứng**: MC/DC dùng cho safety-critical (DO-178B avionics).

### 16. White-box Testing (Tổng quan)
- **What**: Structural / glass-box — dựa trên design, internal logic, code structure.
- **Where**: Unit level, modules high-risk.
- **When**: Khi cần verify đường thực thi & algorithm.
- **Why**: Correctness, quality (standards), maintenance.
- **How**: 2 strategy — Control flow (basis path, loop), Data flow.
- **Dẫn chứng**: Disadvantage: tốn resource, không test non-functional (availability, load).

### 17. Control Flow Graph (CFG)
- **What**: Đồ thị biểu diễn control structure: Node = statement(s), Edge = control flow.
- **Where**: White-box, basis path testing.
- **When**: Trước khi tính cyclomatic.
- **Why**: Visualize execution path.
- **How**: 
  - Decision node: > 1 outgoing arrow.
  - Junction node: > 1 incoming arrow.
  - Region: bounded area.
- **Dẫn chứng**: Sequence → 1 node thẳng; if → 2 edges; loop → cycle.

### 18. Cyclomatic Complexity (V(G))
- **What**: McCabe metric — số lượng linearly independent path qua program.
- **Where**: CFG.
- **When**: Step 2 của basis path testing.
- **Why**: Upper bound số test case để cover mọi independent path.
- **How**: 3 công thức (kết quả giống nhau):
  1. **V(G) = E − N + 2** (E=edges, N=nodes).
  2. **V(G) = P + 1** (P = số predicate/decision node).
  3. **V(G) = R** (R = số region trong planar CFG, đếm cả vùng ngoài).
- **Dẫn chứng**: 
  - Sequential code: V(G) = 1.
  - 1 if: V(G) = 2.
  - 2 nested if: V(G) = 3.
  - Tutorial 10: graph 2 decision node → V(G) = 2 + 1 = 3.

### 19. Basis Path Testing
- **What**: McCabe's technique — derive set of independent paths từ V(G).
- **Where**: White-box, unit testing.
- **When**: Module phức tạp.
- **Why**: Guarantee mọi statement được execute ≥ 1 lần.
- **How**: 
  1. Draw CFG.
  2. Tính V(G).
  3. Identify basis set = V(G) linearly independent path.
  4. Test case force mỗi path.
- **Dẫn chứng**: V(G)=3 → cần 3 test case cho 3 path độc lập.

### 20. Loop Testing — Simple Loops
- **What**: Test boundary của vòng lặp đơn.
- **Where**: For/while loop.
- **When**: Mọi loop với max iterations n.
- **Why**: Off-by-one, infinite loop.
- **How**: Test các case:
  - Skip loop (0 iteration).
  - Exactly 1 iteration.
  - Exactly 2 iterations.
  - m iterations (k < n, "typical").
  - n−1, n, n+1 iterations.
- **Dẫn chứng**: Lecture: input=0→0 pass, input=5→5 pass, input=6→5 pass (capped).

### 21. Loop Testing — Nested Loops
- **What**: Test inside-out để tránh geometric explosion.
- **Where**: Nested for/while.
- **When**: ≥ 2 cấp loop.
- **Why**: Test exhaustive sẽ rất lớn (n×m×k).
- **How**: 
  1. Start innermost, set outer = min.
  2. Apply simple loop test cho innermost.
  3. Work outward, giữ inner ở "typical", outer khác ở min.
  4. Continue cho đến outer cùng.
- **Dẫn chứng**: 2 nested for(n)(m) — không test n×m combination.

### 22. Loop Testing — Concatenated & Unstructured
- **What**: Concat = 2 loop nối tiếp; Unstructured = goto-like.
- **Where**: Sequential or jumbled loop.
- **When**: Theo cấu trúc code.
- **Why**: Independent concat → đơn giản; dependent → giống nested.
- **How**: 
  - Concat independent → simple loop test mỗi cái.
  - Concat dependent (loop1 counter feed loop2) → nested approach.
  - Unstructured → redesign nếu có thể.
- **Dẫn chứng**: Loop2 dùng loop1's final counter làm init.

### 23. Data Flow Testing
- **What**: White-box focus vào variable definition và reference.
- **Where**: Mọi statement gán/đọc biến.
- **When**: Sau control flow, khi muốn catch data-related bugs.
- **Why**: Tìm initialization bug, assignment bug, sequence bug.
- **How**: Life cycle: **Created (d) → Used (r) → Deleted (u)**.
- **Dẫn chứng**: 3 actions:
  - **d (define)**: assigns value/input.
  - **r (reference)**: uses value.
  - **u (undefine)**: deletes/kills variable.

### 24. Data Flow — 9 Pairs of Operations
- **What**: Cặp action liên tiếp trên biến.
- **Where**: Variable trace.
- **When**: Sau khi build DFG.
- **Why**: Mỗi cặp có ý nghĩa correctness khác nhau.
- **How**: Phân loại:
  - **Valid/Normal**: dr (define→ref), rd (ref→redefine), rr (ref→ref), ru (ref→undef), ud (undef→redefine).
  - **Suspicious**: dd (define→define lại — useless overwrite), du (define→undefine — chưa dùng đã xóa).
  - **Definite Error**: ur (undef→ref — SEVERE), uu (undef→undef again).
  - **Initial state ~**: ~d normal, ~r = error (use before define), ~u = abnormal.
- **Dẫn chứng**: Lecture scenario `~dduk` có abnormal pair `dd` → cần check.

### 25. Data Flow Testing Process
- **What**: Quy trình 4 bước.
- **Where**: White-box, sau control flow.
- **When**: Khi cần đảm bảo variable lifecycle đúng.
- **Why**: Phát hiện data anomaly.
- **How**: 
  1. Build DFG từ CFG (label d/r/u trên node/edge).
  2. Tính V(G).
  3. Tạo paths theo V(G).
  4. Test variable life cycle trên mỗi path → tìm abnormal pair.
- **Dẫn chứng**: V(G)=3 → 3 scenarios per variable; check 5 vars × 3 scenarios.

### 26. Def-Use Pairs (DU pairs)
- **What**: Cặp (definition, use) của cùng biến: definition tại node d, use tại node u, có path từ d→u không re-define.
- **Where**: Data flow analysis.
- **When**: All-defs / all-uses / all-du-paths coverage.
- **Why**: Đảm bảo mọi định nghĩa được dùng đến.
- **How**: 
  - **All-defs**: mỗi def reach ít nhất 1 use.
  - **All-uses**: mỗi (def, use) pair được cover.
  - **All-du-paths**: mỗi đường def→use loop-free được cover (mạnh nhất).
- **Dẫn chứng**: All-du-paths ⊇ All-uses ⊇ All-defs.

---

## Lecture 11 — Security Testing

### 27. Quality vs Security
- **What**: High-quality SW phải INHERENTLY include security (không phải retrofit).
- **Where**: Suốt SDLC.
- **When**: Specification phase, không phải sau development.
- **Why**: Security đứng ngang performance, functionality, maintainability — là dimension của quality.
- **How**: Security testing critical như functional testing.
- **Dẫn chứng**: Security retrofit thường thất bại; phải design-in.

### 28. Vulnerability (Định nghĩa)
- **What**: Weakness/flaw trong architecture, code, configuration mà attacker exploit được.
- **Where**: Memory, data, web, network.
- **When**: Bất cứ điểm yếu nào.
- **Why**: Cần biết để defense.
- **How**: Audit, scan, pen-test.
- **Dẫn chứng**: 6 loại common: Buffer Overflow, SQL Injection, XSS, URL Manipulation, Spoofing, weak auth.

### 29. Common Vulnerabilities (Memory & Data)
- **Buffer Overflow**: Ghi data vượt allocated memory (C/C++ phổ biến) → crash, RCE.
- **SQL Injection**: Inject SQL malicious vào input field → manipulate/steal DB.
- **Where**: Input fields, query construction.
- **How prevent**: Bounds check, Prepared Statements.

### 30. Common Vulnerabilities (Web & Network)
- **XSS (Cross-Site Scripting)**: Inject malicious script vào trusted website → hijack session, execute trong browser khác.
- **URL Manipulation**: Sửa URL parameter để bypass auth, access hidden data.
- **Spoofing**: Giả mạo IP/identity là trusted source.
- **How prevent**: Output encoding, authorization check, mutual TLS.

### 31. CIA Triad (Foundational Security)
- **What**: Confidentiality, Integrity, Availability — 3 pillar bảo mật.
- **Where**: Mọi system security model.
- **When**: Threat modeling, requirement definition.
- **Why**: Khung phân loại threat & control.
- **How**: 
  - **Confidentiality**: Encryption, access control.
  - **Integrity**: Hash, signature, checksum.
  - **Availability**: Redundancy, anti-DDoS.
- **Dẫn chứng**: Security testing bảo vệ sensitive data → CIA.

### 32. OWASP Top 10 (Reference)
- **What**: 10 web vulnerability nguy hiểm nhất do OWASP công bố.
- **Where**: Web application security.
- **When**: Threat assessment, pen-test scope.
- **Why**: Industry benchmark.
- **How**: Test cụ thể từng loại (Injection, Broken Auth, XSS, IDOR, Security Misconfig, Sensitive Data Exposure, XXE, Broken Access Control, Insecure Deserialization, Components with Known Vulnerabilities).
- **Dẫn chứng**: DAST tool (ZAP, Burp) test theo OWASP Top 10.

### 33. Penetration Testing
- **What**: Manual exploratory testing simulating real-world attacks.
- **Where**: Production-like environment.
- **When**: Trước go-live, định kỳ.
- **Why**: Discover & exploit vulnerability, assess resilience.
- **How**: 
  - **Black-box pen-test**: zero knowledge, dùng phishing/social engineering.
  - **White-box pen-test**: full code access, tìm internal flaw (SQLi).
- **Dẫn chứng**: Tutorial 11 dùng pentest-tools.com light scan.

### 34. Fuzzing (Fuzz Testing)
- **What**: Tự động bơm invalid/semi-valid data để trigger crash/exception.
- **Where**: Input parser, API, file format.
- **When**: Trong CI hoặc lab security.
- **Why**: Find hidden vulnerability qua unexpected input.
- **How**: 
  - **Black-box random fuzzing**: random data lớn.
  - **Grammar-based fuzzing**: mutate valid format.
  - **White-box fuzzing**: dùng source + solver → force path.
- **Dẫn chứng**: Microsoft OneFuzz; Google ClusterFuzz → tìm 27k Chrome bug + 28k OSS bug.

### 35. SAST (Static Application Security Testing)
- **What**: "White-box" analysis source code/binary at rest, không execute.
- **Where**: IDE plugin, code commit, CI pipeline.
- **When**: Early SDLC.
- **Why**: Tìm hardcoded credentials, weak logic, SQLi early → cheaper fix.
- **How**: Phân tích AST, taint analysis.
- **Pros/Cons**: Pros = early/cheap. Cons = no runtime, false positive.
- **Dẫn chứng**: SonarQube, Checkmarx, Fortify, Veracode.

### 36. DAST (Dynamic Application Security Testing)
- **What**: "Black-box" test running app từ outside-in, simulating attack.
- **Where**: Staging, QA, Production.
- **When**: Later SDLC.
- **Why**: Detect runtime issues (XSS, auth bypass, server misconfig).
- **How**: Send HTTP requests, observe response.
- **Pros/Cons**: Pros = real attack simulation. Cons = no source access.
- **Dẫn chứng**: OWASP ZAP, Burp Suite, Invicti, Acunetix.

### 37. IAST (Interactive Application Security Testing)
- **What**: Hybrid — hoạt động bên trong app runtime, monitor liên tục.
- **Where**: QA env trong automated UI / functional test.
- **When**: Active during testing phase.
- **Why**: Earlier than DAST, pinpoint vulnerable code, verify exploitability, scan 3rd party.
- **How**: Agent in JVM/.NET, observe data flow.
- **Pros/Cons**: Pros = accurate, deep. Cons = không replace DAST/pen-test.
- **Dẫn chứng**: Contrast Security, Synopsys Seeker, Checkmarx IAST, HCL AppScan.

### 38. RASP (Runtime Application Self-Protection)
- **What**: Defense tool integrated vào app server, monitor traffic & behavior, BLOCK attack.
- **Where**: Production live.
- **When**: After deployment.
- **Why**: Prevent runtime attack, virtual patching.
- **How**: Agent in runtime, block malicious request.
- **Pros/Cons**: Pros = deeper than WAF. Cons = không silver bullet.
- **Dẫn chứng**: Imperva RASP, Contrast Protect, OpenRASP, Datadog.

### 39. SAST vs DAST vs IAST vs RASP (So sánh)
- **SAST**: white-box, code at rest, early SDLC, no execution.
- **DAST**: black-box, running app, late SDLC, simulate attack.
- **IAST**: hybrid agent in runtime during testing.
- **RASP**: production agent that BLOCKS attack (active defense).

### 40. Security Best Practices — Error & Logging
- **What**: Display generic error; handle all exceptions; log user activities but NOT password.
- **Where**: App layer.
- **Why**: Error message reveal internal state → attacker enumerate.
- **How**: Catch & log internally, show user-friendly message.
- **Dẫn chứng**: troyhunt.com — error message leak source code.

### 41. Security Best Practices — Network & Permissions
- **What**: HTTPS everywhere (TLS); proper file permission (chown, chmod).
- **Where**: Network transport, filesystem.
- **Why**: HTTP capture lộ password.
- **How**: Force HTTPS, restrict permission by least privilege.

### 42. Security Best Practices — Credentials & Passwords
- **What**: Không hard-code credentials; enforce strong password policy.
- **Why**: Convenience → security flaw.
- **How**: 
  - Store **salted hash** (Bcrypt, Argon2i).
  - Password reset (không restore).
  - Tokenization với encrypted session token.
- **Dẫn chứng**: Bcrypt (salted) > SHA-256 (unsalted) > SHA-1 > MD5. Argon2i là khuyến nghị OWASP hiện đại.

### 43. Security Best Practices — Access Control
- **What**: Account lockout (after N failed logins), least privilege, expire cookies/sessions.
- **Why**: Defend brute-force, limit blast radius.
- **How**: Counter failed attempts, set cookie TTL, principle of least privilege.

### 44. Security Best Practices — Input Validation
- **What**: Validate ALL input (file, field, source); safe defaults; whitelist > blacklist; KHÔNG trust client-side validation.
- **Where**: Mọi entry point.
- **Why**: Client validation bypass dễ; whitelist block unknown.
- **How**: Server-side validation, prepared statements, context-aware encoding.

### 45. Preventing Injection / Bots / DDoS
- **What**: Prepared Statements (SQLi); context encoding (XSS); CAPTCHA (bots); throttle login (DDoS).
- **Where**: DB layer, output layer, auth layer.
- **Why**: Most common attack vector.
- **How**: ORM/parameterized queries, HTML encoding, rate-limit middleware.

---

## Lecture 12 — Testing Tools (Automation)

### 46. Automated Testing
- **What**: Tích hợp tool vào testing process.
- **Where**: Mọi level test.
- **When**: Test lặp lại (regression), volume lớn.
- **Why**: Save time/cost, accuracy, better statistical report.
- **How**: Plan → design → prepare cases → execute (auto) → report → regression.
- **Dẫn chứng**: 5 type: Code Auditing, Coverage Monitoring (white-box), Functional Tests (black-box), Load Tests, Test Management.

### 47. Automated Testing — Adv/Disadv
- **Adv**: Accuracy, completeness, comprehensive info, fewer manpower, shorter cycle, full regression, beyond manual scope (load).
- **Disadv**: High package & training cost, high development cost, high prep manpower, considerable area uncovered.

### 48. Selenium (Tổng quan)
- **What**: Open-source automation suite cho web app.
- **Where**: Web browser (Chrome, Firefox, Edge, Safari).
- **When**: UI regression, smoke test, E2E.
- **Why**: Free, multi-language (Java/C#/Python/Ruby/PHP/Perl/JS/Kotlin), huge community.
- **How**: Simulate user interaction (click, type, navigate).
- **Dẫn chứng**: 4 component — IDE, RC, WebDriver (merged into Selenium 2), Grid.

### 49. Selenium Suite Components
- **Selenium IDE**: record-and-playback, đơn giản, no loop/if, hard maintain, no CI/CD.
- **Selenium RC**: legacy remote control (merged).
- **Selenium WebDriver**: industry standard, full control, fast, CI/CD friendly.
- **Selenium Grid**: parallel execution across machines/browsers.

### 50. WebDriver Architecture
- **What**: 4-layer architecture.
- **How**: 
  1. **Language Bindings** (Java/Python script).
  2. **W3C WebDriver Protocol** (JSON commands over HTTP).
  3. **Browser Drivers** (ChromeDriver, GeckoDriver, EdgeDriver).
  4. **Real Browser** thực thi action.
- **Dẫn chứng**: ChromeDriver intermediate giữa script & Chrome.

### 51. Selenium Locators (8 loại)
- **What**: Cách định danh element trong DOM.
- **Where**: Mọi findElement call.
- **When**: Trước khi interact.
- **Why**: WebDriver phải biết chính xác element.
- **How**: 
  1. `By.id()` — nhanh nhất, reliable nhất.
  2. `By.name()` — alternate khi không có id.
  3. `By.className()` — theo CSS class.
  4. `By.tagName()` — theo HTML tag.
  5. `By.linkText()` — `<a>` theo exact visible text.
  6. `By.partialLinkText()` — `<a>` theo portion text.
  7. `By.cssSelector()` — flexible & fast.
  8. `By.xpath()` — mạnh nhất cho DOM phức tạp, SLOWEST.
- **Dẫn chứng**: Best practice priority: id > name > css > xpath.

### 52. Browser & Navigation Commands
- `driver.get("url")` — open static page, wait full load.
- `driver.getTitle()` — title tab hiện tại.
- `driver.getCurrentUrl()` — URL thực tế (test redirect).
- `driver.close()` — close tab hiện tại.
- `driver.quit()` — quit toàn bộ browser session (best practice end of test).
- `driver.navigate().to("url")` — like get nhưng retain history.
- `driver.navigate().back()` — click Back.
- `driver.navigate().refresh()` — reload.

### 53. Web Element Interaction Commands
- **Action**: `click()`, `sendKeys("text")`, `clear()`, `submit()`.
- **Validation**: `getText()`, `getAttribute("href")`.
- **State**: `isDisplayed()`, `isEnabled()`, `isSelected()`.
- **Dẫn chứng**: `submit()` press Enter trong form.

### 54. Handling Dropdowns (Select class)
- **What**: Dropdown `<select>` không dùng `click/sendKeys` được.
- **Where**: Standard HTML select.
- **How**: 
  ```java
  WebElement dd = driver.findElement(By.id("countryDropdown"));
  Select s = new Select(dd);
  s.selectByVisibleText("Vietnam");
  // s.selectByValue("VN");
  // s.selectByIndex(1);
  ```
- 3 strategies: `selectByIndex()`, `selectByValue()`, `selectByVisibleText()`.

### 55. JUnit 5 Assertions với Selenium
- **What**: Selenium không quyết định pass/fail; cần JUnit assertion.
- **How**: 
  - `assertEquals` — verify title, text, URL.
  - `assertTrue` — check element visible.
  - `assertFalse` — verify loading spinner gone.
  - `assertNotNull` — verify element located.
- **Dẫn chứng**: `assertEquals("https://example.com/dashboard", driver.getCurrentUrl(), "Login failed!");`

### 56. Selenium Waits (Synchronization)
- **What**: Modern page dynamic → cần wait trước khi interact, tránh `NoSuchElementException`.
- **Implicit Wait**: 
  - Global, set 1 lần per session.
  - WebDriver wait up to X giây cho mọi missing element.
  - Syntax: `driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));`
- **Explicit Wait**: 
  - Targeted, industry best practice.
  - Wait condition cụ thể cho element cụ thể.
  - Stop wait moment condition true → save time.
  - VD: `WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10)); wait.until(ExpectedConditions.elementToBeClickable(...));`
- **Fluent Wait**: customizable polling interval + ignore exception types.

### 57. JMeter (Tổng quan)
- **What**: Java open-source app cho load test & performance.
- **Where**: HTTP/HTTPS, JDBC, REST/SOAP, FTP, JMS, …
- **When**: Test capacity, breaking point.
- **Why**: Multi-protocol, simulate concurrent user, browser-like (cookie/cache/header), record-playback.
- **How**: GUI build test plan, run, analyze.
- **Dẫn chứng**: 3 main use — Performance, Load, Stress.

### 58. JMeter — Performance Test Types
- **Load Testing**: simulate expected user traffic, ensure handle.
- **Stress Testing**: push beyond normal → find breaking point.
- **Performance Testing**: tổng quát, analyze overall under various loads.
- (Khác): **Spike test** = sudden surge; **Endurance/Soak test** = long duration; **Volume test** = large data.

### 59. JMeter Test Plan — Anatomy
- **Test Plan**: root node chứa mọi element.
- **Thread Group** (users): pool virtual user. Config: Number of Threads, Ramp-Up Period, Loop Count.
- **Samplers** (actions): send request. VD: HTTP Request, JDBC Request.
- **Timers** (think time): delay simulate user reading (Constant Timer 2000ms).
- **Listeners** (results): View Results Tree, View Results in Table, Summary Report, Aggregate Report.
- **Assertions**: validate response (Response Assertion, Duration Assertion).
- **Config Elements**: HTTP Cookie Manager, HTTP Cache Manager, HTTP Header Manager, CSV Data Set Config, HTTP Request Defaults.
- **Logic Controllers**: If Controller, Loop Controller, Once Only Controller, Transaction Controller.
- **Pre/Post Processors**: BeanShell PreProcessor, JSON Extractor (Post).

### 60. JMeter — Handling Web Forms
- **Parameters**: HTTP Request → Parameters tab → Name-Value pair (`fromPort=Boston`, `toPort=London`).
- **HTTP Cookie Manager**: maintain session/login.
- **HTTP Cache Manager**: simulate browser cache (static asset load realistically).

### 61. JMeter — Script Creation
- **Manual Creation**: add Thread Group, Sampler, URL manually. Good for simple API.
- **Recording (Industry Standard)**: dùng proxy hoặc BlazeMeter Chrome Extension. Click through workflow → tool record HTTP/S → export `.jmx` → import vào JMeter. Lợi: capture hidden request, dynamic param, header tự động.

---

## Tutorial 9-12 (Worked Examples)

### 62. Tutorial 9 — BadMoney (BVA Practice)
- **What**: 3 methods — `calculateDiscount`, `times100`, `calculateSavings`.
- **How**: BVA 100% boundary coverage + JUnit 5 parameterized test.
- **Dẫn chứng rounding boundary**: 
  - 3rd decimal 0-4 → round down (0.0649 → 0.06).
  - 3rd decimal 5-9 → round up (0.0650 → 0.07).
  - BVA boundary tại 0.0050, 0.0049, 0.0050, 0.0051 (just above/below half).
  - `times100`: truncate (4.35 → 435, but 4.34999 → 434).

### 63. Tutorial 9 — Fahrenheit Converter (EP + BVA)
- **Formula**: `C = (F − 32) * 5/9`; `F = C * 9/5 + 32`.
- **Rounding**: 1 decimal half-up (30.5499 → 30.5; 30.55 → 30.6).
- **EP**: valid range, invalid (vd dưới absolute zero -273.15°C / -459.67°F).
- **BVA**: tại boundary rounding: ...x9 vs ...x4.

### 64. Tutorial 9 — Triangle (Decision Table + BVA)
- **Inputs**: a, b, c ∈ [1, 200].
- **Outputs**: 
  - **OUT_OF_RANGE (-2)**: any side out of [1,200].
  - **INVALID (-1)**: violate triangle inequality (a < b+c, b < a+c, c < a+b).
  - **EQUILATERAL (2)**: a == b == c.
  - **ISOSCELES (1)**: exactly 2 sides equal.
  - **SCALENE (0)**: all different.
- **BVA boundary**: 0, 1, 2, 199, 200, 201.
- **Decision Table example rules**: (range OK, triangle ineq OK, eq?, iso?, scalene?) → return code.

### 65. Tutorial 10 — HandleStr & Cyclomatic Complexity
- **What**: Capitalize first letter của word bắt đầu bằng u/v/t/k, ghi mỗi sentence (kết thúc bằng `.?!`) trên 1 dòng vào file.
- **How**: Draw Activity diagram → Flow Graph → tính V(G).
- **Task 2**: Tạo TC đạt 100% Condition Coverage cho HandleStr (stronger than Branch).
- **Dẫn chứng**: Condition coverage requires test mỗi sub-condition T/F (u/v/t/k là OR chain → 4 condition).

### 66. Tutorial 11 — pentest-tools.com (DAST)
- **What**: Web scanner online, light scan website.
- **Where**: http://testaspnet.vulnweb.com:80/.
- **How**: Run light scan ≥ 2 lần → export report → so sánh → list top 3 critical vulnerability.

### 67. Tutorial 11 — Nmap Flags
- `nmap -sn [IP]` — **ping scan** (host discovery, không scan port).
- `nmap -O [IP]` — **OS detection**.
- `nmap -p [port] [IP]` — scan port cụ thể; range: `-p 1-1000`.
- `nmap -sT [IP]` — **TCP connect scan** (full handshake, không cần root).
- `nmap -sU [IP]` — **UDP scan**.
- (Bonus) `nmap -sS` — **TCP SYN stealth scan** (need root, không complete handshake).
- (Bonus) `nmap -A` — **aggressive scan** (OS + version + script + traceroute).
- **Port states**: open, closed, filtered, unfiltered, open|filtered, closed|filtered.

### 68. Tutorial 12 — Selenium WebDriver E2E (BlazeDemo)
- **Target**: https://blazedemo.com/
- **Workflow**: 
  1. Init WebDriver + navigate URL.
  2. Implicit wait (global).
  3. Verify title (assertEquals).
  4. Find Flights — Select dropdown departure/destination.
  5. Choose Flights — Explicit Wait → click "Choose This Flight".
  6. Purchase — fill form + click "Purchase Flight".
  7. Final validation — locate success message.
  8. `driver.quit()`.
- **Dẫn chứng**: `Thread.sleep(2000)` chỉ để visual demo, KHÔNG dùng production.

### 69. Tutorial 12 — JMeter Test Plan (BlazeDemo)
- **Step 1**: Thread Group — 10 threads, ramp-up 5s.
- **Step 2**: HTTP Request Sampler — Protocol https, Server blazedemo.com (homepage).
- **Step 3**: HTTP Request Sampler — POST `/reserve.php`.
- **Step 4**: Parameters tab — `fromPort=Boston`, `toPort=London`.
- **Step 5**: Constant Timer 2000ms ("think time").
- **Step 6**: Listener — View Results Tree or View Results in Table.
- **Step 7**: Save `.jmx`, run, inspect response.

### 70. Maven pom.xml Cho Tutorial 12
- Java 21, Maven build.
- **Dependencies**: 
  - `org.seleniumhq.selenium:selenium-java:4.41.0` (compile scope).
  - `org.junit.jupiter:junit-jupiter-api:5.8.2` (test scope).
