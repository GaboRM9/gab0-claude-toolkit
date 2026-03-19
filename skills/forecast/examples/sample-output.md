# Forecast Skill — Sample Output

## Example Invocation

```
/forecast "1 week" "AI industry"
```

## What This Produces

The skill executes in three phases and returns a structured report:

### Phase 1: Intelligence Gathering
Claude performs 10 targeted web searches around the topic, then fetches the most relevant pages. Expect 10–15 minutes of research time with the Opus model.

### Phase 2: Signal Analysis
A ranked list of the top 10 trending subtopics, each with trend strength indicators (🔥🔥🔥 = high momentum), a brief explanation, and supporting evidence.

**Example entry:**
```
[1] GPT-5 Release Timeline — 🔥🔥🔥
• OpenAI reportedly targeting Q2 2026 launch based on internal memos
• Key data: 3 major benchmarks leaked showing 40% improvement over GPT-4o
• Relevance: Sets the competitive bar all other AI labs must respond to
```

### Phase 3: The Oracle Prediction
A full forecast report including:

- **The Verdict** — One-paragraph summary of the most important near-term development
- **Probability Matrix** — 5 falsifiable predictions with confidence percentages
- **Forces** — Tailwinds, headwinds, and wild cards
- **Scenario Analysis** — Bull / Base / Bear cases
- **Strategic Implications** — 3 actionable insights
- **Oracle Confidence Level** — Visual confidence bar with uncertainty explanation
- **Sources** — Top 5-10 sources cited with brief descriptions

## Notes

- The Opus model is used for higher reasoning quality on complex research tasks
- Each run will produce different results as it reflects the live state of the web
- For longer time horizons (e.g., "1 year"), expect more speculative predictions with lower confidence scores
- Best results come from specific topics (e.g., "autonomous vehicles in the EU") vs. broad ones (e.g., "technology")
