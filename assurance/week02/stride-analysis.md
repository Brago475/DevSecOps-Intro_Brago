# STRIDE analysis

Threat Model v1.0 — CPS 5981 01, Week 02

A category recorded as _checked, nothing found_ is a claim about the search, not about the
system. It is evidence and it is marked as such. A row left blank is not.

## Customer (external entity, User's browser)

| Category | Result |
| --- | --- |
| Spoofing | **Applies** — pretending to be someone else |
| Tampering | Checked, nothing found |
| Repudiation | Checked, nothing found |
| Information disclosure | Checked, nothing found |
| Denial of service | Checked, nothing found |
| Elevation of privilege | Checked, nothing found |

**What I found, and what I looked for and did not find:** I tried a wrong password five times and nothing slowed down or locked the account. I looked for a delay, a lockout, a captcha, or an email about failed sign-ins, and found none.

## Web application (process, Application server)

| Category | Result |
| --- | --- |
| Spoofing | Checked, nothing found |
| Tampering | **Applies** — changing data they should not |
| Repudiation | Checked, nothing found |
| Information disclosure | **Applies** — seeing what they should not |
| Denial of service | Checked, nothing found |
| Elevation of privilege | Checked, nothing found |

**What I found, and what I looked for and did not find:** The review box and the Photo Wall let a customer put content into pages other customers see. That's changing what the application displays to people, which is changing data they shouldn't control. also information disclosure reason: Command 3 showed no Content-Security-Policy header. Without it, the browser puts no restriction on which scripts may run on the page. A script running on a page can read what is on that page. That is a path to seeing what you should not see.

## Login service (process, Application server)

| Category | Result |
| --- | --- |
| Spoofing | **Applies** — pretending to be someone else |
| Tampering | Checked, nothing found |
| Repudiation | **Applies** — doing it without a trace |
| Information disclosure | Checked, nothing found |
| Denial of service | Checked, nothing found |
| Elevation of privilege | Checked, nothing found |

**What I found, and what I looked for and did not find:** What I found is that the login service decides who the customer is for the rest of the session. It accepted repeated wrong passwords with no delay and no lockout, so guessing can continue without limit. any record a customer or the university could read later showing which sign-ins happened or failed. I did not check server-side logs, so this is what the interface shows, not a confirmed absence.

## Product database (data store, Data store)

| Category | Result |
| --- | --- |
| Spoofing | Checked, nothing found |
| Tampering | Checked, nothing found |
| Repudiation | Checked, nothing found |
| Information disclosure | Checked, nothing found |
| Denial of service | Checked, nothing found |
| Elevation of privilege | Checked, nothing found |

**What I found, and what I looked for and did not find:** I saw no evidence about this element directly, only data the application displayed. I looked for whether the connection is authenticated per customer or uses one shared account, and could not determine it from the interface.

## Photo wall uploads (data store, Data store)

| Category | Result |
| --- | --- |
| Spoofing | Checked, nothing found |
| Tampering | Checked, nothing found |
| Repudiation | Checked, nothing found |
| Information disclosure | **Applies** — seeing what they should not |
| Denial of service | Checked, nothing found |
| Elevation of privilege | Checked, nothing found |

**What I found, and what I looked for and did not find:** Photo Wall images and captions from one customer are displayed to all customers. I did not find whether the Complaint form's invoice upload is also served back out.
