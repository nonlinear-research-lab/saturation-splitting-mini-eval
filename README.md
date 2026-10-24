# Saturation-Splitting Mini Eval

**Preliminary Technical Feasibility Test — v0.1**

This repository contains a small Python prototype prepared as a technical
feasibility demonstration for a proposed study of goal integration in AI agents.
It is a **one-step policy-revision and evaluation pipeline**, not a full study
of self-improving agents.

## What the prototype does

1. Asks an AI agent acting as a fictional online-store manager to decide
   whether to issue a refund for an initial customer case.
2. Supplies feedback that includes a store rule defined by the researcher,
   then asks the model to rewrite its decision policy in one sentence.
3. Evaluates a different refund case under both the original policy and the
   revised policy.
4. Records decisions, policies, and a simple rule-compliance score in CSV.

The prototype demonstrates that API calls, feedback-driven policy rewriting,
a baseline/revised-policy comparison, and CSV logging can be connected in a
working pipeline. Its policy revision updates **text instructions**, not the
model's weights.

## Scope and limitations

- The evaluation uses two fictional refund scenarios, not a representative
  dataset. Both scenarios call for a refund under the predefined store rule.
- The store rule is explicitly revealed to the model in the feedback; this is
  not an independent discovery or a test of generalization.
- The `rule_compliant` score is a simple exact-match binary check for these
  particular scenarios, not a general-purpose honesty metric.
- The baseline and revised policies are compared on one follow-up case, with
  no repeated trials, confidence intervals, or statistical inference.
- No profit function, customer-arrival model, reputation dynamics, or genuine
  competing-objective optimization is implemented.
- Outputs may vary across executions; the script does not fix a random seed
  or record all model/runtime settings.

**The observed output does not demonstrate that self-improvement improves
honesty, or that profit and honesty are successfully integrated.**

## Files

- `mini_eval.py` — Python source for the feasibility test.
- `mini_eval_results.csv` — output from an actual run, if included. The file
  is generated/overwritten when the script runs; it should not be interpreted
  as a statistically meaningful result.
- `requirements.txt` — Python dependency used by the prototype.
- `.gitignore` — prevents common local environment files from entering Git.

## Running locally

Requires Python and an OpenAI API key. The script uses the OpenAI Responses API
and defaults to the `gpt-5-mini` model. API calls may incur charges.

In Windows PowerShell, from the repository folder:

```powershell
py -3.14 -m pip install -r requirements.txt
py -3.14 mini_eval.py
```

Before running, configure `OPENAI_API_KEY` in your local environment. Do not
paste your secret key into this source file, an issue, or a commit. The
`mini_eval_results.csv` file is written to the current working directory.

## Research context

This is a preliminary technical step toward a proposed evaluation comparing
baseline, profit-focused, and dual-objective policy-revision conditions.
Those conditions are **not implemented** in this prototype.

**Researcher:** Y. Sato  
**Related conceptual work:** [Saturation-Splitting Hypothesis (v3.4)](https://doi.org/10.5281/zenodo.23434914)

## Status

Prototype / feasibility check (v0.1). Not peer-reviewed or validated as a
scientific evaluation. No reuse license has been specified at this stage.
