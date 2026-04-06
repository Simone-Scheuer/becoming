---
name: goal
description: Goal dialogue and lifecycle management. Add goals with feasibility checks, review what's alive and dying, pause or kill goals with dignity. Invoke with /goal.
disable-model-invocation: true
argument-hint: "add | review | pause [name] | kill [name] | adjust [name]"
---

# /goal — Goal Dialogue and Lifecycle

Goals are living objects. They're born through dialogue, tracked weekly, reviewed automatically, and can be paused or killed with dignity. This skill manages the full lifecycle.

## Arguments

`$ARGUMENTS` can be:
- (empty) — Show all goals with current status and health
- `add` — Full goal dialogue: interrogate a new goal
- `review` — Review all goals: alive/dying/dead assessment
- `pause [name]` — Pause a goal with reason
- `kill [name]` — Kill a goal with reason
- `adjust [name]` — Modify targets for a goal

---

## Before Anything: Load Context

```
1. Read goals.md              — current goals with metadata
2. Read schedule.md           — available time blocks
3. Read values.md             — what the user values (goals must serve a value)
4. Read profile.md            — coaching style, intelligence models
5. Read patterns.md           — behavioral patterns, throughput rate
6. Read docket.json           — tasks linked to goals
7. Read last 2 weeks of checkins/ — recent behavioral data
8. context/ (if present)      — additional context
```

---

## /goal (no args) — Dashboard

Display all goals with a one-line health assessment:

```
## Goals Dashboard

1. **Becoming** (active, do) — 3/4 build sessions this week. On track.
2. **Body** (active, maintain) — 0/3 protocol. Collapsed since Wednesday. FLAGGED.
3. **Math** (active, be) — 1/1 chapter read, HW on time. Solid.
4. **Career** (active, do) — 2 applications submitted. Below target (5). Needs push.
5. **Running** (paused) — Paused Apr 1 (ankle). Reactivation check: May 1.

Protected zones: Music, guitar, reading for pleasure.
```

Include: docket items per goal, days since last activity, weekly target fractions.

---

## /goal add — The Dialogue

This is the Architect half. When the user says "I want to run a marathon," the system does NOT just create a goal. It runs a dialogue.

### Phase 1: Desire Clarification

- "Is this a 'do' goal (run a specific marathon), a 'be' goal (become a runner), or a 'maintain' goal (keep exercise consistent)?"
- "What value does this serve?" Check values.md. If it clearly maps to an existing value, confirm. If not, ask: "I don't see an obvious value match. Is there a new value emerging, or does this connect to [closest match]?"
- "What does done look like this quarter? Not perfectly — roughly."
- "Is there an identity attached to this? Who do you become by doing it?" (Optional — skip if they don't connect with it.)

### Phase 2: Feasibility Check

Read `schedule.md` and `goals.md`. Do the math:

- Count available free blocks per week
- Sum existing goals' weekly action time (use `time_minutes` from docket.json for related tasks, or estimate)
- Estimate new goal's time requirements
- Surface conflicts:

"Your schedule has [N] free hours this week. Current goals use approximately [M] hours. This new goal needs [K] hours per week. That puts you at [M+K]/[N] — [over/under] capacity."

If over capacity: "Something has to give. Options: (a) reduce [existing goal] to minimum viable, (b) pause [existing goal], (c) set a lower target for the new goal. What works?"

If under capacity: "This fits. You have ~[buffer] hours of buffer."

### Phase 3: Relationship Modeling

- "How does this relate to your other goals?"
- Check for enables: "Does running support your body goal? Does it give you energy for builder work?"
- Check for competition: "This competes with [goal] for [morning blocks / energy / time]. Which takes priority when they conflict?"
- Check for dependencies: "Does this require anything first? (Ankle healed, equipment purchased, etc.)"

### Phase 4: Target Setting

- "What's the weekly action? Be specific and countable." (e.g., "3 runs per week")
- "What's the bad-day minimum? The thing that still counts when everything is hard." (e.g., "a 15-minute walk")
- "What should the system watch for? What pattern will kill this goal?" (e.g., "running becoming avoidance of build work")

### Phase 5: Write

Write the goal to `goals.md` with full metadata:
- Status: active
- Created: today
- Type: (from phase 1)
- Value anchor: (from phase 1)
- Identity: (from phase 1, if provided)
- Done state, weekly actions, minimum viable, relationships, what to watch
- History: "Created during /goal add"

If the goal implies immediate tasks, add them to `docket.json`:
- e.g., "Research beginner marathon plans" (goal: Running, time: 30min, energy: low)

Suggest adjustments to the current weekly plan if needed.

Git sync after writing.

### What /goal add does NOT do:
- Does not create goals the user didn't express
- Does not skip the feasibility check
- Does not judge goals as good or bad
- Does not turn protected zones into goals (if they say "I want to make music a goal" — push back: "Music is a protected zone. Making it a goal risks killing the fun. Are you sure?")
- Does not override the user's final decision after the dialogue

---

## /goal review — Lifecycle Assessment

Read all goals. For each one, assess health based on check-in data:

### Health Categories

**Alive:** Hitting weekly targets. Mentioned in check-ins. Has active docket items.

**Overperforming:** Consistently exceeding targets. "You've hit 5/4 build sessions three weeks running. Raise the target to 5, or redirect the energy?"

**Dying:** Targets missed 2+ consecutive weeks. Rarely mentioned. Few or no active docket items. "Body has been 0-1/3 for three weeks. The system keeps prescribing it and you keep not doing it. What's going on?"

**Dead:** 3+ weeks of zero activity toward the goal. "Career Direction hasn't shown any activity in 21 days. Three options: recommit with new targets, pause it with a reactivation date, or kill it."

### For dying/dead goals, present options:
1. **Recommit** with adjusted targets (lower the bar, change the approach)
2. **Pause** with a reactivation date or condition ("revisit when ankle heals")
3. **Kill** with a reason ("this was aspirational, not real")

"Killing a goal isn't failure — it's data. You learned what doesn't work. The time goes back to what does."

### Also check:
- Goals with no docket items (might be dying silently)
- Goals where the value anchor no longer resonates (values can shift)
- Protected zones that are creeping toward goal-like behavior

### Write changes to:
- `goals.md` — status changes, target adjustments, history entries
- `patterns.md` — if the review reveals a new behavioral pattern
- `docket.json` — if tasks need to be added/removed for adjusted goals

---

## /goal pause [name]

Set status to `paused`. Log in History:
```
| YYYY-MM-DD | Paused: [reason] |
```

Ask: "When should we revisit this? Give me a date or a condition."

If they give a date, add to docket.json as a waiting item:
```json
{"id": "t_pause_check", "text": "Revisit paused goal: [name]", "goal": null, "status": "waiting", "waiting_check": "YYYY-MM-DD"}
```

If they give a condition: note it in the goal's History.

---

## /goal kill [name]

Set status to `killed`. Log in History:
```
| YYYY-MM-DD | Killed: [reason] |
```

Remove related active docket items (or ask if they should stay independent).

"This goal is done. [If it was using X hours/week:] That time is now available for [other goals] or buffer."

If the goal has been paused before: "This is the [Nth] time this goal has been attempted. The pattern suggests [observation]. Worth noting for future goals."

---

## /goal adjust [name]

Modify one or more of:
- Weekly targets (up or down)
- Done state (refine or simplify)
- What to watch (new failure mode observed)
- Relationships (changed since creation)

Log every change in History:
```
| YYYY-MM-DD | Target adjusted from 4→3 (auto-review: consistently missing) |
```

If targets are being lowered: "That's a realistic adjustment, not a failure. The minimum viable version keeps the goal alive."

If targets are being raised: "You've been exceeding [old target] for [N weeks]. Raising to [new target]."

---

## The Spirit of This

Goals are not commitments carved in stone. They're hypotheses about what matters. The system tests them against reality. When a goal works, it gets reinforced. When it doesn't, it gets adjusted or killed. The lifecycle is the intelligence — a static goal list is just a to-do app.
