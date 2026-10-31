# Lyra CodeVision (LyraCV)

Fully offline, local-first repository intelligence system for AI coding agents, providing structural code understanding, relationship analysis, and efficient repository retrieval.

- **Role:** Creator & Software Engineer
- **Period:** 2026-10 – Present
- **Relationship:** Independent personal project

## Overview

Lyra CodeVision (LyraCV) is a fully offline, local-first developer tool built to give AI coding agents a richer, more complete understanding of a repository than they would gather by reading files one at a time. Agents query it for structure, code relationships, and the likely impact of a change instead of reading entire files unnecessarily, which keeps token usage down and lets them reach working changes faster.

Unlike conventional code RAG systems focused primarily on semantic similarity, LyraCV builds a structural understanding of repositories, connecting symbol definitions, references, callers, dependencies, imports, and tests.

The system combines AST-based indexing, relationship graphs, and multi-strategy search through a Rust-based core, exposing its capabilities to coding agents through MCP and a CLI.

LyraCV is designed to complement existing coding agents rather than replace them. Agents remain responsible for code analysis, modifications, and testing, while LyraCV provides precise repository intelligence to support their decisions.

## Responsibilities & Contributions

- Conceived the product and defined its technical vision, architecture, and development direction.
- Designed and developed a modular Rust-based system for repository indexing, structural analysis, and code retrieval.
- Built the project using specification-driven, AI-assisted development workflows while maintaining ownership of architecture, engineering decisions, and technical validation.
- Developed a local-first architecture with embedded storage, local inference, and no dependency on hosted AI APIs or external databases for retrieval.
- Integrated repository intelligence into AI coding environments through MCP and dedicated agent integrations.
- Developed desktop integration and background-service management across macOS, Windows, and Linux.
- Directed performance optimization, incremental indexing, retrieval evaluation, and automated testing.

## Notable Implementation Details

- **Structural code intelligence:** Built an AST-aware indexing system using Tree-sitter to extract symbols, definitions, references, imports, and typed relationships. The resulting repository graph supports caller analysis, dependency traversal, and change-impact investigation, so an agent can judge what its changes will affect.
- **Multi-language indexing:** Implemented support for JavaScript, TypeScript, Vue.js, Rust, Swift, Objective-C, C/C++, HTML, and stylesheet languages, including framework-specific relationships and compiler-assisted resolution.
- **Multi-strategy retrieval:** Combined lexical (FTS5/BM25), semantic, fuzzy, prefix, stemming, and trigram search using Reciprocal Rank Fusion (RRF), with targeted symbol inspection for retrieving source code only when necessary.
- **Local AI infrastructure:** Integrated lightweight, 384-dimensional BGE embeddings through FastEmbed and ONNX Runtime, with SQLite, FTS5, and sqlite-vec providing embedded search and vector storage.
- **Context-efficient retrieval:** Designed metadata-first search results, bounded source inspection, reference snippets, and paginated responses to minimize unnecessary code exposure and LLM context consumption.
- **Incremental indexing:** Implemented change detection, reusable extraction and resolution results, embedding reuse, and persistent background indexing jobs to avoid redundant processing.
- **Agent integration:** Exposed repository intelligence through a local HTTP MCP server with 15 tools, a dedicated CLI, and integrations for OpenCode, Claude Code, and Codex.
- **Desktop architecture:** Developed a SwiftUI macOS menu-bar application with core-process supervision, background job monitoring, and live MCP traffic inspection, alongside native system-tray implementations for Windows and Linux.

## Tech Stack

- Rust
- Swift
- SwiftUI
- SQLite
- FTS5
- sqlite-vec
- Tree-sitter
- AST Parsing
- FastEmbed
- ONNX Runtime
- BGE-small-en-v1.5
- Model Context Protocol (MCP)
- Tokio
- Axum
- REST APIs
- HTTP
- CLI Development
- GitHub Actions
- CI/CD

## Related Experience

- [Senior Full-Stack Engineer (Agentic Development) @ Self-Employed / Freelance](../../experiences/senior-full-stack-engineer-agentic-development-self-employed/README.md)
