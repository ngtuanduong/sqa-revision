# Day 2 – MCQ + Fill-in-Blank Practice (Lifecycle, Reviews, UI)

## Part A – Multiple Choice Questions (25)

### MCQ 1
The Waterfall Model has how many phases?
- A) 5
- B) 6
- C) 7
- D) 8

**Answer:** C) 7
**Explanation:** Requirements → Analysis → Design → Coding → System Tests → Installation/Conversion → Operation & Maintenance.

### MCQ 2
Which is NOT a type of maintenance service in Waterfall Phase 7?
- A) Corrective
- B) Adaptive
- C) Perfective
- D) Preventive

**Answer:** D) Preventive
**Explanation:** Three types defined: Corrective (fix faults), Adaptive (new requirements), Perfective (improve performance).

### MCQ 3
The Prototyping Model is BEST suited for:
- A) Large mission-critical systems with stable requirements
- B) Small- to medium-sized projects with active customer participation
- C) Real-time embedded firmware with strict safety needs
- D) Systems where documentation is the primary deliverable

**Answer:** B)
**Explanation:** Prototyping requires customer involvement to examine prototypes; best for small/medium projects.

### MCQ 4
The Spiral Model combines:
- A) Waterfall + V-Model
- B) Agile + DevOps
- C) Iterative nature of prototyping + controlled/systematic aspects of waterfall
- D) Kanban + Scrum

**Answer:** C)
**Explanation:** Explicit definition in Lecture 5.

### MCQ 5
Which of the following is NOT one of the three pillars of Scrum's empiricism?
- A) Transparency
- B) Inspection
- C) Adaptation
- D) Documentation

**Answer:** D) Documentation
**Explanation:** Scrum pillars are Transparency, Inspection, Adaptation.

### MCQ 6
How many Scrum events are there?
- A) 3
- B) 4
- C) 5
- D) 6

**Answer:** C) 5
**Explanation:** Sprint, Sprint Planning, Daily Scrum, Sprint Review, Sprint Retrospective.

### MCQ 7
The time-box of the Daily Scrum is:
- A) 5 minutes
- B) 10 minutes
- C) 15 minutes
- D) 30 minutes

**Answer:** C) 15 minutes
**Explanation:** Daily Scrum is a 15-minute event for Developers.

### MCQ 8
Which commitment is associated with the Increment artifact?
- A) Product Goal
- B) Sprint Goal
- C) Definition of Done
- D) Sprint Backlog

**Answer:** C) Definition of Done
**Explanation:** Product Backlog→Product Goal; Sprint Backlog→Sprint Goal; Increment→Definition of Done.

### MCQ 9
Which is NOT one of the 5 Scrum values?
- A) Commitment
- B) Focus
- C) Respect
- D) Discipline

**Answer:** D) Discipline
**Explanation:** Scrum values: Commitment, Focus, Openness, Respect, Courage.

### MCQ 10
Which is a Project Factor (NOT a Team Factor) affecting QA intensity?
- A) Professional qualifications of members
- B) Percentage of new staff members
- C) Severity of failure outcomes
- D) Team acquaintance with the project

**Answer:** C) Severity of failure outcomes
**Explanation:** Project Factors: Magnitude, Technical complexity, Reusable components, Severity.

### MCQ 11
The four phases of a unit test case are:
- A) Plan → Code → Run → Verify
- B) Set up → Exercise → Verify → Teardown
- C) Init → Execute → Compare → Cleanup
- D) Arrange → Act → Assert → Report

**Answer:** B) Set up → Exercise → Verify → Teardown
**Explanation:** Generic unit test structure per Lecture 6.

### MCQ 12
Who should NOT perform acceptance testing?
- A) Customer
- B) Independent test team
- C) The development team
- D) An external consultant

**Answer:** C) The development team
**Explanation:** "The system development team should not be responsible for acceptance testing."

### MCQ 13
In prioritization formula C = kA + mB, what does Factor A represent?
- A) Probability of failure
- B) Severity (damage to life/finance/essential functions)
- C) Resource availability
- D) Test execution speed

**Answer:** B) Severity
**Explanation:** A = Severity; B = Risk (probability of failure).

### MCQ 14
Which is NOT a valid test termination criterion?
- A) Error seeding
- B) Mathematical models
- C) Customer signoff via email
- D) Resource limit (time/budget)

**Answer:** C) Customer signoff via email
**Explanation:** Five routes: Completed Implementation, Mathematical Models, Error Seeding, Dual Teams, Resource Limit.

### MCQ 15
According to the defect cost model, fixing a bug after release is approximately how many times more expensive than fixing it in the requirements phase?
- A) 10×
- B) 50×
- C) 110×
- D) 1000×

**Answer:** C) 110×
**Explanation:** Lecture 6: "Fixing a bug after release is 110x more expensive than fixing it during requirements."

### MCQ 16
Which one is a DIRECT objective of reviews?
- A) Knowledge exchange
- B) Process improvement
- C) Approval of product for next phase
- D) Career development of reviewers

**Answer:** C) Approval
**Explanation:** Direct: Error Detection, Risk Identification, Standardization, Approval. Indirect: Knowledge Exchange, Process Improvement.

### MCQ 17
The Golden Rule of review meetings is:
- A) Always design solutions during the meeting
- B) Detect errors only, do not design solutions on the spot
- C) The author defends the document at all costs
- D) Decisions are made by majority vote

**Answer:** B)
**Explanation:** Lecture 7 explicitly states: "Detect errors only. Do not design solutions on the spot."

### MCQ 18
Optimal review team size per Pressman's guidelines is:
- A) 1-2
- B) 3-5
- C) 6-8
- D) 10+

**Answer:** B) 3-5
**Explanation:** "Limit team size (3-5 members)".

### MCQ 19
Maximum duration of a review/inspection session is:
- A) 1 hour
- B) 2 hours
- C) 4 hours
- D) 8 hours

**Answer:** B) 2 hours
**Explanation:** Both DR and peer review sessions: Max 2 hours.

### MCQ 20
Which sequence correctly represents the Fagan Inspection 6-step process?
- A) Planning → Preparation → Overview → Meeting → Follow-up → Rework
- B) Overview → Planning → Preparation → Meeting → Rework → Follow-up
- C) Planning → Overview → Preparation → Meeting → Rework → Follow-up
- D) Preparation → Planning → Meeting → Overview → Follow-up → Rework

**Answer:** C) Planning → Overview → Preparation → Meeting → Rework → Follow-up
**Explanation:** Standard Fagan order.

### MCQ 21
In an Inspection, who is typically the presenter?
- A) The author
- B) Someone other than the author (often the Coder)
- C) The customer
- D) The Project Manager

**Answer:** B) Someone other than the author
**Explanation:** Inspection: presenter usually NOT the author; Walkthrough: presenter IS the author.

### MCQ 22
Which specialized role belongs to a Walkthrough (not an Inspection)?
- A) Designer
- B) Coder
- C) Tester
- D) Standards Enforcer

**Answer:** D) Standards Enforcer
**Explanation:** Inspection roles: Designer, Coder, Tester. Walkthrough roles: Standards Enforcer, Maintenance Expert, User Representative.

### MCQ 23
The latency rule for UI feedback says the system must respond within:
- A) 0.01s
- B) 0.1s
- C) 1s
- D) 3s

**Answer:** B) 0.1s
**Explanation:** < 0.1s for solid/responsive feel.

### MCQ 24
Which selection modifier selects a RANGE?
- A) Click
- B) Ctrl+Click
- C) Shift+Click
- D) Alt+Click

**Answer:** C) Shift+Click
**Explanation:** Click = One; Ctrl+Click = Multiple; Shift+Click = Range.

### MCQ 25
Per Cooper's UI principles, the UI should reflect:
- A) The Implementation Model
- B) The User's Mental Model
- C) The database schema
- D) The developer's preference

**Answer:** B) User's Mental Model
**Explanation:** Mask complexity; UI should match how users imagine the system works.

## Part B – Fill-in-the-Blank (15)

### FIB 1
The 7 phases of the Waterfall Model are: Requirements, Analysis, Design, Coding, ________, Installation & Conversion, and Operation & Maintenance.

**Answer:** System Tests

### FIB 2
Scrum has ____ roles, ____ events, and ____ artifacts.

**Answer:** 3 / 5 / 3

### FIB 3
The Sprint is fixed length of ____ month or less.

**Answer:** one (1)

### FIB 4
Sprint Planning addresses three topics: Why is this Sprint valuable? What can be Done? and ________?

**Answer:** How will the chosen work get done

### FIB 5
The commitment associated with the Sprint Backlog is the ________.

**Answer:** Sprint Goal

### FIB 6
The four sub-classes of Development life cycle SQA components are: Formal design reviews, ________, Expert opinions, and Software testing.

**Answer:** Peer reviews

### FIB 7
The four phases of a unit test case (in order) are: Set up → Exercise → ________ → Teardown.

**Answer:** Verify

### FIB 8
In integration testing, the strategy that begins with the lowest-level components is called ________ integration.

**Answer:** Bottom-up

### FIB 9
In the prioritization formula C = kA + mB, factor A represents ________ and factor B represents ________.

**Answer:** Severity (damage to life/finance/essential functions); Risk (probability of failure)

### FIB 10
The four key testing documents are: STP (Software Test Plan), STD (Software Test ________), STR (Software Test Report), and TSR (Test Summary Report).

**Answer:** Description

### FIB 11
Fixing a bug after release is approximately ________ times more expensive than fixing it during the requirements phase.

**Answer:** 110

### FIB 12
The 6 steps of Fagan inspection are: Planning, Overview, ________, Meeting, Rework, Follow-up.

**Answer:** Preparation

### FIB 13
Peer reviews typically cover ____ to ____% of documents, focused on high-risk or complex sections.

**Answer:** 5 / 15

### FIB 14
According to UI feedback rules, the system must respond in less than ________ seconds.

**Answer:** 0.1

### FIB 15
"Excise" is defined as extra work that satisfies the needs of the ________, not the user.

**Answer:** tool
