---
name: xcode-spm-management
description: Manage Swift Package Manager (SPM) packages and dependencies - dump a Swift package, show its dependencies, add external dependencies by URL and version requirement, and build and test pure Swift packages. Use this skill whenever the user asks what a Swift package depends on, wants to add a package dependency, or wants to build or run the tests of a Swift package, mentions SPM, Swift Package Manager, or a package's dependencies, even if they don't say "package manager" explicitly.
---

# Swift Package Manager Integration

## Overview
Manages pure Swift packages and SPM dependencies. Use it for inspecting, extending, building, and testing Swift packages.

## When to use
- The user wants to see a Swift package's details or its dependencies
- The user wants to add an external dependency to a Swift package
- The user wants to build a Swift package or run its tests

## Workflow
1. **Inspect.** Inspect package dependencies with `xcode__dump_swift_package` or `xcode__show_swift_dependencies`.
2. **Add dependencies.** Add external dependencies with `xcode__add_swift_package`, specifying the URL and version requirements.
3. **Validate.** Validate package code with `xcode__build_swift_package` and `xcode__test_swift_package`.

Steps are independent: start at whichever one matches the request. If the user asks to add a dependency without giving a URL or version requirement, ask for them before calling `xcode__add_swift_package`.
