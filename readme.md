## Electronic Wallet System (C)

A simple command‑line wallet manager written in C. It lets you add, view, and remove card records stored in a plain‑text file (`wallet.txt`). Useful as a small CRUD CLI app and a C file I/O example.

### Features
- **Add cards**: store card number, first name, last name, and balance
- **View cards**: list all cards with formatted output
- **Remove cards**: delete a card by its number
- **Persistent storage**: data saved in `wallet.txt` alongside the executable

### Requirements
- C compiler (GCC/Clang)
- macOS/Linux or Windows (via WSL/Git Bash/MinGW)
- Optional: CMake 3.16+ for a CMake build

### Build
You can build with GCC/Clang directly, or via CMake.

#### Option A — GCC/Clang
From the `Electronic Wallet System` directory:

```bash
gcc main.c -o wallet
```

#### Option B — CMake
From the `Electronic Wallet System` directory:

```bash
cmake -S . -B cmake-build-debug
cmake --build cmake-build-debug --config Debug
```

This produces an executable (name may be `C_PP` per `CMakeLists.txt`). You can also rename or add another target that outputs `wallet` if you prefer.

### Run
From the build directory (where the executable exists) or from the source directory if you used GCC:

```bash
./wallet help
```

Commands:

```bash
wallet help
wallet add <card_number> <first_name> <last_name> <balance>
wallet view
wallet remove <card_number>
```

Examples:

```bash
# Show available commands
./wallet help

# Add a new card
./wallet add 123456789012 John Doe 250.75

# List all cards
./wallet view

# Remove a card by number
./wallet remove 123456789012
```

### How it works
- Records are stored in `wallet.txt` in the same directory as the executable.
- Each line represents one card in the format:

```text
<number> <first_name> <last_name> <balance>
```

- On each add/remove, the program reads all records into memory, applies changes, and writes them back to `wallet.txt`.

### Data and limits (from source constants)
- Max cards: `100`
- Max card number length: `20` characters (digits only)
- Max first/last name length: `50` characters each
- Balance is stored as a floating‑point number (printed with 2 decimals)

### Project structure

```text
Electronic Wallet System/
├─ main.c            # CLI implementation
├─ CMakeLists.txt    # Optional CMake build
├─ wallet.txt        # Data file (created on first write)
└─ readme.md         # This file
```

### Notes
- Output uses ANSI color codes. If colors don’t display on Windows, run via WSL/Git Bash/Windows Terminal, or disable ANSI in your terminal settings.
- The CMake target name is currently `C_PP`; feel free to rename it to `wallet` if desired.

### Troubleshooting
- "Command not found": ensure you run with `./wallet` on Unix‑like systems and that the file is executable (`chmod +x wallet`).
- "File not found" for `wallet.txt`: it will be created automatically on first successful add; until then, `view` will show “No cards found.”
- Build errors on macOS with Clang: try `clang main.c -o wallet` instead of `gcc` if your GCC wrapper points to Clang anyway.

### Contributing
Small improvements are welcome: better validation, search/update commands, CSV/JSON export, tests, or refactoring to separate modules.

### License
No license specified by the author. If you plan to use or distribute this code, add a license to the repository.

Electronic Wallet System created by Criste Ioan-Paul

To run it open a terminal into the directory using "gcc main.c -o wallet".
To use it write into the terminal "./wallet help" to get started
