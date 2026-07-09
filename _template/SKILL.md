---
name: skill-name-in-kebab-case
description: >-
  <One or two sentences, third person, that tell Claude WHAT this skill does and
  WHEN to use it. Include the real phrasings that should trigger it. Be specific —
  this is the single most important field for the skill firing at the right time.
  Also say what it does NOT do, if there's a risk of over-triggering.>
---

# <Skill title>

<!-- Delete these comments as you fill the template in. Keep sections that apply;
     remove those that don't. The order below works well for most skills. -->

## Context

<Who this is for and the business background Claude needs. Why the task matters,
and any domain-specific facts that change what "good" looks like. Keep it tight —
only what changes the skill's behaviour.>

## What this skill is and is not

- IS: <the job it does well>
- IS NOT: <adjacent things it should not attempt — route those elsewhere>

## Method

<Step-by-step how Claude should do the task. Favour judgement over string-matching:
describe the concepts to look for, how to weigh them, and how clauses/inputs
interact. Tell Claude to detect what's MISSING, not just what's present.>

1. <step>
2. <step>
3. **Separate what you can judge from what a human must decide.** Mark the latter
   clearly and say exactly what decision is needed — never fake input you don't have.

## Output format

<Give an exact template. Consistent, scannable output is what makes a skill
trustworthy. Show the structure with a fenced block.>

```
<field>: ...
<field>: ...
```

## Few-shot examples

<1–3 worked examples: a realistic input, then the exact output the skill should
produce. Examples calibrate the concepts far better than more instructions —
include a tricky/edge case, not just the easy one.>

### Example 1 — <short label>
**Input:** <realistic input>
**Output:**
```
<the ideal output>
```

## Edge case handling

<How to behave when things are ambiguous, incomplete, or out of scope. The key
rule for most skills: when unsure, escalate or flag for a human — never return a
false "all clear".>

- **<edge case>** → <behaviour>
- **Out of scope / unrecognised input** → say so and stop; don't improvise.
- **Missing information** → ask or flag it; don't assume the convenient case.
