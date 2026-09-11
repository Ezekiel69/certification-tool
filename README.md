# Certification Decision Assessment

An interactive, single-page web tool that helps German e-commerce SMEs decide whether to **pursue, keep, or reconsider** a trust-mark certification (e.g. Trusted Shops), based on the decision logic developed in a master's thesis on certification and online reputation.

**Live demo:** https://ezekiel69.github.io/certification-tool/

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [How It Works](#how-it-works)
- [Decision Logic](#decision-logic)
- [The Six Outcomes](#the-six-outcomes)
- [Optional Module: Certification Type & Quantity](#optional-module-certification-type--quantity)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started Locally](#getting-started-locally)
- [Deployment](#deployment)
- [Academic Grounding](#academic-grounding)
- [Author](#author)
- [Citation](#citation)
- [License](#license)
- [Disclaimer](#disclaimer)

---

## Overview

This tool distills a four-question, branching decision tree into a fast, self-contained assessment: **four questions, about 60 seconds, one of six tailored recommendations.** It requires no installation, no account, and no backend — it is a single static HTML file that runs entirely in the browser. Three of the six results also offer an optional, collapsed deep-dive module on certification type and quantity — opt-in, so it never lengthens the core experience for someone who just wants the fast answer.

It exists to translate an academic finding into a practical decision aid: certified SMEs are considerably more concentrated in the top Trustpilot rating band, yet certification status alone does not statistically predict rating once firm size and review activity are controlled. What actually matters is *how* a firm approaches the certification decision — which is exactly what this tool is built to surface.

## Features

- **Four-question branching assessment** — no question a user sees is irrelevant to their situation; the path adapts after every answer. This core experience is unchanged from the tool's original design.
- **Six tailored outcomes (A–F)** — each with a clear recommendation, a reasoning paragraph, and tags linking back to the source thesis section.
- **Optional deep-dive module** — available from the result screens for Outcomes A, B, and E specifically. Covers certification type (Trusted Shops vs. EHI Geprüfter Online-Shop) and certification quantity (single vs. combined), each grounded in specific thesis sections and clearly labeled as literature-based guidance rather than a tested finding. Collapsed by default; opening it is the user's choice.
- **Progress trail** — pill-shaped chips accumulate at the top of the screen, showing every answer given so far at a glance.
- **Back navigation** — every question (after the first) can be revisited without losing prior answers.
- **Print / save result** — generates a clean, printable version of the final recommendation.
- **Start over** — resets the assessment instantly.
- **Zero dependencies beyond optional web fonts** — falls back gracefully to system fonts if offline.
- **Fully responsive** — works on desktop, tablet, and mobile.

## How It Works

1. **Landing screen** — introduces the assessment and its grounding, with a single "Begin assessment" button.
2. **Question 1 (all users):** *Is your SME currently certified?* This single answer determines which of the two branches follows.
3. **Not-certified branch:**
   - Q2: Is your customer base anonymous/transactional, or are you expanding into new markets?
   - Q3: Do you have dedicated capacity to manage certification's administrative burden?
4. **Certified branch:**
   - Q2: Do you measure certification's contribution to your reputation or sales?
   - Q3: Does that evidence show a measurable return?
5. **Result screen** — one of six lettered outcomes, with the full reasoning and topic tags. For Outcomes A, B, and E, an optional "Certification type & quantity guidance" panel can be expanded for further, literature-grounded input on which certification to pursue or whether a second is worth adding.

There is no scoring system and no hidden weighting. It is a fixed decision tree: the same answers always produce the same recommendation.

## Decision Logic

```
                         Is your SME currently certified?
                         /                              \
                       NO                               YES
                       /                                   \
   Anonymous/transactional customer base,          Do you measure certification's
     or expanding into new markets?                 contribution to reputation/sales?
       /                    \                              /                    \
     NO                    YES                           NO                    YES
      |                      |                             |                      |
  Result C          Dedicated capacity to           Result D          Does the evidence show
  (keep existing      manage admin burden?         (start measuring     a measurable return?
   strengths)              /      \                 before renewal)        /          \
                         YES      NO                                     YES          NO
                          |        |                                      |            |
                     Result A  Result B                              Result E     Result F
                    (pursue,   (build capacity                      (continue,   (reassess,
                     measure    first, revisit                       leverage      don't drop
                     from day1)  later)                               evidence)    reflexively)
```

This is exactly the tool's original four-question, six-outcome structure — unchanged. Certification type and quantity are handled separately; see the next section.

## The Six Outcomes

| Key | Recommendation | Grounding |
|-----|-----------------|-----------|
| **A** | Pursue certification — and build in measurement from day one | Environmental · Organisational · Section 8.1 |
| **B** | Build capacity first — then revisit certification | Organisational · Section 8.2 |
| **C** | Keep investing in your existing trust-building strengths | Environmental · Section 5.4.2 |
| **D** | Start measuring before your next renewal decision | Technological · Section 8.1 |
| **E** | Continue certification — and put your evidence to work | Technological · Section 8.1 |
| **F** | Reassess — but don't assume you should drop it | Institutional · Section 6.4 |

All six outcomes rest on this thesis's tested empirical results (Chapter 5). This is the tool's original structure, unchanged.

Full reasoning text for each outcome is in the tool itself (`index.html`) and in the accompanying Word documentation.

## Optional Module: Certification Type & Quantity

Outcomes A, B, and E each carry a collapsed "Certification type & quantity guidance" panel — closed by default, so it never lengthens the four-question core experience. Opening it surfaces two separate, literature-grounded questions this thesis's Chapter 5 results do not test directly:

- **Type** (Outcomes A and B, i.e. before certifying): a two-way prompt — consumer-facing trust and reviews, or broad operational/legal compliance depth — pointing toward Trusted Shops or EHI Geprüfter Online-Shop respectively, based on Section 3.2's comparison of the two schemes. TÜV SÜD is noted as discontinued and not a live option.
- **Quantity** (Outcome E, i.e. once a return is already established): a short two-step check — which certification is currently held, then whether a second would fill a documented gap or mostly duplicate the first. A "duplicate" answer favors staying single; a "distinct need" answer names the other studied scheme as the more plausible addition, or, if both are already held, points to a needs-based method rather than a named third option, since this thesis studied only these two.

This module offers Level 2/3 guidance — practitioner-oriented strategic depth grounded in literature and reasoned synthesis (Section 2.1.2's diminishing-returns literature; Section 2.2.1's Kirmani & Rao, 2000 signal-type distinction; Section 3.2's Trusted Shops/EHI comparison), complementing the core recommendation's tested Chapter 5 evidence. This distinction is labeled inside the panel itself. It is documented in full in Section 8.4.5 of the thesis, kept deliberately separate from Table 8.1 and Figure 8.1 so the two evidentiary tiers are always clear.

## Tech Stack

- **HTML5** — single-file structure
- **CSS3** — custom properties, no framework or build step
- **Vanilla JavaScript** — no libraries, no dependencies, no bundler
- **Google Fonts** (optional, loaded via CDN with system-font fallback)

No package manager, no build process, and no server-side code are required to run or deploy this project.

### Architecture — config-driven, not hardcoded

The assessment logic is deliberately split into two layers inside `index.html`:

1. **`ASSESSMENT_CONFIG`** — a single JavaScript object holding every question, answer option, branch target, result, and piece of intro/footer copy. This is the *only* section intended to be edited for routine maintenance.
2. **Engine** — generic rendering/routing code below the config that walks whatever tree `ASSESSMENT_CONFIG` describes. It has no knowledge of certification, SMEs, or any specific question, so it never needs to change when the content does.

This keeps the decision logic itself static and deterministic (it still reflects the exact thesis findings — no invented scoring or weights), while making the tool's *content* fully data-driven, so it can be updated, extended, or reused as a template for a different assessment entirely, without touching any rendering code. See the comment block at the top of the `<script>` section in `index.html` for step-by-step instructions on editing a question, adding a new one, or adding a new outcome.

## Project Structure

```
.
├── index.html    # The entire application: markup, styles, config, and engine
└── README.md     # This file
```

Inside `index.html`, the `<script>` section is split into `ASSESSMENT_CONFIG` (content — edit this) and the engine (generic logic — shouldn't need edits). See [Tech Stack](#tech-stack) above.

## Getting Started Locally

No installation required.

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

Then simply open `index.html` in any modern browser — by double-clicking it, or running:

```bash
# macOS
open index.html

# Windows
start index.html

# Linux
xdg-open index.html
```

## Deployment

This project is deployed via **GitHub Pages** directly from this repository.

1. Go to **Settings → Pages** in this repository.
2. Under **Build and deployment**, set **Source** to `Deploy from a branch`.
3. Set **Branch** to `main` and folder to `/ (root)`.
4. Save. GitHub publishes the site within 1–2 minutes at:
   `https://<your-username>.github.io/<repo-name>/`

Any future push to `index.html` on the `main` branch updates the live site automatically — no rebuild step needed.

## Academic Grounding

This tool operationalizes the decision framework developed in the following master's thesis:

> **E-Commerce Certification for German SMEs: A Study of Online Reputation and the Perceived Value of the Certification Process**
> Master's Thesis, MBA Programme (SEPT), University of Leipzig
> Author: **Zek** · Supervisor: Prof. Dr. Rainer Alt

The underlying research is grounded in the **Technology–Organization–Environment (TOE) framework** (Tornatzky & Fleischer, 1990) and an explanatory sequential mixed-methods design combining a quantitative comparison of certified and non-certified German SMEs with qualitative interviews of SME managers.

**Scope note:** the thesis's certified sample for its empirical results (Chapter 5) is defined exclusively as Trusted Shops holders (TÜV SÜD's scheme was discontinued in 2021; EHI Geprüfter Online-Shop was excluded from that sample due to overlap with Trusted Shops holders). All six core outcomes are evidence-based specifically for Trusted Shops, not for e-commerce certification generally. The optional module (see above) does name Trusted Shops or EHI specifically when relevant, but rests on Chapter 3's comparative description of the two schemes plus the certification-signaling literature, not on Chapter 5's tested results — this distinction is stated inside the module itself.

## Versioning

`index.html` tracks its own version and last-updated date inside `ASSESSMENT_CONFIG.META` (`version`, `lastUpdated`). Bump these whenever you edit a question, branch, or outcome, so anyone reading the source later can see at a glance whether they're looking at the version behind a given screenshot, citation, or printed result.

| Version | Date | Change |
|---------|------|--------|
| 2.2.0 | 2026-09-11 | Redesigned the certification type/quantity feedback response for proportionality after defense committee input. Reverted the core assessment to its original four-question, six-outcome structure (Outcomes G1/G2/H and the mandatory identification/scope questions from v2.1.0 removed from the main flow). Certification type and quantity guidance now lives in an optional, collapsed panel on Outcomes A, B, and E only, opened at the user's choice, so the core "four questions, about a minute" experience is unchanged for anyone who does not need it. Documented in full, and clearly labeled Level 2/3 evidence, in a new Section 8.4.5 of the thesis. |
| 2.1.0 | 2026-09-10 | (Superseded by 2.2.0.) Added certification type/quantity questions directly into the main assessment flow, extending it to five questions and nine outcomes. Reverted after review found this changed the tool's core value proposition and blended two evidentiary tiers into the main tree. |
| 2.0.0 | 2026-08-26 | Refactored from hardcoded per-question functions to a config-driven engine (`ASSESSMENT_CONFIG` + generic renderer). No change to questions, branching, or outcomes. |
| 1.0.0 | 2026-08-26 | Initial release: four-question branching assessment, six outcomes. |

## Author

**Zek**
MBA Candidate, SEPT Programme, University of Leipzig

This tool, its decision logic, and all accompanying documentation were authored by Zek as an applied companion to the master's thesis research referenced above. All rights to the underlying research and its findings remain with the author.

## Citation

If referencing this tool or the research it is based on, please cite:

```
Zek. (2026). E-Commerce Certification for German SMEs: A Study of Online Reputation
and the Perceived Value of the Certification Process [Master's thesis, University of
Leipzig, SEPT Programme].
```

## License

© Zek. All rights reserved.

This project is shared for portfolio, academic, and demonstration purposes. Please contact the author before reusing, redistributing, or adapting the tool or its underlying research content.

## Disclaimer

This tool is a decision-support heuristic, not a validated predictive instrument or professional advice. See the source thesis, Figure 8.1 and Section 8.4, for the full grounding and boundary conditions of the underlying findings.
