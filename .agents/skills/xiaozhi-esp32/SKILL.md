```markdown
# xiaozhi-esp32 Development Patterns

> Auto-generated skill from repository analysis

## Overview
The `xiaozhi-esp32` repository is a Python-based project focused on supporting various ESP32 hardware boards. It is structured to facilitate the addition of new board configurations, manage updates to board support, handle dependency and version management, and maintain comprehensive documentation. The project emphasizes modularity, clarity, and maintainability, making it straightforward for contributors to add or update board support and related configurations.

## Coding Conventions

- **File Naming:**  
  Uses `camelCase` for file names.  
  *Example:*  
  ```
  ledStripControl.py
  powerManager.py
  ```

- **Import Style:**  
  Uses **relative imports** within modules.  
  *Example:*  
  ```python
  from .utils import BoardConfig
  ```

- **Export Style:**  
  Prefers **named exports** (explicitly listing what is exported).  
  *Example:*  
  ```python
  __all__ = ['BoardManager', 'ConfigLoader']
  ```

- **Commit Messages:**  
  - Prefixes: `feat`, `fix`
  - Freeform, average ~52 characters  
  *Example:*  
  ```
  feat: add GT911 touch support for lilygo-t-display
  fix: correct pin mapping for m5stack-core2
  ```

## Workflows

### Add New Board Support
**Trigger:** When you want to add support for a new hardware board (e.g., ESP32 variant).  
**Command:** `/add-board`

1. Create a new directory:  
   `main/boards/<vendor>/<board-name>/`
2. Add configuration files:  
   - `config.h`
   - `config.json`
   - Main source file (e.g., `<board-name>.cc`)
3. Add a `README.md` for the new board.
4. Optionally, add extra files as needed (e.g., `led_strip_control.cc/h`, `power_manager.h`, `lcd_init_cmds.h`).
5. Update `main/CMakeLists.txt` and `main/Kconfig.projbuild` to include the new board.

*Example directory structure:*
```
main/boards/acme/esp32-super/
  ├── config.h
  ├── config.json
  ├── esp32-super.cc
  ├── README.md
```

### Fix or Update Board Configurations
**Trigger:** When you need to fix bugs or update configuration/source files for one or more boards.  
**Command:** `/fix-board-config`

1. Edit relevant `.cc` files for affected boards.
2. Update `config.json` or `config.h` as needed.
3. Optionally, update `main/idf_component.yml` if dependencies are affected.
4. Commit with a message referencing the boards and the fix.

*Example commit message:*
```
fix: update GT911 config for lilygo-t-display and m5stack-core2
```

### Bump Project Version
**Trigger:** When releasing a new version or updating the project version number.  
**Command:** `/bump-version`

1. Edit `CMakeLists.txt` to update the `PROJECT_VER`.
2. Optionally, update `scripts/release.py` or related build/release scripts.
3. Commit with a message indicating the new version.

*Example:*
```cmake
set(PROJECT_VER "1.2.3")
```

### Update Dependencies
**Trigger:** When updating third-party library or component versions.  
**Command:** `/update-deps`

1. Edit `main/idf_component.yml` to update dependency versions.
2. Optionally, update related configuration files (e.g., `partitions/v2/4m.csv`).
3. Commit with a message referencing updated dependencies.

*Example commit message:*
```
feat: update esp-idf to v4.4.3 and lvgl to v8.2.0
```

### Update README or Documentation
**Trigger:** When updating documentation, links, or board-specific notes.  
**Command:** `/update-docs`

1. Edit `README.md` and/or language-specific README files.
2. Optionally, edit board-specific `README.md` files.
3. Commit with a message referencing the documentation update.

*Example commit message:*
```
docs: update setup instructions for new boards
```

## Testing Patterns

- **Framework:** Unknown (not explicitly detected).
- **Test File Pattern:** Files named with `*.test.*` (e.g., `boardConfig.test.py`).
- **Typical Structure:**  
  Test files are placed alongside the modules they test, using the `.test.` infix in the filename.

*Example:*
```
main/boards/acme/esp32-super/boardConfig.test.py
```

## Commands

| Command         | Purpose                                                      |
|-----------------|-------------------------------------------------------------|
| /add-board      | Add support for a new hardware board                        |
| /fix-board-config | Fix or update configuration/source files for boards         |
| /bump-version   | Update the project version                                   |
| /update-deps    | Update dependency versions                                   |
| /update-docs    | Update README or documentation files                         |
```
