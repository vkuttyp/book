# The CeeSafe Programming Language Book

## About This Book

This book is an adaptation of "The Rust Programming Language" book, tailored for **CeeSafe** — a modern systems programming language that combines memory safety with C compatibility.

### What is CeeSafe?

CeeSafe is a memory-safe systems programming language with:

- **Rust-like ownership and borrowing**: Safe memory management without garbage collection
- **Direct C compilation**: Compiles to portable, readable C11 code
- **C interoperability**: Seamlessly call C libraries and be called from C
- **Deterministic cleanup**: Values are destroyed at known points with destructors
- **Zero-cost abstractions**: No runtime overhead for safety features
- **Kernel-ready**: Freestanding mode for OS and embedded development

### Why This Adaptation?

While Rust compiles to LLVM IR and machine code, CeeSafe compiles to C. This fundamental difference means:

1. **Different compilation model**: CeeSafe targets C11 compatibility over direct binary generation
2. **C FFI first-class**: Interop with C is built into the language, not an afterthought
3. **Different tooling**: Uses `ceesafec` (not `cargo`) and works with any C compiler
4. **Kernel integration**: Easier integration into existing C codebases like operating systems

### How to Use This Book

This adaptation follows the same structure and pedagogical approach as the original Rust book but:

- All code examples have been converted from Rust to CeeSafe syntax
- Concepts tied to Rust-specific features (like the macro system) are adapted or replaced
- C backend details are explained where they differ from Rust
- CeeSafe-specific features (like pluggable allocators and async executor) are covered

### Structure

- **Part 1**: Getting Started - Installation, hello world, and basic concepts
- **Part 2**: Language Fundamentals - Variables, data types, functions, control flow
- **Part 3**: Ownership & Memory - The core of CeeSafe's safety model
- **Part 4**: Collections & Generics - Building larger programs
- **Part 5**: Advanced Features - Unsafe code, async/await, kernel integration
- **Part 6**: Final Project - Building a practical CeeSafe application

### For Rust Developers

If you're coming from Rust, you'll find many familiar concepts:

- Ownership and borrowing work the same way
- The `unsafe` keyword serves a similar purpose
- Error handling uses `Result` types
- Pattern matching and generics are similar
- The module system is familiar

Key differences to watch for:

- No lifetimes in most code (inferred from scopes)
- C interop is ubiquitous
- Async model is more constrained (tasks must finish when their scope ends)
- Allocators are explicit and per-allocation
- The backend is C, not machine code

### Getting CeeSafe

Install the latest release:

**macOS and Linux:**
```bash
curl -fsSL https://ceesafe.github.io/CeeSafe/install.sh | sh
```

**Windows (PowerShell):**
```powershell
irm https://ceesafe.github.io/CeeSafe/install.ps1 | iex
```

### Building the Book

```bash
mdbook build
```

Open `book/index.html` in a web browser to view the built book.

### Contributing

This is a fork for educational purposes. For:

- **Issues about CeeSafe concepts**: Open an issue in this repository
- **Issues about the language itself**: See [CeeSafe/CeeSafe](https://github.com/CeeSafe/CeeSafe)
- **Original Rust book**: See [rust-lang/book](https://github.com/rust-lang/book)

### License

This book is licensed under the same terms as the original Rust book. See LICENSE-MIT and LICENSE-APACHE.

---

**Start reading**: [Chapter 1: Getting Started](src/ch01-00-getting-started.md)

**Quick reference**: [CeeSafe Documentation](https://ceesafe.github.io/CeeSafe/)
