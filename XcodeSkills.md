# Xcode export skills
Xcode 27 comes with a comand to export skills

```bash
`xcrun agent skills export --output-dir ~/Downloads/xcode-skills`
```

You will see this output
```bash
Exported 10 skills to /Downloads/xcode-skills
  ✓ app-intents-whats-new-27
  ✓ device-interaction
  ✓ adopt-c-bounds-safety
  ✓ swiftui-specialist
  ✓ modernize-tests
  ✓ app-intents-specialist
  ✓ uikit-app-modernization
  ✓ swiftui-whats-new-27
  ✓ audit-xcode-security-settings
  ✓ building-document-based-swiftui-applications
```

**You can use them for development on Mac platforms but *you are not allowed to redistribute the content.***

Below is a detailed breakdown of the available skills, categorized by their area of impact.

## 🚀 Modernizing UI & Frameworks

### SwiftUI Specialist
The **SwiftUI Specialist** is the gold standard for building modern user interfaces. Rather than relying on generic patterns, this skill implements authoritative guidance on:
* **Efficient Data Flow**: Expert utilization of `@Observable` and `@State` to prevent unnecessary view redraws.
* **Performance Optimization**: Guidance on `ForEach` and `List` identity to ensure smooth scrolling and stable state.
* **Advanced Animations**: Implementation of complex animations using `@Animatable` and custom animatable data.
* **Localization**: Ensuring apps are world-ready using `LocalizedStringResource` and proper RTL (Right-to-Left) support.

### SwiftUI What's New (SDK 27)
SwiftUI evolves rapidly. This skill focuses specifically on the cutting-edge features introduced in the 2027 OS releases:
* **Interactive Containers**: Implementing drag-to-reorder functionality across any container (not just Lists).
* **Enhanced Networking**: Modernizing `AsyncImage` with custom caching and `URLSession` configurations.
* **Adaptive Toolbars**: Managing toolbar overflow and visibility priorities for different screen sizes.
* **Macro Migration**: Helping developers navigate the transition of `@State` from a property wrapper to a macro.

### UIKit App Modernization
For those maintaining established apps, the **UIKit Modernization** skill focuses on bringing legacy apps into the multi-window era:
* **Shared-State Elimination**: Replacing deprecated global references (like `UIScreen.main`) with context-aware alternatives.
* **Scene Lifecycle Migration**: Moving from the old `AppDelegate` model to the modern `SceneDelegate` architecture.
* **Dynamic Layouts**: Removing assumptions about symmetric safe areas and fixed orientations to support iPadOS multitasking and Stage Manager.

---

## 🛠 System Integration & Intelligence

### App Intents Specialist (Evergreen)
App Intents are the gateway to Siri, Shortcuts, and Spotlight. This skill ensures that Intents are built for stability and discoverability:
* **Execution Model**: Ensuring `perform()` methods are `Sendable` and handled idempotently.
* **Stable Entities**: Designing `AppEntity` and `AppEnum` identifiers that persist across device launches.
* **User Experience**: Optimizing parameter summaries and localization to make shortcuts intuitive for end-users.

### App Intents What's New (SDK 26/27)
This skill extends Intent capabilities into the realm of Apple Intelligence and advanced system interactions:
* **Visual Intelligence**: Integration with camera and on-screen search via `IntentValueQuery`.
* **Background Execution**: Managing `LongRunningIntent` and background task performance.
* **Interactive Snippets**: Creating rich, actionable UI snippets that appear directly within the Siri interface.

### Document-Based App Architecture
Building apps that handle files requires a deep understanding of system coordination. This skill provides a blueprint for:
* **The Document Protocol**: Implementing the modern `Document` protocol for seamless reading and writing.
* **Auto-save & Undo**: Ensuring a robust user experience by correctly registering undo actions—a prerequisite for SwiftUI's auto-save.
* **Custom File Formats**: Declaring and verifying custom `UTType` identifiers for proprietary document formats.

---

## 🛡 Security & Quality Assurance

### Xcode Security Audit
Security is not a one-time check but a continuous process. This skill automates the hardening of Xcode projects:
* **Enhanced Security**: Enabling compiler warnings and static analyzer checkers to catch vulnerabilities early.
* **Hardening Features**: Implementing Pointer Authentication (PAC) and Hardware Memory Tagging (MTE) on supported ARM64e slices.
* **Runtime Protection**: Configuring "hardened heap" and stack-variable zero-initialization to mitigate memory-based attacks.

### C Bounds Safety Adoption
For projects utilizing C, memory safety is a critical concern. This skill guides the adoption of the `-fbounds-safety` extension:
* **Pointer Annotations**: Implementing `__counted_by` and `__sized_by` to let the compiler prove bounds safety.
* **Deterministic Traps**: Converting exploitable out-of-bounds vulnerabilities into deterministic runtime traps.
* **Adoption Strategy**: Providing a structured workflow to migrate existing C codebases without breaking stability.

### Test Suite Modernization
Testing is the bedrock of reliability. This skill helps teams transition from XCTest to the modern **Swift Testing** framework:
* **Framework Migration**: Converting `XCTestCase` classes into lean Swift Testing structs.
* **Assertion Updates**: Mapping legacy `XCTAssert` calls to modern `#expect` and `#require` macros.
* **Concurrency Testing**: Transitioning from `XCTestExpectation` to the more intuitive `confirmation()` API for async work.

---

## 📱 Testing & Verification

### Device Interaction
Because simulators cannot capture everything, the **Device Interaction** skill allows for automated verification on real hardware:
* **UI Hierarchy Analysis**: Reading the live accessibility and view hierarchy to find exact "hit points" for interaction.
* **Synthesized Events**: Executing complex touch sequences (swipes, pinches, multi-touch) and hardware button presses.
* **Visual Validation**: capturing screenshots and comparing them against expected behaviors to detect layout regressions.

