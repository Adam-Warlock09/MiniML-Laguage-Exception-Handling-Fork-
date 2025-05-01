# Extending the Minimal Language with Exceptions

**A PL Zoo Language Extension Project**

- **Name**: Aric Maji  
- **Roll Number**: CS24BTECH11007  
- **Department**: Computer Science, IIT Hyderabad  

---

## 🧠 Overview

This project extends the `minimal` language from PL Zoo to support exception handling.  
We introduce two new language constructs:

- `raise E` — raises an exception with tag `E`
- `try { e1 } with { |E -> e2 }` — evaluates `e1` and, if it raises `E`, evaluates the handler `e2`

We modified the lexer, parser, abstract syntax tree, compiler, and abstract machine to support these.

---

## 📘 Formal Language Extension

### 🔤 Syntax Additions

New grammar rules:

```ocaml
expr:
  ...
  | raise DivisionByZero;;
  | try {20} with {|DivisionByZero -> 10}
```
Returns 20

## 📦 README (User Guide)
### 🛠️ Build Instructions

1. Clone the PL Zoo repository and navigate to the minimal directory.
2. Build the project using dune:

```bash
dune build
```
3. Run the interpreter:

```bash
./miniml.exe
```

## ⚠️ Limitations

- Only tagged exceptions like `DivisionByZero` and **partially** `GenericException` are supported.
- Payloads like `GenericException of int` are **not deeply pattern matched**.
- Handlers do **not retain stack traces or messages**.
- `GenericException` may still be **buggy or incomplete**.

## ✅ Verification Approach

We tested the following:

- Simple raises and catches
- Uncaught exceptions
- Nested `try-with` blocks
- Arithmetic inside exception handlers
- Problem statement test cases

## 🎓 Key Learnings

- Implemented exceptions via control stacks (not using OCaml's built-in ones)
- Understood virtual machine control flow and environment models
- Learned how high-level features compile into low-level instructions
- Practiced modifying all parts of a language toolchain: lexer, parser, AST, compiler, and virtual machine

