# Google Code Review Skill

Google's written code review standard for AI agents — not ad-hoc AI reviews with no standard.

Most AI reviews are vibes-based: nitpicky comments, no consistent bar, no author guidance. This skill installs Google's actual engineering standard, in both reviewer + author modes.

## Why

- **Without it:** generic AI review comments, inconsistent bar, slow back-and-forth, bad CL descriptions.
- **With it:** Google's documented bar — design, functionality, complexity, tests, naming, comments, style, docs — plus speed, courtesy, and how to resolve pushback.
- **Author mode too:** write good CL/PR descriptions, keep CLs small, prepare code for review, handle reviewer feedback without friction.
- **Emergencies covered:** what counts as a real emergency and what process still applies.

Source: [Google's Engineering Practices documentation](https://github.com/google/eng-practices), licensed under CC-By 3.0.

## Install

```bash
npx skills add instax-dutta/google-code-review
```

Or for Claude Code / opencode:

```bash
npx skills add instax-dutta/google-code-review -g -y
```

## How an agent uses it

Triggers automatically when you:

- Ask for a code review on your PR/CL
- Ask how to write good commit/PR descriptions
- Ask how to prepare code for review
- Ask about code review standards and processes
- Ask how to handle pushback from a reviewer

Two modes:

- **Reviewer:** standard, what to look for, navigating CLs, review speed, writing comments, handling pushback
- **Author:** CL descriptions, small CLs, handling reviewer comments + emergencies

## Proof

- Based directly on `google/eng-practices`
- Ships 3 reference guides: `reviewer-guide.md` + `developer-guide.md` + `emergencies.md`
- Covers reviewer behavior AND developer workflow, not just linting
- Same CC-By 3.0 source Google engineers actually use

If this saved you a bad review, star it.

## Source Material

This skill is based on [Google's Engineering Practices documentation](https://github.com/google/eng-practices), which is licensed under CC-By 3.0.

## More agent skills by me

- [flash-compare](https://github.com/instax-dutta/flash-compare) - Flash-style top-1% product comparisons, exactly how flash.co works
- [master-pitcher](https://github.com/instax-dutta/master-pitcher) - Audit, draft, or roast pitch decks with an 18-check VC framework
- [brand-vibes](https://github.com/instax-dutta/brand-vibes) - Apply any company's design language while vibecoding, 66 brand profiles
- [roadmap-tutor](https://github.com/instax-dutta/roadmap-tutor) - Learn any roadmap.sh roadmap one topic at a time, tracked across sessions
- [market-validator](https://github.com/instax-dutta/market-validator) - Validate SaaS ideas with real user complaints across 10+ platforms
- [scroll-3d-world](https://github.com/instax-dutta/scroll-3d-world) - Scroll-scrubbed 3D fly-through landing pages in Three.js, no AI video
