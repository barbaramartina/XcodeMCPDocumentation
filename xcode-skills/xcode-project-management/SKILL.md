---
name: xcode-project-management
description: Manage which Xcode project is active and keep its targets up to date - check the active project, find available projects, set the project path and open it in Xcode, and add new source or asset files to a project target and group. Use this skill whenever the user wants to know or change which Xcode project is being worked on, needs to find an Xcode project, or has just created new source or asset files that must be added to a target so they are included in the build, even if they don't say "project context" or "target membership" explicitly.
---

# Xcode Project Management

## Overview
This skill manages project resolution and target configuration for Xcode projects. Use it to establish which project is active and to make sure newly created files belong to the right target.

## When to use
- The user wants to confirm which project is active, or switch to a different one
- No project is active and one needs to be found and activated
- New source or asset files were created and need to be added to a target

## Workflow
1. **Check context.** Verify the active project context with `xcode__get_active_project` or `xcode__detect_active_project`.
2. **Find and activate.** If no project is active, find available projects with `xcode__find_projects`, then activate the target with `xcode__set_project_path(projectPath=..., openInXcode=true)`.
3. **Add new files.** When new source or asset files are created, call `xcode__add_file_to_project` with explicit `target` and `group` arguments to ensure inclusion in build phases.
