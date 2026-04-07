# Becoming

A system that tells you what to do every morning, checks if you did it every night, and gets smarter about you over time. Built on Claude Code and markdown files. Every conversation picks up where the last one left off.

## First Time?

Run `/setup`. It takes 15 minutes. You'll answer some questions and the system will build itself around your answers.

## How This Works

**Morning:** Run `/checkin`. The system reads your goals, schedule, tasks, and what happened yesterday. It tells you what to do today — time-slotted into your real free blocks, ordered by what matters most. You negotiate if you want. Then you go do it.

**Evening:** Run `/checkin evening`. Score what happened, triage the docket, track habits. The system updates everything — your task list, your weekly plan checkboxes, your habit progress. Tomorrow's morning check-in reads tonight's updates. Nothing falls through the cracks.

**Weekly:** Run `/checkin weekly` on Sunday or Monday. Review last week's data, set this week's targets, build a daily plan fitted to your schedule.

**Goals:** Run `/goal` to see your goals. `/goal add` to add one (the system will interrogate it — is it feasible? what value does it serve? what gives way?). `/goal review` to assess what's alive and what's dying.

**Review:** Run `/review` for a pattern analysis across weeks of data. `/review health` to check if the system itself needs maintenance.

**Dashboard:** Open `dashboard.html` in a browser (serve with `python3 -m http.server`) for a live view of habits, docket, today's plan, and deadlines.

## Your Files

- `core/profile.md` — who you are, how you work, coaching style (built during /setup, enriched over time)
- `core/values.md` — what matters to you (inferred during /setup, refined as the system learns)
- `core/schedule.md` — your weekly time grid: fixed blocks, free blocks, constraints
- `core/goals.md` — what you're working toward, with lifecycle metadata
- `core/patterns.md` — what the system has learned about you (system-maintained)
- `data/habits.json` — weekly recurring habits with targets and progress (the rhythm layer)
- `data/docket.json` — discrete tasks only (things that end — system-managed, don't edit directly)
- `data/docket-archive.json` — completed/killed tasks (history)
- `weeks/` — weekly plans with daily checkboxes (the sync hub — evening check-ins update these)
- `checkins/` — daily check-in files (your behavioral data over time)
- `context/` — optional personal context layer (power users add files here for deeper coaching)
- `dashboard.html` — live dashboard (serve locally, auto-refreshes every 30s)

## How the Intelligence Works

The system builds models of how you work — not from assumptions, but from your intake answers and your actual behavioral data over time:

- **Energy:** When you peak and trough. What depletes you. What restores you.
- **Capacity:** How many hours you realistically have. Your actual throughput rate (planned vs. completed).
- **Work style:** Breadth vs. depth. Batching vs. interleaving. Sprints vs. steady.
- **Avoidance:** What you put off. What conditions make it worse. What helps.
- **Deadlines:** Whether you front-load or procrastinate. How much buffer you need.
- **Recovery:** What happens after a bad day. How long it takes. What speeds it up.

These models start as self-report (during /setup) and get refined by real data. The system uses them to produce intelligent prescriptions — not just "do these 4 things" but "here's what fits in your 3 free hours today, sequenced by energy, with the thing you've been avoiding scheduled in your peak block."

## Design Principles

1. **It prescribes.** It doesn't ask "what do you want to do today?" It tells you what to do based on what you said you cared about.
2. **It remembers.** Every check-in is saved. Every conversation picks up where the last one left off.
3. **It syncs.** When you say "I did the homework" tonight, tomorrow morning won't re-prescribe it. Evening is the sync point — everything gets updated in one pass.
4. **It reasons about time.** Prescriptions are fitted to your real schedule, not a wish list. It won't tell you to do a 2-hour build session when class starts in 45 minutes.
5. **It counts.** "3/4 sessions this week" not "are you doing enough?" Progress is a fraction, not a feeling.
6. **It has a floor.** Every goal has a bad-day version. The bar lowers but never disappears.
7. **It flags.** Tasks track how long they've been sitting. "Day 5. Do it or kill it."
8. **It challenges.** "I'll work on my project" gets pushed back to "which part, when, how long?"
9. **It protects.** Some things stay fun and never become goals.
10. **It learns.** The system gets smarter about you over time — what works, what doesn't, what patterns to watch for.
11. **It intervenes.** When you fuse with a self-defeating thought, the system names the pattern, redirects to your values, and moves on. One sentence. Not therapy — coaching.

## The context/ Folder

For most users, `context/` stays empty and the system works great with just the standard files.

Power users can drop additional files into `context/` to give the system deeper awareness — therapy notes, career plans, class schedules, strategic documents, whatever helps the coaching. The system reads what's there and incorporates it. It never requires it.
