# Agent, Model, and Tools

## Agent and Model
- Agent: GitHub Copilot coding agent
- Model: GPT-5.3-Codex

## Core Notebook Tools
- Python libraries: `pandas`, `numpy`, `sentence-transformers`, `scikit-learn`
- Embedding model: `sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2`
- Retrieval math: cosine similarity over normalized embeddings

## SQL MCP and Vector Tools Used

### 1) Vector similarity tool
- Tool: `mcp_sql_mcp_serve_find_similar_docs_by_doc_id`
- Purpose: nearest-neighbor retrieval from precomputed vectors by `DocId`
- Evidence of calls:
  - `DocId=1, TopN=5` -> returned top doc ids `[1, 24, 11, 15, 9]`
  - `DocId=2, TopN=5` -> returned top doc ids `[2, 7, 18, 21, 3]`
  - `DocId=3, TopN=5` -> returned top doc ids `[3, 7, 2, 21, 6]`

### 2) SQL MCP execute path
- Tool: `mcp_sql_mcp_serve_execute_entity`
- Entity executed: `FindSimilarDocsByDocId`
- Purpose: verify equivalent retrieval through SQL MCP execute pipeline
- Evidence of call:
  - `entity=FindSimilarDocsByDocId, DocId=2, TopN=5` -> returned top doc ids `[2, 7, 18, 21, 3]`

### 3) SQL MCP entity discovery
- Tool: `mcp_sql_mcp_serve_describe_entities`
- Purpose: identify available entities and callable operations
- Evidence:
  - Returned entities including `Doc` and `FindSimilarDocsByDocId`

## Tool Consistency Check Added to Notebook
From the MCP-backed calculation section:
- Mean non-self distance@5 across seed docs: `0.2987`
- Agreement between the two MCP retrieval paths for DocId 2:
  - `Jaccard@5 = 1.0`
  - `Exact order match = True`
