# Skill: setup

First-time onboarding. Collects context about the user and writes it into the repo so every future session starts with full context.

## When to Use

Triggered when:
- User says "start", "setup", "onboard", or runs `/setup`
- HEARTBEAT detects that context files are still empty (contain placeholder text like `[Your Name]`)

---

## Steps

### 0. Check if already set up

Read `context/me.md`. If it still contains `[Your Name]` or empty fields, proceed with setup. If it's already filled, say: "Context is already set up. Want to update a specific section?"

---

### 1. Introduce

Say exactly this (adapt tone to match your communication style):

> "let's set up your EA. i'll ask you ~10 questions and write your context directly into the repo. takes about 5 minutes. ready?"

Wait for confirmation before proceeding.

---

### 2. Ask questions — one at a time

Ask each question, wait for the answer, then move to the next. Do NOT ask multiple questions at once.

**Block 1 — Who you are**

1. "what's your name, location, and LinkedIn URL?"
2. "describe yourself in 2-3 sentences — who you are, what you've built, what you're known for."
3. "list 3-5 background highlights — past roles, companies, wins, credentials."
4. "how do you split your time? (e.g. Mon-Fri 9-6: day job | evenings/weekends: side project + content)"

**Block 2 — Work**

5. "what's your day job? (role, company, what the company does, team you lead)"
6. "what are your active projects at work right now? give me a quick list with status."
7. "do you have a side project, teaching role, or advising work? describe it briefly."
8. "do you use GitHub Projects to track work? if yes, give me the board IDs and org names."

**Block 3 — Team**

9. "who are your direct reports or key collaborators? (name, role, what they own)"
10. "how does your team communicate? (Slack, WhatsApp, etc.)"

**Block 4 — Content**

11. "do you post on LinkedIn or other platforms? how often, and what topics?"
12. "describe your content voice — how do you write? (e.g. lowercase, punchy, no fluff, practitioner not observer)"

**Block 5 — Priorities + Goals**

13. "what are your top 3 P0 priorities this week across all tracks?"
14. "what are your top goals for this quarter?"

---

### 3. Write context files

After all answers are collected, write them to the appropriate files. Do NOT ask for confirmation before writing — just do it and report what you wrote.

**Files to write:**
- `context/me.md` — answers from Block 1
- `context/work.md` — answers from Block 2
- `context/team.md` — answers from Block 3
- `context/current-priorities.md` — answer from Q13
- `context/goals.md` — answer from Q14

**Also write `CLAUDE.local.md`** with today's date:
```
# Local Overrides

# currentDate
Today's date is YYYY-MM-DD.
```

**For content voice** — if they described a distinct voice style, update the relevant section of `.claude/rules/content-style.md` to reflect it. If they don't post content, note that in the file.

---

### 4. Confirm and brief

After writing all files, say:

> "done. here's what i set up:"

List the files written (one line each). Then give a one-line summary of their current P0.

Then say:

> "you're set. next time you open a session, i'll brief you automatically. what do you want to work on?"

---

## Rules

- Ask one question at a time. Don't batch them.
- Write answers verbatim where possible — don't summarize away detail.
- If an answer is vague ("a few projects"), follow up with "can you be more specific?"
- Never skip writing a file because the answer was short. Write what you have.
- If the user skips a question, leave that section as a placeholder and move on.
