# Skill: sprint-summary

Pull and summarize the current sprint status across both tracks.

## When to Use

Triggered by `/sprint-summary` or when asked "what's the sprint look like", "where are we this week", "sprint status".

## Steps

### 1. Pull GitHub Data (run in parallel)

Read board IDs and org names from `context/work.md`, then run:

```bash
gh project item-list WORK_BOARD_ID --owner WORK_ORG --format json
gh project item-list PERSONAL_BOARD_ID --owner PERSONAL_ORG --format json
```

Work board = sprint tasks | Personal board = content + invoices + side project

### 2. Parse and Group

**For work board:**
Group items by project/workstream.
Within each group, sort by priority (P0 first) and status.

Status buckets:
- OVERDUE P0 — past due date, not done
- IN PROGRESS — active, on track
- IN REVIEW — submitted, waiting
- BLOCKED — explicit blocker or no update
- DONE

**For personal board:**
Group by type (Content, Invoices, Side Project).
Flag content that's overdue based on posting cadence and today's date.

### 3. Flag Blockers

Mark anything that:
- Is P0 and past its due date
- Has "blocked" in the title/notes
- Is assigned to you directly (needs your action, not the team's)

### 4. Output Format

```
## [Work Track] — Sprint [N] (dates)

**[Project]**
- [status] [item] — [owner] (due: date)

**Blockers / Needs You:**
- ...

---

## Personal — This Week

**Content**
- [status] [post] (due: day)

**Invoices**
- [status] [invoice]

**Blockers:**
- ...
```

Keep it scannable. No prose. Just the signal.
