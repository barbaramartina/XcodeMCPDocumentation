---
name: xcode-file-operations
description: Perform path-safe file operations in Xcode projects - check whether a file exists, get file information, search files for symbols or patterns with regex, and write file updates using paths relative to the project root. Use this skill whenever the user wants to find where a symbol or pattern appears in the codebase, check that a file exists, or create or update a source file in a Swift or Apple project, even if they don't mention Xcode explicitly. Use it before reading or modifying files to confirm they exist.
---

# Source & File Operations

## Overview
Handles path-safe source code editing and directory exploration. Use it to locate, verify, and update files in a project.

## When to use
- The user wants to find a symbol or pattern in the codebase
- You need to confirm that a file exists, or get information about it, before reading or modifying it
- The user wants a source file written or updated

## Workflow
1. **Verify.** Before modifying or reading files, verify existence with `xcode__check_file_exists` or `xcode__get_file_info`.
2. **Search.** Search for codebase symbols or patterns with `xcode__search_files` using a regex, before opening full files.
3. **Write.** Write updates with `xcode__write_file`, using an exact path relative to the project root.
