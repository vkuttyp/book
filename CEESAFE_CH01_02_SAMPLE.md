## Hello, World! (CeeSafe Edition)

Now that you've installed CeeSafe, it's time to write your first CeeSafe program.
It's traditional when learning a new language to write a little program that
prints the text `Hello, world!` to the screen, so we'll do the same here!

> Note: This book assumes basic familiarity with the command line. CeeSafe makes
> no specific demands about your editing or tooling or where your code lives, so
> if you prefer to use an IDE instead of the command line, feel free to use your
> favorite IDE. CeeSafe has VS Code extension support. See [Appendix D][devtools]
> for more details.

### Project Directory Setup

You'll start by making a directory to store your CeeSafe code. It doesn't matter
to CeeSafe where your code lives, but for the exercises and projects in this book,
we suggest making a _projects_ directory in your home directory and keeping all
your projects there.

Open a terminal and enter the following commands to make a _projects_ directory
and a directory for the "Hello, world!" project within the _projects_ directory.

For Linux, macOS, and PowerShell on Windows, enter this:

```console
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

For Windows CMD, enter this:

```cmd
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

### CeeSafe Program Basics

Next, make a new source file and call it _main.cee_. CeeSafe files always end with
the _.cee_ extension. If you're using more than one word in your filename, the
convention is to use an underscore to separate them. For example, use
_hello_world.cee_ rather than _helloworld.cee_.

Now open the _main.cee_ file you just created and enter the code in Listing 1-1.

**Listing 1-1: A program that prints `Hello, world!`**

```ceesafe
fn main() {
    Console.writeLine("Hello, world!");
}
```

Save the file and go back to your terminal window in the
_~/projects/hello_world_ directory. On Linux or macOS, enter the following
commands to compile and run the file:

```console
$ ceesafec build
$ ./out/hello_world
Hello, world!
```

On Windows, enter the command `.\out\hello_world` instead of `./out/hello_world`:

```powershell
$ ceesafec build
$ .\out\hello_world
Hello, world!
```

### Understanding the Program

Let's review this simple CeeSafe program in detail:

```ceesafe
fn main() {
    Console.writeLine("Hello, world!");
}
```

These lines define a function named `main` with:

- `fn` is the keyword to declare a function
- `main()` is the name of the function, with no parameters
- `{ }` marks the beginning and end of the function body
- `Console.writeLine("Hello, world!");` calls a function to print text to the console
  - `Console` is a built-in module for console I/O
  - `writeLine` writes text followed by a newline
  - The text is a string literal enclosed in double quotes
  - The line ends with a semicolon `;`, indicating the end of the statement

The `main` function is special: it's always the first code that runs in every 
CeeSafe program.

### Compilation and Execution with ceesafec

CeeSafe's compiler, `ceesafec`, is responsible for compiling your program. Unlike
`rustc`, which compiles directly to machine code, `ceesafec` first compiles your
code to C11, then uses your system's C compiler (gcc, clang, or MSVC) to produce
the final executable.

When you run `ceesafec build`:

1. CeeSafe parses and type-checks your code
2. CeeSafe generates portable C11 code
3. Your system's C compiler (automatically detected) compiles the C to an executable
4. The final binary is placed in `out/` directory

This two-stage compilation has several advantages:

- **Portability**: CeeSafe code compiles anywhere C11 compiles
- **Interoperability**: You can inspect the generated C code
- **Compatibility**: Works with existing C libraries seamlessly
- **Debugging**: Debuggers can show both CeeSafe and C source code

Let's verify this by looking at the generated C code:

```console
$ ceesafec build --emit c
$ cat out/main.c
```

You'll see the generated C code that implements your CeeSafe program. Understanding
this generated code can be enlightening and is covered in [Chapter 20][advanced].

### Difference from Compiled Rust

While Rust also compiles ahead of time, there are key differences:

| Feature | Rust | CeeSafe |
|---------|------|---------|
| **Output** | Machine code or LLVM IR | C11 source code |
| **C interop** | Via FFI (foreign function interface) | First-class citizen |
| **Build system** | Integrated (cargo) | Separate compiler + C compiler |
| **Intermediate code** | Not visible to user | Can inspect and debug |
| **Kernel integration** | Via `unsafe` and careful abstractions | Freestanding mode for kernel code |

### Debugging CeeSafe Programs

CeeSafe programs can be debugged with standard tools:

- **lldb** (macOS and Linux):
  ```console
  $ lldb out/hello_world
  ```
  
- **gdb** (Linux):
  ```console
  $ gdb out/hello_world
  ```
  
- **VS Code**: Install the CeeSafe extension for built-in debugging support

When debugging CeeSafe programs, the debugger shows your original CeeSafe source
code thanks to `#line` directives embedded in the generated C code.

### Quick Compilation Without Running: `ceesafec check`

To quickly check if your code compiles without building the full executable, use:

```console
$ ceesafec check
```

This performs parsing, type checking, and borrow checking, but skips C code
generation and linking. This is much faster for development.

### Next Steps

You've successfully compiled and run your first CeeSafe program! Now let's move on
to something more substantial. In the next section, we'll explore how to use
`ceesafec` to create a project with proper structure.

---

**Key Takeaways:**
- CeeSafe files end with `.cee` extension
- Use `ceesafec build` to compile (produces C, then executable)
- Use `ceesafec check` for quick type checking
- Use `ceesafec run` to compile and run directly
- The generated C code is readable and debuggable
- Standard debuggers work with CeeSafe programs

[devtools]: appendix-04-useful-development-tools.html
[advanced]: ch20-00-advanced-features.html
