# Emergencies

## What Is An Emergency?

An emergency CL is a **small** change that:
- Allows a major launch to continue instead of rolling back.
- Fixes a bug significantly affecting users in production.
- Handles a pressing legal issue.
- Closes a major security hole.

In emergencies, speed of the entire review process matters, not just response speed. The reviewer should care more about speed and correctness (does it resolve the emergency?) than anything else. Such reviews take priority over all others.

After the emergency is resolved, look over the CL again and give it a more thorough review.

## What Is NOT An Emergency?

- Wanting to launch this week instead of next (unless a hard deadline).
- The developer has worked on a feature for a long time.
- Timezone differences.
- Friday end-of-day desire to merge before weekend.
- Manager says it must be done today due to a soft deadline.
- Rolling back a CL causing build/test failures.

## Hard Deadlines vs Soft Deadlines

A **hard deadline** is one where something disastrous would happen if missed (contractual obligation, product failure in marketplace, annual hardware manufacturer submission).

Most deadlines are **soft deadlines** — important but should not sacrifice code health to make them. Sacrificing code review quality to meet soft deadlines leads to overwhelming technical debt.
