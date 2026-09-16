# Trust boundaries

Threat Model v1.0 — CPS 5981 01, Week 02

Boundaries are derived from the zone each element sits in. A flow whose endpoints are in
different zones crosses one. Direction matters: the two directions between the same pair of
zones are separate boundaries, because the assumption being made differs.

Crossing flows: 8  —  distinct boundaries: 4

## 1. User's browser → Application server

**What crosses:** email address and password; search terms and order details; photo file and caption; review text displayed to other customers

**Why this is a real boundary:** This is a real trust boundary because data is moving from the user-controlled browser into the application server. The browser cannot be fully trusted because a user can modify requests, submit unexpected values, upload malicious files, or bypass normal interface restrictions.The application server is being asked to trust that the email address, password, search terms, order details, uploaded photo and caption, and review text are valid and safe. The server must therefore validate, sanitize, authenticate, and authorize this data before storing it, processing it, or displaying it to other users.

**Confidence, and what would settle it:** I am highly confident this is a real trust boundary because the browser is controlled by the user while the application server is responsible for protecting the system and its data.

## 2. Application server → User's browser

**What crosses:** session token in a cookie

**Why this is a real boundary:** This is a real trust boundary because the application server is sending a session token into the user-controlled browser. Once the token reaches the browser, it is outside the server’s direct control and could potentially be stolen, copied, or misused. The browser is being trusted to store and return the session cookie securely without exposing or altering it. The server also relies on the token to correctly identify the authenticated user when future requests are made. Command 3 showed no Content-Security-Policy header is sent, so the browser lacks an additional defense against malicious or injected scripts running on the page.

**Confidence, and what would settle it:** I am highly confident this is a real trust boundary because session tokens move from a trusted server environment into a less trusted client environment. Checking the cookie settings and authentication implementation would settle it, especially confirming protections such as HttpOnly, Secure, SameSite, expiration, and server-side session validation.

## 3. Application server → Data store

**What crosses:** product and order records; photo file and caption

**Why this is a real boundary:** The server sends data into a separate storage system, so trust changes between the application and database/storage layer. The data store trusts that product, order, photo, and caption data sent by the server is valid and authorized.

**Confidence, and what would settle it:** Least confident of the four. I never observed a query or looked at the database, so this rests on how applications of this kind are usually built rather than on anything I saw. Reading the data access code, or watching a single order being written, would settle it.

## 4. Data store → User's browser

**What crosses:** photo file and caption shown to every customer

**Why this is a real boundary:** This is a real boundary because stored photo and caption data is sent into the user-controlled browser and displayed to customers. The browser is trusting that the stored photo and caption are safe to display and do not contain malicious content.

**Confidence, and what would settle it:** High confidence. Reviewing how stored captions and uploaded photos are validated and encoded before display would confirm it.
