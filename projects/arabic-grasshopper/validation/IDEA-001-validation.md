# Arabic Grasshopper — Learn to Code in Arabic — Validation

**Date**: 2026-11-12
**Source**: IDEA-001
**Verdict**: **GREEN** (upgraded from YELLOW on the same date, after a follow-up competitive scan requested by the owner) — Audience and first-release shape are concrete, kill criteria are articulable, and the scan articulated a real differentiation: no Arabic-first incumbent offers a Grasshopper-style *guided text-coding* path; the Arabic options are block-based creation platforms or school curricula.

## Starting context

IDEA-001 — Arabic Grasshopper: an Arabic-language, beginner-friendly coding-learning app inspired by Google Grasshopper (discontinued) — teaching programming thinking through bite-sized interactive lessons, quizzes, and puzzles, easy for everyone (kids and up). Captured 2026-11-12; tracked as GH#3.

## Q1. Target user

Owner initially answered "all Arabic beginners." Probed once for the narrowest plausible group; answer: **Arab children aged 8–14 learning programming for the first time** (parents/teachers selecting for them). Concrete after probe; owner may expand later.

## Q2. Current alternative

Owner answer: "no real alternative." Probed once on whether the gap is real-but-low-priority or fictional, and what evidence exists. Answer: **intuition only — no direct evidence yet.** Captured as-is; this is the weakest answer.

**Revised by competitive scan (see below):** the owner's "no real alternative" was too strong — Arabic-supporting options exist (Scratch, Code.org, OctoStudio, ArabCode). The corrected statement: alternatives exist, but they are **block-based creation platforms or school curricula**, not a Grasshopper-style guided text-coding journey. The gap is narrower and more specific than originally claimed, but real.

## Q3. Smallest version

Owner explicitly rejected the validation-test framing: "I want to build a product I ship, and I don't have the luxury of experimentation and observation — Grasshopper really was a complete product, that's what we're modeling." Probed once on the first shippable release; answer: **first release = complete interactive Arabic lesson engine + one full module (JS fundamentals: sequencing, variables, loops, functions), published publicly; remaining modules ship as updates.** This is larger than the 1–2-day test slice, but it is a deliberate product-first stance, not an unexamined scope mistake. The first-module launch doubles as the demand-evidence mechanism.

## Q4. Kill criteria

Owner answer: "I'll define the numbers myself." A workable shape agreed in the question framing: post-launch, if after ~3 months the product shows fewer than ~100 active users or near-zero module completion, development is parked. Articulable — not a RED signal. Note: exact thresholds must be pinned in the PRD, not left implicit.

## Q5. Build / buy / rent

Owner answer: **BUILD**. No probe applied (Q2 produced no working competitor product to challenge against). Differentiator claimed: Arabic-first, RTL-native, complete product for a 8–14 audience. Weakness noted: Scratch and Code.org both have Arabic localizations; "Arabic" alone is a positioning angle, not a hard moat. A sharper statement of what beats localized incumbents for this age group is needed.

## Competitive scan (post-validation follow-up, 2026-11-12)

Requested by the owner to resolve the Q5 differentiation weakness. Findings from web search (secondary sources; not exhaustive, not store-audited):

| Player | Arabic support | Shape | Threat to the idea |
|--------|---------------|-------|--------------------|
| **Scratch** (MIT/Scratch Foundation) | Full Arabic UI + RTL (since 2018), resources 100% translated | Free block-based creation platform, ages 8–16 | High brand trust, but free-creation sandbox, not a guided beginner path |
| **Code.org (CodeAI)** | Arabic site + curriculum | Free K–12 school curriculum (CS + AI) | Broad and institutional, classroom-oriented, not mobile-first |
| **OctoStudio** (MIT) | Arabic listed | Free app, offline, no ads, ages 7+ | Block-based creative coding, no text-code progression |
| **عرب كود (ArabCode)** — arabcode.ae | Arabic-native | Kids platform: visual blocks generating Arabic code, 12 missions/4 worlds from Arab culture, certificates | Closest Arabic-native kids competitor; block-based, generates code rather than teaching to write it |
| **funarabicgames.com** | Arabic-native | 3 free Blockly-style games (maze/loops/conditionals), ages 6–14 | Tiny scope (3 games), but validates demand for Arabic coding games |
| **Octucode** | Arabic content | Video lessons + challenges (Python, C++), freemium | Not kids-specific, video-lesson format, not interactive puzzles |
| **كودي (Cody)** | Arabic-native | Behance concept only — not shipped | None yet |
| **Grasshopper (Google)** | English only | — | Discontinued; only unofficial APKs circulate |

**Differentiation statement (now articulated):** *"The first Arabic-first, mobile-first, guided journey that teaches beginners — and kids 8–14 — to write real code (JavaScript), one bite-sized interactive puzzle at a time. Not a block sandbox (Scratch, OctoStudio), not a school curriculum (Code.org), not blocks-generating-code (ArabCode): the Grasshopper experience, in Arabic, built from scratch."*

Residual honesty note: this is a positioning + execution moat, not a technological one — any incumbent could add an Arabic text-coding track. Speed and content quality are the defense.

## Read-out

The kernel is real and the owner is coherent about intent: this is a ship-a-product effort, not a market experiment, and the first-release shape (one complete module on a full engine) is a legitimate consequence of that stance. The original YELLOW weaknesses have been partially resolved by the follow-up scan: (a) differentiation is now articulated with a concrete gap — no Arabic incumbent does guided *text*-coding; (b) the competitive landscape itself supplies third-party demand evidence — multiple players (ArabCode, funarabicgames) are actively serving Arabic kids' coding, which the owner's "no real alternative" underestimated in both directions. Remaining risk stays honest: demand is still indirectly evidenced (competitors exist, not that users will adopt *this* product), and the moat is positioning, not technology.

## Next step

GREEN → proceed to `/write-spec Arabic Grasshopper — Learn to Code in Arabic` when the owner is ready. The PRD must pin: (1) the differentiation statement above as positioning, (2) concrete Q4 kill thresholds (e.g., active-user and module-completion numbers ~3 months post-launch), (3) the first-release module scope, and (4) a content-authoring plan, which is the heaviest ongoing cost.
