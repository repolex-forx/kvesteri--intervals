# Repolex Knowledge Graph of kvesteri/intervals

RDF knowledge graph data for [kvesteri/intervals](https://github.com/kvesteri/intervals), parsed by [repolex](https://repolex.ai).

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
rlex download kvesteri/intervals
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   ├── 60d6f00cbbd11e30dc1a0f67e57321638676a1f3
│   │   │   └── chunk-001.nq.gz
│   │   └── 97445fe2d57a98969c0fa8188fae585cc529522a
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 60d6f00cbbd11e30dc1a0f67e57321638676a1f3.nq.gz
│   └── repolex
│       ├── 60d6f00cbbd11e30dc1a0f67e57321638676a1f3
│       │   └── chunk-001.nq.gz
│       └── 97445fe2d57a98969c0fa8188fae585cc529522a
│           └── chunk-001.nq.gz
├── blob
│   ├── 07a47f8838037f8dc92cf3e28f33f3b8e44323b1.nq.gz
│   ├── 083c9a4c730e763ca2eb62c7a03771f5262bfd82.nq.gz
│   ├── 0c31faa9a19ca130228e58124683969f03bdbeb5.nq.gz
│   ├── 1a53c14dcc4b7ba487bc0aede111cfa5fbb59ed6.nq.gz
│   ├── 1a9c8f6094e02ec2d73ae0d03f6abcaaa6b9e027.nq.gz
│   ├── 2a4ca679b6b7c38bbf959665492741249b9a948e.nq.gz
│   ├── 32d7508c1eed543a67a67afc89bd8507862ef27c.nq.gz
│   ├── 3742b2f599cfd07c5db4e4ac5d58ca53ee991113.nq.gz
│   ├── 41c7cdc7f9fe80e7b535ced49a178cb7ddef7f79.nq.gz
│   ├── 4bfed420a73ceb928529e526087bbca1e5051d24.nq.gz
│   ├── 53419d533bef681b04a32cb41e16771394adc71f.nq.gz
│   ├── 5db83658bafed472667bb35bfc0ed46dec3b2793.nq.gz
│   ├── 6bea66965530e801ccdfb783ccd432491fa44ae7.nq.gz
│   ├── 7176384e5314c6be6855e972bee925283d2cca43.nq.gz
│   ├── 7b05772aaf0d6275e765af01c4f4e76484197f07.nq.gz
│   ├── 8df112b20be623fd03af0012e67ad49ac9cb406c.nq.gz
│   ├── 8eb2d93aa688f1f7258886eed92e4f58caa53bbf.nq.gz
│   ├── 9d1b9c96c1534437edb2de86b818dfe4061fd93f.nq.gz
│   ├── 9d6c5817e43bfebe5078957764285ebbd825fb37.nq.gz
│   ├── b2cf48d1c5d18962dc170932742038cf3f916c80.nq.gz
│   ├── b5762e514c06ca9ccbd1afec0ed49edc1ebc92e4.nq.gz
│   ├── bfde912143c272c4e3ca12539efff3013742ab27.nq.gz
│   ├── c28e582b226e9a80b1a56b2ead01f7dab5157ac7.nq.gz
│   ├── cc1d1c8b48bd600a553630b9c93c8ebaf740cc25.nq.gz
│   ├── d6eda1df6d53feb2529d680c1ededda279e6283c.nq.gz
│   ├── dce6ef8e5d8a4c07e9f560c9560f7bbf01b73eb6.nq.gz
│   ├── ded606788041fc9cd4d017e2dfe5a6e9bdeefbae.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── f0b7e92c3bf5ef7ec12fe86a304984d43f1f606f.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 60d6f00cbbd11e30dc1a0f67e57321638676a1f3.nq.gz
├── filetree
│   ├── 60d6f00cbbd11e30dc1a0f67e57321638676a1f3.nq.gz
│   └── 97445fe2d57a98969c0fa8188fae585cc529522a.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

17 directories, 42 files
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

[kvesteri/intervals](https://github.com/kvesteri/intervals)

---
*Parsed on 2026-11-21 by [repolex](https://repolex.ai)*
