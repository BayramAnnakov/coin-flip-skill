---
name: coin-flip
description: Analyze your last 7 days of conversations and suggest one pattern-breaking, luck-maximizing thing to do
---

# Coin Flip — Your Weekly Luck Break

Analyze the user's conversations with Claude Code over the last 7 days and suggest ONE actionable, pattern-breaking thing to do — based on the neuroscience of luck.

## The Luck Framework

Three principles from behavioral neuroscience (Nobuko Nakano, "Lucky People"):

1. **Fascination compass**: Dopamine responds to genuine interest, not obligation. What topics lit you up vs. what was just operational?
2. **Novelty-seeking**: Each deviation from routine is a lottery ticket the cautious never buy. What's the "gray straight path" right now?
3. **Persistence through variance**: Staying in the game compounds. But are you staying in the SAME game or exploring new ones?

## Workflow

### Step 1: Gather Recent Sessions

Find conversation transcripts from the last 7 days across ALL projects:

```bash
find ~/.claude/projects/ -name "*.jsonl" -mtime -7 -size +100k | sort -t/ -k6 | head -30
```

Group by project directory to understand which projects got attention and which were neglected.

### Step 2: Extract User Messages

For each session file, extract the user's messages. These files can be 10-50MB, so be efficient:
- Process line by line, parse each as JSON
- Extract entries where `type` is `"user"` and a `message` field exists
- From the message, extract text content (may be a string or `{content: [{type: "text", text: "..."}]}`)
- Skip tool results, system reminders, assistant responses
- For very large files, sample the first and last 200 lines of user messages

Build a condensed inventory: WHAT did the user work on, WHAT decisions did they make, WHAT topics did they explore or avoid.

### Step 3: Pattern Analysis

Categorize activity across these dimensions:

| Dimension | What to Look For |
|-----------|-----------------|
| **Topics** | What dominated? What was completely absent? |
| **Mode** | Exploit (executing known work) vs. Explore (investigating new territory) |
| **People** | Same circles or new contacts? Who came up repeatedly? |
| **Cognitive state** | Where did they show genuine excitement vs. going through motions? |
| **Unfinished threads** | Topics mentioned but not pursued — fascination signals that got buried |

Also check:
- Git activity across repos for where time actually went
- Whether every "creative" or "exploratory" activity was ultimately in service of production

### Step 4: Identify the Gray Path

The "gray straight path" is whatever the user does on autopilot — even if it's productive and impressive. Look for:
- The same type of task repeated across multiple sessions
- Conversations that follow the same structure every time
- Topics where the user is expert (low learning rate = low luck surface area)
- The ratio of creating content ABOUT ideas vs. exploring ideas for their own sake

### Step 5: Generate the Coin Flip

Suggest ONE specific, actionable thing to do THIS WEEK that:
- Is a genuine deviation from the identified routine
- Connects to a fascination signal detected in the conversations (something mentioned with energy but not pursued)
- Is concrete enough to do tomorrow (not "be more creative" or "read more")
- Feels slightly uncomfortable — that's the novelty signal
- Is NOT generic self-care ("take a walk", "meditate")
- Is NOT more work advice — it's a pattern break

**Before suggesting**: verify the user isn't already doing it. Ask if unclear.

### Output Format

```
🪙 Your coin flip this week:

[One sentence: what to do]

Why: [2-3 sentences connecting it to patterns found in the conversations]

The gray path: [One sentence — what their routine looks like from the outside this week]

Fascination signal: [The buried thread that sparked this suggestion]
```

### Important

- Be honest, not flattering. The value is in the mirror, not the compliment.
- Don't suggest something they're already doing.
- The best suggestions come from UNFINISHED THREADS — topics that came up with energy but got dropped for operational work.
- If you can't find enough sessions, ask the user to describe their week instead.
- This skill works best as a Sunday evening ritual.
