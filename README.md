# Chain-of-Thought & Persona Prompting — Before/After Comparison

**Project:** GenAI & Prompt Engineering Internship — Week 2, Project 2
**Organization:** Neurofive Solutions

## Overview

This project demonstrates the impact of **Chain-of-Thought (CoT) prompting** combined with **persona/role prompting** on a reasoning task. A single math word problem is run through an LLM twice:

1. **Plain prompt** — the question asked directly, with no reasoning instruction and no persona.
2. **CoT + persona prompt** — the same question, wrapped with an explicit "think step-by-step" instruction and a relevant expert persona.

The two responses are compared for **correctness** and **clarity**.

## The problem used

> A bat and a ball cost $1.10 together. The bat costs $1.00 more than the ball. How much does the ball cost?

This is a well-known reasoning-trap problem: the intuitive answer ($0.10) is wrong, because it doesn't satisfy the problem's own conditions. It's a strong test case for showing whether a prompting technique induces real reasoning or just surface-level pattern matching.

## Repo structure

```
cot-persona-prompting/
├── README.md                       <- this file
├── prompts/
│   ├── 01_plain_prompt.txt         <- prompt with no CoT, no persona
│   └── 02_cot_persona_prompt.txt   <- prompt with CoT instruction + persona
├── outputs/
│   ├── 01_plain_response.md        <- model's response to the plain prompt
│   └── 02_cot_persona_response.md  <- model's response to the CoT+persona prompt
├── comparison_and_explanation.md   <- side-by-side comparison + written analysis
└── video/
    └── demo_link.md                <- link to the 2-3 min side-by-side video
```

## Key concepts covered

- **Chain-of-Thought (CoT) prompting** — explicitly instructing a model to reason step by step before giving a final answer, which surfaces (and often prevents) reasoning errors that a direct answer would hide.
- **Persona / role prompting** — framing the request as coming from a specific expert role, which biases the model toward that role's vocabulary, conventions, and rigor.
- **Reasoning models vs. standard chat models** — some models reason step-by-step by default; standard chat models only do so when explicitly prompted, which is why CoT prompting is such a strong lever for them.

## Result summary

| | Plain Prompt | CoT + Persona Prompt |
|---|---|---|
| Answer | $0.10 (incorrect) | $0.05 (correct) |
| Reasoning shown | None | Full step-by-step derivation + verification |

Full analysis in [`comparison_and_explanation.md`](./comparison_and_explanation.md).

## Video demo

2–3 minute recording showing both runs side by side: see [`video/demo_link.md`](./video/demo_link.md) (LinkedIn post, tagging Neurofive Solutions).

## How to reproduce

1. Copy the contents of `prompts/01_plain_prompt.txt` into any LLM chat interface. Record the response.
2. Start a **new, separate conversation** (important — don't reuse the same context) and copy in `prompts/02_cot_persona_prompt.txt`. Record the response.
3. Compare against the conditions in the original problem to check correctness.
