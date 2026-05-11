# DAY 3 — Flashcards (Testing, Security, Automation)

> 60+ flashcards. Mix MCQ-style và fill-in-blank. Tự kiểm tra trước khi xem đáp án.

---

## Flashcard 1
**Q:** Cyclomatic complexity có 3 cách tính. Liệt kê công thức.
**A:** (1) **V(G) = E − N + 2** với E=edges, N=nodes; (2) **V(G) = P + 1** với P=số predicate (decision) nodes; (3) **V(G) = R** với R=số region của planar CFG (đếm cả region ngoài).

## Flashcard 2
**Q:** Điền: Trong BVA cho range [min, max], các giá trị test theo "just above/below" gồm: _____, _____, _____, _____, _____, _____.
**A:** min−1, min, min+1, max−1, max, max+1.

## Flashcard 3
**Q:** Equivalence Partitioning với input là range tạo ra bao nhiêu valid và invalid class?
**A:** 1 valid + 2 invalid.

## Flashcard 4
**Q:** Equivalence Partitioning với input là boolean tạo ra bao nhiêu class?
**A:** 1 valid + 1 invalid.

## Flashcard 5
**Q:** Black box testing còn được gọi là gì?
**A:** Behavioral testing / behavior-based testing.

## Flashcard 6
**Q:** White box testing còn được gọi là gì?
**A:** Structural testing / glass-box testing.

## Flashcard 7
**Q:** 5 kỹ thuật black-box testing chính trong Lecture 9 là gì?
**A:** (1) Equivalence Partitioning, (2) Boundary Value Analysis, (3) Decision Table, (4) State Transition, (5) Pairwise.

## Flashcard 8
**Q:** Điền: Cho input range 1-100, BVA 6-value cho test values _____, _____, _____, _____, _____, _____.
**A:** 0, 1, 2, 99, 100, 101.

## Flashcard 9
**Q:** Decision Table dùng để mô hình hóa gì?
**A:** System logic dưới dạng RULES = combination của multiple INPUT conditions → ACTIONS (outputs).

## Flashcard 10
**Q:** All-states coverage và All-transitions coverage, cái nào mạnh hơn?
**A:** All-transitions mạnh hơn. Đạt 100% all-transitions ⇒ tự động đạt 100% all-states + valid transitions.

## Flashcard 11
**Q:** Pairwise testing đảm bảo điều gì?
**A:** Mỗi cặp giá trị (pair) giữa 2 parameter bất kỳ xuất hiện cùng nhau ít nhất 1 lần.

## Flashcard 12
**Q:** Coverage hierarchy từ yếu đến mạnh: Statement, Branch, Path, Condition. Sắp xếp.
**A:** Statement < Branch/Decision < Condition < Multiple Condition < Path / MC-DC.

## Flashcard 13
**Q:** Branch coverage 100% có đảm bảo Statement coverage 100% không?
**A:** Có. Branch ⇒ Statement.

## Flashcard 14
**Q:** Condition coverage 100% có đảm bảo Branch coverage 100% không?
**A:** KHÔNG. Condition không đảm bảo Branch.

## Flashcard 15
**Q:** Công thức Statement Coverage?
**A:** SC = (số statements được execute / tổng số statements) × 100%.

## Flashcard 16
**Q:** Trong CFG, "decision node" là gì?
**A:** Node có **> 1 outgoing arrow** (>1 mũi tên đi ra).

## Flashcard 17
**Q:** Trong CFG, "junction node" là gì?
**A:** Node có **> 1 incoming arrow** (>1 mũi tên đi vào).

## Flashcard 18
**Q:** Basis path testing được đề xuất bởi ai?
**A:** Tom McCabe.

## Flashcard 19
**Q:** Số lượng test case tối thiểu trong basis set bằng?
**A:** Bằng V(G) (cyclomatic complexity).

## Flashcard 20
**Q:** Simple loop testing với max n iterations cần test bao nhiêu case?
**A:** 6 case: skip (0), 1, 2, m (k<n), n−1, n, n+1.

## Flashcard 21
**Q:** Nested loop testing dùng cách tiếp cận nào để tránh combination explosion?
**A:** Inside-out: bắt đầu innermost loop với outer = min, sau đó work outward.

## Flashcard 22
**Q:** Trong Data Flow Testing, 3 actions trên biến là gì? (ký hiệu + nghĩa)
**A:** **d** (define — gán giá trị), **r** (reference — đọc giá trị), **u** (undefine — xoá biến).

## Flashcard 23
**Q:** Cặp action `ur` (undefine → reference) là gì?
**A:** SEVERE BUG / Definite Error — dùng biến đã bị xoá (no value exists).

## Flashcard 24
**Q:** Cặp action `dd` (define → define lại) là gì?
**A:** Suspicious — useless overwrite, có thể là programming error.

## Flashcard 25
**Q:** Cặp `~r` (initial → reference) nghĩa là gì?
**A:** Error — dùng biến trước khi define.

## Flashcard 26
**Q:** Liệt kê 5 cặp action VALID/NORMAL trong data flow.
**A:** dr, rd, rr, ru, ud.

## Flashcard 27
**Q:** Coverage hierarchy của data flow: all-defs, all-uses, all-du-paths. Sắp xếp từ yếu → mạnh.
**A:** All-defs < All-uses < All-du-paths.

## Flashcard 28
**Q:** CIA triad gồm những gì?
**A:** **C**onfidentiality, **I**ntegrity, **A**vailability.

## Flashcard 29
**Q:** Điền: ___ Injection là kỹ thuật bơm câu lệnh SQL độc hại vào input để manipulate DB.
**A:** SQL Injection.

## Flashcard 30
**Q:** XSS viết tắt của gì và nghĩa là?
**A:** Cross-Site Scripting — inject script độc hại vào trusted website để hijack session/execute trên browser khác.

## Flashcard 31
**Q:** Buffer Overflow phổ biến trong ngôn ngữ nào?
**A:** C/C++.

## Flashcard 32
**Q:** SAST là gì? Hoạt động ở pha SDLC nào?
**A:** Static Application Security Testing. White-box, analyze source code AT REST (no execution). Áp dụng EARLY SDLC (IDE, commit).

## Flashcard 33
**Q:** DAST là gì? Hoạt động ở pha SDLC nào?
**A:** Dynamic Application Security Testing. Black-box, test RUNNING app từ outside-in. Áp dụng LATER SDLC (Staging, QA, Production).

## Flashcard 34
**Q:** IAST khác DAST ở điểm nào?
**A:** IAST là hybrid với agent BÊN TRONG runtime app, monitor liên tục → pinpoint vulnerable code; phát hiện sớm hơn DAST.

## Flashcard 35
**Q:** RASP làm gì khác biệt so với SAST/DAST/IAST?
**A:** RASP integrated vào app server ở PRODUCTION, ACTIVELY blocks attack (virtual patching), không chỉ detect.

## Flashcard 36
**Q:** Điền: Fuzzing là kỹ thuật ____ inject ____ data để trigger crash/lỗi.
**A:** Automated; invalid hoặc semi-valid.

## Flashcard 37
**Q:** Tool fuzzing của Microsoft và Google lần lượt là?
**A:** Microsoft **OneFuzz** (Azure framework). Google **ClusterFuzz** (đã tìm 27k Chrome bugs + 28k OSS bugs).

## Flashcard 38
**Q:** Hash algorithm nào sau đây dùng salt: MD5, SHA-1, SHA-256, Bcrypt, Argon2i?
**A:** Bcrypt và Argon2i (có salt). MD5, SHA-1, SHA-256 trong slide đều không salt.

## Flashcard 39
**Q:** Penetration testing black-box vs white-box khác nhau ra sao?
**A:** Black-box pen-test: zero internal knowledge, dùng external attack (phishing, social engineering). White-box: full code access, tìm internal flaw (SQLi).

## Flashcard 40
**Q:** OWASP Top 10 là gì?
**A:** Top 10 lỗ hổng web nguy hiểm nhất do OWASP công bố (Injection, Broken Auth, XSS, ...) — industry benchmark.

## Flashcard 41
**Q:** Tại sao không trust client-side validation?
**A:** Client-side validation có thể bypass dễ dàng (disable JS, modify request); luôn phải re-validate ở server-side.

## Flashcard 42
**Q:** Whitelist vs Blacklist, cái nào an toàn hơn?
**A:** Whitelist (block tất cả unexpected, chỉ allow những thứ defined). Blacklist không an toàn bằng vì không thể enumerate hết bad input.

## Flashcard 43
**Q:** Selenium suite gồm 4 component nào?
**A:** Selenium IDE, Selenium RC, Selenium WebDriver (RC + WebDriver = Selenium 2), Selenium Grid.

## Flashcard 44
**Q:** Selenium WebDriver Architecture gồm 4 layer nào?
**A:** (1) Language Bindings, (2) W3C WebDriver Protocol (JSON), (3) Browser Drivers (ChromeDriver/GeckoDriver/EdgeDriver), (4) Real Browsers.

## Flashcard 45
**Q:** Liệt kê 8 Selenium Locator.
**A:** id, name, className, tagName, linkText, partialLinkText, cssSelector, xpath.

## Flashcard 46
**Q:** Selenium locator nào nhanh và reliable nhất? Locator nào chậm nhất?
**A:** Nhanh nhất: `By.id()`. Chậm nhất: `By.xpath()`.

## Flashcard 47
**Q:** Sự khác biệt giữa `driver.close()` và `driver.quit()`?
**A:** `close()` đóng tab hiện tại; `quit()` đóng toàn bộ browser và destroy session (best practice cuối test).

## Flashcard 48
**Q:** Để chọn item trong dropdown `<select>`, Selenium dùng class nào và 3 strategies nào?
**A:** Class `Select`. 3 strategies: `selectByIndex()`, `selectByValue()`, `selectByVisibleText()`.

## Flashcard 49
**Q:** Selenium có quyết định pass/fail không?
**A:** Không. Selenium chỉ automate browser. Cần kết hợp **JUnit 5 assertion** (assertEquals, assertTrue, assertFalse, assertNotNull).

## Flashcard 50
**Q:** 3 loại Selenium Wait là gì?
**A:** Implicit Wait (global, set 1 lần per session), Explicit Wait (targeted, best practice), Fluent Wait (customizable polling + ignore exception).

## Flashcard 51
**Q:** Exception nào thường gặp khi Selenium tương tác element chưa load?
**A:** `NoSuchElementException`.

## Flashcard 52
**Q:** JMeter dùng để test loại gì?
**A:** Performance Testing, Load Testing, Stress Testing (và mở rộng: Spike, Endurance/Soak, Volume).

## Flashcard 53
**Q:** Liệt kê các element chính của JMeter Test Plan.
**A:** Thread Group (users), Samplers (actions), Timers (think time), Listeners (results), Assertions, Config Elements, Logic Controllers, Pre/Post Processors.

## Flashcard 54
**Q:** Trong JMeter Thread Group, 3 setting chính là gì?
**A:** Number of Threads (users), Ramp-Up Period, Loop Count.

## Flashcard 55
**Q:** Listener nào của JMeter cho biết log chi tiết request/response để debug?
**A:** **View Results Tree**.

## Flashcard 56
**Q:** Config Element nào của JMeter để maintain session/login?
**A:** **HTTP Cookie Manager**.

## Flashcard 57
**Q:** Điền: Nmap flag `-sS` là _____ scan, `-sT` là _____ scan, `-sU` là _____ scan, `-O` là _____ detection.
**A:** SYN stealth; TCP connect; UDP; OS.

## Flashcard 58
**Q:** Lệnh nmap để kiểm tra status (live host) của máy đích là gì?
**A:** `nmap -sn [IP]` (ping scan / host discovery, không scan port).

## Flashcard 59
**Q:** Cyclomatic complexity của 1 graph có 2 decision node bằng bao nhiêu?
**A:** V(G) = P + 1 = 2 + 1 = **3**.

## Flashcard 60
**Q:** Tutorial 9 Triangle: phạm vi hợp lệ của các cạnh là?
**A:** 1 ≤ a, b, c ≤ 200 (inclusive). Out of range → return −2 (OUT_OF_RANGE).

## Flashcard 61
**Q:** Tutorial 9 Triangle Inequality Theorem: với 3 cạnh a, b, c, điều kiện form valid triangle là?
**A:** a < b+c AND b < a+c AND c < a+b (strictly less).

## Flashcard 62
**Q:** Tutorial 9 Triangle return code: EQUILATERAL, ISOSCELES, SCALENE, INVALID, OUT_OF_RANGE lần lượt là?
**A:** 2, 1, 0, −1, −2.

## Flashcard 63
**Q:** Fahrenheit → Celsius formula?
**A:** C = (F − 32) × 5 / 9.

## Flashcard 64
**Q:** Trong Tutorial 12 JMeter, parameter cho `reserve.php` POST request là gì?
**A:** `fromPort=Boston`, `toPort=London`.

## Flashcard 65
**Q:** Loop testing — concatenated loop, khi nào treat như nested?
**A:** Khi **dependent** (loop1's counter dùng làm loop2's initial value). Nếu independent thì test như simple loop.

## Flashcard 66
**Q:** Theo Lecture 11, hard-code credentials có vấn đề gì?
**A:** "Convenience leads to security flaws" — credentials lộ trong source code/binary, dễ bị extract.
