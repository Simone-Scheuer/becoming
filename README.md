# Becoming 

A personal coaching system that runs on Claude Code. It tells you what to do every morning based on your goals and routines, checks if you did it, and adapts over time. 

I built it because I personally believe self-actualization is the biggest unsolved problem of our generation. And I have struggled my entire life to manage the gap between who I am and who I want to become. 

Becoming isn't about replacing your agency, it's about **getting you out of your own way**, so that you can actually have it. 

By building a personalized "mind outside of your mind" that understands your life, your routine, and your short and long term goals you can shift your mental energy from repeated small decision making (should I go to the gym or watch tiktok rn) to the big picture and become the architect of your ideal life. Imagine if you could ask "who do I want to be in six months," have a dialogue that helps you understand the real answer to that question, and then watch as the organization of your daily routine effortlessly adjusts to get you there. 

**You just don't have to do it all yourself anymore.**

## Why It Works

Most productivity systems fail (especially for ADHD people) because they demand effort just to know what effort you need to do. Becoming is designed around six principles:

1. **Centralized** — One system holds everything. Goals, tasks, habits, schedule, patterns, journal. No app-switching, no syncing, no "where did I put that."

2. **Zero friction** — Just talk to it. Speech-to-text, stream of consciousness, whatever. The system organizes it for you. If you have to do work to know what work you have, you'll never do the work.

3. **Prescriptive, not descriptive** — It doesn't ask "what do you want to do today?" It tells you. Based on your goals, your schedule, your energy, what you've been avoiding, and what's due. You negotiate, not brainstorm.

4. **You're the architect** — You set the direction. "I want to be a product designer." "I want to run again." The system breaks that into weekly targets, daily actions, and time-slotted prescriptions fitted to your actual free blocks. You design your life; it project-manages the days.

5. **It learns you** — The system tracks what you avoid, what correlates with good days, when you're about to crash. Prescriptions get smarter over time because they're based on your behavioral data, not generic advice.

6. **It has a floor** — Every goal has a bad-day version. The system still works when you're at a 3. Most productivity systems only work when you're already motivated. This one is designed for the days you're not.

And it produces something: a **living journal**. Every check-in is saved. Over weeks and months you build a record of who you were, what you did, and how you felt — not because you sat down to journal, but because the system captured it while coaching you. It encourages mindfulness as a side effect of showing up.

## Getting Started

### Prerequisites
- [Claude Code](https://claude.ai/code) (requires a Claude subscription)
- Git
- [SuperWhisper](https://superwhisper.com) or similar speech-to-text — highly recommended! Talking through check-ins is faster and more natural

### Setup

1. Clone this repo:
```bash
git clone https://github.com/Simone-Scheuer/becoming.git
cd becoming
```

2. Open in your editor with Claude Code active.

3. Run the setup:
```
/setup
```

The system will ask you questions about your goals, schedule, and how you work. It takes about 10 minutes. After that, you're ready for your first check-in.

### Daily Use

**Morning:**
```
/checkin
```
The system reads your goals and yesterday's data, then tells you what to do today.

**Evening:**
```
/checkin evening
```
Score what happened. The system updates everything.

**Weekly (Sunday or Monday):**
```
/checkin weekly
```
Review last week, set this week's targets, clean up your task list.

### Dashboard

Open `dashboard.html` with a local server to see a live view of your habits, tasks, deadlines, and today's plan:
```bash
python3 -m http.server 8080
# then open localhost:8080/dashboard.html
```

## How It Works

Every check-in is saved as a markdown file in `checkins/`. When you start a new conversation, the system reads your profile, goals, task list, habits, and recent check-ins. It picks up where it left off.

Over time, it builds a picture of how you actually work: what you keep doing, what you keep avoiding, what correlates with good days, what falls apart. It uses this to make better prescriptions.

The design decisions come from me iterating on what actually works over 60+ days of daily use:

- **Prescribe, don't ask.** Remove the decision load so you can be the architect of your life rather than getting bogged down with every little thing.
- **Count everything.** "3/4 sessions this week" is better than "am I doing enough?" Tracking doesn't need to be work.
- **Have a floor.** Every goal has a bad-day version. The system still works when you're at a 3.
- **Track drift.** Tasks count how long they've been sitting. It's a to-do list you can negotiate with.
- **Protect play.** Some things stay fun. The system never optimizes them. Because sometimes you need permission to relax.
- **Separate the layers.** Habits (weekly rhythms) are different from tasks (things that end). They live in different files because they work differently.

## Files

```
core/profile.md         — who you are, how you work (built during /setup)
core/values.md          — what matters to you
core/schedule.md        — your weekly time grid
core/goals.md           — your goals with weekly targets
core/patterns.md        — what the system learns about you
data/docket.json        — discrete tasks
data/habits.json        — weekly recurring habits
data/docket-archive.json — completed/killed task history
weeks/                  — weekly plans
checkins/               — daily check-in files
dashboard.html          — live dashboard
```

## Questions?

Built by [Simone Scheuer](https://simonescheuer.com). DM me on [LinkedIn](https://linkedin.com/in/simone-scheuer) if you try it.
