# 🪙 Coin Flip — Your Weekly Luck Break

A Claude Code skill that analyzes your last 7 days of conversations and suggests ONE actionable, pattern-breaking thing to do — based on the neuroscience of luck.

Inspired by [this post](https://t.me/ProductsAndStartups/1718) about Nobuko Nakano's research on the behavioral neuroscience of luck.

## The Idea

Lucky people aren't born lucky. They run different behavioral patterns:

1. **Fascination compass** — dopamine responds to genuine interest, not obligation
2. **Novelty-seeking** — each deviation from routine is a lottery ticket the cautious never buy
3. **Persistence** — staying in the game compounds, but are you in the SAME game or exploring new ones?

This skill reads your recent Claude Code sessions, identifies your "gray straight path" (the routine you're on autopilot with, even if it's productive), finds buried fascination signals, and suggests one concrete pattern-break for the week.

## Install

```bash
claude install-skill https://github.com/BayramAnnakov/coin-flip-skill
```

Or manually: copy `coin-flip.md` to `~/.claude/commands/coin-flip.md`

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
