# TinyLanguage Compiler

A C# desktop application that implements a **Scanner (Lexer)** and **Recursive Descent Parser** for the **Tiny language** — a compact, educational programming language commonly used in compiler design courses.

---

## Overview

This project walks through the two front-end phases of a compiler:

1. **Scanning / Lexical Analysis** — reads raw source code and breaks it into a stream of classified tokens.
2. **Parsing / Syntax Analysis** — consumes those tokens and builds a visual parse tree that reflects the syntactic structure of the program.

The application comes with a simple GUI that lets you load or type Tiny source code, run the scanner to inspect tokens, then parse them into a tree — all in one window.

---

## Features

- Lexical analysis of Tiny language source code
- Token classification (keywords, identifiers, numbers, operators, symbols, etc.)
- Recursive descent parser producing a structured parse tree
- Interactive GUI for inputting code and visualizing output
- Test case file included for quick demos

---

## Project Structure

```
TinyLanguage_Compiler/
├── Tiny_Compiler/
│   ├── Scanner.cs          # Lexer — tokenizes input source code
│   ├── Parser.cs           # Parser — builds the parse tree from tokens
│   ├── Form1.cs            # Main GUI form
│   ├── Form1.Designer.cs   # Auto-generated UI layout
│   └── Program.cs          # Entry point
├── Tiny_Compiler.sln       # Visual Studio solution file
└── TinyTestCase.txt        # Sample Tiny language program for testing
```

---

## Getting Started

### Prerequisites

- [Visual Studio](https://visualstudio.microsoft.com/) 2019 or later (Community edition works fine)
- .NET Framework (version used by the solution)

### Running the Project

1. Clone the repository:
   ```bash
   git clone https://github.com/habibaQotb/TinyLanguage_Compiler.git
   ```
2. Open `Tiny_Compiler.sln` in Visual Studio.
3. Build the solution (`Ctrl+Shift+B`).
4. Run the application (`F5`).
5. Paste or load Tiny source code (use `TinyTestCase.txt` as a starting point).
6. Click **Scan** to see the token list, then **Parse** to generate the parse tree.

---

## The Tiny Language

Tiny is a minimal imperative language designed for teaching compiler construction. It supports:

| Construct | Syntax |
|---|---|
| Variable assignment | `x := 5` |
| Read input | `read x` |
| Write output | `write x` |
| If-then-else | `if <expr> then ... else ... end` |
| Repeat loop | `repeat ... until <expr>` |
| Arithmetic expressions | `+`, `-`, `*`, `/` |
| Comparison | `<`, `=` |

### Example Program

```
read x;
if x < 0 then
  write 0
else
  write x
end
```

---

## Token Types

The scanner recognizes the following token categories:

| Category | Examples |
|---|---|
| Keywords | `if`, `then`, `else`, `end`, `repeat`, `until`, `read`, `write` |
| Identifiers | `x`, `myVar`, `result` |
| Numbers | `0`, `42`, `100` |
| Operators | `:=`, `<`, `=`, `+`, `-`, `*`, `/` |
| Symbols | `;`, `(`, `)` |

---

## How It Works

### Scanner (`Scanner.cs`)

Reads the source string character by character, groups characters into lexemes, and emits a `(token_type, value)` pair for each one. Whitespace and comments are skipped. The result is a flat list of tokens passed to the parser.

### Parser (`Parser.cs`)

Implements a **recursive descent parser** following the Tiny grammar. Each grammar rule maps to a method (e.g., `ParseStmtSequence`, `ParseIfStmt`, `ParseExpr`). As the parser matches rules, it constructs a tree of nodes, which is then displayed in the GUI.

---

## Authors

Developed as a compiler design course project.

---

## License

This project is for educational purposes. Feel free to use or adapt it for your own studies.
