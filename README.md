# Xcode MCP Tools Documentation

This repository provides detailed documentation for all Xcode Model Control Protocol (MCP) tools available. These tools enable automation and interaction with Xcode projects, development workflows, testing, debugging, and other iOS/macOS development capabilities.

## Overview

Xcode MCP tools are a comprehensive set of commands that allow for:

- Project exploration and management
- Build automation and testing
- Debugging and runtime interaction
- Code analysis and diagnostics
- Localization and translation support
- Xcode configuration management
- Device interaction capabilities

## Core Tool Categories

### 1. Project and Workspace Management

#### Opening and Managing Projects

`XcodeOpenWorkspace`
- Opens an Xcode workspace or project at the given path
- Returns workspace identifier for targeting other tools

`XcodeCloseWorkspace`
- Closes a workspace that was opened with XcodeOpenWorkspace

`XcodeListWorkspaces`
- Lists all currently open workspaces with their identifiers and paths

#### Project Structure Navigation

`XcodeLS`
- Lists files and directories in the Xcode project structure
- Works on project organization, not filesystem structure

`XcodeGlob`
- Finds files matching wildcard patterns in the Xcode project structure
- Supports patterns like '*.swift', '**/*.json', 'src/**/*.{swift,m}'

`XcodeRead`
- Reads contents of a file within the Xcode project organization
- Returns content with line numbers (cat -n format)

`XcodeWrite`
- Creates or overwrites files with content in the Xcode project
- Automatically adds new files to the project structure

`XcodeUpdate`
- Edits files by replacing text content in Xcode project structure
- Works on project paths, not filesystem paths

`XcodeRM`
- Removes files and directories from the Xcode project structure
- Optionally deletes underlying files from filesystem

`XcodeMV`
- Moves or renames files and directories in the project navigator

`XcodeMakeDir`
- Creates directories and groups in the Xcode project structure

#### Target Management

`XcodeListTargets`
- Lists all targets in workspace with details about product types and roles
- Includes name, project container, product type, and role flags

`GetTargetBuildSettings`
- Retrieves all build settings for a specified target
- Uses target name to get specific build configuration values

`UpdateTargetBuildSetting`
- Updates, appends, or deletes build settings for a specified target
- Used for modifying compilation or linking configurations

`GetFileCompilerFlags`
- Gets additional per-file compiler flags for a single source file in a target
- Useful for identifying why one file compiles differently from others

`UpdateFileCompilerFlags`
- Updates, appends, or deletes per-file compiler flags on a source file
- For advanced compilation control, typically not used for standard development

#### New Project and Target Creation

`XcodeNewProject`
- Creates a new Xcode project from a template
- Supports various project types through templates (iOS, macOS, etc.)
- Configures language, organization ID, team ID, and destination

`XcodeNewTarget`
- Adds a new target to an existing project using specified template
- Supports embedding targets in applications (extensions, widgets, etc.)
- Configures options specific to each target type

#### Schemes and Test Plans

`XcodeListSchemes`
- Lists all schemes available in the current workspace
- Identifies which one is currently active

`XcodeSwitchScheme`
- Changes the active scheme in an Xcode workspace

`XcodeListTestPlans`
- Lists test plans associated with the currently active scheme

`XcodeSwitchTestPlan`
- Changes the active test plan for currently active scheme

#### Run Destinations

`XcodeListRunDestinations`
- Lists all available run destinations for active scheme
- Groups them by devices, simulators, build, etc.
- Identifies which one is currently active

`XcodeSwitchRunDestination`
- Changes the active run destination for the currently active scheme

### 2. Building and Testing Tools

#### Building Projects

`BuildProject`
- Builds an Xcode project and waits for completion
- Can be configured to build for testing

#### Running Applications and Tests

`RunProject`
- Builds and runs current scheme (equivalent to pressing Cmd+R)
- Optional: attach debugger to the launched process

`StopProject`
- Stops currently running app in Xcode (equivalent to pressing Cmd+.)

`RunAllTests`
- Runs all tests from the active scheme's active test plan

`RunSomeTests`
- Runs specific tests using the active scheme's test plan
- Takes array of test specifiers with target names and identifiers

`GetTestList`
- Gets all available tests from the active scheme's active test plan
- Returns grep-friendly format for easy parsing

#### Test and Debugging Integration

`InvokeDebuggerCommand`
- Sends an lldb command to Xcode's active debugging session
- Can debug running processes, set breakpoints, step through code

### 3. Debugging and Runtime Interaction

`DeviceInteractionStartSession`
- Prepares a runtime for device interaction without workspace
- Finds and boots a desired device/simulator
- Enables later device interaction but doesn't build/install project

`DeviceInteractionStartWorkspaceSession`
- Prepares a runtime for device interaction WITH a workspace
- Enables installing and running projects on devices
- Better for full development workflow

`DeviceInteractionEndSession`
- Closes previous device session created in DeviceInteractionStartSession or DeviceInteractionStartWorkspaceSession

`DeviceInteractionInstallAndRun`
- Builds, installs, and starts the current application on targeted device
- Required for up-to-date testing after code changes

`DeviceInteractionSynthesize`
- Synthesizes device events (tap, swipe, type) on physical/simulator devices
- Captures screenshots and UI hierarchies after interaction

### 4. Code Analysis and Diagnostics

#### Build Logs and Diagnostics

`GetBuildLog`
- Gets the log of current or most recently finished build
- Supports filtering by severity, message regex patterns, file glob patterns

`GetConsoleOutput`
- Retrieves console output (stdout, stderr, OSLog) from launched app sessions
- Supports filtering, context extraction, and output type selection

#### Crashes and Performance Analysis

`GetTopCrashIssues`
- Retrieves top crash signatures from Apple's crash reporting service
- Identifies most impactful crashes in last 14 days

`GetCrashIssueLogs`
- Gets detailed crash logs and expert triage knowledge for specific crash signature
- Provides actionable recommendations for crashes

`GetTopFieldPerformanceIssues`
- Analyzes app performance and identifies top issues across diagnostic types
- Supports launches, hangs, disk writes, energy usage diagnostics

`GetFieldPerformanceIssueLogs`
- Gets detailed logs and performance data for specific field performance issue
- Provides stack traces, timeline data, expert analysis guidance

#### Code Quality Issues

`XcodeRefreshCodeIssuesInFile`
- Retrieves current compiler diagnostics (errors, warnings, notes) for a file
- Returns formatted diagnostic information with severity levels

### 5. Localization and Translation Tools

`LocalizationPlanner`
- Ensures project is ready for adding translations
- Used when adding new languages to the project

`StringCatalogRead`
- Reads string keys grouped by translation state for requested locale
- Shows which strings are untranslated, in progress, or translated

`StringCatalogContext`
- Returns context and source language value for a given string key
- Useful for understanding translation context before translation

`StringCatalogEdit`
- Inserts a translation for a given locale into a String Catalog
- Supports simple strings as well as template-based variations with substitutions

### 6. Documentation and Help Tools

`DocumentationSearch`
- Searches Apple Developer Documentation using semantic matching
- Can search specific frameworks or across all documentation

`list_swift_topics`
- Lists all available Swift documentation topics

`search_swift_docs`
- Searches for keywords or phrases across offline Swift Markdown docs

`read_swift_doc`
- Reads the full content of a specific Swift documentation file

### 7. Template Management and Discovery

`XcodeListTemplates`
- Lists Xcode templates available in current Xcode install
- Supports filtering by platform, category, name, and template kind (target or project)

### 8. Preview and Rendering Tools

`RenderPreview`
- Builds and renders a Preview and waits for resulting UI snapshot
- Support for preview variants, localization overrides, and canvas control overrides

### 9. Code Snippet Execution

`RunCodeSnippet`
- Builds and runs a snippet of code in context of specific source file
- Useful for quick experimentation with code changes without full build cycles

### 10. Utility Tools

`XcodeGrep`
- Searches text patterns in files within the Xcode project structure using regex
- Works on project organization, not filesystem structure

## Authentication and Environment Setup

To use Xcode MCP tools effectively, you need to:

1. Have a valid Xcode installation (typically on macOS)
2. Have access to a developer account with proper entitlements
3. The agent must be approved by the user to interact with Xcode
4. A project or workspace must be opened first using `XcodeOpenWorkspace` or `XcodeNewProject`
5. For device interaction, a valid device session must be started with `DeviceInteractionStartSession`

## Sample Usage Scenarios

### Opening and Exploring a Project

1. `XcodeOpenWorkspace(path: "/Users/developer/Projects/MyApp.xcworkspace")`
2. `XcodeListTargets()`
3. `XcodeLS(path: "Sources/")`

### Building and Running a Project

1. `BuildProject()`
2. `RunProject(attachDebugger: false)`
3. `GetConsoleOutput(pattern: "error")`

### Testing an Application

1. `RunAllTests()`
2. `GetTestList()` to get available tests
3. `RunSomeTests(tests: [{targetName: "MyAppTests", testIdentifier: "MyAppTests/testExample"}])`

### Device Interaction for UI Testing

1. `DeviceInteractionStartWorkspaceSession(deviceIdentifier: "iPhone 15 Pro", sessionIdentifier: "UI Tests")`
2. `DeviceInteractionInstallAndRun()`
3. `DeviceInteractionSynthesize(interactionCommand: "t 100 200")` (tap at position)
4. `DeviceInteractionEndSession(interactionSessionKey: sessionKey)`

### Localization Workflow

1. `LocalizationPlanner(targetLocaleIdentifier: "fr")`
2. `StringCatalogRead(filePath: "en.lproj/Localizable.stringsdict", targetLocaleIdentifier: "fr")`
3. `StringCatalogEdit(filePath: "en.lproj/Localizable.stringsdict", stringKey: "hello", translation: "Bonjour", targetLocaleIdentifier: "fr")`

## Version Compatibility

The Xcode MCP tools require a specific version of Xcode with the MCP server installed and running. The server status can be checked using:
- `xcrun mcp-server status` (command line)

Tools may vary in availability based on:
- Installed Xcode version
- User approvals for agent permissions
- Project configuration and access permissions
- Available development team and provisioning profiles

## Error Handling

Most Xcode MCP tools will return clear error messages when:
- The user hasn't authorized the agent to use Xcode
- Required parameters are missing from tool calls
- Operations are attempted on non-existent files or targets
- Device interaction fails due to connection issues or permissions
- Build failures occur during project operations

Always check for appropriate error handling before calling tools, particularly when dealing with device interactions or build operations.
