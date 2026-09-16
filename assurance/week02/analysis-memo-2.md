# Analysis Memo 2

CPS 5981 01, Week 02 — 10 points, two pages maximum

## As a vulnerability

The finding: The application sends no Content-Security-Policy header on any page..
Named as: CWE-693, Protection Mechanism Failure. It's a missing protection rather than a flaw in the code..

## As a risk

If an attacker gets any script onto a page that a signed-in customer opens, then that script can act as that customer, and nothing on our side records that it happened.

## Which one goes in front of the manager, and why

_Your judgment here. Name the manager and the decision they are making._

## What I am not sure about

I could not confirm whether files uploaded through the Complaint form are served back to other customers, which would change how easily a script gets onto a page.
