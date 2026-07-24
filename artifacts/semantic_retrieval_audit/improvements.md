# What To Test or Improve Next

## 1) Evaluation quality
- Replace baseline auto-labels with double-blind human annotation.
- Track inter-annotator agreement (for example Cohen's kappa).
- Add confidence intervals for Precision@5 using bootstrap resampling.

## 2) Retrieval robustness
- Expand query set across more intents and languages.
- Add hard-negative examples to stress semantic boundaries.
- Compare multiple embedding models and rankers (bi-encoder vs reranker).

## 3) SQL MCP integration depth
- Resolve MCP read-path configuration mismatch (the `read_records` `EntityNotFound` state) so table reads can be fully reproduced in-notebook.
- Add automated capture of MCP call outputs to artifact JSON for complete reproducibility.
- Increase MCP seed-doc sample size beyond 3 documents for stronger consistency evidence.

## 4) Bias and safety checks
- Slice Precision@5 by language, source type, sentiment, and complaint severity.
- Measure false-positive concentration across languages.
- Add a manual policy review checkpoint before operational use.

## 5) Operationalization
- Add a repeatable script to regenerate all artifact files in one command.
- Add versioned data snapshots and model metadata.
- Add a CI check that fails if key metrics regress beyond threshold.
