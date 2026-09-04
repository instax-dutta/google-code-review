# Google Code Review Skill

Google's official code review best practices, packaged as an AI agent skill.

This skill teaches AI coding agents to apply Google's code review guidelines when reviewing code, preparing code for review, writing CL/PR descriptions, handling reviewer feedback, and resolving code review conflicts.

## Contents

- **`skills/google-code-review/`** — The skill files
  - `SKILL.md` — Main skill instructions (both reviewer and author modes)
  - `references/reviewer-guide.md` — Full reviewer guide (standard, what to look for, navigating CLs, speed, comments, pushback)
  - `references/developer-guide.md` — Full developer guide (CL descriptions, small CLs, handling comments)
  - `references/emergencies.md` — Emergency definitions and policies

## Installation

```bash
npx skills add instax-dutta/google-code-review
```

Or for Claude Code / opencode:

```bash
npx skills add instax-dutta/google-code-review -g -y
```

## Usage

Once installed, the skill triggers automatically when you:

- Ask for a code review on your PR/CL
- Ask how to write good commit/PR descriptions
- Ask how to prepare code for review
- Ask about code review standards and processes
- Ask how to handle pushback from a reviewer

## Source Material

This skill is based on [Google's Engineering Practices documentation](https://github.com/google/eng-practices), which is licensed under CC-By 3.0.

## More agent skills by me

- [flash-compare](https://github.com/instax-dutta/flash-compare) - Flash-style top-1% product comparisons, exactly how flash.co works
- [master-pitcher](https://github.com/instax-dutta/master-pitcher) - Audit, draft, or roast pitch decks with an 18-check VC framework
- [brand-vibes](https://github.com/instax-dutta/brand-vibes) - Apply any company's design language while vibecoding, 66 brand profiles
- [roadmap-tutor](https://github.com/instax-dutta/roadmap-tutor) - Learn any roadmap.sh roadmap one topic at a time, tracked across sessions
- [market-validator](https://github.com/instax-dutta/market-validator) - Validate SaaS ideas with real user complaints across 10+ platforms
- [scroll-3d-world](https://github.com/instax-dutta/scroll-3d-world) - Scroll-scrubbed 3D fly-through landing pages in Three.js, no AI video
