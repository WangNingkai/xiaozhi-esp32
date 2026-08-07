---
name: fix-board-config-or-implementation
description: Workflow command scaffold for fix-board-config-or-implementation in xiaozhi-esp32.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /fix-board-config-or-implementation

Use this workflow when working on **fix-board-config-or-implementation** in `xiaozhi-esp32`.

## Goal

Fixes bugs or issues in the configuration or implementation of an existing board.

## Common Files

- `main/boards/*/*/config.h`
- `main/boards/*/*/config.json`
- `main/boards/*/*/*.cc`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit config.h and/or config.json for the board
- Edit the main source file ([board-name].cc) for the board
- Optionally update other board-specific files (e.g., lcd_init_cmds.h)

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.