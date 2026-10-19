---
name: xcode-simulator-management
description: Manage iOS, iPadOS, watchOS, and tvOS simulators - list available simulators, boot a simulator, install and launch an app on it, take screenshots, and record video to inspect UI output. Use this skill whenever the user wants to see which simulators are available, start a simulator, get an app running on one, or capture a screenshot or video of the app's UI, even if they don't say "simulator" explicitly (for example "show me what it looks like on an iPad" or "run it on the watch").
---

# iOS Simulator Control

## Overview
Handles simulator device lifecycles, app deployment, and visual feedback collection. Use it to get an app running on a simulator and to capture what it looks like.

## When to use
- The user wants to know which simulators or runtimes are available
- The user wants to boot a simulator
- The user wants to install and launch an app on a simulator
- The user wants a screenshot or a video recording of the UI

## Workflow
1. **List.** Query available runtimes with `xcode__list_simulators`.
2. **Boot.** Boot the required runtime with `xcode__boot_simulator(udid=...)`, using the `udid` of the simulator from step 1.
3. **Deploy.** Install the app with `xcode__install_app`, then start it with `xcode__launch_app`.
4. **Capture.** Capture layout renders with `xcode__take_screenshot` or `xcode__record_video` to inspect UI output.

Steps are independent: start at whichever one matches the request, though booting needs a `udid` and the install and launch steps follow booting.
