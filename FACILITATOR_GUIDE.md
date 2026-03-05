# Facilitator Guide

This guide is for the event host(s) running the GitHub Copilot Hackathon. It covers the run-of-show, talking points, and tips for a successful event.

---

## Before the Event

### 1-2 Weeks Prior
- [ ] Confirm all attendees have active **GitHub Copilot Enterprise** licenses
- [ ] Send pre-event communication with:
  - Link to this repository
  - Instructions to install VS Code + Copilot extensions
  - Request to **bring a codebase** (clone their repo locally before the event)
  - Suggestion to identify 1-2 backlog items (features, bugs, tech debt) to work on
- [ ] Set up a communication channel (Teams/Slack) for event-day Q&A
- [ ] Test Copilot access in the event venue (firewall/proxy considerations)
- [ ] Prepare a short demo codebase for the kickoff demo (5-10 min live coding)

### Day Before
- [ ] Verify venue WiFi can handle simultaneous Copilot usage
- [ ] Prepare screen sharing for kickoff demo
- [ ] Print or share digital copies of the [Copilot Cheat Sheet](resources/copilot-cheat-sheet.md)
- [ ] Pre-form teams (or plan team formation activity)

---

## Run-of-Show

### 9:00 – 9:30 · Kickoff (30 min)

**Talking Points:**
1. **Welcome & goals** (5 min)
   - "Today's goal: learn GitHub Copilot by shipping real work on your own codebase"
   - This isn't a competition — focus on learning and experimenting
   - By end of day, every team should have something to showcase

2. **Copilot feature walkthrough** (15 min) — Live demo covering:
   - **Inline completions** — Type a comment, let Copilot complete the code
   - **Copilot Chat** — Ask questions, explain code, get suggestions (`Ctrl+Alt+I`)
   - **Inline Chat** — Quick edits in context (`Ctrl+I`)
   - **Agent Mode** — Multi-step autonomous coding (`Ctrl+Shift+I`)
   - **Context references** — `@workspace`, `#file`, `#selection`, `@terminal`
   - **Slash commands** — `/tests`, `/fix`, `/explain`, `/doc`
   - **Enterprise features** — Bing web search, knowledge bases, PR summaries

3. **Challenge structure walkthrough** (10 min)
   - Explain the 6 challenge tracks and the BYOC format
   - Show how to navigate this repo
   - Emphasize: "Pick challenges relevant to YOUR codebase — you don't need to do them all"
   - Point out the [Prompt Library](resources/prompt-library.md) and [Cheat Sheet](resources/copilot-cheat-sheet.md)

### 9:30 – 10:00 · Setup (30 min)

- Walk teams through the [Getting Started guide](00-getting-started/SETUP.md)
- Circulate and help with any access/config issues
- Have teams complete the warm-up exercises before moving to challenges
- **Key check:** Every team member can open Copilot Chat and get a response

### 10:00 – 12:00 · Challenge Block 1 (2 hrs)

- Teams self-select challenges from the menu
- Facilitators float between teams:
  - Help teams pick appropriate challenges for their codebase
  - Share prompt tips when teams get stuck
  - Encourage teams to try the `@workspace` context reference early — it's a game-changer
  - Remind teams to document effective prompts and interesting results

**Check-in prompts to ask teams:**
- "What challenge are you working on?"
- "Have you tried using `@workspace` to give Copilot more context?"
- "What's the most useful thing Copilot has done so far?"
- "Have you tried Agent mode yet?"

### 12:00 – 12:45 · Lunch (45 min)

### 12:45 – 1:00 · Mid-Day Check-in (15 min)

**Quick round-robin (2 min per team):**
- What challenge did you work on this morning?
- What's one thing Copilot did really well?
- What's one thing that surprised you (good or bad)?

**Facilitator notes:**
- Highlight common wins across teams
- Address any shared pain points
- Suggest afternoon challenges based on morning experiences
- If teams finished early: point them to Agent Mode challenges or stretch goals

### 1:00 – 3:30 · Challenge Block 2 (2.5 hrs)

- Encourage teams to try a different challenge track
- Push teams toward Agent Mode if they haven't tried it
- At 2:30, give a **60-minute warning** for showcase prep
- Remind teams to prepare a 3-5 minute demo of their work

### 3:30 – 4:15 · Team Showcase (45 min)

**Format:** Each team gets 3-5 minutes to present.

**Suggested showcase structure:**
1. What challenge(s) did you tackle?
2. Live demo or screen share of what you built/improved
3. Most effective prompt or workflow you discovered
4. One "aha moment" and one limitation you hit

**Facilitator tips:**
- Keep time strictly — use a visible timer
- Encourage applause/reactions after each team
- Note common themes across presentations for the retro

### 4:15 – 4:30 · Retro & Wrap-up (15 min)

**Discussion prompts:**
- "What's one thing you'll start using Copilot for tomorrow?"
- "What feature were you most impressed by?"
- "Where did Copilot struggle or give you bad results?"
- "What would help you use Copilot more effectively going forward?"

**Closing:**
- Share this repo link for continued reference
- Encourage teams to share their best prompts / workflows with the broader org
- Collect feedback (short survey if prepared)
- Thank everyone for participating

---

## Tips for Facilitators

### Common Challenges & How to Help

| Situation | Response |
|-----------|----------|
| Team doesn't know what to work on | Help them pick a small, well-defined feature or bug from their backlog |
| Copilot gives poor suggestions | Check the context: are they using `@workspace`? Is the prompt specific enough? Suggest the [Prompt Library](resources/prompt-library.md) |
| Team is stuck on setup | Pair them with a team that's already running; check [Troubleshooting](resources/troubleshooting.md) |
| Team finishes challenges early | Point them to Agent Mode track, stretch goals, or ask them to help other teams |
| Copilot isn't activating | Check license, extension version, network connectivity. See [Troubleshooting](resources/troubleshooting.md) |

### Team Composition Suggestions

The ideal team has a mix of roles for richer exploration:

- **2 developers** — Drive coding challenges, compare prompt strategies
- **1 tester/QA** — Focus on testing challenges, validate generated tests
- **1 architect/tech lead** — Drive planning and review challenges, evaluate architecture suggestions

Teams of all developers work fine too — the key is having at least 2 people so they can compare approaches and learn from each other.

### What Success Looks Like

By end of day, successful teams will have:
- ✅ Shipped at least one real change (feature, bugfix, refactor, tests, docs) to their codebase
- ✅ Identified 3-5 effective prompt patterns they'll reuse
- ✅ Understood when Copilot excels and when it needs more guidance
- ✅ Tried at least 2 different Copilot interaction modes (completions, Chat, inline Chat, Agent)
- ✅ Have a personal workflow for integrating Copilot into their daily development

---

*Questions about facilitating? Reach out to the event organizers.*
