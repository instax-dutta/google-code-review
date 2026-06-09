# Google Code Review: Reviewer Guide

This document compiles Google's code review guidelines for reviewers. It is organized into six sections.

## Table of Contents

1. [The Standard of Code Review](#the-standard-of-code-review)
2. [What to Look For In a Code Review](#what-to-look-for-in-a-code-review)
3. [Navigating a CL in Review](#navigating-a-cl-in-review)
4. [Speed of Code Reviews](#speed-of-code-reviews)
5. [How to Write Code Review Comments](#how-to-write-code-review-comments)
6. [Handling Pushback in Code Reviews](#handling-pushback-in-code-reviews)

---

## The Standard of Code Review

The primary purpose of code review is to make sure that the overall code health of the codebase is improving over time.

**The central principle:** In general, reviewers should favor approving a CL once it is in a state where it definitely improves the overall code health of the system being worked on, even if the CL isn't perfect.

There is no such thing as "perfect" code — there is only *better* code. Instead of seeking perfection, seek *continuous improvement*. A CL that improves maintainability, readability, and understandability shouldn't be delayed for days or weeks because it isn't "perfect."

Reviewers should always feel free to leave comments expressing that something could be better, but if it's not very important, prefix it with "Nit: " to let the author know it's just a point of polish.

### Mentoring

Code review can teach developers. If your comment is purely educational but not critical to meeting standards, prefix it with "Nit: " or otherwise indicate it's not mandatory.

### Principles

- Technical facts and data overrule opinions and personal preferences.
- On matters of style, the style guide is the absolute authority. Purely personal style points not in the style guide should accept the author's choice.
- Software design aspects are almost never pure style — they're based on underlying principles. If the author can demonstrate several approaches are equally valid, accept the author's preference.
- If no other rule applies, ask the author to be consistent with what is in the current codebase, as long as it doesn't worsen code health.

### Resolving Conflicts

1. First, try to come to consensus.
2. Face-to-face or video conference (record results as a comment).
3. Escalate — broader team discussion, Technical Lead, maintainer, Engineering Manager.
4. Don't let a CL sit around because of disagreement.

---

## What to Look For In a Code Review

### Design
The most important thing — does the overall design make sense? Does this change belong in the codebase? Does it integrate well with the rest of the system?

### Functionality
Does the CL do what the developer intended? Is what the developer intended good for users? Think about edge cases, concurrency problems, bugs. For UI changes, validate. For parallel programming, think carefully about deadlocks and race conditions.

### Complexity
Check at every level — lines, functions, classes. "Too complex" means can't be understood quickly by code readers, or developers are likely to introduce bugs when calling or modifying.

Watch for **over-engineering**: code made more generic than needed, or functionality added that isn't needed now. Encourage solving the problem that needs to be solved *now*, not the future problem that *might* need solving.

### Tests
Ask for appropriate unit, integration, or end-to-end tests. Tests should be in the same CL (unless emergency). Ensure tests actually fail when code is broken, produce no false positives, make simple assertions. Tests are also code that must be maintained — don't accept complexity in tests.

### Naming
Good names are long enough to fully communicate, without being so long they're hard to read.

### Comments
Comments should explain **why** code exists, not **what** it does. If code isn't clear enough to explain itself, make the code simpler. Exceptions: regular expressions and complex algorithms.

### Style
Follow the style guides. Non-style-guide points should be prefixed "Nit:". Don't block on personal style preferences. Major style changes should be separate CLs.

### Consistency
Style guide is absolute authority. If the style guide makes recommendations vs requirements, bias toward the style guide unless local inconsistency would be too confusing. If no other rule applies, maintain consistency with existing code.

### Documentation
Update READMEs, docs, generated reference docs when user-facing behavior changes.

### Every Line
Review every line of code assigned to you. If you can't understand it, ask the developer to clarify — if you can't, other developers likely can't either. If you're not qualified for part of the review, ensure someone qualified is.

### Context
Look at the broader context — the whole file, the system as a whole. Is this CL improving or degrading code health? Don't accept CLs that degrade code health.

### Good Things
Praise good work. Telling developers what they did right is sometimes more valuable than pointing out mistakes.

---

## Navigating a CL in Review

### Step 1: Take a broad view
Read the CL description. Does the change make sense? If rejecting, explain why and suggest what the developer should have done instead. Be courteous.

### Step 2: Examine the main parts
Find the file(s) with the largest logical change; review those first. If you see major design problems, send those comments **immediately** — even before reviewing the rest — to avoid wasted work.

### Step 3: Look through the rest
Once no major design issues, go through files in order. Optionally read tests first to understand what the change is supposed to do.

---

## Speed of Code Reviews

### Why fast reviews matter
Optimize for **team velocity**, not individual velocity. Slow reviews decrease team velocity, cause frustration, and harm code health (fewer cleanups, refactorings).

### How fast?
If not in focused work, review shortly after a CL comes in. **Maximum response time: one business day.** A typical CL should get multiple rounds of review in a single day.

### Speed vs. Interruption
If in a focused task (writing code), don't interrupt yourself. Wait for a break point (task completion, after lunch, after a meeting).

### Fast Responses
The **response time** is more important than total turnaround. Quick individual responses significantly ease developer frustration.

### LGTM With Comments
Give approval even with unresolved comments when:
- You're confident the developer will address all remaining comments.
- The comments don't *have* to be addressed.
- The suggestions are minor (sort imports, fix a typo, etc.).

Especially valuable across time zones.

### Large CLs
Ask the developer to split into smaller CLs. If it truly can't be split, at least write comments on the overall design and send it back.

---

## How to Write Code Review Comments

### Summary
- Be kind.
- Explain your reasoning.
- Balance giving explicit directions with just pointing out problems.
- Encourage simplification / code comments instead of explaining complexity in comments.

### Courtesy
Comment on the **code**, not the **developer**.
- Bad: "Why did **you** use threads here?"
- Good: "The concurrency model here is adding complexity without performance benefit..."

### Explain Why
Help the developer understand *why* you're making your comment — your intent, the best practice you're following, how your suggestion improves code health.

### Giving Guidance
The developer is responsible for fixing the CL, not the reviewer. Pointing out problems lets the developer learn and often yields better solutions. But sometimes direct instructions/suggestions/code are more helpful. Comment on good things too.

### Label Comment Severity
- **Nit:** Minor — technically should do but won't hugely impact things.
- **Optional / Consider:** Not strictly required.
- **FYI:** Informational, for future consideration.

This makes review intent explicit and helps authors prioritize.

### Accepting Explanations
If you don't understand code, the developer should **rewrite the code more clearly**, not just explain in the review tool. Explanations in the review tool are acceptable only in rare circumstances.

---

## Handling Pushback in Code Reviews

### Who is right?
First consider if the developer is correct — they are often closer to the code. If so, let the issue drop. If not, explain why your suggestion is correct with good reasoning. Continue advocating if you believe the improvement justifies the effort.

### Upsetting Developers
Usually overblown. Brief upset is common; developers often become thankful later. Problems are usually about **how** comments are written, not about insistence on quality.

### Cleaning It Up Later
A common pushback is "I'll clean it up in a later CL." Experience shows this rarely happens unless done immediately. Insist on cleaning up **now** before code is "done." If the CL introduces new complexity, it must be cleaned up before submission (unless emergency). If exposing surrounding problems, file a bug and assign it to the developer.

### General Complaints About Strictness
If switching from lax to strict reviews, expect loud complaints. Speeding up reviews helps complaints fade. It may take months, but developers eventually see the value.

### Resolving Conflicts
If unable to resolve, see The Standard of Code Review for conflict resolution guidelines.
