---
name: xcode-direct-control
description: Directly control the running Xcode IDE through JavaScript for Automation - run server and bridge health checks, inspect open workspaces, list run destinations, switch the active scheme, build and run the app, start debug sessions, and stop active sessions. Use this skill whenever the user wants Xcode itself to do something - build and run the project, debug it, stop a running session, change the active scheme, check which workspaces or run destinations are available - or asks whether the Xcode tooling or bridge is working, even if they don't mention automation or scripting.
---

# Direct Xcode Control & Environment Health

## Overview
Interacts directly with the Xcode GUI application state and manages interactive debugging sessions. Use it when the request is to act on the running Xcode app, such as launching, debugging, stopping, or switching schemes, rather than only to read information from it.

## When to use
- The user wants to build and run the app from Xcode
- The user wants to debug the app, or stop a running or debugging session
- The user wants to change the active scheme
- The user asks which workspaces are open or which run destinations are available
- Xcode tools are failing or unresponsive and the server or bridge needs a health check

## Workflow
1. **Check health.** Run server and bridge diagnostics with `xcode__xcode_health_check`.
2. **Inspect the environment.** Inspect open IDE workspaces with `xcode__xcode_get_workspace_info` and list available destinations with `xcode__xcode_get_run_destinations`.
3. **Set the scheme.** Switch the active scheme with `xcode__xcode_set_active_scheme`.
4. **Run, debug, or stop.** Execute the application with `xcode__xcode_build_and_run`, debug it with `xcode__xcode_debug`, and terminate active sessions with `xcode__xcode_stop`.

Steps are independent: start at whichever one matches the request. If a tool call fails, step 1 is the place to start diagnosing.
