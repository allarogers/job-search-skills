# Building a Job Fit Assessment skill with Claude
## Initial Prompt to Claude
```
Help me create a skill called job-fit - it should take in a pasted job description and rate it against my professional background - my resume and my project descriptions.  It should specialize in the following matrix of roles:  level -- Director, Senior, Staff, Principal, Lead;  role - Technical Product Management, Software Product Management, Technical Program Management, Technical Project Management.  The title on the job description does not necessarily need to match the combination of these (ex: Director, Technical Product Management), but the skill should have an objective definition of each of these roles to be able to classify the job description and one or more of these roles for further evaluation against my background.  The output should be formatted as follows:  Line 1 - Percentage fit;  Line 2 - 1-3 sentence explanation for the rating reasoning; then an analysis table of position requirements, my level of match to the requirement (strong, medium, low) - color coded as red, yellow, blue respectively, and a short description / example from my background indicating the reason for the specific rating.  Ask me questions about this skill first, don't start writing the skill yet.  Once we've ironed out the details, I will ask you to generate a markdown file that I can use in a prompt to create a skill.
```

## Claude Q&A
### Questions
```
1. Background source: will you paste your resume and project descriptions into the skill file, attach them each time, or should the skill read them from a file or Drive path?
2. Role definitions: should I draft objective definitions for the four roles (distinguishing criteria like what/why vs. how/when, customer vs. delivery ownership) for you to edit, or do you have your own?
3. Level definitions: should I use a fixed ladder by scope, org size, and autonomy? Is “Lead” a people-lead or an IC lead? What is your relative ordering of Staff, Principal, and Director?
4. Multi-match: if a JD fits several role/level combinations, should the skill score each and report the best, or report one primary and one secondary?
Classification line: should the output show the identified role/level before Line 1, or stay strictly to your format?
5. Scoring: how should the percentage be weighted? Options are must-have vs. nice-to-have, equal weight per requirement, and a level mismatch penalty. Are there deal-breakers such as location, clearance, or domain?
6. Color coding: markdown can’t render color, so I’d use 🔴🟡🔵 emoji. Confirm red = strong, yellow = medium, blue = low. This is the reverse of the usual convention, so I want to be sure.
7. Requirements: should it extract all stated requirements, or the top N? Should it include implicit ones (years of experience, seniority, domain)?
8. Evidence gaps: when your background has no evidence for a requirement, should it rate “low” and say so, or never infer beyond what’s written?
9. Target level: do you have a target level or role it should favor, or rate neutrally?
10. Format preferences: should the skill ignore your revise/short/long preferences and always use the specified format?
```

### Answers
1. I will paste the job description when invoking the skill.  I plan to invoke it in a project that is connected to a local file folder + project context that contains information about my background and my resumes.  
2. Yes - please draft definitions
3. I have attached a markdown table showing levels.  It is likely that the level will be conveyed on the job description, which would trump the skill leveling work.
4. This is a good idea - include a classification line under Line 2 (new Line 3) display it as: "This job most closely aligned with the following classification:..."
5. Scoring should be based on must-haves; treat nice-to-haves as extra credit that would raise percentage. Strong fit gets 1 point, medium fit gets .5 points, low fit gets 0 poitns. So, for example if I am a strong fit for 8/10 must-haves, score 80%.  Then if I have a strong fit for any of the nice-to-haves, it is a .5 point towards the score, medium fit for a nice-to-have is a .25 point towards the score.  I understand with this scoring, it is possible to have more than 100%, and it's ok.
6. Confirmed
7. Extract all requirements: most of the job descriptions will have a bulleted reuquirements list.  If there is no list, then mine the text for requirements.
8. rate the requirement is low, explain why, and - below the report - ask a series of questions to probe the low matching requirements to give me a chance to increase that rating with supporting experience.
9. Rate neutrally - I will determine myself how I feel about the role in terms of my own wishes and ambitions
10. the skill should follow the format I specified for the skill and ignore my general format for conversations

### Markdown Table
_Note: for Question #3, I went to my Career Management project and promoted the following: 
```Help me define Product Management levels: senior, lead, staff, principal, manager, sr. manager, associate director, director - my understanding is that IC levels are: senior, lead, staff, principal (in the order of from least senior to most senior); Mgmt level are manager, sr. manager, associate director, director.  Is this correct? Could you please summarize the scope for each for a standardized defininition.```_

| Level | Track | Scope (standardized) | Typically Plans Ahead for |
|---|---|---|---|
| **Senior PM** | IC | Owns a product area or large feature set end to end. Sets the roadmap for it and works independently. Influences within one team and its adjacent partners. | 6–12 months |
| **Lead PM** | IC (or a team lead without direct reports) | Owns a multi-team product or a complex cross-functional initiative. Mentors PMs and sets team standards, often with informal leadership of 1–3 PMs. Equivalent to Staff at some companies. | 12 months |
| **Staff PM** | IC | Owns a product line or platform spanning several teams. Resolves ambiguity and sets strategy for a large problem space. Influences without authority at the director level. | 1–2 years |
| **Principal PM** | IC | Shapes strategy across a business unit or the company, with company-level or market-level impact. Acts as an executive advisor and sets the PM craft and standards. Peer of a Director. | 2–3+ years |
| **Manager of PM** | Mgmt | First people-management level. Manages 2–5 PMs, coaches them, and is accountable for a product area's outcomes. | 6–12 months |
| **Sr. Manager** | Mgmt | Manages a larger team, or several managers or senior ICs. Owns a product line's strategy and roadmap, and does hiring and performance management. | 12 months |
| **Associate Director** | Mgmt | Owns a portfolio of related products through managers. Builds the portfolio P&L case and aligns with peer functions. Not used at all companies. | 1–2 years |
| **Director** | Mgmt | Owns the strategy, P&L or business outcomes, and org design for a product area. Leads managers and presents to executives. Sets vision, headcount, and budget. | 2–3 years |


