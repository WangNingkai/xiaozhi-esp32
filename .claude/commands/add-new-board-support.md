---
name: add-new-board-support
description: Workflow command scaffold for add-new-board-support in xiaozhi-esp32.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-new-board-support

Use this workflow when working on **add-new-board-support** in `xiaozhi-esp32`.

## Goal

Adds support for a new hardware board (e.g., ESP32 variant) including configuration, source, and documentation.

## Common Files

- `main/boards/*/<board-name>/config.h`
- `main/boards/*/<board-name>/config.json`
- `main/boards/*/<board-name>/*.cc`
- `main/boards/*/<board-name>/README.md`
- `main/CMakeLists.txt`
- `main/Kconfig.projbuild`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create new board directory under main/boards/<vendor>/<board-name>/
- Add config.h, config.json, and main source file (e.g., <board-name>.cc)
- Add README.md for the board
- Optionally add extra files (e.g., led_strip_control.cc/h, power_manager.h, lcd_init_cmds.h)
- Update main/CMakeLists.txt and main/Kconfig.projbuild to include the new board

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.