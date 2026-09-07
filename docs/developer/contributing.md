# Contributing Guide

Contributions are welcome. This project values small, focused changes and a
green test suite.

## Workflow

1. Fork and branch from the default branch.
2. Make your change, keeping the scope tight.
3. Build and run the tests: `.\mediaflyouts.ps1 build -RunTests`.
4. Format your C++ (see below).
5. Open a pull request describing the change and why.

## Coding standards

- **C++20**, Qt 6. Keep portable logic in `Model/`; isolate Windows APIs in
  `Controllers/`.
- **Formatting** — C++ is formatted with the repository
  [`.clang-format`](../../.clang-format) (K&R braces, indented access
  specifiers). Run it before committing:
  ```powershell
  clang-format -i <files>
  ```
- **Comments** — explain *why*, not *what*; keep them short.
- **QML** — follow the existing structure; shared pieces live in `Views/` as
  small components (`IconLabel`, `RoundedArt`, `Setting*`, …).

### QML component reuse

- Flyouts derive from `FlyoutBase.qml` for shared window chrome, positioning,
  animation and auto-hide behavior. Do not duplicate that logic in a flyout.
- Taskbar-docked widgets derive from `DockableWidget.qml` for shared monitor
  placement, fullscreen/lock suppression and taskbar z-order handling.

## Adding a setting (common task)

1. Add a `Q_PROPERTY` + member + getter/setter + `reload()` line in
   [`Model/Settings`](../../Model/Settings.h).
2. Add a dashboard control in the relevant `Views/*` page.
3. Add default assertions to `tests/Model/SettingsTest.cpp` and
   `SettingsQtTest.cpp`.

## Commit messages

Use short, imperative, lower-case summaries describing the effect of the change
(e.g. *"add per-app icons to the volume mixer"*).

## Tests

New behavior should come with tests where practical — prefer putting logic in the
portable Model so it can be covered without Windows APIs. See the
[Testing Guide](testing.md).

## CI

Every push is built and tested (debug + release) by GitHub Actions. PRs must keep
CI green.
