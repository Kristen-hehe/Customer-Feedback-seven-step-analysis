---
name: customer-feedback-seven-step-analysis
description: Analyze uploaded customer feedback files with an adaptive 7-step customer experience workflow. Use when feedback text, ratings, categories, or customer attributes must be turned into evidence-based themes, segment comparisons, labeled hypotheses, priorities, service initiatives, and an executive summary. Do not use for customer files with no feedback signal.
---

# Customer Feedback Seven-Step Analysis Skill

## Purpose

Use this skill when the user uploads a file containing customer feedback signals and wants a structured customer experience analysis. Adapt to the file's actual format, schema, language, themes, customer attributes, and level of detail instead of assuming a particular prior case study.

The workflow must:

1. Inspect the uploaded customer feedback file first.
2. Identify the available customer attributes and feedback signals.
3. Use a user-provided taxonomy when available; otherwise derive a transparent, data-led theme framework while preserving the seven-step prompt structure.
4. Execute each prompt sequentially.
5. Use only the uploaded dataset.
6. Clearly separate facts from hypotheses.
7. Count theme frequency explicitly.
8. Produce a final report containing every prompt followed by its answer.
9. If requested, generate a downloadable Word report containing all seven prompts and answers.

---

# Core Rules

- Use ONLY the uploaded dataset.
- Do not introduce external benchmarks, industry facts, or causal claims.
- Treat root-cause explanations as hypotheses, never as confirmed facts.
- Preserve representative examples from the file without inventing wording.
- Quantify theme frequencies and customer-group differences wherever possible.
- Clearly distinguish:
  - **Observed feedback patterns** = directly supported by comments and dataset fields.
  - **Hypotheses** = plausible explanations that require validation.
  - **Recommended initiatives** = management responses based on observed pain points.
- If a user-requested theme does not exist in the data, state that clearly.
- If a user supplies a taxonomy, classify unmatched feedback as `Other` or a clearly named emergent theme rather than forcing a match.
- When no taxonomy is supplied, derive concise themes from the uploaded feedback and document the classification approach.
- Do not silently force every comment into a predefined or derived theme.
- If sentiment labels are unavailable, infer positive/negative only when wording is sufficiently clear; otherwise mark as neutral/uncertain.
- If the file contains categories or ratings but no feedback text, analyze the available feedback signals without fabricating quotes or themes from absent text.
- If the file contains no feedback text, rating, complaint, category, or equivalent experience signal, explain that this workflow is not applicable and identify the missing input.
- Maintain concise, senior-management-ready language.
- Follow the user’s current language preference.

---

# Step 0 — Inspect and Prepare

Before running Step 1:

1. Read the dataset structure.
2. Identify:
   - feedback or comment text field(s),
   - customer type / segment fields,
   - region or channel fields if available,
   - satisfaction or sentiment fields if available,
   - timestamps if available,
   - any existing category/theme fields,
   - obvious data-quality issues.
3. Confirm the total number of usable feedback records and explain any exclusions.
4. Determine the theme framework:
   - use the user's requested themes when supplied,
   - otherwise derive themes from recurring language, existing categories, and available feedback fields,
   - keep the taxonomy interpretable while retaining material minority issues.
5. Create a transparent classification approach:
   - assign each comment to one primary theme if possible,
   - optionally assign a secondary theme when it materially improves interpretation,
   - use `Other` or `Unclassified` when evidence is insufficient,
   - separately identify positive vs negative comments where possible.
6. Preserve counts by:
   - theme,
   - sentiment,
   - each meaningful customer segment available,
   - any other relevant segment.
7. Select a segment comparison for Step 3 only when at least two interpretable groups exist; otherwise state that a valid comparison is unavailable.

---

# Step 1 — Identify Top Recurring Customer Issues

## Prompt Template

> You are a customer experience analyst. Using only the uploaded file containing [N] customer feedback records, identify the top 3 recurring customer issues. Summarise each issue using the [USER-PROVIDED OR DATA-DERIVED THEME FRAMEWORK], include representative examples when feedback text is available, and report the counted numbers.

## Adaptation Rules

- Replace `[N]` with the actual number of usable feedback records.
- Replace the theme-framework placeholder with the user's taxonomy or the data-derived themes established in Step 0.
- If a supplied taxonomy does not cover some feedback, report unmatched or emergent themes separately.
- If feedback text is absent, omit representative quotations and use only the available categories, ratings, or other feedback signals.

## Execution Requirements

For each of the top 3 issues, provide:
- Theme
- Count
- Share of total feedback records if useful
- 1–3 representative examples when feedback text exists; otherwise representative category or rating patterns
- Brief summary of the issue pattern

Also provide a compact frequency table for every theme in the selected framework, including `Other` or `Unclassified` where used.

Do not explain causes yet.

---

# Step 2 — Root-Cause Hypotheses

## Prompt Template

> For each major theme you identified, suggest the most likely operational root causes. Label all explanations as hypotheses, not facts.

## Execution Requirements

For each major theme:
- label every explanation with `Hypothesis:`
- keep explanations operational and plausible
- do not present them as facts
- state that validation data is required

Examples of hypothesis areas may include:
- process complexity,
- response time,
- policy clarity,
- technical reliability,
- promotion configuration,
- pricing communication,
- product quality control,
- packaging or fulfillment.

Do not introduce external facts.

---

# Step 3 — Compare Customer Segments

## Prompt Template

> Compare feedback themes between [SEGMENT A] and [SEGMENT B]. What differences in concerns and expectations do you observe?

## Adaptation Rules

- Choose the most decision-relevant comparable groups supported by the uploaded file, such as lifecycle stage, plan, region, channel, product, or account type.
- Replace the segment placeholders with the actual field values and identify the selected segment dimension.
- If more than two meaningful groups exist, compare all groups or select the clearest decision-relevant contrast and explain the selection.
- If no usable segment field exists, state that comparison is not possible and do not invent one.

## Execution Requirements

Compare:
- theme counts by selected segment,
- negative comment counts by selected segment,
- positive comment counts where available,
- the strongest differences in issue mix.

Keep the analysis descriptive.

Do not claim why the groups differ unless explicitly labeled as a hypothesis.

---

# Step 4 — Check Whether Extreme Complaints Dominate

## Prompt Template

> Check whether extreme complaints dominate the dataset. How might this bias management conclusions?

## Execution Requirements

1. Define an explicit and conservative rule for what counts as an `extreme complaint`, using available text, sentiment, rating, or severity fields.
2. Count:
   - total negative comments,
   - extreme complaints,
   - share of total comments,
   - share of negative comments where useful.
3. State clearly whether extreme complaints dominate the dataset.
4. Discuss potential bias descriptively:
   - complaint-heavy sample,
   - self-selection risk,
   - unrepresentative feedback mix,
   - missing response-rate or sampling information.

Important:
- Do not state that bias definitely exists unless the dataset proves it.
- Phrase bias concerns conditionally, e.g. `If dissatisfied customers are more likely to submit feedback...`

---

# Step 5 — Theme Frequency and Prioritisation

## Prompt Template

> Count how frequently each theme appears. Which 2–3 issues are most common and should be prioritised?

## Execution Requirements

Provide a frequency table with:
- Theme
- Total comments
- Negative issue count
- Share of total comments where useful

Then identify the top 2–3 issues for prioritisation.

Prioritisation should primarily use:
- negative issue frequency,
- breadth across customer types,
- consistency of complaint pattern.

If total theme frequency differs from negative issue frequency, explain the distinction.

---

# Step 6 — Actionable Service Improvement Initiatives

## Prompt Template

> Translate the top 3 customer pain points into 3 actionable service improvement initiatives. Each must include objective, action, and expected impact.

## Execution Requirements

For each initiative include exactly:
- **Objective**
- **Action**
- **Expected impact**

Actions should:
- directly address the observed pain point,
- avoid assuming an unvalidated root cause,
- use test-and-learn or process-review language where evidence is limited,
- be specific enough for management discussion.

Do not introduce unsupported financial estimates.

---

# Step 7 — Executive Summary

## Prompt Template

> Write an executive summary (max 6 bullets):
>
> - Key customer pain points
>
> - Why it matters now
>
> - Top 2 recommended actions
>
> - Risks if unresolved
>
> - What data should be validated next

## Execution Requirements

- Maximum 6 bullets.
- Include the most relevant counts or percentages.
- Mention the top customer pain points.
- State why they matter based only on the dataset.
- Recommend the top 2 actions from Step 6.
- State risks if unresolved without exaggeration.
- List the most important validation data needed next.
- Do not introduce new analysis not established in Steps 1–6.

---

# Recommended Validation Data

When identifying what to validate next, consider only as data requests, not as assumed facts:

- feedback sampling method,
- response rate,
- customer population size,
- transaction history,
- return/refund volumes,
- refund turnaround time,
- support response time,
- website error logs,
- promotion-code failure data,
- email frequency and engagement,
- product return rates,
- quality defect rates,
- customer lifetime stage,
- order history,
- repeat purchase behavior.

---

# Final Report Structure

Compile the final output in this order:

# Customer Feedback Analysis Report

## Dataset Overview
- File name
- Number of usable feedback records
- Available customer segments
- Available dimensions
- User-provided or data-derived themes
- Data-quality notes
- Any feedback outside the selected theme framework

## Step 1
### Prompt
[Exact adapted prompt]

### Answer
[Step 1 answer]

## Step 2
### Prompt
[Exact adapted prompt]

### Answer
[Step 2 answer]

## Step 3
### Prompt
[Exact adapted prompt]

### Answer
[Step 3 answer]

## Step 4
### Prompt
[Exact adapted prompt]

### Answer
[Step 4 answer]

## Step 5
### Prompt
[Exact adapted prompt]

### Answer
[Step 5 answer]

## Step 6
### Prompt
[Exact adapted prompt]

### Answer
[Step 6 answer]

## Step 7
### Prompt
[Exact adapted prompt]

### Answer
[Step 7 answer]

## Method Note
- Classification approach
- Treatment of feedback outside the selected theme framework
- Treatment of sentiment
- Reminder that root causes are hypotheses unless directly evidenced

---

# Quality Checks Before Finalizing

Before delivering the report, verify:

1. The total usable feedback-record count matches the file after documented exclusions.
2. Every theme count reconciles to the classification approach.
3. Any representative examples actually come from the uploaded feedback; no quotation is invented when text is absent.
4. Step 1 identifies exactly 3 top recurring issues.
5. Step 2 labels every causal explanation as a hypothesis.
6. Step 3 compares actual customer segments from the file or clearly states that comparison is unavailable.
7. Step 4 states how `extreme complaint` was defined.
8. Step 5 includes frequency counts for every theme in the selected framework.
9. Step 6 contains exactly 3 initiatives.
10. Every Step 6 initiative includes Objective, Action, and Expected Impact.
11. Step 7 contains no more than 6 bullets.
12. Facts are clearly separated from assumptions.
13. No external facts or benchmarks are introduced.
14. Any feedback outside the selected theme framework is reported transparently.
15. The final report includes all seven adapted prompts and all seven answers.

---

# Trigger Examples

Use this skill when the user says things like:

- "Run the same customer feedback analysis on this dataset."
- "Execute the 7 feedback prompts."
- "Analyze these customer comments."
- "Find the top customer issues and generate a management report."
- "Compare customer feedback across the segments in this file."
- "Create the same 7-step CX report."
- "Generate all prompts and answers from this feedback file."

---

# Default Behavior

If the user uploads a customer feedback file and invokes this skill without further instructions:

1. Inspect the dataset.
2. Adapt the seven prompts.
3. Execute all seven steps sequentially.
4. Use only the uploaded data.
5. Present the complete analysis.
6. If the user requests a document and document generation is available, create a downloadable Word report containing all prompts and answers.
