# Becoming

A system that tells you what to do every morning, checks if you did it every night, and gets smarter over time. Built on Claude Code and markdown files. Every conversation picks up where the last one left off.

## First Time?

Run `/setup`. It takes 10 minutes. You'll answer some questions and the system will build itself around your answers.

## How This Works

**Morning:** Run `/checkin`. The system reads your goals, your task list, and what happened yesterday. It tells you what to do today, in order, with reasons. You negotiate if you want. Then you go do it.

**Evening:** Run `/checkin evening`. Score what happened. The system updates your task list, tracks your weekly targets, and flags anything that's been slipping.

**Weekly:** Run `/checkin weekly` on Sunday or Monday. Review last week, set this week's targets.

## Your Files

- `profile.md` — who you are and how you work (built during /setup, enriched over time — when you mention something new about your life, work, or patterns, the system updates this file automatically)
- `goals.md` — what you're working toward, with countable weekly targets
- `docket.md` — your rolling task list (the system maintains this)
- `weeks/` — weekly plans (accumulate over time)
- `checkins/` — daily check-in files (your behavioral data over weeks and months)

## Design Principles

This system works because of specific decisions:

1. **It prescribes.** It doesn't ask "what do you want to do today?" It tells you what to do based on what you said you cared about.
2. **It remembers.** Every check-in is saved. A new conversation reads the last few and picks up where you left off.
3. **It adapts.** If you keep skipping the same thing, it notices and changes the prescription.
4. **It counts.** "3/4 sessions this week" not "are you doing enough?" Progress is a fraction, not a feeling.
5. **It has a floor.** Every goal has a bad-day version. The bar lowers but never disappears.
6. **It flags.** Tasks track how long they've been sitting. "Day 4. Today or kill it."
7. **It challenges.** "I'll work on my project" gets pushed back to "which part, when, how long?"
8. **It protects.** Some things stay fun and never become goals.
