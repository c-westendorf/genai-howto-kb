---
title: DS-Specific Patterns
updated: 2026-01-17
---

# DS-Specific Patterns

Patterns for data science work: experiment design, statistical analysis, model interpretation, data quality.

---

## Experiment design

### Pattern: Hypothesis exploration

Before committing to an experiment:

```text
I want to test: [hypothesis]

Context:
- Business goal: [what we're trying to achieve]
- Available data: [what we have]
- Constraints: [time, resources, ethical]

Help me explore:
1. Is this hypothesis testable? How would we measure it?
2. What are the key assumptions?
3. What sample size would we need?
4. What confounders should we control for?
5. What's the null hypothesis? What would falsify our hypothesis?
```

### Pattern: Experiment plan

Structure the experiment:

```text
Design an experiment for: [hypothesis]

Return:
1. **Objective**: What we're measuring
2. **Hypothesis**: H0 and H1
3. **Metrics**: Primary and secondary
4. **Sample**: Who, how many, how selected
5. **Duration**: How long and why
6. **Controls**: What we're holding constant
7. **Analysis plan**: Statistical methods
8. **Success criteria**: What result means we act
9. **Risks**: What could invalidate results
```

### Pattern: Pre-mortem on experiment design

Stress-test before running:

```text
Here's my experiment plan:
"""
[paste plan]
"""

Pre-mortem: The experiment ran but results are useless. Why?

1. What statistical problems could occur?
2. What business/practical issues could arise?
3. What confounders did we miss?
4. What if the effect is real but we can't detect it?
5. What if we detect an effect that isn't real?
```

---

## Statistical analysis

### Pattern: Analysis approach exploration

Before diving into analysis:

```text
I have this data: [describe dataset]

Question: [what I'm trying to answer]

Explore analysis approaches:
1. What's the right statistical framework?
2. What assumptions does this require?
3. How should I handle [specific issue: missing data, outliers, etc.]?
4. What visualizations would help?
5. What would make me confident in the results?
```

### Pattern: Results interpretation

Interpret findings carefully:

```text
Here are my results:
"""
[paste statistical output]
"""

Help me interpret:
1. What does this actually tell us?
2. What does it NOT tell us?
3. How should I communicate this to non-technical stakeholders?
4. What caveats or limitations should I mention?
5. What would I want to investigate next?
```

### Pattern: Sanity check

Verify analysis makes sense:

```text
I ran this analysis: [describe]

Results: [key findings]

Sanity check:
1. Do these numbers make sense given domain knowledge?
2. What would explain this if it's wrong?
3. What simple check could validate this?
4. If I were a skeptic, what would I attack?
```

---

## Model interpretation

### Pattern: Model explanation

Explain model behavior:

```text
This model [type] predicts [target] using [features].

Key metrics: [performance numbers]

Help me explain:
1. What's driving predictions? (feature importance intuition)
2. How should I explain this to stakeholders?
3. What are the model's blindspots?
4. Where would I expect it to fail?
5. What would make me trust/distrust its predictions?
```

### Pattern: Model card generation

Document a model:

```text
Create a model card for:

Model type: [type]
Target: [what it predicts]
Features: [input features]
Training data: [description]
Performance: [metrics]

Include:
1. Intended use cases
2. Out-of-scope use cases
3. Known limitations
4. Bias considerations
5. Performance across subgroups (if known)
6. When to retrain
```

### Pattern: Failure mode analysis

Understand where model breaks:

```text
This model: [description]

Analyze failure modes:
1. What inputs would likely cause wrong predictions?
2. What data drift would degrade performance?
3. What edge cases are poorly covered?
4. How would we detect these failures in production?
5. What's the cost of each failure type?
```

---

## Data quality

### Pattern: Data quality assessment

Evaluate a dataset:

```text
Assess this dataset:
"""
[paste schema, sample rows, or description]
"""

Check:
1. Completeness: Missing values, coverage
2. Consistency: Conflicting records, duplicates
3. Accuracy: Do values make sense?
4. Timeliness: Is it current enough?
5. Relevance: Does it answer our questions?

For each issue: severity (critical/medium/low) and suggested fix.
```

### Pattern: Data assumptions audit

Before using data:

```text
I'm about to use this data for: [analysis purpose]

Data: [description]

Audit my assumptions:
1. What am I assuming about data quality?
2. What am I assuming about data generation process?
3. What would invalidate these assumptions?
4. What checks should I run before proceeding?
```

---

## Business-outcome analysis methods

### Pattern: Analysis method selection

Map business questions to appropriate analytical methods:

```text
I have this business question: [question]

Business function: [marketing/operations/finance/product/etc.]
Available data: [what data exists]

Help me select the right analysis approach:
1. What type of business outcome are we trying to understand/predict/optimize?
2. What analysis methods map to this outcome type?
3. What data requirements does each method have?
4. What are the assumptions and limitations?
5. How do we translate results back to business terms?
```

### Analysis-to-outcome mapping table

| Business Outcome | Analysis Type | Methods | Key Considerations |
|------------------|---------------|---------|-------------------|
| Customer behavior prediction | Classification | Logistic regression, XGBoost, survival analysis | Interpretability vs. accuracy trade-off |
| Market segmentation | Clustering | K-means, hierarchical, latent class | Cluster validation, business meaning |
| Revenue optimization | Causal inference | A/B tests, diff-in-diff, propensity matching | Confounders, selection bias |
| Demand forecasting | Time series | ARIMA, Prophet, neural nets | Seasonality, trend, stationarity |
| Attribution | Multi-touch | Shapley values, Markov chains | Channel interactions, data availability |

### Pattern: Outcome-driven analysis planning

Start with the decision, work backward:

```text
Decision to be made: [decision]
Decision-maker: [who]
Timeline: [when needed]

Work backward:
1. What information would make this decision obvious?
2. What analysis would provide that information?
3. What data do we need?
4. What methods are appropriate given data constraints?
5. What confidence level is needed?
6. How should results be presented to this audience?
```

---

## Modeling methods for data tasks

### Pattern: Model selection framework

Map data tasks to modeling approaches:

```text
Data task: [prediction/classification/clustering/ranking/etc.]
Target variable: [what we're predicting/modeling]
Data characteristics:
- Size: [rows, columns]
- Types: [structured/unstructured/mixed]
- Quality: [clean/messy/missing values]

Help me select modeling approach:
1. What model families are appropriate for this task?
2. What are the trade-offs (interpretability, performance, complexity)?
3. What preprocessing is needed?
4. How should I validate?
5. What's the minimum viable approach to try first?
```

### Data task to modeling method map

| Data Task | Business Context | Methods | When to Use |
|-----------|------------------|---------|-------------|
| Binary classification | Churn, fraud, conversion | Logistic regression, trees, XGBoost | Need probability output, interpretability |
| Multi-class classification | Categorization, routing, tagging | Softmax, random forest, neural nets | Discrete categories, enough examples per class |
| Regression | Revenue, LTV, duration, pricing | Linear regression, XGBoost, neural nets | Continuous outcome, quantitative prediction |
| Clustering | Segmentation, anomaly grouping | K-means, DBSCAN, hierarchical | Discovery task, no labels available |
| Time series | Forecasting, trend analysis | ARIMA, Prophet, LSTM | Temporal patterns, seasonality |

### Pattern: Complexity ladder

Start simple, add complexity only when justified:

```text
Task: [task description]
Current approach: [what you have or tried]

Apply the complexity ladder:
1. **Baseline**: What's the simplest approach? (mean, mode, rule-based)
2. **Standard**: What's the standard industry approach? (logistic regression, random forest)
3. **Advanced**: What if standard underperforms? (XGBoost, neural nets)
4. **State-of-art**: If cost/complexity no object? (ensemble, deep learning)

For my case:
- Where should I start?
- What metric improvement justifies moving up?
- What are the costs of each level (compute, interpretability, maintenance)?
```

---

## Common DS pitfalls

| Pitfall | Signs | Fix |
|---------|-------|-----|
| P-hacking | Finding significance by trying many things | Pre-register analysis plan |
| Survivorship bias | Only looking at successful cases | Ask "what's missing from this data?" |
| Confounding | Correlation ≠ causation | Explicitly list potential confounders |
| Overfitting | Great training, poor generalization | Ask about cross-validation, holdout |
| Wrong metric | Optimizing for the wrong thing | Start with business goal, work backward |

---

## Verification for DS work

- [ ] **Reproducible**: Someone else could run this and get same results
- [ ] **Assumptions stated**: Statistical assumptions are explicit
- [ ] **Limitations acknowledged**: Know what this doesn't tell us
- [ ] **Robustness checked**: Sensitivity to different approaches
- [ ] **Domain sense-checked**: Results pass domain expert sniff test

---

## Related

- [Analysis Playbook](analysis.md) — general analysis patterns
- [Trust Calibration](../concepts/trust_calibration.md) — verification for DS work
- [Research Playbook](research.md) — literature and background research
