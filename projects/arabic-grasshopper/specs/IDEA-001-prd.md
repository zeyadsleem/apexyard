# PRD: Arabic Grasshopper — Learn to Code in Arabic

**Status**: In Review
**Author**: Mariam (Product Manager)
**Created**: 2026-11-12
**Last Updated**: 2026-11-13

---

## Summary

This PRD defines the first release of Arabic Grasshopper: a free, Arabic-first, mobile-first web app that teaches children aged 8–14 to write real JavaScript through bite-sized interactive puzzles, in the style of Google Grasshopper (discontinued). The first release ships a complete interactive lesson engine plus one full module (JavaScript fundamentals: sequencing, variables, loops, functions). Development targets launch in 4–6 weeks by a solo developer on the Cloudflare free tier. Next action: Tech Lead review to start the tech-design phase.

---

## Overview

### Problem Statement

Google Grasshopper taught programming to beginners through short interactive puzzles on a phone, and Google discontinued it. Arabic-speaking children today have no equivalent. Existing Arabic-supporting products are block-based creation sandboxes (Scratch, OctoStudio), school curricula (Code.org), or blocks-generating-code games (ArabCode). None offers a guided path from puzzle to writing real text code. Children who start with real code early gain a durable skill, and Arabic-first, right-to-left interfaces remove the language barrier that current tools impose.

### Target User

**Primary**: Arab children aged 8–14 who are learning programming for the first time. Parents and teachers usually select the product for them.
**Secondary**: Parents and teachers who evaluate and guide the child. Older Arabic-speaking beginners are a future expansion, not a launch target.

### Goals

1. Ship the first release (lesson engine + one full module) publicly within 4–6 weeks.
2. Reach at least 100 monthly active users within 3 months of launch.
3. Reach at least 30% first-module completion rate among active users within 3 months.
4. Let a child aged 8–14 complete the first module without adult help.

### Non-Goals (Out of Scope)

- No monetization. The product is free forever at launch.
- No native mobile apps at launch. The product is a mobile-first web app.
- No user-generated content, community, or social features.
- No classroom management dashboard for teachers.
- No languages other than Arabic (simplified Modern Standard Arabic) in the interface and content.
- Modules beyond JavaScript fundamentals ship as later updates, not in the first release.

### Success Metrics

| Metric | Target | How Measured |
|--------|--------|--------------|
| Monthly active users | ≥ 100 by day 90 | Privacy-friendly analytics (aggregate, no personal data) |
| First-module completion rate | ≥ 30% of active users by day 90 | Progress events (aggregate) |
| Puzzle-level drop-off | Identify the puzzles where > 40% of users stop | Progress events (aggregate) |
| 7-day return rate | ≥ 15% of new users return within 7 days | Aggregate analytics |

**Kill criteria (pinned, owner-confirmed)**: development is parked if, at day 90 after launch, monthly active users are below 100, or first-module completion is below 10% of active users. The owner confirmed these thresholds on 2026-11-13.

---

## User Stories

### US-1: Start the journey without friction
>
> As a child, I want to start learning immediately without creating an account, so that I can play my first puzzle within seconds.

**Acceptance Criteria**:

- [ ] The first screen lets me start the first lesson in one tap.
- [ ] No account, email, or sign-up is required to start.
- [ ] The interface is entirely in simplified Modern Standard Arabic, laid out right-to-left.

### US-2: Solve a coding puzzle
>
> As a child, I want to solve a short coding puzzle with instant feedback, so that I learn one concept at a time without feeling lost.

**Acceptance Criteria**:

- [ ] Each puzzle teaches one concept and takes under 5 minutes.
- [ ] My code runs in a sandbox and I see the result immediately.
- [ ] Wrong answers give a hint in Arabic; repeated failures reveal a step-by-step nudge, never the full answer.
- [ ] A correct answer shows a success state and advances me automatically.

### US-3: Keep my progress
>
> As a child, I want my progress saved automatically, so that I continue where I stopped.

**Acceptance Criteria**:

- [ ] Progress persists in the browser without an account.
- [ ] Reopening the app resumes the last puzzle.
- [ ] A visible progress bar shows module and lesson completion.

### US-4: Write real code with a safe editor
>
> As a child, I want to type real JavaScript code in a simple editor, so that I practice the actual skill.

**Acceptance Criteria**:

- [ ] The editor supports typing JavaScript with basic syntax highlighting.
- [ ] The editor detects Arabic-script characters inside code and warns me, because RTL keyboards often produce them by mistake.
- [ ] Code validation runs safely in the browser with no access to network or storage.

### US-5: Stay motivated
>
> As a child, I want stars and visible progress, so that finishing lessons feels rewarding.

**Acceptance Criteria**:

- [ ] Each puzzle awards a star on first-try success and a star with hints on later success.
- [ ] The module screen shows total stars earned.

### Edge Cases

| Scenario | Expected Behavior |
|----------|-------------------|
| Child types Arabic characters into code | Inline warning marks the characters and shows a one-tap fix |
| Browser storage is blocked or cleared | App warns that progress will not persist; no crash |
| JavaScript sandbox fails to run code | App shows a plain Arabic error message and a retry option |
| Very long or malformed code | Editor keeps layout stable; parser error shows the line in Arabic |
| Slow connection on a low-end phone | First screen loads under 3 seconds on a 3G-class connection |

---

## Requirements

### Functional Requirements

| ID | Requirement | Priority | Notes |
|----|-------------|----------|-------|
| FR-1 | Interactive lesson engine supporting multiple puzzle types: fill-in-the-code, arrange-the-lines, predict-the-output, and free-code challenges | Must | Engine is content-driven; puzzles are data, not code |
| FR-2 | In-browser JavaScript validation with a sandboxed runner and instant Arabic feedback | Must | No server execution at launch |
| FR-3 | Hint ladder: progressive hints per puzzle, culminating in a near-solution nudge | Must | Hints are part of lesson content |
| FR-4 | One complete launch module: JavaScript fundamentals covering sequencing, variables, loops, and functions | Must | Target 25–40 puzzles; final scope set during content authoring |
| FR-5 | Full right-to-left Arabic interface in simplified Modern Standard Arabic with code areas kept left-to-right | Must | Code is always LTR with Latin characters |
| FR-6 | Local progress persistence (localStorage or equivalent) with automatic resume | Must | No accounts at launch |
| FR-7 | Star rewards and module progress display | Must | |
| FR-8 | Kid-oriented editing protections: Arabic-character-in-code detection, stable editor layout | Must | |
| FR-9 | Structured content format so new modules are added as data files without engine changes | Must | Content authoring is the main ongoing cost; format must be simple for a solo author |
| FR-10 | Aggregate, privacy-friendly analytics (no personal data, no cookies beyond a pseudonymous event id) | Should | Needed to measure success metrics and kill criteria |
| FR-11 | Installable as a PWA (add to home screen) | Should | Cheap win on mobile-first web |
| FR-12 | Optional progress export/import as a file | Could | Protects against storage clearing |

**Priority Key**: Must (required for launch) | Should (important) | Could (nice to have)

### Non-Functional Requirements

| Category | Requirement | Target |
|----------|-------------|--------|
| Performance | First screen load on 3G-class mobile network | < 3 seconds |
| Performance | Puzzle interaction latency (run code, show feedback) | < 1 second |
| Accessibility | WCAG 2.1 AA for the Arabic RTL interface; readable Arabic typography for children | Level AA |
| Security | Sandboxed code execution in the browser; no secrets, no server execution | No network/storage access from child code |
| Privacy | No personal data collection at launch; suitable for children | Aggregate events only |
| Availability | Cloudflare Pages free tier | ≥ 99.9% platform availability |

---

## Design

Design work starts after PRD approval. Direction from the positioning and audience:

- Mobile-first, RTL-native layout; playful but calm visual style for ages 8–14.
- Code areas are always left-to-right with a monospace font.
- A friendly guide character (Arabic mascot) introduces concepts, in the spirit of Grasshopper.

A UX review and a DESIGN.md follow in the design phase.

---

## Technical Notes

### Dependencies

| Dependency | Type | Status | Owner |
|------------|------|--------|-------|
| Cloudflare Pages/Workers free tier | External | Ready | zeyad |
| Lesson content authoring (Arabic pedagogy) | Internal | Blocked until engine format exists | zeyad |
| Analytics (privacy-friendly, aggregate) | External | To choose during tech design | zeyad |

### Technical Constraints

- Solo developer; total build time 4–6 weeks. Scope discipline is a hard constraint.
- Cloudflare free tier only; no paid services at launch.
- TypeScript strict mode; 80% test coverage target per project standards.
- JavaScript validation runs client-side in a sandbox (Web Worker or equivalent); no server code execution.

---

## Launch Plan

### Rollout Strategy

- [x] All users at once (public, free launch)
- [ ] Phased rollout
- [ ] Beta program first

Launch is public and free. Distribution relies on sharing in parent and teacher communities and Arabic tech channels. The first-module launch doubles as the demand-evidence mechanism defined by the kill criteria.

---

## Open Questions

| Question | Owner | Status | Resolution |
|----------|-------|--------|------------|
| Confirm pinned kill thresholds (100 MAU / 10% completion at day 90) | zeyad | Resolved | Owner confirmed on 2026-11-13 |
| Exact puzzle count and content outline for the launch module | zeyad | Open | Set during content authoring |
| Choice of aggregate analytics tool | zeyad | Open | Tech design phase |
| Hosting project name and domain | zeyad | Open | Before launch |

---

## Timeline

| Milestone | Target Date | Status |
|-----------|-------------|--------|
| PRD Approved | 2026-11-14 | |
| Tech Design Complete | 2026-11-21 | |
| Engine + Editor Working | 2026-12-05 | |
| Content Complete (Module 1) | 2026-12-12 | |
| QA Complete | 2026-12-16 | |
| Launch | 2026-12-18 | |

Target window: 4–6 weeks from approval (late November to mid-December 2026).

---

## Approvals

| Role | Name | Date | Status |
|------|------|------|--------|
| Product Manager | Mariam | 2026-11-12 | Author |
| Head of Product | | | Pending |
| Tech Lead | | | Pending |
| Head of Design | | | Pending |

---

## Glossary

| Term | Definition |
|------|------------|
| Lesson engine | The app system that presents puzzles, runs validation, and gives feedback. Content is data; the engine is code. |
| Puzzle | One bite-sized interactive coding challenge that teaches one concept and takes under 5 minutes. |
| Hint ladder | A sequence of progressive hints for a puzzle, from gentle to near-solution, never revealing the full answer. |
| Kill criteria | The pre-agreed numbers that, if missed, mean development is parked. |

---

*Source: IDEA-001 (GH#3). Validation: `projects/arabic-grasshopper/validation/IDEA-001-validation.md` (verdict GREEN).*
