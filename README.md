# Repolex Knowledge Graph of getsentry/responses

RDF knowledge graph data for [getsentry/responses](https://github.com/getsentry/responses), parsed by [repolex](https://repolex.ai).

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
rlex download getsentry/responses
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e68019c21a2d8ff0ab48484d4d6f1d81a3fc100b
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── e68019c21a2d8ff0ab48484d4d6f1d81a3fc100b
│           └── chunk-001.nq.gz
├── blob
│   ├── 10ef075297a59c40a741d13320f91844111dabe7.nq.gz
│   ├── 2459fc35edf09aae4bffcb53695ff707445a870d.nq.gz
│   ├── 25548d57f4fd51996a381371ca32b849622779fc.nq.gz
│   ├── 25aab7d1122398f8b9e6d892c4509961d340e18c.nq.gz
│   ├── 2ac7ea7d52ad9a1ea4d089655d7e17682f752b51.nq.gz
│   ├── 333578fa1fe9669e2cc5670fefd17a1bd2843658.nq.gz
│   ├── 3534373ad2c4647d4786e0ae27142b6d28febd8e.nq.gz
│   ├── 4e3e6fe333d381d265a52de245daa3c6ed27a1ce.nq.gz
│   ├── 4e979a580ef4fe32d245f4e4b23d3dfb54d509fc.nq.gz
│   ├── 52b44b20a37c4dd392a655d250cba7c8399c9a8c.nq.gz
│   ├── 5b1546a3a7997278bb79d281ed682999167340b2.nq.gz
│   ├── 6580d477883c45692583d06e5cef8f3299af7e8a.nq.gz
│   ├── 6802db143e19ed9d9f08271120a5137b2a6f3267.nq.gz
│   ├── 6817390862be2bbe2f67a14ea072043a6101e03f.nq.gz
│   ├── 6fb4e473fa4f45f0a2289e9e19ff3be972335124.nq.gz
│   ├── 77fdee0a4817dbd734f5f53655a5668560f63087.nq.gz
│   ├── 8170aedc96ec83d05c358e4044144c7afe5c597f.nq.gz
│   ├── 893b7f2507024ba2e153633ff1b73553cb65b6f2.nq.gz
│   ├── 966feea32361bcf414307fa920a53956555ebb14.nq.gz
│   ├── 97b841531a713be183d720f46d4d5b5ab5855bb9.nq.gz
│   ├── 98b0d029125b50e53693454c478a304e005bb8a9.nq.gz
│   ├── 9ed9d0ef34a229e93fdc1d9d2dec5aad510587cb.nq.gz
│   ├── b6d7b9540fffb70db424c85f572b70c1fc839319.nq.gz
│   ├── bc8f1e0459f24e1022551e2cc00ac52a6243eab9.nq.gz
│   ├── c2c90d978120ae0aeed196bb6de283d90223dee8.nq.gz
│   ├── c3823d6547142896d8facfd56989b0b15dc9cb8c.nq.gz
│   ├── c67301220e14879521cb63098f0e9576163e631c.nq.gz
│   ├── c9c7d7304809002fda1b65fe6c77311a1751e87d.nq.gz
│   ├── cb17a623c6c66042cf58b71f9d00c88f908ba3f0.nq.gz
│   ├── cf3f81e4b9223227f4643237d3e99414e999603a.nq.gz
│   ├── d68f0f55224fdb1e83bf70500eb6679e98a1193b.nq.gz
│   ├── e020369898332b205a189d68155c11b3a1808e47.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f297ba2ab9cdc36f9a1722b8f26d414f5fc40393.nq.gz
│   ├── f676d017aa5b45aceb8233de58a35e8f18d51ff6.nq.gz
│   └── fcf481a880c9bcc0efbdfe6492470041b531219c.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── e68019c21a2d8ff0ab48484d4d6f1d81a3fc100b.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 44 files
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

[getsentry/responses](https://github.com/getsentry/responses)

---
*Parsed on 2026-10-18 by [repolex](https://repolex.ai)*
