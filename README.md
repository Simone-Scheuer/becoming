# Becoming 

A personal coaching system that runs on Claude Code. It tells you what to do every morning based on your goals and routines, checks if you did it, and adapts over time. 

I built it because I personally believe self-actualization is the biggest unsolved problem of our generation. And I have struggled my entire life to manage the gap between who I am and who I want to become. 

Becoming isn't about replacing your agency, it's about **getting you out of your own way**, so that you can actually have it. 

By building a personalized "mind outside of your mind" that understands your life, your routine, and your short and long term goals you can shift your mental energy from repeated small decision making (should I go to the gym or watch tiktok rn) to the big picture and become the architect of your ideal life. Imagine if you could ask "who do I want to be in six months" have a dialogue that helps you understand the real answer tto that question, and then watch as the organization of your daily routine effortlessly adjusts to get you there. 

**You just don't have to do it all yourself anymore.**

## What This Is

Most productivity systems fail (especially for ADHD people) because of two reasons:
1. friction - if I have to do work (manual data entry, organization, etc) just to know what work I have, it's just not gonna get done! This is the number one reason people quit using these systems. By using a file based system with a coordinating AI agent like Claude, literally all you have to do is talk to it about your day, your goals, or your unfulfilled desire to master the accordion, and it will design your days and weeks for you based on YOUR desires.

2. intelligence - setting good, realistic, well paced daily deliverables to work towards your long term goals is a ton of effort, and it's work an algorithmic to-do list simply cannot do for you. By engaging conversationally with an intelligent system that can self organize, you relieve yourself of the mental load of tracking everything you want to do and aren't, and free yourself up to spend more time actually doing it!

It runs on markdown files and Claude Code. No app, no backend, no account. Literally anyone could do this. 

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

The system was designed by someone with ADHD who failed spectacularly at every productivity system she's ever tried. The design decisions come from me iterating on what actually works:

- **Prescribe, don't ask.** Removing the decision load and letting you be the architect of your life rather than getting bogged down with every little thing.
- **Count everything.** "3/4 sessions this week" is better than "am I doing enough?" One of my biggest problems was not having a sense of my progress. Tracking doesn't need to be work.
- **Have a floor.** Every goal has a bad-day version. The system still works when you're at a 3. It's a to-do list you can negotiate with, because some days "the gym" is a walk in the park.
- **Track drift.** Tasks count how long they've been sitting. This one is pretty similar to a to-do list, but I do notice it doesn't make me feel guilt the same way. Claude's friendlier.
- **Protect play.** Some things stay fun. The system never optimizes them. Cuz sometimes I feel like I need permission to relax :3

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
