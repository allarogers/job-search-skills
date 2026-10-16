---
name: n/a
description: claude prompts
purpose: go through all conversations in my job search Claude project to extract information I provided in addition the the background I gave in the context

---
# Prompt 1 - in every chat
Review this entire conversation. Extract every fact I gave you about my background that is NOT already in my master resume (Cowork_Master_Resume.pdf) or my Resume and Experience Bank ("my background"). Treat everything I said as factual. Do not challenge, soften, or infer. The content must describe my experience and the role I held at the time, not the job I was applying for. Use the target company and role only to name the file.

Capture:
- New experience: any role or engagement not in my background (for example, Meet4Trip product consulting between Medco and Certify Data Systems): employer/client, title, dates, scope, outcomes.
- New wins: accomplishments, metrics, or outcomes that surfaced when you asked me questions and I answered: result, numbers (revenue, users, cost, time, team size, percent change), what I did, how I did it.
- Clarifications: places where I expanded on, reframed, or corrected something in my background (scope, ownership, level of responsibility, how the work was done, who I influenced).
- Summary points: statements about who I am professionally, my positioning, themes, or value that belong in a resume summary.
- Core competencies: skills, methods, tools, frameworks, technologies, and leadership practices not in my background.

Exclude: your suggestions, resume drafts, cover letter text, and job description content.

Output format, in this order:
1. New summary points: bullets
2. New core competencies: bullets
3. Experience: one subsection per employer (exact name from my resume), one bullet per accomplishment or fact, my wording where possible, numbers preserved

Every bullet in all three sections ends with a designation:
🟢 AUGMENTS: adds to my background
🔴 CONFLICTS: contradicts my background, followed by one line stating the original item and the new version

If a section has nothing, write "None."

Save the output as a doc to the connected folder [fill in the folder name] on my computer named "Context - [Target Company] - [Target Role]" using project_write. If project_write is unavailable, save it to the connected folder [fill in the folder name] on my computer. If neither works, tell me so and print the full output in a single code block that I can copy.
