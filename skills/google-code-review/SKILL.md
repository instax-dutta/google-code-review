---
name: google-code-review
description: |
  Apply Google's official code review best practices to review code, prepare code for review, write CL/PR descriptions, handle reviewer feedback, and resolve code review conflicts. Use this skill whenever the user asks for a code review, wants their PR/CL reviewed, asks how to write better code for review, needs guidance on code review etiquette, asks how to structure a changelist or pull request description, wants advice on splitting large changes, or asks about code review standards and processes. This skill covers both the reviewer's perspective (what to look for, how to comment) and the developer/author's perspective (writing good CL descriptions, keeping changes small, handling feedback). Use it when the user mentions code review, PR review, CL review, changelist, pull request review, review comments, reviewer feedback, or any code review process question. Make sure to use this skill even if the user doesn't explicitly mention "Google" — the practices are broadly applicable.
---

# Google Code Review Skill

This skill helps you apply Google's code review best practices. It has two main modes that map to the two audiences in Google's guide:

1. **Reviewer Mode** — when you are asked to review someone else's code
2. **Author Mode** — when someone needs help preparing their code for review

When the user gives you code to review, also consider whether you should look at the relevant reference docs (reviewer-guide.md for reviewing, developer-guide.md for preparing code) — but don't load them unnecessarily; use the guidance in this skill first.

## Using This Skill

### Step 1: Determine the user's role
- Are they asking you to **review** code? → Use the **Reviewer Mode** instructions in this skill.
- Are they asking how to **prepare** code for review, write a description, or handle feedback? → Use the **Author Mode** instructions in this skill.
- Are they asking about **general process** (e.g. "how fast should reviews be?", "what counts as an emergency?")? → Load the relevant reference file.

### Step 2: Apply the appropriate mode

---

## Reviewer Mode: How to Review Code

When someone asks you to review code, follow Google's process. The overarching philosophy is:

> **Favor approving a CL once it is in a state where it definitely improves the overall code health of the system, even if the CL isn't perfect.**

There is no "perfect" code — seek *continuous improvement*.

### Before you start

Read the CL/PR description. Does it explain what the change does and why? If not, flag this — it's important for future readers.

### What to look for (in order of importance)

1. **Design** — Is the code well-designed and appropriate for the system?
2. **Functionality** — Does it behave as intended? Think about edge cases, concurrency, bugs.
3. **Complexity** — Could it be simpler? Can another developer easily understand it? Watch for over-engineering (solving future problems that don't yet exist).
4. **Tests** — Are there appropriate tests? Will they actually fail when the code is broken? Are they well-designed and maintainable?
5. **Naming** — Clear, communicative names that aren't overly long.
6. **Comments** — Do they explain *why* (not *what*)? If the code needs comments to explain what it does, simplify the code instead.
7. **Style** — Follow established style guides. Personal preferences (not in the style guide) get a "Nit:" prefix.
8. **Documentation** — Are READMEs and docs updated?
9. **Every line** — Review every line. If you can't understand it, ask for clarification. Future readers will also struggle.
10. **Context** — Look at the whole file and system. Is this change improving or degrading code health?

### Structure of your review

1. Start with the **broad view**: does the change make sense? If it shouldn't be happening at all, say so immediately (courteously, with reasoning).
2. Examine the **main parts** first — the files with the largest logical changes. If you see major design problems, flag them immediately to avoid wasted work.
3. Review the **rest** in logical order. Optionally read tests first to understand intent.

### How to write review comments

- **Be kind.** Comment on the code, not the developer. ("This approach has these issues..." not "Why did you do this?")
- **Explain why.** Help the developer understand your reasoning and the best practice you're following.
- **Balance guidance.** Pointing out problems helps developers learn; direct suggestions help move faster. Use judgment.
- **Label severity:**
  - `Nit:` — Minor polish point, not blocking
  - `Optional:` or `Consider:` — Not strictly required
  - `FYI:` — Informational, for future consideration
- **Praise good work.** Tell developers what they did right — it's powerful mentoring.
- **Don't accept "I'll clean it up later."** Experience shows this rarely happens. Insist on cleaning up now (unless it's a genuine emergency).

### Speed of review

- Respond within **one business day** (maximum).
- If you're in a focused task (coding), wait for a break point — don't interrupt your flow.
- Response speed matters more than total turnaround time.
- **LGTM With Comments:** Approve even with unresolved minor comments when you trust the developer to address them.
- For large CLs, ask the developer to split them.

### Handling pushback

- First consider whether the developer is right (they're often closer to the code).
- If you're right, explain why — with good reasoning and an understanding of their perspective.
- Stay polite. Upsets are usually about *how* comments are written, not the reviewer's standards.
- If you can't reach consensus, escalate (team discussion, tech lead, engineering manager).
- **Don't let a CL sit around because of disagreement.**

### When to treat something as an emergency

Only small changes that fix production bugs, security holes, legal issues, or unblock major launches qualify. Most "urgent" requests are not emergencies — don't sacrifice code health for soft deadlines.

---

## Author Mode: How to Prepare Code for Review

When someone asks you to help prepare their code for review, focus on these areas:

### Write a good CL/PR description

- **First line:** Short, imperative summary of what's being done. Must stand alone.
- **Body:** Explain *why* — the problem being solved, why this approach, tradeoffs, context. Future readers need this.
- Bad examples: "Fix bug", "Fix build", "Add patch", "Phase 1".
- Good examples follow the pattern: clear action + context + reasoning.

### Make CLs small

- One self-contained change per CL. ~100 lines is reasonable; ~1000 lines is too large.
- Benefits: reviewed faster, more thoroughly, fewer bugs, easier to merge/rollback.
- Strategies for splitting: stacking, splitting by files, horizontal (by layer), vertical (by feature).
- Separate refactorings from feature changes.
- Keep tests in the same CL.

### Handle reviewer comments

- **Don't take it personally.** Review is about code quality, not you.
- **Fix the code**, not the explanation. Future readers won't see the review conversation.
- **Think collaboratively.** Ask clarifying questions, discuss tradeoffs, provide context.
- Never respond in anger. Walk away if needed.

### Before submitting

Review your CL description one more time — CLs change during review, and the description should reflect the final state.

---

## When to Load Reference Files

- For **detailed reviewer guidelines** (every aspect of what to look for, how to navigate, speed, comments, pushback): load `references/reviewer-guide.md`
- For **detailed developer/author guidelines** (CL descriptions, small CLs, handling comments): load `references/developer-guide.md`
- For **emergency definitions and policies**: load `references/emergencies.md`

Only load a reference file when you need more depth than what's covered above. Start with the guidance in this skill and load references when the user's question requires the full detail.
