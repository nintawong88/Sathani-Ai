# AI Learning Hub — Program Plan & Site Structure

**Product concept:** One public website that routes any learner — a 9-year-old, a Mathayom student, a university job-seeker, a warehouse supervisor, someone managing a chronic illness, a 68-year-old retiree — onto a *line* that fits their life, and moves them station by station to the same destination: **using AI confidently and safely**.

**Organising metaphor:** a transit route map. Six colour-coded lines, four stations each, one shared terminus. Universally legible (BTS/MRT literacy in Thailand), works bilingually, and makes "transfer between lines" a natural product feature rather than a support ticket.

**Assumption stated up front:** "real ill" is read as two distinct groups — (a) learners with limited energy from chronic illness or homebound status, and (b) retirees. They are given separate lines because their constraints differ: one is an *energy budget* problem, the other is a *confidence and fraud-exposure* problem. Confirm or collapse.

---

## 1. Tier design

Every line shares the same spine — **Watch → Try → Make → Show** — but the *dose*, the *content*, and the *safety layer* differ. Line thickness on the map encodes weekly minutes, so the commitment is visible before anyone clicks.

| Line | Who | Dose | Cadence | Capstone |
|---|---|---|---|---|
| **Sprouts** (amber) | Ages 7–12, adult beside them | 15 min | 3×/wk, 4 wks | 3-page illustrated story made with a grown-up |
| **Explorers** (rose) | Ages 13–17, school | 25 min | 4×/wk, 5 wks | Personal study helper + 60-sec explainer video |
| **Builders** (violet) | 18–24, employability | 45–60 min | 5×/wk, 4 wks | Deployed agent + case study + public post |
| **Operators** (teal) | Working professionals | 20 min | 5×/wk, 8 wks | One automation running weekly + before/after time log |
| **Adaptive Pace** (forest) | Limited energy, chronic illness, homebound | 10 min | No schedule, no streaks | Personal admin assistant (appointments, letters, forms) |
| **Second Act** (copper) | 60+, retirees | 30 min | 2×/wk, 6 wks | A written life-story chapter + teach one friend |

### Station sequences

**Sprouts** — 1. A machine that guesses · 2. Ask a better question · 3. Make something together · 4. Show your family
**Explorers** — 1. How it actually works · 2. Honest use at school · 3. Build a study helper · 4. Spot the fake
**Builders** — 1. Prompting as a skill · 2. Tools and data · 3. Build an agent · 4. Ship it publicly
**Operators** — 1. Find your five repeat tasks · 2. Rewrite one task · 3. Automate a two-step workflow · 4. Prove the hours saved
**Adaptive Pace** — 1. One task, ten minutes · 2. Speak instead of type · 3. An assistant for admin · 4. Share on your own terms
**Second Act** — 1. Your first conversation · 2. Spot the scam · 3. A helper for daily life · 4. Your story, written down

### Safety layer (non-negotiable, differs per line)

- **Sprouts** — adult co-pilot required, no learner accounts, curated prompt cards only (no open free-text chat), no personal information rule, screen-time cap.
- **Explorers** — academic integrity module gates Station 3; deepfake, consent and digital-footprint module mandatory; no companion/romantic use cases anywhere in content.
- **Builders** — API key hygiene, cost caps, prompt-injection basics, licence/attribution of scraped data.
- **Operators** — employer data policy checkpoint before Station 3, no customer PII in prompts, human sign-off gate on every automation.
- **Adaptive Pace** — explicit boundary: the roadmap gives no medical advice and does not replace a clinician. Low-stimulation mode default. No streaks, no "you've been away" nudges.
- **Second Act** — fraud defence taught *before* capability (Station 2 of 4). Never enter bank, ID card, or OTP details. "Ask a family member" checkpoint before any payment or download.

### Interchanges
Explorers → Builders (on leaving school) · Builders → Operators (on getting hired) · Operators → Second Act (on retiring) · Any line → Adaptive Pace (temporarily, without losing progress). Transfers preserve completed stations.

---

## 2. Site structure

```
/                        Route map + find-your-line
/find-your-line          3-question placement (age band, weekly time, goal)
/lines/{slug}            Line overview: dose, stations, capstone, safeguards
/lines/{slug}/{n}        Station page: Watch · Try · Make · Show
/toolbox                 Tool cards — free vs paid, device needs, TH availability
/safety                  Scams, school integrity, privacy, workplace data policy
/facilitators            Guides + printable session cards for parents, teachers, HR, community centres
/glossary                Plain-language TH/EN terms
/showcase                Learner projects (opt-in, moderated, no minors' faces or names)
/about
```

### Station page template (identical across all six lines)
1. **Watch** — 3–6 min video, captioned TH + EN
2. **Try** — guided exercise with the exact prompt supplied
3. **Make** — the learner's own version, one artifact
4. **Show** — proof step: family, class, colleague, or the Showcase

### Content model
```json
{
  "line": "operators",
  "station": 3,
  "title": { "en": "Automate a two-step workflow", "th": "ทำงานสองขั้นให้อัตโนมัติ" },
  "minutes": 20,
  "watch": { "url": "", "captions": ["th", "en"], "duration": 340 },
  "try": { "prompt": "", "tool": "claude|gemini|chatgpt", "expected_output": "" },
  "make": { "deliverable": "", "rubric": [] },
  "show": { "channel": "colleague|class|family|showcase" },
  "safety_gate": "employer_data_policy",
  "prerequisites": ["operators/2"],
  "accessibility": { "voice_first": true, "print_pdf": "" }
}
```
Content lives as MDX with this frontmatter — writers edit text, not code.

---

## 3. Accessibility and language (build requirement, not a phase 2 feature)

- WCAG 2.2 AA baseline; keyboard-complete; visible focus; `prefers-reduced-motion` respected.
- Persistent toolbar: text size (100/112/125%), high contrast, reduce motion, TH/EN.
- Thai is the primary language; English secondary. Font stack must carry Thai (IBM Plex Sans Thai or Noto Sans Thai) — no Latin-only display faces on body copy.
- Every station downloadable as a print-friendly PDF for Second Act and Adaptive Pace learners with poor connectivity.
- Voice-first path through Adaptive Pace: every Try step has a spoken-prompt alternative.
- Target: usable on a ฿4,000 Android phone over 4G.

---

## 4. Technical recommendation

| Layer | Choice | Why |
|---|---|---|
| Framework | Astro + MDX content collections | Static output, near-zero JS, content authored in Markdown by non-developers |
| Styling | Tailwind + CSS custom properties | Text-scaling and contrast toggles are token swaps |
| i18n | Astro i18n routing (`/th/`, `/en/`) | Real URLs per language, indexable |
| Progress | `localStorage` only, no account (MVP) | No PII, no consent burden, no minors' data |
| Hosting | Netlify or Vercel free tier | Zero ops |
| Analytics | Plausible or Umami (cookieless) | PDPA-friendly |
| V2 auth | Supabase, facilitators only | Learners still stay anonymous |

**Deliberately not in MVP:** logins, certificates, payments, an LLM chat widget on the site itself. Each adds legal or moderation load disproportionate to its learning value.

---

## 5. Build phases

| Phase | Scope | Est. |
|---|---|---|
| **1 — MVP** | Home + route map + placement quiz + **two complete lines** (Operators, Second Act) + Safety + facilitator printables + TH/EN | 4 weeks |
| **2 — Full map** | Remaining four lines, Toolbox, Glossary, Showcase with moderation queue | 4–6 weeks |
| **3 — Cohorts** | Facilitator dashboard, cohort codes, printable certificates, group progress | 4 weeks |

Launch with two lines built properly rather than six built thinly. Operators and Second Act are the recommended first pair: the widest audience and the sharpest, most demonstrable outcomes.

---

## 6. Open decisions

1. Confirm the split between Adaptive Pace and Second Act, or collapse into one line.
2. Thai-first or English-first at launch?
3. Under-13 content — parent-facing only, or a child-facing UI with a parent gate? This drives the entire compliance surface.
4. Is the Builders line a front door to the existing 4-week intensive curriculum already in this project, or a separate lighter track?
5. Who moderates the Showcase, and at what daily volume?
