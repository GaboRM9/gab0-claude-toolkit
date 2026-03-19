# /forecast

**Predict the future of any topic using live internet research.**

THE ORACLE runs 10 adaptive web searches, builds a Topic Profile before touching the web, finds the historical parallel, and delivers a sharp forecast report — for any topic, any language, any domain.

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
| `topic` | Yes | What to forecast | Literally anything |

**Rules:**
- `$0` = time-horizon, `$1` = topic
- One argument → treated as topic, time horizon defaults to **1 month**
- Broad topics auto-narrow to the most signal-rich sub-topic — no prompting

---

## Examples

### Business & Tech
```
/forecast "1 month" "OpenAI"
/forecast "3 months" "NVIDIA stock"
/forecast "6 months" "electric vehicle adoption"
/forecast "1 year" "quantum computing"
/forecast "2 weeks" "crypto market"
```

### Politics & World
```
/forecast "3 months" "Brazilian elections"
/forecast "1 month" "US-China trade war"
/forecast "6 months" "French politics"
/forecast "1 week" "Mexico"
/forecast "1 year" "Indian economy"
```

### Culture & Entertainment
```
/forecast "1 month" "Taylor Swift"
/forecast "3 months" "K-pop"
/forecast "1 season" "anime spring 2026"
/forecast "6 months" "Netflix"
/forecast "2 months" "Kendrick Lamar"
```

### Sports
```
/forecast "1 month" "Real Madrid"
/forecast "season" "Formula 1 2026"
/forecast "3 months" "NBA playoffs"
/forecast "1 year" "women's football"
/forecast "tournament" "2026 FIFA World Cup"
```

### Science & Environment
```
/forecast "1 year" "coral reef bleaching"
/forecast "5 years" "nuclear energy"
/forecast "6 months" "GLP-1 weight loss drugs"
/forecast "2 years" "gene editing"
/forecast "1 month" "California wildfire season"
```

### Weird & Niche
```
/forecast "1 year" "Minecraft"
/forecast "3 months" "Stanley cups"          ← the water bottle brand
/forecast "6 months" "remote work"
/forecast "1 month" "Joe Rogan"
/forecast "2 years" "lab-grown meat"
```

---

## What It Produces

All research runs silently. The user sees only the final report:

| Section | What It Contains |
|---------|-----------------|
| **Pull quote** | One bold, falsifiable sentence — the Oracle's sharpest call |
| **The Verdict** | 2–3 sentences on the most important thing that will happen and why |
| **Momentum** | ACCELERATING / STABLE / DECELERATING — rate of change, not just direction |
| **What I'm Betting On** | 5 predictions with explicit causal chains: *Because [signal] → Therefore [outcome]* |
| **What Everyone's Getting Wrong** | Consensus vs. strongest counter-argument, backed by specific data |
| **The Historical Parallel** | Closest historical analogue, what it predicts, where it breaks down |
| **The Forces at Play** | Tailwinds, headwinds, and wild cards from real research |
| **How It Plays Out** | Best / Most likely / Worst scenarios, probabilities summing to 100% |
| **What to Do With This** | 3 human-level takeaways — useful whether you're involved or just curious |
| **How Confident Is The Oracle?** | Honest uncertainty — names the single biggest risk to the forecast |
| **Sources** | 6–8 primary sources, linked |
| **Now try:** | Best follow-up question surfaced by the research |

---

## How the Research Works (Internal)

Hidden from the user. Every run:

1. **Date resolution** — TODAY, CURRENT_YEAR, LAST_YEAR, NEXT_YEAR. Never hardcoded.
2. **Topic Profile** — before any searching, derives four things:
   - *Language:* what language are the authoritative sources in?
   - *Source type:* who produces ground truth here — government agency, journal, sports federation, fan database, trade press?
   - *Native vocabulary:* what words do insiders use for "things going well" and "things going wrong"?
   - *Time scale:* what's the natural cadence of change — election cycles, season arcs, fiscal quarters, product windows?
3. **Domain classification** — for orientation only. The Topic Profile overrides.
4. **10 adaptive searches** — constructed from the Topic Profile, not from preset templates:
   - Ground truth in the topic's own terms
   - Primary authoritative sources (derived per topic and language)
   - Expert forward view in native terminology
   - Where observers in this community were wrong
   - Historical parallel
   - 3 signal categories specific to this topic
   - Contrarian case from inside the community
   - Most relevant external pressure
5. **Fetch** 6 most information-dense pages — in any language
6. **Internal synthesis** — momentum score, historical analogue, 5 signals with counter-evidence, noise exclusion

---

## Why It's Domain-Agnostic

The skill builds the right research strategy for each topic instead of applying the same template to everything:

| Topic | Authoritative sources | Native signal vocabulary |
|-------|----------------------|-------------------------|
| K-pop act | Hanteo/Gaon charts, Melon streams | "차트 성적", fandom size, comeback schedule |
| Brazilian election | TSE filings, Datafolha polling | coalização, segundo turno, IBGE demographics |
| Manga series | Oricon sales, Weekly Shonen Jump | tankōbon volume ranking, sequel greenlight |
| Coral reef | NOAA, IUCN, CoralWatch | bleaching alert level, SST anomaly, recovery rate |
| NBA team | Basketball-Reference, ESPN | net rating, injury report, trade deadline |
| OpenAI | Bloomberg, FT, SEC filings | ARR, compute cost, model release cadence |

Same Oracle. Different lens for each world.

---

## Tips

- **Shorter horizon = higher confidence.** 1-week forecasts are sharper than 1-year forecasts.
- **Specific > broad.** `"USMCA renegotiation"` beats `"trade"`. `"Zach Bryan"` beats `"country music"`.
- **Single-arg shorthand works.** `/forecast "Real Madrid"` defaults to 1 month — fastest way to run it.
- **Each run is live.** Results reflect the web at the moment of invocation. Run it again tomorrow and you might get a different answer.
- **Follow the "Now try:"** — the Oracle suggests the most interesting adjacent topic from its own research. It's usually better than whatever you were going to ask next.

---

## Model

Uses the latest Claude Opus — maximum reasoning quality for research synthesis and probabilistic forecasting.

---

## Files

```
skills/forecast/
├── SKILL.md                    # The skill prompt
├── README.md                   # This file
└── examples/
    └── sample-output.md        # Annotated example output
```
