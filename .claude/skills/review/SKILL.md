---
name: review
description: Pattern analysis, model refinement, and system health. Reads weeks of check-in data and surfaces what's working, what's not, and what the system itself needs. Invoke with /review.
disable-model-invocation: true
argument-hint: "health"
---

# /review — Pattern Analysis and System Health

This skill reads your behavioral data across weeks, surfaces patterns, refines the intelligence models, and checks whether the system itself is healthy. It's the brain's maintenance cycle.

## Arguments

`$ARGUMENTS` can be:
- (empty) — Full pattern analysis and model update
- `health` — System health check only (quick)

---

## Before Anything: Load Everything

```
1. git pull
2. Read ALL files: core/profile.md, core/values.md, core/schedule.md, core/goals.md, data/docket.json, core/patterns.md
3. Read ALL check-in files from the past 4 weeks (or all if < 4 weeks of data)
4. Read ALL weekly plans from that period
5. context/ (if present): read all .md files
6. Get current date
```

---

## /review — Full Pattern Analysis

### 1. Goal Trajectories

For each goal in `core/goals.md`:
- Weekly target completion over the review period (e.g., "Body: 1/3, 2/3, 0/3, 1/3 — declining")
- Is it alive, dying, dead, or overperforming? (Use same criteria as /goal review)
- Docket items linked to this goal: count, average age, completion rate
- Does the goal still serve the value anchor in core/values.md?

### 2. Behavioral Pattern Analysis

Read all check-in data. Surface:

**Energy patterns:**
- What time of day correlates with highest ratings and best output?
- What activities correlate with energy boosts vs. drains?
- Does self-reported peak time (core/profile.md) match actual data?

**Capacity patterns:**
- Planned items vs. completed items per day/week
- Calculate updated throughput rate: completed / prescribed
- Is the system over-scheduling or under-scheduling?

**Work style patterns:**
- Do breadth days (multiple goal types) or depth days (single focus) produce better ratings?
- Is the user a batcher or interleaver in practice?

**Avoidance patterns:**
- Which tasks/goals consistently roll? What do they have in common?
- Is avoidance time-of-day dependent? Energy dependent? Context dependent?

**Deadline patterns:**
- How close to deadlines does work actually get done?
- Does time pressure help or hurt quality (inferred from ratings)?

**Recovery patterns:**
- After low-rated days, how many days until baseline?
- What activities appear on recovery days?

**Fusion patterns:**
- Recurring self-defeating thoughts logged in check-ins
- Conditions that trigger fusion (specific contexts, time of day, goal types)

**Coaching effectiveness:**
- Time-slotted prescriptions vs. unslotted: completion rates
- First-prescribed vs. last-prescribed item: completion rates
- Which prescription formats get followed most?

### 3. Update core/patterns.md

Based on the analysis:

- **Reliable Patterns:** Add new patterns with first-observed and confirmed dates. Add confirmation dates to existing patterns.
- **Emerging:** Observations with only 1-2 data points. Include what would confirm them.
- **Intelligence Models:** Update with data-confirmed findings. If data contradicts self-report in core/profile.md, note the divergence: "Self-reported morning peak — data shows afternoon peak after exercise."
- **Fusion Patterns:** Add or refine based on check-in content.
- **Coaching Effectiveness:** Update with prescription-type completion rates.
- **Stale:** Move patterns not confirmed in 4+ weeks.
- **Throughput rate:** Update with current calculated rate.

Update `*Last updated: YYYY-MM-DD*` at the top of core/patterns.md.

### 4. Update core/profile.md (if warranted)

If behavioral data reveals something about the user that contradicts or enriches their self-report, update the Intelligence Models section in core/profile.md. Label data-confirmed findings: "Energy: self-reported morning peak → confirmed by data (7+ ratings correlate with pre-noon deep work)."

### 5. Check values alignment

Read core/values.md. For each value:
- Is the user living it? (Check-in data shows behaviors aligned with the value)
- Is the user NOT living it? (Named value with no supporting behavior)
- Is there an un-named value being lived? ("You've chosen creative approaches over efficient ones 8 of 10 times. Is there a value there?")

Present findings but don't change core/values.md without user consent.

### 6. Recalibration check

If planned vs. actual diverges by >30% for 2+ consecutive weeks:
"My capacity model is off. I've been [over/under]-scheduling by ~[N] hours/week. Recalibrating throughput rate from [old]% to [new]%."

### 7. Present findings

Format as observations with prescriptions. Not "I notice that..." — "Here's what I see, here's what we're doing about it."

2-4 paragraphs covering:
- What's working (protect it)
- What's collapsing (prescription to fix)
- What the data reveals that wasn't obvious
- Recommendation for next week's emphasis

### 8. Git sync

```bash
git add core/patterns.md core/profile.md core/goals.md
git commit -m "Review YYYY-MM-DD"
git push
```

---

## /review health — System Health Check

Quick diagnostic. Flag each of these:

### File Currency
- [ ] No weekly plan exists for the current week
- [ ] Most recent weekly plan is older than 10 days
- [ ] core/patterns.md hasn't been updated in 14+ days
- [ ] core/goals.md hasn't been reviewed (no `/goal review` or auto-review evaluation) in 30+ days

### Goal Health
- [ ] Any goal with zero check-in mentions in 14+ days
- [ ] Any goal with weekly targets missed 3+ consecutive weeks
- [ ] Any goal with zero active docket items

### Docket Health
- [ ] Active items count > 15 (overload)
- [ ] Items with days_rolling > 7 (stale tasks)
- [ ] Waiting items past their waiting_check date (forgotten follow-ups)
- [ ] Done items older than 30 days (needs archiving)

### Data Quality
- [ ] Check-in streak broken (gap > 2 days in last 2 weeks)
- [ ] data/docket.json fails to parse (corruption)
- [ ] Weekly plan has unchecked items from 3+ days ago (sync failure)

### Profile Completeness
- [ ] Intelligence models in core/profile.md still all marked as self-report (no data confirmation yet)
- [ ] Protected zones not defined
- [ ] core/schedule.md has blank entries

### Output

Present as a clean checklist with pass/fail and recommended actions:

```
## System Health — YYYY-MM-DD

✓ Weekly plan current (Apr 7-13)
✓ Patterns updated 3 days ago
✗ 4 docket items rolling 7+ days — triage needed
✗ Career goal: zero docket items — add tasks or flag for /goal review
✓ Check-in streak intact (42 days)
✓ data/docket.json valid

Recommendations:
1. Run docket triage: kill or do the 4 stale items
2. Add career tasks or review goal viability with /goal review
```

---

## The Spirit of This

The review is the system examining itself. It's not just analyzing the user — it's analyzing whether the system's own prescriptions are working, whether its models are accurate, whether its files are healthy. A system that can't maintain itself will slowly degrade and lose the user's trust. This skill prevents that.
