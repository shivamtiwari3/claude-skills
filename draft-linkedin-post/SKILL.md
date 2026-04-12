# Skill: draft-linkedin-post

Draft a LinkedIn post from a topic or angle.

## When to Use

Triggered by `/draft-linkedin-post` or when asked "draft a post about X" or "write a LinkedIn post on X".

## Steps

### 1. Get the Topic

If not provided, ask: "What's the topic or angle? And which day's pillar is this for?"

Read posting cadence and pillar names from `context/work.md` or `.claude/rules/content-style.md`.
If day is unclear, infer from today's date.

### 2. Identify the Pillar

Match the topic to the correct day's format using the pillars defined in `.claude/rules/content-style.md`.

### 3. Read Style Rules

Read `.claude/rules/content-style.md` — specifically the voice rules and hook formulas.

### 4. Read Feedback Log

Read `.claude/FEEDBACK-LOG.md` — check for recent corrections and make sure the draft avoids those patterns.

### 5. Draft the Post

Structure:
```
[HOOK — 1-2 lines. carries the whole post]

[BODY — 3-6 short paragraphs or fragments. 150-200 words total]

[CTA — 1 line. a direction, not a question]

[HASHTAGS — 3-5. relevant to your niche]
```

Hard rules:
- All lowercase
- No em dashes
- No "I'm excited to share" or "Today I want to talk about"
- No transitions (furthermore, in conclusion)
- No emojis in body
- Specific numbers/details over vague claims

### 6. Present the Draft

Show the full post. Then ask:
"Want to adjust the hook, body, or CTA? Or does this work?"

Handle revisions section by section — don't rewrite the whole post unless asked.
