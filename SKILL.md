---
name: coin-flip
description: Analyze your last 7 days of conversations and suggest one pattern-breaking, luck-maximizing thing to do
---

# Coin Flip — Your Weekly Luck Break

Analyze the user's conversations with Claude Code over the last 7 days and suggest ONE actionable, pattern-breaking thing to do — based on the neuroscience of luck.

## The Luck Framework

Five mechanisms from behavioral neuroscience (Nobuko Nakano, "Lucky People", Gallery UK 2026):

1. **Self-narrative**: Declaring "I am lucky" activates the prefrontal cortex, shifting perception from threat-detection mode toward opportunity-recognition mode. Over weeks, these perceptual micro-advantages compound. Are you framing your work as problems to solve or opportunities to seize?
2. **Fascination compass**: The brain's dopamine system responds most powerfully to genuine interest. "Pursue what society tells you to want, and dopamine trickles. Pursue what fascinates you and it floods the circuits of perception and creativity." What topics lit you up vs. what was just operational?
3. **Novelty-seeking**: Lucky people try the unfamiliar restaurant, take the scenic route, talk to strangers. "Each small departure from routine is, in effect, a ticket in a lottery that the cautious never enter." What's the "gray straight path" right now?
4. **Authentic generosity**: Acts of genuine giving activate the striatum (the brain's deepest reward center) more powerfully than receiving. Transactional helping mutes the response; authentic caring amplifies it. This builds the social capital that "opens doors they did not even know existed." Are all your interactions transactional?
5. **Persistence**: Game theory simulations show long-term outcomes overwhelmingly favor those who stay in the game. "The arithmetic is merciless: withdraw, and your probability of future success falls to zero." But are you staying in the SAME game or exploring new ones?

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
| **Framing** | Threat-detection ("fix this", "we have a problem") vs. opportunity-recognition ("what if we", "I want to try")? This maps to Nakano's self-narrative mechanism — prefrontal cortex activation |
| **People** | Same circles or new contacts? Who came up repeatedly? Were interactions purely transactional or was there authentic generosity — helping without expectation of return? |
| **Cognitive state** | Where did they show genuine excitement vs. going through motions? What made them lose track of time (fascination compass)? |
| **Unfinished threads** | Topics mentioned but not pursued — fascination signals that got buried under operational work |

Also check:
- Git activity across repos for where time actually went
- Whether every "creative" or "exploratory" activity was ultimately in service of production
- The ratio of giving (teaching, helping, sharing) vs. extracting (selling, optimizing, producing)

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

💡 Luck hygiene check:
- Morning sunlight: Are you getting natural light in your first waking minutes? (Serotonin production requires it — Nakano's biology pillar)
- If you wear a sleep tracker, share your sleep data — irregular sleep suppresses serotonin and "closes down the peripheral awareness where serendipity lives"
```

### Important

- Be honest, not flattering. The value is in the mirror, not the compliment.
- Don't suggest something they're already doing.
- The best suggestions come from UNFINISHED THREADS — topics that came up with energy but got dropped for operational work.
- If you can't find enough sessions, ask the user to describe their week instead.
- This skill works best as a Sunday evening ritual.
