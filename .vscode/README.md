# VS Code MAME Arcade Workflow (Pi 5)

This workspace is configured for native Raspberry Pi development with two build modes:

- Debug: source-level stepping and easier inspection
- Release: faster runtime while keeping symbols

## Build Scripts

- `./build_arcade_debug.sh`
  - `SUBTARGET=arcade`
  - `SYMBOLS=1`
  - `OPTIMIZE=0`
  - `USE_CHEATS=0`
  - `USE_TOOLS=0`
  - `USE_TESTS=0`

- `./build_arcade_release.sh`
  - `SUBTARGET=arcade`
  - `SYMBOLS=1`
  - `OPTIMIZE=2`
  - `USE_CHEATS=0`
  - `USE_TOOLS=0`
  - `USE_TESTS=0`

## Tasks (tasks.json)

Use Terminal -> Run Task:

- Build arcade debug
  - Normal incremental debug build

- Build arcade release
  - Normal incremental release build

- Clean arcade debug
  - Force-clean debug objects

- Clean arcade release
  - Force-clean release objects

- Rebuild arcade debug
  - Clean arcade debug, then Build arcade debug

- Rebuild arcade release
  - Clean arcade release, then Build arcade release

## Launch Profiles (launch.json)

Use Run and Debug:

- Debug mamearcade (prompt machine)
  - Fast debug iteration (incremental build first)

- Debug mamearcade (rebuild, prompt machine)
  - Full clean + rebuild, then debug launch

- Run mamearcade release (prompt machine)
  - Fast release run (incremental build first)

- Run mamearcade release (rebuild, prompt machine)
  - Full clean + rebuild, then release run

- Attach gdb to running mamearcade
  - Attach to an already-running process

## Recommended Daily Flow

1. Use Debug mamearcade (prompt machine) for normal C++ stepping.
2. Use rebuild variants only when you suspect stale objects.
3. Use release profiles when you want runtime behavior closer to normal play.

## Notes

- Binary path in launch configs is `${workspaceFolder}/mamearcade`.
- Machine name is prompted each run (default: pacman).
- GDB path is `/usr/bin/gdb`.
