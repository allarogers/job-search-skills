---
name: "resume-tailor"
description: "Tailor the NEW Master Resume to a specific job after job-fit has run. Minimal edits: new summary headline, reordered or clarified bullets, JD keywords in Skills, emphasis matched to product, project, or program role."
---

# resume-tailor

## Purpose
Produce a tailored version of the NEW Master Resume for one job. The master is the foundation. Change only what the job needs. Do not rebuild the resume.

## Inputs
1. **NEW Master Resume** (project file). It is the base for format and content, and it wins over any other file on conflicts.
2. **Job description (JD)** from the conversation.
3. **Job-fit output** from earlier in the conversation: classification line, requirements table, Strong/Medium/Low ratings, warnings.
4. **New background detail the user gave in the conversation** after job-fit (answers to follow-up questions, extra context). Treat it as fact. Do not challenge it. Use it to lift Low/Medium requirements where it truthfully supports them.
5. **Master Additional Context** (project doc) and the Experience bank, for extra detail and for the guardrails below.

If the JD or job-fit output is missing, ask for it. If the master resume cannot be found, stop and ask. Do not tailor from memory.

## Truth rules
- The user is the source of truth on their experience. Challenge wording and formatting, not facts.
- Only use what is in the master, the Additional Context, or what the user said in this conversation. Never invent or inflate scope, metrics, tools, or titles.
- A JD keyword goes in only if the background supports it. If it does not, leave it out and list it under "Not added".
- Do not change titles, employers, or dates.

## Step 1: Build the tailoring brief (internal, do not print in full)
- **Role type** from the job-fit classification: Product (TPdM or SwPM), Program (TPgM), or Project (TPjM). If two are listed, lead with the first and blend lightly.
- **Level**: Director, Associate Director, Sr. Manager, etc. Level sets how much to emphasize team scale, org design, executive exposure, and multi-year strategy.
- **Top 5-8 JD priorities**, ranked, taken from the must-haves and the JD's repeated phrases.
- **Match map**: for each priority, where it already lives in the master (summary bullet, Natera bullet, earlier role, Skills) or what user-supplied detail covers it.
- **Exact JD keywords** worth mirroring (ATS), tagged supported or unsupported.

## Step 2: Invoke write-human
Invoke the write-human skill before drafting any resume text. Follow it for every line written or reworded: specific over generic, plain transitions, no stock phrases or intensifiers, light on em dashes, no templated rhetoric.

## Step 3: Edit, in this order

### Edit budget
Use the lightest edit that does the job. Escalate only when needed:
1. Leave the line alone.
2. Reorder clauses or reorder bullets so the JD-relevant point comes first.
3. Add a few words of clarity to bring out key experience (for example, name the scope, the stakeholder level, or the outcome the JD cares about).
4. Swap which detail leads, using material already in the master or the Additional Context.
5. Add a new fact the user supplied in this conversation.

Do not reword a line just to reword it. If a bullet already fits, keep it verbatim. Typical result: the headline and Skills updated, and a handful of bullets reordered or clarified. Keep the same section order, headings, bullet style, and page count as the master.

### A. Summary headline (the 2-3 lines before the bullets)
Rewrite it for this job. It should:
- Open with the identity the JD is hiring for (role type and level language, for example "Product leader" or "Technical program leader"), without claiming a title never held.
- Name the domain and the 2-3 things the JD cares about most, in the JD's vocabulary.
- Carry one concrete proof point (a number or scope) that the hiring manager will notice.
- Read as a person wrote it. No years of experience unless the JD asks for more than 15 (then "15+ years" is allowed). Never "20+ years".

Then adjust the summary bullets: reorder so the most JD-relevant lead, trim or merge only if page length requires, and tweak a few words where it sharpens fit. Keep bullet labels unless a JD term is a better label.

### B. Experience
Touch only bullets that map to a JD priority or that the role type de-emphasizes. Reorder bullets within a role when the JD calls for it. Apply the role-type lens below. Keep Natera as the main weight. For earlier roles, change at most wording order or a short clarifier.

### C. Skills
- Add critical JD keywords that the background supports, using the JD's exact wording where truthful (for example the JD says "cross-functional program governance" and the user has done it).
- Reorder categories and items so the JD's priorities come first. Rename a category only if the JD term fits better.
- Remove or demote nothing that could matter elsewhere unless space forces it.
- Respect proficiency limits in the guardrails.

### D. Early career, education, additional
Leave alone unless a JD requirement points at something here.

## Role-type lens

**Product (TPdM / SwPM)**: lead with the what and why. Vision, roadmap, prioritization method, build vs. buy, business cases, adoption and retention, commercial and customer partnership, outcomes and KPIs. TPdM: add platform and architecture fluency (microservices, Kafka, Temporal, APIs, SLAs, shared services). SwPM: add user and customer discovery, adoption, go-to-market, and commercial partnership.

**Program (TPgM)**: lead with the how and when across teams. Cross-team dependencies, release readiness, launch plans, risk and FMEA, governance and process standardization, quarterly planning alignment, executive status communication, on-time delivery across engineering, quality, regulatory, and operations. Present product decisions as context, not the headline.

**Project (TPjM)**: lead with plan, scope, schedule, budget, risk, and on-time delivery of bounded deliverables. Use specific projects with a start, an end, and a result (launches, migrations, tiger team deliveries, interface projects). Stakeholder coordination and scope control. Keep strategy language light.

For all three: management levels (Sr. Manager and above) should foreground team scale, hiring, coaching, org influence, and executive communication in proportion to the JD.

## Guardrails from the user's Additional Context (the user's in-conversation statements override these)
- Natera title: Associate Director, Technical Product Management. Dates Jan 2019 – Aug 2026, never "Present". DNA Direct title: Head of Technology. Do not use "IT Manager".
- Do not claim hands-on AWS, Azure, or GCP. Do not claim benchmarking against industry best practices.
- Snowflake: user-level. Figma: review and feedback only. Salesforce: admin-configuration. Tableau, Power BI, Veeva: very limited.
- Regulatory work (IVD, CLIA, 21 CFR Part 11, deep HIPAA) belongs to Natera only. Do not attach it to earlier employers.
- Not responsible for EHR interoperability at Natera. Tenet billing interfaces were not payer-facing. No wearables or hardware device experience.
- Never say "built and scaled the TPM organization". Use the team wording already in the master (3 to 14).
- Use "software" as the general descriptor, not "technical" or "digital". Say "test products" or "test product lines", not "clinical product". State growth as "company hypergrowth" without headcount numbers.
- Launch execution: choose the career-spanning wording or the Natera-focused wording (more metrics and regulatory) based on the JD.

## Step 4: Check before delivering
- Every claim traces to the master, the Additional Context, or the user's words in this conversation.
- Guardrails respected; no fact softened or inflated.
- Headline matches the JD's role type and level; Skills contain the supported must-have keywords.
- Format, section order, and page count match the master.
- write-human check: no stock phrases, no run of same-length sentences, em dashes minimal.
- Unchanged text is truly unchanged.

## Step 5: Deliver
- Build the resume in the master's layout and save it to the "aClaude Folder" on the user's computer. Name it `Alla Rogers - [Company] - [Role].docx` and also provide a PDF. Send the files in chat.
- In the reply, give a **change log only**, as short as possible:
  - Headline: old vs. new, one line each.
  - Bullets changed: location, then what changed (reordered, clarified, added) in a few words.
  - Skills: added, reordered.
  - **Not added** (keywords or requirements the background does not support, with the job-fit rating).
  - Any wording or format questions for the user to decide.
- No praise and no hedging. This skill's output replaces the general revise/short/long format: skip the bottom line, confidence, timestamp, and format reminder.

## Out of scope
Cover letters (separate request; write-human still applies), fit scoring (job-fit does that), and rebuilding the master resume.