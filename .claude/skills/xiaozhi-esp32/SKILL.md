```markdown
# xiaozhi-esp32 Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill covers the development patterns and workflows used in the `xiaozhi-esp32` repository, a Python-based project for ESP32 board support and configuration. The repository is organized for extensibility, allowing easy addition of new hardware boards, configuration updates, and multi-board maintenance. You'll learn the coding conventions, file organization, and step-by-step workflows for contributing effectively to this codebase.

## Coding Conventions

**File Naming**
- Uses camelCase for files and directories.
  - Example: `boardConfig.py`, `mainSource.cc`

**Import Style**
- Relative imports are preferred.
  - Example:
    ```python
    from .utils import parseConfig
    ```

**Export Style**
- Named exports are used (explicitly listing exported items).
  - Example:
    ```python
    __all__ = ['BoardManager', 'ConfigLoader']
    ```

**Commit Messages**
- Freeform, but often start with `fix:` or `feat:`
- Average length: ~52 characters
  - Example: `fix: correct GPIO mapping for lilygo-t-display`

## Workflows

### Add New Board Support
**Trigger:** When you want to add support for a new hardware board (e.g., ESP32 variant).  
**Command:** `/add-board`

1. Create a new directory under `main/boards/[vendor]/[board-name]/`.
2. Add the following files in the new directory:
    - `config.h`
    - `config.json`
    - Main source file: `[board-name].cc`
3. Add a `README.md` describing the board.
4. Optionally, add other board-specific files (e.g., `lcd_init_cmds.h`, `led_strip_control.h`, `power_manager.h`).
5. Update `main/CMakeLists.txt` and `main/Kconfig.projbuild` to include the new board.

**Example Directory Structure:**
```
main/
  boards/
    lilygo/
      tdisplay/
        config.h
        config.json
        tdisplay.cc
        README.md
        lcd_init_cmds.h
```

### Fix Board Config or Implementation
**Trigger:** When you need to fix a bug or update configuration for an existing board.  
**Command:** `/fix-board-config`

1. Edit `config.h` and/or `config.json` for the affected board.
2. Edit the main source file (`[board-name].cc`) as needed.
3. Optionally, update other board-specific files (e.g., `lcd_init_cmds.h`).

**Example Commit Message:**
```
fix: update SPI frequency in config.json for tdisplay
```

### Multi-Board Bugfix
**Trigger:** When a bug or config issue affects several boards at once (e.g., touch controller bug, GPIO config).  
**Command:** `/fix-multi-board`

1. Edit the main source file (`*.cc`) for each affected board.
2. Optionally, update shared configuration files (e.g., `main/idf_component.yml`).

**Example:**
```python
# In each affected board's main source file
def fix_touch_controller():
    # Apply bugfix for all boards using XPT2046
    pass
```

### Update Board Config JSON
**Trigger:** When you need to update metadata or minor settings in `config.json` files.  
**Command:** `/update-config-json`

1. Edit `config.json` for one or more boards to update metadata, fix typos, or adjust minor settings.

**Example:**
```json
{
  "manufacturer": "LilyGO",
  "model": "T-Display",
  "notes": "Added manufacturer field"
}
```

### Dependency or Version Bump
**Trigger:** When dependencies need to be updated or a new release/version is made.  
**Command:** `/bump-version`

1. Edit `CMakeLists.txt` or `main/idf_component.yml` to update version or dependencies.
2. Optionally, update partition files or other build-related scripts (e.g., `partitions/*/*.csv`).

**Example Commit Message:**
```
feat: bump IDF version to v4.4.3 in idf_component.yml
```

## Testing Patterns

- Test framework is unknown.
- Test files follow the pattern: `*.test.*`
- Place test files alongside the modules they test, using the naming convention:
  - Example: `boardManager.test.py`

**Example Test File:**
```python
# boardManager.test.py
from .boardManager import BoardManager

def test_board_init():
    bm = BoardManager()
    assert bm.is_initialized()
```

## Commands

| Command             | Purpose                                                         |
|---------------------|-----------------------------------------------------------------|
| /add-board          | Add support for a new hardware board                            |
| /fix-board-config   | Fix bugs or update configuration for an existing board          |
| /fix-multi-board    | Apply a bugfix or config change across multiple boards          |
| /update-config-json | Make minor updates to config.json for one or more boards        |
| /bump-version       | Update project dependencies or bump the project version         |
```