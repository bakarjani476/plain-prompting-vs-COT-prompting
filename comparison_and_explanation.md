# Comparison & Explanation

## Side-by-side comparison

| | Run 1 (Plain Prompt) | Run 2 (CoT + Persona Prompt) |
|---|---|---|
| **Answer given** | $0.10 (incorrect) | $0.05 (correct) |
| **Reasoning shown** | None | Full algebraic setup, solved step by step |
| **Verification** | None | Explicitly checks the answer against both original conditions |
| **Correctness** | Fails — violates the problem's own conditions | Passes — satisfies both conditions |
| **Clarity** | Single unsupported statement | Transparent, auditable reasoning chain |

## Why Chain-of-Thought + Persona changed the result (3–4 sentences)

Chain-of-Thought prompting improved the result because it forced the model to write out its algebraic reasoning (defining variables, setting up an equation, solving step by step) instead of jumping straight to a superficially plausible answer. This is exactly what avoided the classic "$0.10" trap: the plain prompt pattern-matched to the intuitive-but-wrong subtraction, while the step-by-step version derived the answer from an actual equation and then verified it against both original conditions. The persona ("expert mathematician who always double-checks") reinforced this specifically — it's a persona chosen to target this problem's known failure mode, not a generic label, so it nudged the model toward the careful verification step that caught the error. Together, the two techniques didn't just make the output sound more expert — they changed the actual computational path the model took, which is why correctness improved, not just clarity.
