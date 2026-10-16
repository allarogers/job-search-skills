---
name: job-fit
description: Rates a pasted job description against the user's resume and project descriptions. Classifies the JD by level and role (Technical Product Management, Software Product Management, Technical Program Management, Technical Project Management), scores must-haves and nice-to-haves, and outputs a fit percentage with a color-coded requirements table. Trigger when the user says "job-fit" or "rate this fit" and pastes a job description.
---

# job-fit

## Purpose
Take a pasted job description (JD), classify it by level and role, and rate the user's fit using only evidence from the user's own background. Rate neutrally. Do not factor in the user's wishes or ambitions for the role.

## Output format overrides
This skill's output format replaces the user's general conversation preferences (revise/short/long). Do not add the bottom line, confidence, timestamp, or format reminder sections. Stay concise and do not praise the user or soften the findings.

## Step 1: Load background (do this first)
1. Read the user's resume(s) and project descriptions from project context and the connected local folder.
2. If none can be found, stop and ask the user where they are. Do not rate from assumptions.
3. Use only what is written in the background materials. Never infer experience that is not documented. If evidence is thin, rate it low and let the follow-up questions surface more.

## Step 2: Classify the JD

### Role definitions (use the decision rules below)
- **Technical Product Management (TPdM):** Owns the what and why of a technical product: platform, API, infrastructure, developer tooling, data/ML. Customers are often developers or internal engineering teams. Requires deep technical fluency (architecture, APIs, systems tradeoffs). Success measures: adoption, platform health, developer experience, roadmap outcomes.
- **Software Product Management (SwPM):** Owns the what and why of a software product, typically end-user or business-facing (SaaS, apps). Emphasis on customer and market discovery, UX, pricing/packaging, go-to-market. Technical depth is moderate. Success measures: revenue, retention, engagement, market share.
- **Technical Program Management (TPgM):** Owns the how and when across multiple teams or projects delivering a technical outcome. Manages dependencies, cross-team risk, architecture-level tradeoffs, release readiness. Does not own product strategy or the roadmap's priorities. Success measures: delivery predictability, cross-team execution, risk reduction.
- **Technical Project Management (TPjM):** Owns plan, schedule, scope, budget, and risks for a single project or bounded set of deliverables with a defined end. Coordinates tasks and stakeholders. Narrower scope than program management. Success measures: on-time, on-budget, in-scope delivery.

### Role decision rules
1. Who owns prioritization and the roadmap? If the role decides what gets built and why, it is a Product role (TPdM or SwPM). If it drives delivery of what was already decided, it is Program or Project.
2. Product roles: if the customer is developers or internal engineers and the product is a platform/API/infrastructure, choose TPdM. If the customer is an end user or business buyer and the product is an application, choose SwPM.
3. Delivery roles: if the scope spans multiple interdependent teams or projects and involves ongoing coordination, choose TPgM. If it is a single bounded project with a defined deliverable, schedule, and budget, choose TPjM.
4. If rules leave two roles equally plausible, list both (maximum two). Otherwise list the single best match.

### Level definitions (extended from the user's PM table to all four roles)
For Program and Project roles, apply the same scope ladder with "product" replaced by "program" or "project."

| Level | Track | Scope (standardized) | Plans ahead for |
|---|---|---|---|
| Senior | IC | Owns a product area, large feature set, or program/project end to end. Works independently. Influences within one team and adjacent partners. | 6-12 months |
| Lead | IC (or team lead without direct reports) | Owns a multi-team product, program, or complex cross-functional initiative. Mentors others, sets team standards, often informally leads 1-3 people. Equivalent to Staff at some companies. | 12 months |
| Staff | IC | Owns a product line, platform, or multi-team program portfolio. Resolves ambiguity and sets strategy for a large problem space. Influences without authority at director level. | 1-2 years |
| Principal | IC | Shapes strategy across a business unit or the company with company-level or market-level impact. Executive advisor. Sets the craft and standards. Peer of a Director. | 2-3+ years |
| Manager | Mgmt | First people-management level. Manages 2-5 people, coaches them, accountable for an area's outcomes. | 6-12 months |
| Sr. Manager | Mgmt | Manages a larger team or several managers/senior ICs. Owns a line's strategy, roadmap or delivery plan. Hiring and performance management. | 12 months |
| Associate Director | Mgmt | Owns a portfolio through managers. Builds the portfolio business case and aligns with peer functions. Not used at all companies. | 1-2 years |
| Director | Mgmt | Owns strategy, P&L or business outcomes, and org design for an area. Leads managers, presents to executives. Sets vision, headcount, and budget. | 2-3 years |

### Level rules
1. If the JD title or text states a level, use it. Do not override or correct the title.
2. Compare the JD's actual scope (team count, planning horizon, people management, executive exposure, P&L) against the table.
3. If the actual scope aligns better with a different level than the title, keep the title but note the divergence in the classification line (Line 3).
4. If no level is stated, infer it from scope using the table.
5. All eight levels in the table are valid classifications. Manager, Sr. Manager, and Associate Director are not out of scope.

## Step 3: Extract requirements
1. If the JD has a bulleted requirements list, use it. If not, mine the full text for requirements.
2. Extract all requirements, including implicit ones (years of experience, seniority, domain, scope, leadership).
3. Classify each as must-have or nice-to-have:
   - "required," "must," "minimum," "basic qualifications" = must-have
   - "preferred," "plus," "ideal," "bonus," "nice to have" = nice-to-have
   - Unlabeled items default to must-have

## Step 4: Rate each requirement
Rate each against the user's background evidence:
- **Strong:** direct, clear, documented experience at the required scope.
- **Medium:** related or partial experience, or similar experience at a smaller scope or different context.
- **Low:** no documented evidence, or only tangential evidence.

## Step 5: Score
Points per requirement:

| Rating | Must-have | Nice-to-have |
|---|---|---|
| Strong | 1.00 | 0.50 |
| Medium | 0.50 | 0.25 |
| Low | 0 | 0 |

Calculation:
- Must-have points = sum of must-have points.
- Bonus points = sum of nice-to-have points.
- Fit % = (must-have points + bonus points) / (number of must-haves) x 100, rounded to the nearest hundredth.
- Over 100% is acceptable.

Example: 8.5 of 10 must-haves + 0.75 bonus = 9.25 / 10 = 92.50%.

## Output format (follow exactly)

**Line 1:** `Fit: XX.XX%` followed by the raw breakdown, e.g. `(Must-haves: 8.50/10; Bonus: +0.75)`

**Line 2:** 1-3 sentences explaining the rating.

**Line 3:** `This job most closely aligned with the following classification: [Level] [Role]` (maximum two classifications; one unless two fit equally). If the title's level differs from the scope-based level, add: `Title says [X]; scope aligns with [Y].`

**Requirements table:**

| Requirement | Type | Match | Evidence from your background |
|---|---|---|---|

- Type: Must-have or Nice-to-have
- Match uses color-coded labels: 🔴 Strong, 🟡 Medium, 🔵 Low
- Evidence: a short description or example from the user's resume or projects explaining the rating. For Low, state what is missing.

**Warnings (only if applicable):** list hard mismatches the percentage does not capture, such as a required security clearance, specific degree, license, location, or work authorization the background does not show. Keep to one line each.

**Follow-up questions (below the report):** for each Low-rated requirement, ask up to 5 questions probing for experience that could raise the rating. Ask fewer if it is clear there is no relevant experience. Prioritize must-haves first. Group by requirement and number the questions.

## Rules
- Never invent or embellish background evidence.
- Do not correct JD titles.
- Do not rate the role against the user's preferences or ambitions.
- No praise, no hedging, no filler.
