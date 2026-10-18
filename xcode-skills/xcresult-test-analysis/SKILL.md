---
name: xcresult-test-analysis
description: Analyze .xcresult bundles from Xcode build and test runs - find recent result bundles, summarize test execution, browse failure details, extract console logs from failures, and for UI test failures retrieve failure screenshots, view layout hierarchies, and inspect individual UI elements. Use this skill whenever the user asks why a test failed, wants test results or a test summary, mentions an .xcresult bundle or result bundle, wants console output from a failed test, or wants to see what the screen or view hierarchy looked like when a UI test failed, even if they don't mention xcresult by name.
---

# XCResult Test Analysis & Visual Debugging

## Overview
Provides deep diagnostics for test runs by analyzing `.xcresult` bundle outputs, visual attachments, console logs, and UI element trees. Use it when the question is about the results of a build or test run that has already happened.

## When to use
- The user asks why a test failed or wants the failure details
- The user wants a summary of a test run
- The user mentions an `.xcresult` bundle, or asks for the latest build or test results
- The user wants the console log from a failed test
- A UI test failed and the user wants to see the failure screenshot, the view hierarchy, or a specific UI element

## Workflow
1. **Find the bundle.** Locate recent build/test result bundles with `xcode__find_xcresults`.
2. **Summarize and browse.** Generate test execution metrics with `xcode__xcresult_summary`, and navigate failure details with `xcode__xcresult_browse`.
3. **Get the logs.** Extract failure logs with `xcode__xcresult_browser_get_console`.
4. **For UI test failures:**
   - Retrieve failure screenshots with `xcode__xcresult_get_screenshot`.
   - Inspect the view layout hierarchy with `xcode__xcresult_get_ui_hierarchy`, and inspect specific elements with `xcode__xcresult_get_ui_element`.

Steps 2 to 4 build on the bundle located in step 1. Use steps 3 and 4 as the failure details call for them.
