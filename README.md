# Repolex Knowledge Graph of colcon/colcon-devtools

RDF knowledge graph data for [colcon/colcon-devtools](https://github.com/colcon/colcon-devtools), parsed by [repolex](https://repolex.ai).

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
rlex download colcon/colcon-devtools
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 5c8e31a9b5340863c065ced023f38c204b9ad7d2
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 5c8e31a9b5340863c065ced023f38c204b9ad7d2
│           └── chunk-001.nq.gz
├── blob
│   ├── 0f17157ed42b486a0c57cbffddd97987a4844e6b.nq.gz
│   ├── 3764e76f150d34bd1f935bf75d7be1ec87ec7b21.nq.gz
│   ├── 415b0add71bafc253b6e2e509b14295b4cc65309.nq.gz
│   ├── 4b6c2e4218a51536d69c822f76557d644e420685.nq.gz
│   ├── 5154de144aa0983550b53b5aa5998536c1c5b1d5.nq.gz
│   ├── 5640c2e81e8751c0bfa097872f4d823c212579f7.nq.gz
│   ├── 80e2b2f5970459ba13c7b4e1d998b320a471b23b.nq.gz
│   ├── a03bb3ce5e0d73e5ae20d24c73e5abc75e011eff.nq.gz
│   ├── bd7c8693b373f16474a10254e75b502ef8389f27.nq.gz
│   ├── cd3bb3fa5262eec00bc004bebb52744a72df9435.nq.gz
│   ├── d645695673349e3947e8e5ae42332d0ac3164cd7.nq.gz
│   ├── d7b2e255af0ddc58d1cfbf72427e6db5b2196965.nq.gz
│   ├── dd516e10587223b8b920258d4d5cf6da80f5c339.nq.gz
│   ├── dffe460f162da9929178a7ce342532e7ba896425.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── e82fd0b0abbf1472480d19d468efe7819276e80d.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 5c8e31a9b5340863c065ced023f38c204b9ad7d2.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 24 files
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

[colcon/colcon-devtools](https://github.com/colcon/colcon-devtools)

---
*Parsed on 2026-10-17 by [repolex](https://repolex.ai)*
