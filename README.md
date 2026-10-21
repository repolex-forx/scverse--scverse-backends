# Repolex Knowledge Graph of scverse/scverse-backends

RDF knowledge graph data for [scverse/scverse-backends](https://github.com/scverse/scverse-backends), parsed by [repolex](https://repolex.ai).

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
rlex download scverse/scverse-backends
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── dcb5383413b4fa976656116df554469235b4a6d5
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── dcb5383413b4fa976656116df554469235b4a6d5
│           └── chunk-001.nq.gz
├── blob
│   ├── 02db9c1dfa246fa88e5798749ae0471217ce62f3.nq.gz
│   ├── 0a789fd3ff343155305e5ec807672664828803c8.nq.gz
│   ├── 0e4559ea97c8c7b7339ddd04cee0ff7f45f7ab5d.nq.gz
│   ├── 16591df2592d345c4523214b009633994c2ace03.nq.gz
│   ├── 1abd6dba1cfaf5c48aba9ebdc729e6d3d34939db.nq.gz
│   ├── 208b1ee6a8f3273594c452c0ee2e1b3fd510a650.nq.gz
│   ├── 23edbd13e4406baa36a4e7e45a6b655c9859687a.nq.gz
│   ├── 2ee6f72c16de3d40945f5aabfa015385abb86b8f.nq.gz
│   ├── 366a7afc9137ba7a41db2f4eadf6285976b0bc3b.nq.gz
│   ├── 4ef3c863276616b550647d32eee862444408b0c3.nq.gz
│   ├── 51cce8d326c945662ac9559e7800a6c968ed6fef.nq.gz
│   ├── 56cfb338ec2ed6e6545831a455ee13ac646d9b48.nq.gz
│   ├── 62084fd8a3216ecbd60c19bbc965eba8488b9596.nq.gz
│   ├── 6537d180444370e062c7caa7a75c8b836efd6ebe.nq.gz
│   ├── 7f94cfc18503eb5bef5b543a6dbf578328d6151c.nq.gz
│   ├── 91fa2aa1a9adee65e4382783376621adc90a8f7b.nq.gz
│   ├── 92493bbbfed1dec52662098a22b7a9ec3921c3d5.nq.gz
│   ├── 94ecb7fa04165af1896e933d2e5fb1e5a5e9923f.nq.gz
│   ├── 96bd2cb643e23fbfde927dbf4f64394a56aac0da.nq.gz
│   ├── 9b2ff1ef20b44f246d9eed33b9c6d3c286180a92.nq.gz
│   ├── af1f2f85551ea1d3af91367ec0bd16472da6f48e.nq.gz
│   ├── b08113110c4d377e238d7f101d8c580ef833920c.nq.gz
│   ├── beacec65870241f8c5890cba06953f8829e1c33c.nq.gz
│   ├── c29f20f13562f8542bf28f8743b9d95d73c70011.nq.gz
│   ├── cdb3cb8026fad73a8409f8725614011435e572bd.nq.gz
│   ├── d05d9962ee6a304e16f10a4c526e0a4d398d8db4.nq.gz
│   ├── dc42a0ccc3ef5d7169c47032ac9cb7dc660d0201.nq.gz
│   ├── de54975a8851faa98582da020d7e59d5abb554b4.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── edf539d79c08f9e674e92480a09bbb2473d4273b.nq.gz
│   ├── f2825e41de6cde3e5d8cad55d26db4142f163d96.nq.gz
│   ├── fd497d0388425e20a45fea6c05e5dc4c7f5bd3f9.nq.gz
│   ├── fd7200b54859155dae05c973b791670f273d7c00.nq.gz
│   └── ff5b5be6c0b9ef181dbf8b6efa94c48b16519728.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── dcb5383413b4fa976656116df554469235b4a6d5.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 41 files
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

[scverse/scverse-backends](https://github.com/scverse/scverse-backends)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
