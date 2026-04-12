# Skill: cold-email-founder

Research AI, tech, or e-commerce founders. Find their email. Draft a cold email with a genuine hook. Get approval. Send.

## Triggers

- `/email-founder find` — pick oldest queued target, or auto-discover 3 candidates if list is empty
- `/email-founder add [name/company]` — add a founder to the targets list
- `/email-founder update [name]` — update status or notes on an existing target
- `/email-founder share [name/company]` — research and draft immediately for a named founder

---

## Step 1: Discover or Pick Founder

**If `find` with targets in list:**
Read `.claude/skills/cold-email-founder/targets.md`. Pick the oldest `queued` entry.

**If `find` with empty list:**
Search for 3 trending founders in AI, tech, or e-commerce (Indian + global). Show:
```
1. [Name] — [Company] ([what they build, 1 line])
2. ...
3. ...
Pick one (1/2/3):
```
Wait for input before proceeding.

**If `share [name]`:**
Skip list, go straight to Step 2 with that founder/company.

---

## Step 2: Deep Research

Run in parallel:

**Company research (Firecrawl):**
- Scrape homepage, /about, /product pages
- Extract: what they build, current focus, recent launches, pricing, gaps

**Founder research (WebSearch + Firecrawl):**
- Search LinkedIn, Twitter/X, recent interviews, podcasts, press
- Extract: what are they saying publicly, what problem are they obsessing over, recent posts

**Email finding (in order, stop when found):**
1. LinkedIn about/contact section
2. Website /team, /about, /contact pages
3. Google: `"firstname lastname" "companyname" "@"`
4. Pattern guess: `first@company.com`, `first.last@company.com`, `f.last@company.com`

---

## Step 3: Show Research Summary

Show before drafting:
```
Founder: [Name], [Title]
Company: [Name] — [one line description]
Hook: [strong/weak] [the specific observation]
Email: [email] ([source])
```

Ask: "Hook look right? I'll draft from this — or tell me a different angle."

Wait for confirmation or override before drafting.

---

## Step 4: Draft Subject + Body

**Subject rules:**
- Under 8 words
- Specific, not clickbait
- No "Quick question", "Opportunity", "Following up"
- Feels like a human sent it

**Body rules:**
- Under 150 words
- All lowercase
- No em dashes
- No transitions (furthermore, in conclusion, etc.)
- No corporate speak
- Structure: genuine observation → specific detail → soft ask or open close
- Sign off: shivam + one line of context

**Shivam's background (use selectively):**
- ex-founder, apli.ai (acquired by edulab)
- head of product and growth at the good bug
- building claw-work (AI agent platform)
- teaching gen ai at masters union
- based in mumbai

---

## Step 5: Approval Screen

Show:
```
To: [email]
Subject: [subject]

[body]

Send? (yes / edit subject / edit body / skip)
```

- **yes** → send via Gmail CLI: `echo "[body]" | mail -s "[subject]" [email]`
- **edit subject** or **edit body** → take input, redraft that section, re-show approval screen
- **skip** → mark as `skipped` in targets.md, stop

---

## Step 6: Update Targets List

After sending, update `.claude/skills/cold-email-founder/targets.md`:
- Set status to `emailed`
- Add date sent
- Add one-line note on what the hook was

---

## Targets List Format

File: `.claude/skills/cold-email-founder/targets.md`

```markdown
| Founder | Company | Domain | Status | Date | Notes |
|---------|---------|--------|--------|------|-------|
| Siddharth | Provylak | D2C / delivery | emailed | 2026-04-13 | multi-city re-registration friction |
```

Statuses: `queued` → `emailed` → `replied` → `skipped`
