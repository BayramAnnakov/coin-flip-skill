# 🪙 Coin Flip — Your Weekly Luck Break

A Claude Code skill that analyzes your last 7 days of conversations and suggests ONE actionable, pattern-breaking thing to do — based on the neuroscience of luck.

Inspired by [this post](https://t.me/ProductsAndStartups/1718) about Nobuko Nakano's research on the behavioral neuroscience of luck.

## The Idea

Lucky people aren't born lucky. They run different neurological software — and it can be installed. Nakano identifies five mechanisms:

1. **Self-narrative** — declaring "I am lucky" shifts the prefrontal cortex from threat-detection to opportunity-recognition mode
2. **Biology** — serotonin production requires morning sunlight, tryptophan, and regular sleep
3. **Fascination compass** — dopamine responds to genuine interest, not obligation. "Each small departure from routine is a ticket in a lottery that the cautious never enter."
4. **Authentic generosity** — genuine giving activates the brain's reward center more powerfully than receiving
5. **Persistence** — game theory simulations show outcomes overwhelmingly favor those who stay in the game

This skill reads your recent Claude Code sessions, identifies your "gray straight path" (the routine you're on autopilot with, even if it's productive), finds buried fascination signals, and suggests one concrete pattern-break for the week.

## Install

```bash
npx skills add BayramAnnakov/coin-flip-skill -g -y
```

Or manually: copy to `~/.claude/skills/coin-flip/SKILL.md`

## Usage

```
/coin-flip
```

Best used as a **Sunday evening ritual**.

## What It Does

1. Scans your conversation transcripts from the last 7 days across all projects
2. Extracts your messages to map topics, cognitive mode (exploit vs. explore), and excitement signals
3. Identifies your "gray straight path" — what you do on autopilot
4. Finds unfinished threads — fascination signals that got buried under operational work
5. Suggests ONE specific, actionable thing to do this week

## Example Output

```
🪙 Your coin flip this week:

Have a 30-minute conversation with someone outside your field. No agenda.

Why: Your last 7 days were 100% exploit mode across 15 projects.
Every interaction was transactional — students, customers, team, leads.
The only pure-curiosity thread lasted 3 messages before you got interrupted.

The gray path: Build → ship → write about it → adapt → ship again.

Fascination signal: Two non-work reading items have survived 4 weeks
of inbox triage without being deleted or acted on.
```

## The Science

Based on Nobuko Nakano's "Lucky People" (Gallery UK, 2026) and supported by:
- Cascio et al. (2016) — self-affirmation activates medial prefrontal cortex
- DeYoung (2013) — dopamine as the neuromodulator of exploration
- Levitt (2020) — random coin flips help overcome status quo bias by 25%
- Mauboussin "Success Equation" — result = skill + luck; only skill is controllable

## License

MIT
