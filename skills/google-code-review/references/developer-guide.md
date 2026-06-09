# Google Code Review: Developer / CL Author Guide

This document compiles Google's guidelines for developers going through code review.

## Table of Contents

1. [Writing Good CL Descriptions](#writing-good-cl-descriptions)
2. [Small CLs](#small-cls)
3. [How to Handle Reviewer Comments](#how-to-handle-reviewer-comments)

---

## Writing Good CL Descriptions

A CL description is a public record of change. It must communicate:
1. **What** change is being made — summary of major changes.
2. **Why** the changes are being made — context, decisions not reflected in code.

The description becomes a permanent part of version control history and may be read by hundreds of people over the years. Future developers will search for your CL based on its description.

### First Line
- Short summary of what is being done.
- Complete sentence, written as an imperative ("Delete the FizzBuzz RPC and replace it...").
- Followed by a blank line.
- Must stand alone — allows readers to skim history.

### Body
Fill in details — the problem being solved, why this is the best approach, shortcomings, bug numbers, benchmark results, links to design documents. Include enough context for future readers (external links may rot).

### Bad CL Descriptions
"Fix bug," "Fix build," "Add patch," "Moving code from A to B," "Phase 1," "Add convenience functions," "kill weird URLs."

### Good CL Descriptions
- **Functionality change:** First line describes what the CL does. Body explains the problem, why this is a good solution, and implementation specifics.
- **Refactoring:** First line describes what the CL does and how this is a change from the past. Body talks about specific implementation, context, why this change is being made.
- **Small CL needing context:** First line describes what's being done. Body explains *why* the change is being made.

### Tags
Optional labels like `[banana]`, `#banana`, `tag:`. Keep short; don't let them overwhelm the first line.

### Review the description before submitting
CLs can change during review — update the description to match the final code.

---

## Small CLs

### Why Write Small CLs?
- Reviewed more quickly.
- Reviewed more thoroughly.
- Less likely to introduce bugs.
- Less wasted work if rejected.
- Easier to merge.
- Easier to design well.
- Less blocking on reviews.
- Simpler to roll back.

Reviewers can reject a change outright for being too large.

### What is Small?
One self-contained change addressing just one thing:
- Minimal change addressing one thing (err on the side of too small).
- Include related test code.
- Everything needed to understand is in the CL, its description, or already-reviewed CLs.
- System continues to work well after submission.
- Not so small that implications are hard to understand.
- ~100 lines is reasonable; ~1000 lines is too large.

### When Large CLs Are Okay
- File deletions (count as one line of change).
- Fully trusted automatic refactoring tool output.

### Writing Small CLs Efficiently
Don't block waiting for review — use multiple projects, find immediately available reviewers, do in-person reviews, pair program, or split CLs.

### Strategies for Splitting CLs
- **Stacking:** Write one CL, send for review, start next CL based on the first.
- **Splitting by files:** Group files by reviewer (e.g., proto changes in one CL, code changes in another).
- **Splitting horizontally:** Create shared code/stubs between layers to isolate changes.
- **Splitting vertically:** Break into smaller full-stack vertical features.
- **Combining horizontal and vertical:** Chart a grid of CLs (layers x features).

### Separate Refactorings
Do refactorings in a separate CL from feature changes or bug fixes. Small cleanups (e.g., fixing a local variable name) can be included.

### Keep related test code in the same CL
Tests are expected for all Google changes. Independent test modifications can go into separate CLs first.

### Don't Break the Build
When CLs depend on each other, ensure the system keeps working after each submission.

### Can't Make it Small Enough?
This is very rarely true. Precede large CLs with refactoring-only CLs. Talk to teammates. If all fails (extremely rare), get advance consent from reviewers.

---

## How to Handle Reviewer Comments

### Don't Take It Personally
The goal of review is to maintain codebase quality. When a reviewer critiques your code, think of it as their attempt to help. If they express frustration, ask "What is the constructive thing they're trying to communicate?"

**Never respond in anger.** That is a serious breach of professional etiquette. Walk away from your computer if needed.

### Fix the Code
If a reviewer doesn't understand something in your code, clarify the code itself first, not the response. Future readers won't see the review comments. If the code can't be clarified, add a comment. Only then should you explain in the review tool.

### Think Collaboratively
When disagreeing with a reviewer:
- Bad: "No, I'm not going to do that."
- Good: "I went with X because of [pros/cons]. Are you suggesting Y better serves the tradeoffs?"

Ask for clarifications, discuss pros/cons, provide explanations. If you know something the reviewer doesn't, give them context.

### Resolving Conflicts
First try to come to consensus with your reviewer. If you can't, see The Standard of Code Review for resolution principles.
