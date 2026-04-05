# Becoming

A personal coaching system that runs on Claude Code. It tells you what to do every morning based on your goals and what happened yesterday, checks if you did it every night, and adapts over time.

## What This Is

Most productivity systems fail because they require you to do the planning. Becoming does the planning for you. You tell it what you care about, and it prescribes specific daily actions, tracks whether they happen, and adjusts when things slip.

It runs on markdown files and Claude Code. No app, no backend, no account. Your data lives on your machine in plain text.

## Getting Started

### Prerequisites
- [Claude Code](https://claude.ai/code) (requires a Claude subscription)
- Git

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
Score what happened. The system updates your targets and flags patterns.

**Weekly (Sunday or Monday):**
```
/checkin weekly
```
Review last week, set this week's targets.

## How It Works

Every check-in is saved as a markdown file in `checkins/`. When you start a new conversation, the system reads your profile, goals, task list, and recent check-ins. It picks up where it left off.

Over time, it builds a picture of how you actually work: what you keep doing, what you keep avoiding, what correlates with good days, what falls apart. It uses this to make better prescriptions.

The system was designed by someone with ADHD who failed at every productivity system she tried. The design decisions come from lived failure, not productivity theory:

- **Prescribe, don't ask.** Removing the decision is the intervention.
- **Count everything.** "3/4 sessions this week" is better than "am I doing enough?"
- **Have a floor.** Every goal has a bad-day version. The system still works when you're at a 3.
- **Track drift.** Tasks count how long they've been sitting. No guilt, just facts.
- **Protect play.** Some things stay fun. The system never optimizes them.

## Files

```
profile.md      — who you are, how you work (built during /setup)
goals.md        — your goals with weekly targets
docket.md       — rolling task list
weeks/          — weekly plans
checkins/       — daily check-in files
```

## Questions?

Built by [Simone Scheuer](https://simonescheuer.com). DM me on [LinkedIn](https://linkedin.com/in/simone-scheuer) if you try it.
