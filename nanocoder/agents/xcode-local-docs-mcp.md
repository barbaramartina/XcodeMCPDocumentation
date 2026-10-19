---
name: xcode-local-docs-mcp
description: Offline lookup of Swift and Apple framework documentation via local MCP tools - search API docs, fetch full framework pages with code examples, retrieve symbol signatures, read Swift Evolution proposals, and re-index local Markdown reference files. Use this skill whenever the user asks about Apple platform APIs (SwiftUI, UIKit, AppKit, Foundation, Combine, SwiftData, Swift concurrency, XCTest, and similar), needs a method signature, parameter list, availability, or usage example, asks about a Swift Evolution proposal (SE-xxxx), wants to confirm an API exists or is deprecated before writing Swift code, or has added new Markdown docs that need indexing. Prefer this over memory or web search for Apple API details, even if the user never says "documentation."
---

# Local Documentation Index & Knowledge Context

## Overview
Offline lookup for Apple framework documentation, and local API references. Use it to ground Swift and Apple-platform answers in the indexed docs instead of relying on memory, which may be outdated for fast-moving frameworks.

## When to use
- The user asks how an Apple API works, what its signature is, or how to use it
- You are about to write or review Swift code that calls an API you are not certain about
- The user references a language feature (macros, actors, `@Observable`, typed throws, and so on)
- The user has added new Markdown reference files and wants them searchable

Skip it for general programming questions with no Apple or Swift angle.

## Workflow
1. **Search first.** Call `xcode__search_documentation` with a short, specific query (symbol name, framework plus concept). Try one or two alternative phrasings if the first returns nothing useful.
2. **Fetch when you need depth.** Call `xcode__fetch_documentation_page` on the best search hit to get the full topic, including declarations, parameters, discussion, and code examples. Search snippets alone are not enough to quote a signature.
3. **Re-index after adding docs.** After new Markdown reference files are added, call `xcode__index_local_docs` and then re-run the search to confirm they are found.

## Answering from the results
- Quote signatures and examples as returned by the docs; do not reconstruct them from memory.
- Name the page you used so the user can verify it.
- If the docs and your prior knowledge disagree, trust the docs and mention the difference.
- If nothing relevant is indexed, say so plainly, then answer from general knowledge and flag it as unverified against the local docs.
