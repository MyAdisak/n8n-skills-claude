---
name: graphify
description: Visualize and explore n8n workflow codebases as knowledge graphs using graphify. Use when mapping relationships between n8n skills, understanding codebase structure, generating architecture diagrams, querying code connections, or onboarding to a new n8n project. Activates when asked to visualize workflows, map skill dependencies, understand codebase structure, or explore relationships between n8n nodes and skills.
---

# graphify

Turn your n8n-skills codebase (or any project) into a queryable knowledge graph.

---

## Installation

```bash
# Recommended (uv puts graphify on PATH automatically):
uv tool install graphifyy

# Alternatives:
pipx install graphifyy
pip install graphifyy
```

After installing, register with your AI assistant:

```bash
graphify install
```

---

## Quick Start

```bash
# In your n8n-skills project directory:
/graphify .
```

This creates three output files:
- **HTML** — interactive visual graph you can open in a browser
- **Markdown** — insights report with key connections and suggested questions
- **JSON** — raw graph data for programmatic use

---

## Common Commands

### Build & Update

```bash
/graphify .                        # Build graph for current folder
/graphify ./skills --update        # Re-extract only changed files
/graphify . --cluster-only         # Rerun clustering without re-extracting
```

### Query

```bash
/graphify query "which skills depend on MCP tools?"
/graphify query "what connects n8n-expression-syntax to n8n-code-javascript?"
```

### Architecture Diagrams

```bash
graphify export callflow-html      # Call-flow diagram
```

### Auto-rebuild on commits

```bash
graphify hook install              # Rebuild graph on every git commit
```

---

## Useful for n8n-skills

| Goal | Command |
|------|---------|
| Map all 7 skills and their relationships | `/graphify ./skills` |
| Find which skills share common concepts | `/graphify query "shared concepts"` |
| Understand evaluation coverage | `/graphify ./evaluations` |
| Explore docs structure | `/graphify ./docs` |

---

## Key Concepts

- **God nodes** — Most-connected concepts (e.g., `$json`, `validate_node`)
- **Surprising connections** — Cross-file links ranked by unexpectedness
- **Relationship tags** — `EXTRACTED` (from code), `INFERRED` (by AI), `AMBIGUOUS`
- **Clusters** — Related files grouped by Leiden algorithm

---

## Optional Extras

```bash
pip install "graphifyy[pdf]"       # PDF support
pip install "graphifyy[video]"     # Video transcription (local, via faster-whisper)
pip install "graphifyy[neo4j]"     # Neo4j integration
```

---

## Works With

Claude Code, Cursor, Gemini CLI, GitHub Copilot, Aider, and 10+ other AI assistants.
