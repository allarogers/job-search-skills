
# Job Search Skills Toolkit for AI Assistants

## TLDR: What's in it for you?
A Claude skills toolkit that took me from **4-6 hours per application** to **40 minutes** per application, retaining my resume voice and the accuracy of my background.

| **Skill** | **Purpose** | **Input** | **Output** |
|---|---|---|---|
|[Job fit assessment](src/job-fit.md)| Compares your background to the pasted job description to tell you how your experience aligns to requirements | job description + your background context (see more below) | % fit for the job, review of strengths and gaps that prompts a discussion to narrow the gaps|
|[Tailor resume skill](src/tailor-resume.md)| Tailors your resume to the job description | Job description + your background context + chat context from the job fit conversation | Tailored Resume as .pdf and .docx |
|[ATS Screener](src/ats-screener.md)|Checks how your application would do against a potential ATS when submitted<sup>1</sup>.|job description + tailored resume + tailored cover letter (optional)|ATS rating and an overview of various criteria|

<sup>1</sup> this is not an actual ATS, it's a hypothetical scoring mechanism I put together with Claude

> **Bonus skill**: [Write human](src/write-human.md) - Makes your LLM avoid the obvious 'AI-written-content' patterns

## To use these:
1. Install the skills: download the .md files listed above and ask your Claude to install each skill one-by-one - it will show you a card to review the content and install
2. Set up a project with your master resume and experience narrative
2. In the project instructions, add "invoke write-human skill"
3. For each job:
    1. /job-fit
    2. /resume-tailor
    3. /ats-screener

***To learn about my journey to create these, read on...***

## How it started

I have been using Claude extensively in my job search.  

1. I created a Claude project called Job Search
2. Built the project context
    1. My cleanest, best resume for structure and format
    2. Supplemental narrative of what I had done in each of my positions for context.


For each new job I found, I would...:
1. Create a new chat in my Job Search project
2. Paste the job description to discuss my fit
3. Tailor my resume / cover letter by giving relevant context to Claude and iterating on each resume section until it was perfect

And... ***each application would take me 4-6 hours***! 

### The conflict
I told myself that it's taking so long because I'm taking my time to _truly tailor my resume_ for jobs that seem like the _perfect fit_; in this market, it's about quality, not quantity.

Yet, in the back of my head, I still had the nagging question: 
>If AI is supposed to make things easier, why is it still taking me more than half a day to apply to a job.

My challenge was that... **I did not trust Claude**: early in our conversations, it would get creative with phrasing like 
- "Built HL7 products" and
- "Applied pharmacogenomics to business processes"

For anyone who is in the interoperability or pharmacogenomics industries, this sounds like complete nonsense, but to Claude the combination of words made sense and was completely relevant to the context I provided.

### The Redesign
After a few iterations, I realized a few things all at once:
1. After 4+ months of applying, my chats held a lot of experience details that never made it back into my main project context, so I kept retyping them. My first fix was a [context refresh](/docs/prompt_context_refresh.md) prompt. I ran it in every chat, saved the outputs, then ran a reconciliation prompt over those files to update the master context.
2. I developed a pattern:
   - I would start each new job conversation by asking the following: `review this position and tell me my % fit for the role based on my background. Summarize where I'm a strong fit and the gaps. Ask me questions about my gaps` 
   - Most of the time, my fit % would come back at somewhere between 60- 80% even for positions where I felt I was more than perfect.  Great confidence booster in this market, I tell ya!
3. I still did not trust claude to tailor my resume as it continued to get creative with word combinations of my experience, but I realized that I was able to iterate to fix the poor wording.

So - with the help of my friendly Claude - I built 3 skills

1. [Job fit skill assessment](src/job-fit.md): scores your fit against a job description and surfaces the gaps to talk through.
2. [Tailor resume skill](src/tailor-resume.md): tailors your master resume to the job without rewriting your voice.
3. [ATS Screener](src/ats-screener.md): scores the tailored resume against typical ATS criteria before you apply. _Spoiler: it scores lower than job fit. Be ready for that small disappointment._

> Note: I cannot take credit for "write-human" skill mentioned in the Resume tailoring skill - I took the tip from Abhijay Vuyyuru on LinkedIn <https://lnkd.in/p/giY4cQ9v> If you want to see my version of the skill, here it is: [Write Human skill](src/write-human.md)

## Operationalizing it
1. I added /write-human skill in my *Job Search project instructions* as: 
    >invoke **write-human** before drafting any resume or cover letter text
2. For each new job
    - I open a new chat under my Job Search Project
    - I type **/job-fit** and paste the job description
    - I chat with claude to provide more information on any weak / medium points and we iterate on the job match % until we can't iterate anymore.  Once I am satisfied..
    - I type **/resume-tailor**
    - I get my original master resume, text preserved mostly, tailored with additional words / bullets or reordered to fit the job description.
    - Finally, I run **/ats-screener** for the finishing touches to make sure the tailored resume doesn't get filtered out 

## The win
I applied to four jobs the day I finished my skills (the whole rebuild took me about 3 days)
1. All 100+% fit, clearly indicated where I meet the requirements and where I meet the nice-to-haves
2. I passed on one job that was a 75% fit - it was tempting to apply, but I prioritized another role at that company which was a better fit.
3. It took me on average 40 minutes to apply to each role!  I felt confident about my resume

## Womp-womp-womp moment
I was so confident in one of the job applications, that I completely forgot to run ats-screener before applying.  I ran it after I applied, and it scored my application at 83/100 with gaps in an area for which I had high experience and confidence - it just never made it into my resume because it was at a deeper level of detail.

Bottom line... ***don't skip the /ats-screener*** even if you are 10000% confident you are the perfect fit for the role (in fact, even more so! Don't skip it!) :)