# /forecast

**Predict the future of any topic using live internet research.**

THE ORACLE runs 13 structured web searches, classifies signals, finds the historical parallel, and delivers a sharp forecast report — for any topic, any time horizon.

---

## Install

```bash
cp skills/forecast/SKILL.md ~/.claude/commands/forecast.md
```

---

## Invoke

```
/forecast "[time-horizon]" "[topic]"
```

**Arguments:**

| Argument | Required | Description | Example |
|----------|----------|-------------|---------|
| `time-horizon` | No | How far ahead to predict | `"1 week"`, `"3 months"`, `"1 year"` |
| `topic` | Yes | What to forecast | `"Mexico"`, `"OpenAI"`, `"K-pop"` |

**Argument rules:**
- Both arguments are positional: `$0` = time-horizon, `$1` = topic
- If you pass only one argument, it is treated as the topic and the time horizon defaults to **1 month**
- Broad topics (e.g. "AI", "sports") are auto-narrowed to the most timely sub-topic — no prompting required

---

## Examples

```
/forecast "1 week" "Mexico"
/forecast "3 months" "OpenAI"
/forecast "1 year" "electric vehicles"
/forecast "quantum computing"         ← single arg, defaults to 1 month
/forecast "2 weeks" "2026 FIFA World Cup"
/forecast "6 months" "US immigration policy"
/forecast "1 month" "K-pop"
```

---

## What It Produces

The skill runs all research silently. The user sees only the final report, structured as:

### Output Sections

| Section | What It Contains |
|---------|-----------------|
| **Pull quote** | One bold, screenshot-worthy sentence — the Oracle's sharpest single call |
| **The Verdict** | 2–3 sentences on the most important thing that will happen and why |
| **Momentum** | ACCELERATING / STABLE / DECELERATING — rate of change, not just direction |
| **What I'm Betting On** | 5 falsifiable predictions with explicit causal chains: *Because [signal] → Therefore [outcome]* |
| **What Everyone's Getting Wrong** | The contrarian case: consensus vs. strongest counter-argument, backed by data |
| **The Historical Parallel** | Closest historical analogue, what it predicts, where it breaks down |
| **The Forces at Play** | Tailwinds, headwinds, and wild cards tied to real research signals |
| **How It Plays Out** | Bull / Base / Bear scenarios with triggers and outcomes, probabilities summing to 100% |
| **What to Do With This** | 3 human-level takeaways for anyone curious about the topic |
| **How Confident Is The Oracle?** | Honest uncertainty paragraph naming the single biggest risk to the forecast |
| **Sources** | 6–8 primary sources used in the research |
| **Now try:** | Suggested follow-up invocation based on what surfaced in research |

---

## How the Research Works (Internal)

Hidden from the user. Runs in this order:

1. **Date resolution** — determines TODAY, CURRENT_YEAR, LAST_YEAR, NEXT_YEAR dynamically
2. **Domain detection** — classifies the topic: Business/Markets, Technology/Science, Politics/Geopolitics, Culture/Society, Environment/Health, or Other
3. **13 searches across 4 tiers:**
   - Tier 1 (all domains): ground truth, primary news sources, research papers
   - Tier 2 (all domains): expert forecasts, failed predictions, historical analogues
   - Tier 3 (domain-adaptive): 4 searches tuned to the detected domain
   - Tier 4 (all domains): skeptics/critics, disruption signals, cross-domain spillover
4. **Fetch** the 8 most information-dense pages
5. **Momentum scoring**: ACCELERATING / STABLE / DECELERATING
6. **Signal synthesis**: 5 highest-conviction signals with counter-evidence
7. **Noise exclusion**: 2 prominent-but-irrelevant items identified and excluded
8. **Historical analogue**: closest parallel from history identified

---

## Domain-Adaptive Searches

Tier 3 search queries change based on the detected topic type:

| Domain | Searches focus on |
|--------|------------------|
| Business/Markets | Investment, workforce, regulation, market share |
| Technology/Science | Breakthroughs, adoption, talent/funding, failure cases |
| Politics/Geopolitics | Polling, legislation, international reaction, historical precedent |
| Culture/Society | Audience/reach, cultural impact, backlash, what's replacing it |
| Environment/Health | Measurements, policy adoption, scientific consensus, tipping points |
| Other | Momentum, key events, stakeholders, adjacent field spillover |

---

## Tips

- **Shorter horizons = higher confidence.** A 1-week forecast will be sharper than a 1-year forecast.
- **Specific topics = better results.** `"USMCA renegotiation"` beats `"trade"`.
- **Broad topics auto-narrow.** The skill picks the most signal-rich sub-topic and tells you what it chose.
- **Each run is unique.** Results reflect the live state of the web at the time of invocation.
- **The "Now try:" suggestion** at the end of every report gives you the logical next question to ask.

---

## Model

Uses `claude-opus-4` (or latest Opus) — the most capable model — because research synthesis and probabilistic reasoning benefit from maximum reasoning quality.

---

## Files

```
skills/forecast/
├── SKILL.md                    # The skill prompt
├── README.md                   # This file
└── examples/
    └── sample-output.md        # Annotated example output
```
