## graphify

This project has a graphify knowledge graph at graphify-out/.

### Wiki Navigation
- **Entry Point**: `graphify-out/wiki/index.md` - Start here for architecture questions
- **Quick Reference**: `graphify-out/wiki/README.md` - Usage guide and statistics
- **Community Articles**: Each community is documented in `wiki/Community_*.md`
- **God Nodes**: Key abstractions documented in `wiki/<NodeName>.md`

### Rules
- Before answering architecture or codebase questions, read `graphify-out/wiki/index.md` first
- Navigate using wikilinks `[[ArticleName]]` to drill into specific areas
- Each community article shows: Key Concepts, Relationships, Source Files
- After modifying code files, regenerate wiki:
  ```bash
  python3 -c "from graphify.watch import _rebuild_code; from pathlib import Path; _rebuild_code(Path('.'))"
  ```
