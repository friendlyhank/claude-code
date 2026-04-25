# Claude Code Knowledge Wiki

> Auto-generated knowledge graph from claude-code source code

## Quick Navigation

### 📊 Graph Statistics
- **Nodes**: 12,411
- **Edges**: 38,767
- **Communities**: 1,709
- **God Nodes**: 10 (most connected concepts)

### 🗺️ Entry Points

1. **Start Here**: [[index.md]] - Complete catalog of all communities
2. **Largest Community**: [[Community_0.md]] - Core utilities (883 nodes)
3. **God Nodes**: Most connected abstractions - see below

### 🔝 Top Communities by Size

| Community | Nodes | Key Concepts |
|-----------|-------|--------------|
| [Community 0](wiki/Community_0.md) | 883 | Core utilities (debug, log, config, env) |
| [Community 1](wiki/Community_1.md) | 449 | ANSI terminal handling |
| [Community 2](wiki/Community_2.md) | 392 | Plugin system & marketplace |
| [Community 3](wiki/Community_3.md) | 390 | (see wiki for details) |
| [Community 4](wiki/Community_4.md) | 307 | (see wiki for details) |

### 🎯 God Nodes (Key Abstractions)

These are the most connected concepts in the codebase:

| Node | Connections | Type |
|------|-------------|------|
| [Node](wiki/Node.md) | 92 | Core abstraction |
| [Cursor](wiki/Cursor.md) | 57 | UI component |
| [YogaLayoutNode](wiki/YogaLayoutNode.md) | 51 | Layout system |
| [mk()](wiki/mk().md) | 47 | Constructor pattern |
| [Ink](wiki/Ink.md) | 45 | React CLI framework |

## How to Use This Wiki

### For AI Agents (Claude, GPT, etc.)

1. Read `index.md` first to understand the overall structure
2. Navigate to relevant community articles based on the task
3. Follow wikilinks `[[ArticleName]]` to drill into details
4. Use the "Key Concepts" section to find important functions/modules
5. Check "Relationships" section to understand cross-cutting concerns

### For Developers

1. **Explore Architecture**: Start with god nodes to understand core abstractions
2. **Find Related Code**: Each community shows its source files and key concepts
3. **Understand Dependencies**: Cross-community relationships reveal module boundaries
4. **Locate Functions**: Use grep on wiki files to find relevant concepts

### Example Navigation Path

```
Task: "How does the tool system work?"

1. Open index.md
2. Search for "tool" → Find Community_447, Community_892
3. Open Community_447.md
4. See key concepts: Tool, ToolExecutor, tool_registry
5. Click [[Community_892]] to see related tool components
6. Check source files section to locate actual code
```

## Wiki Structure

```
graphify-out/wiki/
├── index.md              # Main navigation hub
├── Community_*.md        # 1,709 community articles
└── <GodNode>.md         # 10 god node articles
```

Each community article contains:
- **Key Concepts**: Top 25 most connected nodes
- **Relationships**: Cross-community connections
- **Source Files**: Original file paths
- **Audit Trail**: Edge confidence breakdown

## Regenerating the Wiki

After code changes, regenerate the wiki:

```bash
# Method 1: Using graphify CLI (recommended)
python3 -m graphify update .

# Method 2: Using Python directly
python3 -c "
from graphify.watch import _rebuild_code
from pathlib import Path
_rebuild_code(Path('.'))
"
```

## Integration with Obsidian

This wiki uses Obsidian-compatible wikilink syntax:
- `[[ArticleName]]` - Link to article
- `[[ArticleName|Display Text]]` - Link with display text

You can open the `graphify-out/wiki/` folder in Obsidian for:
- Graph view of knowledge structure
- Backlinks navigation
- Full-text search
- Tag-based organization

## Graph Metadata

- **Generated**: 2026-04-25
- **Tool**: graphify 0.5.0
- **Repository**: claude-code
- **Corpus**: 3,014 files · ~3,693,844 words
- **Extraction**: 100% EXTRACTED · 0% INFERRED

---

*This wiki is auto-generated from code structure. For manual annotations, create a separate notes directory.*
