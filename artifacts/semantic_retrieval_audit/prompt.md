# Prompt Used

## Overarching Goal
Evaluate whether Zava's semantic retrieval system can reliably identify cross-language customer feedback themes across reviews and support conversations, and measure retrieval quality using a hand-labeled Precision@5 evaluation.

## Working Prompt (Consolidated)
Create a notebook artifact named `voc_semantic_retrieval_audit.ipynb` that:
1. Loads or synthesizes a multilingual VoC corpus from reviews and support conversations.
2. Runs semantic retrieval over cross-language theme queries.
3. Exports top-k retrieval outputs for inspection.
4. Produces a hand-label template for `is_relevant` at top-5.
5. Computes Precision@5 by query and macro average from completed labels.
6. Includes error analysis for likely false positives.
7. Includes a short model-card note describing strengths, limitations, overclaim risk, and mitigation.
8. Incorporates SQL MCP and vector-tool evidence into calculations and narrative.

## Scope Boundaries
- Retrieval audit and evaluation workflow only.
- Not a production claim of reliability without human labels and review.
- Baseline auto-labeling is for acceleration, not ground truth.
