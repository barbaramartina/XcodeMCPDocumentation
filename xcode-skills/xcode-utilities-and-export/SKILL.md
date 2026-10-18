---
name: xcode-utilities-and-export
description: Run low-level Xcode developer tool commands with xcrun, compile asset catalogs, generate app icon sets, and handle release and export workflows - validate an archive and export it. Use this skill whenever the user wants to recompile assets or regenerate app icons after changing them, validate or export an Xcode archive, prepare a release build for distribution, or run an xcrun command or other developer tool CLI command that the higher-level Xcode tools don't cover, even if they don't mention xcrun or asset catalogs by name.
---

# Xcode Utilities & Distribution

## Overview
Handles low-level tool execution and binary export workflows. Use it for asset compilation, release and export steps, and developer tool commands that no higher-level MCP endpoint covers.

## When to use
- Assets were updated and need recompiling, or app icons need generating
- The user is working on a release pipeline: creating an archive, validating it, or exporting it
- The user wants to run an `xcrun` command, or another developer tool CLI command, that the higher-level tools don't cover

## Workflow
1. **Update assets.** After asset updates, recompile with `xcode__compile_asset_catalog` or `xcode__generate_app_icons`.
2. **Release pipeline.** Create an archive, run `xcode__validate_archive`, then export with `xcode__export_archive`.
3. **Fall back to xcrun.** Use `xcode__run_xcrun` for developer tool CLI commands not covered by higher-level MCP endpoints. Prefer the dedicated tools above when one fits.

Steps are independent: start at whichever one matches the request.
