# Turn-by-Turn Journey

## Turn 1: Notebook creation
- Built `voc_semantic_retrieval_audit.ipynb` with:
  - multilingual retrieval pipeline
  - top-k export
  - hand-label template
  - Precision@5 evaluation
  - error analysis
- Added fallback demo corpus so the notebook runs end-to-end without external data.

## Turn 2: First execution attempt
- Attempted to run notebook.
- Dead end: kernel was not selected in the environment path used by the tool.
- Correction: shifted to file-level validation and subsequent deterministic generation steps outside notebook runtime where needed.

## Turn 3: Missing completed labels
- Notebook reported no completed labels file.
- Correction: generated `precision_at_5_labels.csv` from the template + retrieval output using a baseline auto-label rule:
  - `is_relevant = 1` when `query_id == auto_theme_label`, else `0`.
- Result: evaluation cell could run immediately.

## Turn 4: Embedded the working script
- User asked to include the script in the artifact.
- Added an optional auto-fill section in notebook:
  - markdown explanation
  - code cell producing completed labels and baseline Precision@5 summary.

## Turn 5: Model-card requirement
- Added short model-card style note at notebook end:
  - what system is good for
  - what it is not good for
  - overclaim and reined-in statement.

## Turn 6: SQL MCP incorporation request
- User asked whether SQL MCP was used, then requested incorporation.
- Dead end:
  - `mcp_sql_mcp_serve_read_records(entity='Doc')` returned `EntityNotFound` in current MCP runtime config.
- Correction:
  - Used `mcp_sql_mcp_serve_describe_entities` to confirm available entity metadata.
  - Used `mcp_sql_mcp_serve_find_similar_docs_by_doc_id` for vector retrieval evidence.
  - Used `mcp_sql_mcp_serve_execute_entity(entity='FindSimilarDocsByDocId', ...)` as second SQL MCP path.
  - Added notebook section with MCP-backed calculations and tool-agreement check.

## Final state
- Artifact notebook includes retrieval audit, labeling workflow, evaluation, MCP cross-check calculations, and model-card note.
- Companion documentation package added in the artifact folder.
