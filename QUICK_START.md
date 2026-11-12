# CeeSafe Book Adaptation - Quick Start

## 🎯 Project Goal

Adapt "The Rust Programming Language" book to teach **CeeSafe** - a memory-safe systems programming language that compiles to C.

## 📍 Repository

- **Fork**: https://github.com/vkuttyp/book
- **Branch**: `ceesafe-book`
- **Original**: https://github.com/rust-lang/book

## 🚀 Quick Clone & Setup

```bash
git clone https://github.com/vkuttyp/book.git
cd book
git checkout ceesafe-book
```

## 📚 Key Documentation Files

1. **CEESAFE_ADAPTATION.md** - Start here! Overview of the project
2. **CEESAFE_EXPLORATION.md** - Deep dive into CeeSafe features
3. **ADAPTATION_ROADMAP.md** - Chapter-by-chapter mapping
4. **CEESAFE_CH01_02_SAMPLE.md** - Example of adapted chapter

## 🔧 CeeSafe vs Rust Quick Reference

| Task | Rust | CeeSafe |
|------|------|---------|
| Hello world | `println!()` | `Console.writeLine()` |
| Create project | `cargo new` | `ceesafec new` |
| Check code | `cargo check` | `ceesafec check` |
| Build | `cargo build` | `ceesafec build` |
| Run | `cargo run` | `ceesafec run` |
| Test | `cargo test` | `ceesafec test` |
| File extension | `.rs` | `.cee` |
| Config file | `Cargo.toml` | `ceesafe.toml` |
| Mutable borrow | `&mut x` | `borrow mut x` |
| Self reference | `self` | `this` |

## 📖 Chapter Adaptation Checklist

When adapting a chapter:

- [ ] Read the original Rust chapter
- [ ] Review ADAPTATION_ROADMAP.md for that chapter
- [ ] Study CEESAFE_CH01_02_SAMPLE.md for style
- [ ] Convert Rust examples to CeeSafe syntax
- [ ] Add CeeSafe-specific notes
- [ ] Test all code examples: `ceesafec check`
- [ ] Build book: `mdbook build`
- [ ] Review HTML output: `open book/index.html`
- [ ] Commit with descriptive message
- [ ] Push to `ceesafe-book` branch

## 🧪 Validating Code Examples

```bash
# Quick compile check
ceesafec check example.cee

# Build and run
ceesafec run example.cee

# Run tests
ceesafec test example.cee

# View generated C
ceesafec build --emit c example.cee
cat out/example.c
```

## 🎓 Key Differences Explained

### Compilation Model
- **Rust**: → LLVM IR → Binary
- **CeeSafe**: → C11 → Binary

### Memory Management
- **Rust**: Ownership + LLVM optimization
- **CeeSafe**: Ownership + C compiler optimization

### C Integration
- **Rust**: FFI (separate mechanism)
- **CeeSafe**: Native (first-class feature)

## 📋 Chapters Status

- [ ] Ch 1: Getting Started
- [ ] Ch 2: Guessing Game
- [ ] Ch 3: Common Concepts
- [ ] Ch 4: Ownership
- [ ] Ch 5: Structs
- [ ] Ch 6: Enums
- [ ] Ch 7: Modules
- [ ] Ch 8: Collections
- [ ] Ch 9: Error Handling
- [ ] Ch 10: Generics
- [ ] Ch 11: Testing
- [ ] Ch 12: I/O Project
- [ ] Ch 13: Functional Features
- [ ] Ch 14: More Cargo (ceesafec)
- [ ] Ch 15: Smart Pointers
- [ ] Ch 16: Concurrency
- [ ] Ch 17: Async/Await
- [ ] Ch 18: OOP
- [ ] Ch 19: Patterns
- [ ] Ch 20: Advanced
- [ ] Ch 21: Final Project

**Status: 0/21 chapters adapted** (Foundation complete)

## 🔗 Important Links

- **CeeSafe GitHub**: https://github.com/CeeSafe/CeeSafe
- **CeeSafe Docs**: https://ceesafe.github.io/CeeSafe/
- **Rust Book Repo**: https://github.com/rust-lang/book
- **mdBook**: https://rust-lang.github.io/mdBook/

## 💡 Pro Tips

1. **Start with basics**: Chapters 1-5 are foundational, easiest to adapt
2. **Test as you go**: Verify code compiles with `ceesafec check`
3. **Reference existing**: Compare with CEESAFE_CH01_02_SAMPLE.md
4. **Document differences**: Note where CeeSafe differs from Rust
5. **Ask questions**: Open an issue if unclear about concepts

## 🤝 Contributing

1. Pick a chapter (see status above)
2. Read the original Rust chapter
3. Refer to ADAPTATION_ROADMAP.md for guidance
4. Convert examples to CeeSafe
5. Test everything
6. Commit with clear messages
7. Push to `ceesafe-book` branch

## ❓ Quick FAQ

**Q: Do I need to know Rust?**
A: No! But it helps. CeeSafe is designed for people new to systems programming.

**Q: What if a concept doesn't translate?**
A: Document the difference and explain CeeSafe's approach. Check ADAPTATION_ROADMAP.md.

**Q: How do I test code examples?**
A: Use `ceesafec check`, `ceesafec run`, and `ceesafec test` on .cee files.

**Q: Can I request a specific chapter?**
A: Yes! Open an issue to claim a chapter and prevent duplicated work.

**Q: Where's the CeeSafe install command again?**
A: macOS/Linux: `curl -fsSL https://ceesafe.github.io/CeeSafe/install.sh | sh`

## 🎯 Next Milestone

Complete adaptation of Part 1 (Chapters 1-3: Getting Started) with all code examples tested and verified.

---

**Questions?** Check the full project summary in the repository!

