# Getting Started

## What You Need
- A Claude subscription (Claude Code, Claude Pro, or Claude Max)
- Git installed on your machine
- A text editor (VS Code recommended — Claude Code integrates directly)
- **SuperWhisper** (recommended, free) — download from [superwhisper.com](https://superwhisper.com). System-wide speech-to-text so you can talk to the system instead of typing. Makes check-ins feel like a 2-minute conversation instead of a typing exercise. Not required, but it changes the experience.

## Setup (15 minutes)

1. **Clone the repo:**
   ```bash
   git clone https://github.com/Simone-Scheuer/becoming.git
   cd becoming
   ```

2. **Open it in VS Code** (or your editor) with Claude Code active.

3. **Run `/setup`** in Claude Code. The system will interview you about:
   - What you do and what your week looks like
   - How you work — energy patterns, work style, what falls apart
   - What matters to you (the system infers your values from the conversation)
   - What you're trying to accomplish (2-4 goals, with feasibility checks)
   - What's currently on your plate

   Just talk naturally. The system structures everything into the files it needs.

4. **Do your first check-in.** The system runs one automatically at the end of setup.

## Daily Use

**Every morning:** `/checkin`. 2-5 minutes. The system tells you what to do today — time-slotted into your real free blocks, ordered by what matters most.

**Every evening:** `/checkin evening`. 1-2 minutes. Score what happened. The system syncs everything — your weekly plan, task list, and goal progress all update automatically.

**Every week:** `/checkin weekly` on Sunday or Monday. 5-10 minutes. Review last week's data, build next week's plan.

## Goal Management

**See your goals:** `/goal` — dashboard with health assessment for each goal.

**Add a goal:** `/goal add` — the system interrogates it. Is it feasible? What value does it serve? What gives way?

**Review goals:** `/goal review` — what's alive, dying, dead, overperforming. Kill or adjust as needed.

## System Review

**Pattern analysis:** `/review` — surfaces what's working, what's not, and what the system has learned about you.

**Health check:** `/review health` — is the system itself healthy? Stale data, dying goals, docket overload.

## Tips

- **Talk, don't type.** Use SuperWhisper or any speech-to-text. The system is designed for voice input.
- **Be honest in evenings.** The system doesn't judge — it adjusts.
- **The first week is calibration.** The system gets smarter as it learns your patterns.
- **Push back.** "That's not the priority today" is valid. The system adjusts.
- **The context/ folder** is for power users who want to give the system deeper awareness — therapy notes, career plans, class schedules. Drop files in and the system reads them. Totally optional.
