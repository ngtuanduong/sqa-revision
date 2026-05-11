# DAY 3 — MCQ & Fill-in-Blank Practice

> 30 MCQ + 20 fill-in-blank. Trọng tâm: chi tiết công thức, ký hiệu, tool flag, đúng tên kỹ thuật.

---

## PART A — MULTIPLE CHOICE (30 questions)

### MCQ 1
Black box testing còn được gọi là:
- A. Glass-box testing
- B. Structural testing
- C. Behavioral testing
- D. Internal logic testing

**Answer: C** — Behavioral / behavior-based.

### MCQ 2
Trong BVA với input range [1, 100], giá trị nào KHÔNG thuộc bộ test BVA cơ bản?
- A. 0
- B. 50
- C. 101
- D. 99

**Answer: B** — 50 là giá trị giữa, BVA test các giá trị tại/gần biên: 0, 1, 2, 99, 100, 101.

### MCQ 3
Công thức Cyclomatic Complexity nào sau đây ĐÚNG?
- A. V(G) = N − E + 2
- B. V(G) = E − N + 2
- C. V(G) = E + N − 2
- D. V(G) = P − 1

**Answer: B** — V(G) = E − N + 2 (edges − nodes + 2).

### MCQ 4
Equivalence Partitioning cho input boolean tạo ra bao nhiêu class?
- A. 1 valid + 2 invalid
- B. 2 valid + 0 invalid
- C. 1 valid + 1 invalid
- D. 2 valid + 2 invalid

**Answer: C** — Boolean: 1 valid + 1 invalid.

### MCQ 5
Decision Table coverage 100% đảm bảo điều gì?
- A. Mọi statement được execute
- B. Mọi rule (mọi combination của conditions) được test
- C. Mọi path được cover
- D. Branch coverage 100%

**Answer: B** — DT coverage = mọi rule (mọi combination) được test.

### MCQ 6
Cặp action data flow nào sau đây là DEFINITE ERROR?
- A. dr
- B. rd
- C. ur
- D. dd

**Answer: C** — `ur` (undefine → reference) = severe bug.

### MCQ 7
Trong State Transition Testing, "guard condition" là gì?
- A. Trạng thái cuối của hệ thống
- B. Một điều kiện qualify thêm cho event để cho phép transition
- C. Action được thực hiện khi transition
- D. Một invalid transition

**Answer: B** — Guard condition là điều kiện thêm qualify cho event.

### MCQ 8
Coverage criterion nào MẠNH NHẤT trong các option sau?
- A. Statement coverage
- B. Branch coverage
- C. Condition coverage
- D. Path coverage (MC/DC)

**Answer: D** — Path/MC-DC mạnh nhất.

### MCQ 9
SAST KHÔNG có khả năng nào sau đây?
- A. Tìm hardcoded credentials
- B. Phát hiện SQL injection trong source
- C. Phát hiện runtime errors
- D. Tích hợp vào IDE

**Answer: C** — SAST không execute code → không detect runtime error.

### MCQ 10
Trong CIA triad, chữ "I" đại diện cho:
- A. Identification
- B. Integrity
- C. Inspection
- D. Isolation

**Answer: B** — Integrity.

### MCQ 11
Selenium locator nào CHẬM nhất?
- A. By.id
- B. By.name
- C. By.cssSelector
- D. By.xpath

**Answer: D** — XPath chậm nhất.

### MCQ 12
Để đóng toàn bộ browser session trong Selenium, dùng lệnh nào?
- A. driver.close()
- B. driver.quit()
- C. driver.exit()
- D. driver.terminate()

**Answer: B** — `quit()` đóng toàn bộ browser + destroy session.

### MCQ 13
Trong Selenium, để chọn item trong `<select>` dropdown bằng văn bản hiển thị, dùng:
- A. selectByIndex()
- B. selectByValue()
- C. selectByVisibleText()
- D. click()

**Answer: C** — `selectByVisibleText()`.

### MCQ 14
JMeter element nào đại diện cho "virtual users"?
- A. Sampler
- B. Listener
- C. Thread Group
- D. Timer

**Answer: C** — Thread Group = pool virtual users.

### MCQ 15
JMeter Listener nào CHI TIẾT NHẤT để debug request/response?
- A. Aggregate Report
- B. Summary Report
- C. View Results in Table
- D. View Results Tree

**Answer: D** — View Results Tree (detailed log).

### MCQ 16
Nmap flag `-sU` dùng để:
- A. Scan UDP ports
- B. Detect OS
- C. Scan TCP connect
- D. Stealth SYN scan

**Answer: A** — `-sU` = UDP scan.

### MCQ 17
Nmap lệnh kiểm tra OS của máy đích là:
- A. nmap -sT [IP]
- B. nmap -sU [IP]
- C. nmap -O [IP]
- D. nmap -sn [IP]

**Answer: C** — `-O` = OS detection.

### MCQ 18
Trong loop testing — simple loops với max n iterations, các test case bao gồm:
- A. 0, 1, n, n+1
- B. Skip, 1, 2, m (k<n), n−1, n, n+1
- C. 1, 2, ..., n
- D. n−2, n−1, n, n+1

**Answer: B** — 6 case theo Lecture 10.

### MCQ 19
Đặc điểm nào sau đây ĐÚNG về Implicit Wait trong Selenium?
- A. Targeted per element
- B. Global, set once per session
- C. Customizable polling interval
- D. Wait cho specific condition

**Answer: B** — Implicit Wait là global rule.

### MCQ 20
Trong Decision Table car insurance (Lecture 9), khi Male = T và < 25 = T thì fee là?
- A. 500
- B. 1000
- C. 1500
- D. 3000

**Answer: D** — Rule 1: Male T, <25 T → fee = 3000.

### MCQ 21
RASP khác SAST/DAST/IAST ở điểm:
- A. Chỉ test ở dev phase
- B. Phân tích source code at rest
- C. Bảo vệ runtime ở production, có khả năng BLOCK attack
- D. Cần access source code

**Answer: C** — RASP active defense ở production, block attack.

### MCQ 22
Fuzzing tool nào của Microsoft đã open-source?
- A. ClusterFuzz
- B. OneFuzz
- C. AFL
- D. libFuzzer

**Answer: B** — OneFuzz (Azure). ClusterFuzz là của Google.

### MCQ 23
Hash algorithm nào sau đây dùng salt theo bảng Lecture 11?
- A. MD5
- B. SHA-1
- C. SHA-256
- D. Bcrypt

**Answer: D** — Bcrypt (và Argon2i) có salt. MD5/SHA-1/SHA-256 trong bảng không salt.

### MCQ 24
Pairwise testing với 3 parameter, mỗi parameter 3 value, số TC exhaustive vs pairwise lần lượt:
- A. 9 và 3
- B. 27 và 9
- C. 27 và 27
- D. 81 và 27

**Answer: B** — Exhaustive 3³=27, pairwise = 9 (theo bảng Lecture 9).

### MCQ 25
Statement coverage CÓ HẠN CHẾ nào?
- A. Không phát hiện dead code
- B. Không phát hiện lỗi trong complex logical expression và empty branches
- C. Không phát hiện missing statement
- D. Không phát hiện unused branch

**Answer: B** — Statement coverage thiếu khả năng với complex boolean expression, empty branch.

### MCQ 26
Tutorial 9 Triangle: với a=1, b=200, c=200, kết quả nào?
- A. OUT_OF_RANGE
- B. INVALID
- C. ISOSCELES
- D. EQUILATERAL

**Answer: C** — Valid range, triangle inequality OK (1 < 400, 200 < 201, 200 < 201), hai cạnh bằng → ISOSCELES (1).

### MCQ 27
Tutorial 9 Triangle với a=1, b=1, c=2: kết quả?
- A. ISOSCELES
- B. INVALID (vì 1+1 = 2, không > 2)
- C. SCALENE
- D. EQUILATERAL

**Answer: B** — Triangle inequality cần STRICTLY GREATER (1+1=2 không > 2) → INVALID (−1).

### MCQ 28
Trong JMeter, Constant Timer 2000ms dùng để:
- A. Set timeout cho request
- B. Mô phỏng think time (delay giữa request) của người dùng
- C. Set ramp-up
- D. Loop count

**Answer: B** — Think time simulation.

### MCQ 29
Achieve all-transitions coverage 100% thì đồng thời đạt:
- A. Chỉ all-states
- B. Cả all-states và valid-transitions
- C. Chỉ valid-transitions
- D. Không đảm bảo cái nào

**Answer: B** — All-transitions ⇒ cả all-states và full valid-transitions.

### MCQ 30
Verification trả lời câu hỏi:
- A. "Are we building the right product?"
- B. "Are we building the product right?"
- C. "Is the product suitable for operations?"
- D. "Is the product secure?"

**Answer: B** — Verification = consistency = "build the product right". Validation = "build the right product".

---

## PART B — FILL IN THE BLANK (20 questions)

### Fill 1
Cyclomatic Complexity được đề xuất bởi __________ để đo độ phức tạp logic và xác định số path độc lập tối đa cần test.
**Answer:** Tom McCabe.

### Fill 2
Cho CFG có 10 edges, 8 nodes, V(G) = __________.
**Answer:** 10 − 8 + 2 = **4**.

### Fill 3
Cho CFG có 5 predicate nodes, V(G) = __________ (theo công thức P+1).
**Answer:** 5 + 1 = **6**.

### Fill 4
Trong data flow testing, 3 actions trên biến là __________, __________, __________.
**Answer:** d (define), r (reference), u (undefine).

### Fill 5
Cặp action `du` trong data flow nghĩa là __________ và được phân loại là __________.
**Answer:** Define → Undefine; **Suspicious** (chưa dùng đã xoá).

### Fill 6
3 strategies của Selenium `Select` class là: __________, __________, __________.
**Answer:** `selectByIndex()`, `selectByValue()`, `selectByVisibleText()`.

### Fill 7
8 locator của Selenium là: id, name, __________, __________, __________, __________, __________, __________.
**Answer:** className, tagName, linkText, partialLinkText, cssSelector, xpath.

### Fill 8
Công thức Fahrenheit → Celsius: C = ( __________ − 32 ) × __________ / __________.
**Answer:** F; 5; 9.

### Fill 9
Trong JMeter, 3 setting chính của Thread Group là: Number of Threads, __________, __________.
**Answer:** Ramp-Up Period; Loop Count.

### Fill 10
Nmap flag __________ thực hiện TCP connect scan (không cần root).
**Answer:** `-sT`.

### Fill 11
Nmap flag __________ thực hiện SYN stealth scan (cần root).
**Answer:** `-sS`.

### Fill 12
Nmap flag __________ thực hiện aggressive scan (OS + version + script + traceroute).
**Answer:** `-A`.

### Fill 13
Tool SAST phổ biến gồm SonarQube, __________, Fortify, Veracode.
**Answer:** Checkmarx.

### Fill 14
Tool DAST phổ biến gồm OWASP __________, Burp Suite, Invicti, Acunetix.
**Answer:** ZAP (OWASP ZAP).

### Fill 15
Trong Tutorial 9 Triangle, range hợp lệ cho mỗi cạnh là [__________, __________] inclusive.
**Answer:** 1; 200.

### Fill 16
Trong Tutorial 12 JMeter, target site là __________ và POST path là __________ với param `fromPort=Boston`, `toPort=London`.
**Answer:** blazedemo.com; `/reserve.php`.

### Fill 17
2 dạng pen-test là __________ pen-test (zero knowledge, dùng phishing/social engineering) và __________ pen-test (full code access, tìm internal flaw).
**Answer:** Black-box; White-box.

### Fill 18
Để prevent SQL Injection, best practice là dùng __________ (parameterized queries).
**Answer:** Prepared Statements.

### Fill 19
Trong Selenium, exception thường gặp khi element chưa load là __________.
**Answer:** `NoSuchElementException`.

### Fill 20
Coverage hierarchy của data flow từ yếu → mạnh: All-defs → __________ → __________.
**Answer:** All-uses; All-du-paths.
