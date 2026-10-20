# Repolex Knowledge Graph of PyCQA/flake8-json

RDF knowledge graph data for [PyCQA/flake8-json](https://github.com/PyCQA/flake8-json), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download PyCQA/flake8-json
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 482ef7ee7afb44d82589bd54160401c2ac2515f9
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 482ef7ee7afb44d82589bd54160401c2ac2515f9
│           └── chunk-001.nq.gz
├── blob
│   ├── 0542d1e31b01a8b7105d1d5ad055e8cc3fc44897.nq.gz
│   ├── 09c75d150a6f09b17e8887a6a0541b7699f324ef.nq.gz
│   ├── 0a7bb1c3f507c9853ebe8add8f09988c32f95723.nq.gz
│   ├── 0cab696ba0f5aaad845edf30f4d2bdefb6cfd1ee.nq.gz
│   ├── 31e05432387be5da6a132e766c24d30b4ed420d6.nq.gz
│   ├── 38883093a1d4341604f969db47f7b41b31bec6b7.nq.gz
│   ├── 559432dfd2a21ce5b7a6be690cf3aefd4a6402d5.nq.gz
│   ├── 6aa8e6cbb5f4d4d326560a8a312fdd46f8f3ef0e.nq.gz
│   ├── bb547f34c6049636d9c0d9e990f6b3276209900e.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f2aed64bcf1938b7c1566364c348ceaca867f0e7.nq.gz
│   └── fe8936215986784461acbb531af89963d9daa206.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 482ef7ee7afb44d82589bd54160401c2ac2515f9.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 20 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[PyCQA/flake8-json](https://github.com/PyCQA/flake8-json)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
