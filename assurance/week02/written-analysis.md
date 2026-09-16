# Written analysis — Threat Model v1.0

CPS 5981 01, Week 02

**Fork:** https://github.com/Brago475/DevSecOps-Intro_Brago
**Commit:** f5743e439c6ce22c27ea97c7eaff22a80925a9e0
**Visibility:** Public
**Collaborators:** none
**Declared AI use:** Used AI for wording and structure on the step 8 analysis answers, and for grammar on the mission sentence. The findings, the STRIDE decisions and the boundary reasoning are mine.

## 1. Which of your abuse cases are supported by evidence you gathered, and which rest on reasoning about the design?

Cases 2 and 3 are backed by direct evidence: five incorrect password attempts caused no slowdown or lockout, Command 3 showed no Content-Security-Policy header, and the review box was visible on product pages.
Cases 1, 4, 5, and 6 are based on reasoning about how the system appears to be designed.
I did not observe an actual checkout request, generate extra traffic, inspect sign-in logs, or have any visibility into staff actions

## 2. What does STRIDE not surface for this target?

STRIDE does not clearly capture misuse by authorized users, such as a staff member viewing far more customer data than their job requires, because no spoofing, tampering, or other STRIDE category necessarily occurs. It also focuses on individual elements, so a sequence of actions that seems harmless step by step but becomes damaging when combined can be missed.

## 3. Which trust boundary are you least confident about, and what would settle it?

I am least confident about the application server to data store boundary because I did not directly observe a database query or inspect the database. Reviewing the data access code or watching an order being written to the data store would confirm it.

## 4. If this system had twice as many users, which case moves up your list, and why?

Case 5, flooding, would move up my list because twice as much normal traffic makes malicious requests harder to distinguish and increases the impact on availability. Case 2 also becomes more serious because there are more accounts to target, while Case 1 keeps the same likelihood but could cause greater financial loss because more orders are being processed.
