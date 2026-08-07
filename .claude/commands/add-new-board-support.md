---
name: add-new-board-support
description: Workflow command scaffold for add-new-board-support in xiaozhi-esp32.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-new-board-support

Use this workflow when working on **add-new-board-support** in `xiaozhi-esp32`.

## Goal

Adds support for a new hardware board (e.g., ESP32 variant) to the project.

## Common Files

- `main/CMakeLists.txt`
- `main/Kconfig.projbuild`
- `main/boards/*/*/config.h`
- `main/boards/*/*/config.json`
- `main/boards/*/*/*.cc`
- `main/boards/*/*/README.md`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Add new board directory under main/boards/[vendor]/[board-name]/
- Create config.h, config.json, and main source file ([board-name].cc) in the new directory
- Add README.md for the board
- Optionally add other board-specific files (e.g., lcd_init_cmds.h, led_strip_control.h, power_manager.h, etc.)
- Update main/CMakeLists.txt and main/Kconfig.projbuild to include the new board

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.