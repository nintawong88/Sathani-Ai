# WEBSITE_PLAN.md
**Sathani AI · สถานี AI** — consolidated website plan · v1.0
Supersedes the site-structure section of `ai-learning-hub-plan.md`. Incorporates comparison Rev 5 (A1–A15, B1–B12).

---

## 1. Sitemap

```
/  (Thai default; /en/ mirror)
├── /find-your-line          3-tap placement → literacy check → recommendation   [built]
├── /lines/{slug}            6 line overviews                                    [2 built: operators, second-act]
│   └── /lines/{slug}/{n}    Station pages: Watch·Try·Make·Show                  [8 built]
├── /about                   Founder story + case→module index (A2, A10)         [Phase 1]
├── /blueprints              Operations AI Blueprints library (A2, B12)          [Phase 1]
├── /patron                  Ladder + THB pricing + deck request (A3, A13)       [Phase 1]
├── /safety                  Scams · school integrity · workplace data policy    [Phase 1]
├── /facilitators            Guides + printable session kits                     [Phase 1]
├── /toolbox                 Tool cards, free/paid, TH availability              [Phase 2]
├── /glossary                Plain-language TH/EN terms                          [Phase 2]
├── /showcase                Opt-in, moderated, 18+ faces/names only             [Phase 2]
├── /journal                 Build-in-public log (A9)                            [Phase 0]
└── /pilot                   Pilot programme page + impact reports (A7)          [Phase 2]
```

Removed vs. earlier drafts, per decision register: no /pricing for individuals (C7), no /careers or jobs matching (C1/C9), no /community forums (B7 → facilitator LINE OpenChat instead), no AI playground page (B3 → alternate prompts inside stations).

## 2. Page briefs (new pages only)

**/about** — Kimi's TH structure condensed: hero thesis line ("ช่องว่าง…ที่คนไทยเชื่อว่าตัวเองทำได้"), 1994→2026 timeline, track-record table (28 yrs, 25,000 pallets, ฿280M, 1,200+ stores, 7 apps), why-I-built-this stories (Makro supervisor, Minor manager, Khon Kaen), case→module index, contact. No hiring section until pilot report exists (B9).

**/blueprints** — Gemini's card pattern: 6–10 real operational prompt templates (SAP eWM variance, cold-chain vision-AI work order, reorder requisition, + PIC-sourced additions). Each card: scenario, full prompt, expected output, safety note. Free, no email gate — this page IS the B2B lead magnet. Community submissions behind review gate in Phase 3 (B12).

**/patron** — Ladder table (community/bronze/silver/gold) with THB anchors adapted from Kimi (institutional ฿48k–300k/yr by seats; white-label ฿100k–500k — validate before publishing). Impact-loop line (A5). One-field form → Corporate Patronage Deck (A13). Partner/patron asks folded in (B9). Explicit "what we never sell": learner access, lesson placements.

**/journal** — dated build-in-public entries; doubles as sponsor progress evidence.

## 3. Cross-cutting requirements (unchanged, restated as build gates)

- WCAG 2.2 AA · persistent toolbar (text ก/ก+/ก++, contrast, motion, TH/EN) · Thai body font (IBM Plex Sans Thai / Noto Sans Thai) · print-PDF per station · ฿4,000-Android-on-4G budget
- PDPA architecture: no learner accounts (MVP), facilitator-owned accounts for minors, live data ledger on any form, no health data ever, 18–20 learning-only gate, 21+ for CV/employer/jobs directory
- Station template: Watch → Try → Make → Show; safety stations non-skippable; prompt copy-buttons; "if stuck" blocks; B10 static rubric on Operators/Builders Try steps

## 4. Tech (unchanged from decision register)

Astro + MDX content collections · Tailwind + CSS custom properties · Astro i18n (/th/, /en/) · localStorage progress, no accounts · Netlify/Vercel · Plausible (cookieless) + 3 demand events (A12: line_selected, signup, station_complete) · Supabase deferred to Phase 3 with facilitator accounts (B8).

## 5. Phases (durations per A18 — realistic for a founder running PIC + CWx in parallel)

| Phase | Duration | Scope | Exit criterion |
|---|---|---|---|
| **0** | 1–2 wks | GitHub org + PMO scaffold, VISION.md + IMPACT.md commit #1, existing deliverables filed against the 20-doc list (A8/A15, ≤10 pages each per A17) · /journal started (A9) · signup + analytics on prototypes, optional low-budget FB ads to feed it (A12) · domain + DBD name check · counsel brief sent | Repo live; demand data flowing; name locked |
| **1 — MVP** | 4–6 wks | Astro build of built content + /about /blueprints /patron /safety /facilitators · 8 videos shot per production brief · grant + dev-credit applications (A13) · Operators case-study rewrite (A6/A10) | Site live TH/EN; SA+OP lines complete with video |
| **2** | 8–12 wks | Lines 3–6 in demand-ranked order (A12 data decides) · SME track (B4) · capstone certificates (B1) · Second Career module (A10) · /toolbox /glossary /showcase /pilot · related-station links (B11) | All 6 lines live; first pilot running |
| **3** | 12–16 wks | White-label kit (A4) · facilitator accounts on Supabase/RLS (B8) · facilitator LINE community (B7) · scoped AI helper + Prompt Trainer, 20+ (B2/B10) · community blueprints (B12) · hiring page after pilot report (B9/A7) | First institutional patron signed |

## 6. KPIs (measured, never projected — per C8)

Phase 0–1: signups per line · placement-check completion rate · station-1 → station-4 progression. Phase 2: capstones submitted · pilot report delivered (100 learners, 5 facilitators). Phase 3: patrons signed · free learners funded per patron baht.

## 7. Open items

1. Domain + DBD trademark check on **Sathani AI / สถานี AI** (this week — gates GitHub org name)
2. Counsel sign-off: 18–20 carve-out, facilitator-as-data-subject, privacy notice
3. Validate THB price anchors with 2–3 friendly CFOs before /patron publishes
4. SA2 fraud-content review by an elder-fraud practitioner before video publishes
