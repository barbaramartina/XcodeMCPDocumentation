---
name: apple-xcode-mcp-bridge
description: Connect to the live, running Xcode IDE through Apple's native MCP bridge (xcrun mcpbridge) to list open Xcode windows and editor tabs, read live issue navigator errors and warnings, refresh code issues in a file, execute Swift snippets, and render SwiftUI previews. Use this skill whenever the user wants to check what Xcode is currently reporting (build errors, warnings, issue navigator), see what is open in Xcode, test a piece of Swift logic in isolation, or see how a SwiftUI view renders in a preview, even if they don't mention MCP or the bridge. Also covers Apple native documentation lookup.
---

# Apple Native Xcode MCP Bridge

## Overview
Provides direct access to live Xcode IDE features and Apple native tools using `xcrun mcpbridge`. Use it when the answer depends on the current state of Xcode rather than on static knowledge.

## When to use
- The user asks about errors or warnings Xcode is showing, or wants the issue navigator checked
- The user wants issues refreshed for a specific file
- The user wants to know which Xcode windows or editor tabs are open
- The user wants to try out Swift code in isolation
- The user wants to see a SwiftUI view rendered in a preview

## Workflow
1. **Find the active tab.** List open editor tabs with `xcode__XcodeListWindows` and retrieve the active `tabIdentifier`.
2. **Check diagnostics.** Query live syntax errors and warnings with `xcode__XcodeListNavigatorIssues`, or refresh the issues for a single file with `xcode__XcodeRefreshCodeIssuesInFile`.
3. **Test logic.** Run Swift code in isolation with `xcode__ExecuteSnippet`.
4. **Preview UI.** Render a live SwiftUI view preview with `xcode__RenderPreview`.

Steps are independent: start at whichever one matches the request, but step 1 is where the `tabIdentifier` comes from.
