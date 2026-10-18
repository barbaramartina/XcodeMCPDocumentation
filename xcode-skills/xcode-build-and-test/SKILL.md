---
name: xcode-build-and-test
description: Build Xcode projects, read build logs to find compiler errors and their line locations, run XCTest tests, and analyze files affected by test failures. Use this skill whenever the user wants to compile or build the project, check whether recent code changes still compile, run unit or UI tests, or understand a compilation error or build failure, even if they don't mention Xcode or XCTest by name. Use it after modifying code to verify the change.
---

# Build & Automated Testing

## Overview
Automates compilation, error diagnosis, and XCTest execution. Use it to verify code changes by building and testing, and to diagnose what went wrong when they fail.

## When to use
- Code was modified and needs to be compiled or verified
- The user wants to run unit or UI tests
- The user is troubleshooting a compilation error or build failure
- A test failed and the affected components need analysis

## Workflow
1. **Build.** Compile the active target with `xcode__build_project`, passing `scheme` and `configuration` (for example `Debug`).
2. **Diagnose build failures.** If compilation fails, call `xcode__get_build_log` to filter for compiler errors and line locations.
3. **Test.** Execute tests with `xcode__run_tests`. If test failures occur, run `xcode__analyze_file` on the affected components.
