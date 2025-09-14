# Assembler in C – OU 20465

This repository contains my **Assembler project in C** for the Open University course 20465.

## Project Structure
A quick glance at the folders/files:

```
projectLinoyBiton/
└── Maman14
    ├── .vscode
    │   └── settings.json
    ├── assembler
    │   ├── assembler.c
    │   ├── assembler.h
    │   ├── assembler.o
    │   └── assembler_program
    ├── include
    │   ├── constants.h
    │   ├── first_pass.h
    │   ├── opcode_table.h
    │   ├── pre_process.h
    │   ├── second_pass.h
    │   ├── symbol_table.h
    │   ├── syntax_analyzer.h
    │   └── utility.h
    ├── invalid_tests
    │   ├── error_test_update.png
    │   ├── errors_test_updated.am
    │   ├── errors_test_updated.as
    │   ├── file.kkk
    │   ├── filekkk-nameincorrent.png
    │   ├── incorrentoperands.am
    │   ├── incorrentoperands.as
    │   ├── incorrentoperands.png
    │   ├── invalid1-5.png
    │   ├── invalid1.as
    │   ├── invalid2.as
    │   ├── invalid3.as
    │   ├── invalid4.as
    │   ├── invalid5.as
    │   ├── invalid6.am
    │   ├── invalid6.as
    │   ├── invalid6.png
    │   ├── invalidtest1.as
    │   └── invalidtest1.png
    ├── makefile
    ├── name&id
    ├── obj
    │   ├── first_pass.o
    │   ├── opcode_table.o
    │   ├── pre_process.o
    │   ├── second_pass.o
    │   ├── symbol_table.o
    │   ├── syntax_analyzer.o
    │   └── utility.o
    ├── src
    │   ├── first_pass.c
    │   ├── first_pass.o
    │   ├── opcode_table.c
    │   ├── opcode_table.o
    │   ├── pre_process.c
    │   ├── pre_process.o
    │   ├── second_pass.c
    │   ├── second_pass.o
    │   ├── symbol_table.c
    │   ├── symbol_table.o
    │   ├── syntax_analyzer.c
    │   ├── syntax_analyzer.o
    │   ├── utility.c
    │   └── utility.o
    └── tests
        ├── assembly_mac.am
        ├── assembly_mac.as
        ├── assembly_mac.ob
        ├── bacis_code_test.am
        ├── bacis_code_test.as
        ├── bacis_code_test.ob
        ├── complex_assembly_test.am
        ├── complex_assembly_test.as
        ├── complex_assembly_test.ent
        ├── complex_assembly_test.ext
        ├── complex_assembly_test.ob
        ├── fib_sequence.am
        ├── fib_sequence.as
        ├── fib_sequence.ent
        ├── fib_sequence.ext
        ├── fib_sequence.ob
        ├── guidance_test.am
        ├── guidance_test.as
        ├── guidance_test.ent
        ├── guidance_test.ob
        ├── ps.am
        ├── ps.as
        ├── ps.ent
        ├── ps.ext
        ├── ps.ob
        ├── test.am
        └── test.as
```

---

## ⚙️ Build Instructions

This repository is a **public showcase** of the Assembler project structure.  
The full source code is private and available upon request.


---

# Assembler in C – OU 20465

This project was developed as part of the **"Systems Programming Lab (20465)"** course at the Open University of Israel.
The assignment (Maman 14) required implementing an **Assembler in C** that translates a simplified assembly language into machine code, including full handling of symbols, macros, and errors.

---

## 📂 Project Structure

```
src/            # Source code (.c files)
include/        # Header files (.h files)
assembler/      # Main assembler module
tests/          # Example input/output files
invalid_tests/  # Invalid input tests (error handling)
makefile        # Build instructions
```

---

## ⚙️ Build Instructions

The project must be compiled on **Linux (Ubuntu)** with `gcc`, using the following flags (as required by the course):

```bash
make            # uses the provided makefile
```

Or manually:

```bash
gcc -ansi -pedantic -Wall -o assembler src/*.c assembler/assembler.c
```

> The code compiles **without warnings**.

---

## ▶️ Running the Assembler

The assembler accepts one or more assembly source files (`.as`) as input.
For each input file, it generates the appropriate output files:

* **`.ob`** – Object file (machine code)
* **`.ent`** – Entries file (labels declared as `.entry`)
* **`.ext`** – Externals file (labels declared as `.extern`)

Example:

```bash
./assembler tests/example.as
```

Output:

```
example.ob
example.ent
example.ext
```

---

## 📝 Example

Input file (`tests/fib_sequence.as`):

```asm
MAIN:   mov r3, LENGTH
        add r2, r3
        cmp r2, #-1
        bne END
        stop
LENGTH: .data 6,-9,15
END:    stop
```

After running:

* `fib_sequence.ob` – contains translated machine code
* `fib_sequence.ent` – contains entry labels (if any)
* `fib_sequence.ext` – contains external labels (if any)

---

## 📖 Features Implemented

* **Pre-processor**: macro expansion before assembly.
* **Two-pass assembler**:

  1. First pass – build symbol table, validate syntax.
  2. Second pass – encode instructions and resolve labels.
* **Symbol table management** (internal, external, entry).
* **Error detection** with detailed messages.
* **Support for directives**: `.data`, `.string`, `.entry`, `.extern`.
* **Support for addressing methods** and instruction set defined in the assignment.

---

## 📦 Notes

* All tests provided with the project (`tests/`, `invalid_tests/`) demonstrate the assembler’s correctness.
* Output files (`*.ob`, `*.ent`, `*.ext`) are ignored by Git (see `.gitignore`).

---

