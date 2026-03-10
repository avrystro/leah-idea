# Quiz Design

## Flow

Welcome screen -> Q1 -> Q2 -> Q3 -> Q4 -> Q5 -> Results (top 3 ranked)

## Questions

### Q1: "What's most affecting your wellbeing right now?"
Maps to: mental health condition

| Answer | Maps To |
|--------|---------|
| "I've been feeling down or sad" | depression |
| "I've been feeling worried or anxious" | anxiety |
| "I've been feeling stressed or overwhelmed" | stress |
| "I've been feeling low energy or unmotivated" | low_energy (maps to depression + general_wellbeing) |
| "I just want to feel better overall" | general_wellbeing |

### Q2: "How active are you right now?"
Maps to: activity level (affects intensity recommendation)

| Answer | Maps To |
|--------|---------|
| "Not very active - mostly sitting" | sedentary |
| "A little active - some walking or light movement" | light |
| "Fairly active - I move regularly but want more" | moderate |

### Q3: "What kind of movement appeals to you?"
Maps to: exercise preference category

| Answer | Maps To |
|--------|---------|
| "Something calm and mindful" | mindful (yoga, tai chi/qigong, pilates, stretching) |
| "Something more active and energetic" | energetic (cardio, running, cycling, sports, HIIT) |
| "A mix of both" | mixed (walking, dance, swimming, moderate exercise) |

### Q4: "Where would you prefer to move?"
Maps to: setting filter

| Answer | Maps To |
|--------|---------|
| "At home - no equipment needed" | home |
| "Outdoors" | outdoor |
| "A gym or studio" | gym |
| "No preference" | any |

### Q5: "How much time could you set aside for this?"
Maps to: duration recommendation

| Answer | Maps To |
|--------|---------|
| "15-20 minutes" | short |
| "About 30 minutes" | medium |
| "45 minutes or more" | long |

## Scoring Logic

1. Q1 determines the PRIMARY scoring axis - which mental health condition we're matching against
2. Q3 determines the PREFERENCE filter - which exercise categories score bonus points
3. Q2 determines the INTENSITY recommendation within the chosen exercise
4. Q4 applies a SETTING filter (boost exercises that fit the setting, don't eliminate others)
5. Q5 shapes the DURATION in the final recommendation text

### Scoring Algorithm

For each exercise in the matrix:
- Start with base_score = evidence_strength for the user's Q1 condition
  - strong = 10, moderate = 7, promising = 4, insufficient = 1
- Apply Q3 preference multiplier:
  - If exercise matches preference category: x1.5
  - If exercise is in "mixed" and user chose "mixed": x1.3
- Apply Q4 setting bonus:
  - If exercise fits the chosen setting: +2
  - "No preference" = no bonus applied (all equal)
- Sort by final score, return top 3

### Result Output Per Exercise

Each of the 3 results shows:
1. Exercise name (friendly, not clinical)
2. Why it matches them (1-2 sentences connecting their Q1 answer to the evidence)
3. A simple starter routine (what to do, for how long, based on Q2 activity level and Q5 time)
4. Evidence callout ("X% of studies found significant benefits for [condition]")
5. "Build from here" note on the #1 pick: "Start with once a week. Research shows 3-5 sessions per week delivers optimal benefits - let this become your foundation."

## Tone

Warm, encouraging, personal. Not clinical. Not preachy.
- "Go for a brisk 30-minute walk" not "Engage in moderate-intensity ambulatory exercise"
- "87% of studies found this helps" not "p < 0.05 in 87% of RCTs"
- "This is your starting point" not "Recommended protocol"
