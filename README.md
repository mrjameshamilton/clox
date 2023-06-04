# clox compiler

This is an implementation of the C Lox compiler from [Crafting Interpreters](https://github.com/munificent/craftinginterpreters). 
The implementation is mostly the same as in the book but with the following changes:

* Constants use 8 or 16-bit indices.
* New instructions:
    - `OP_ZERO` push 0 onto the stack
    - `OP_ONE` push 1 onto the stack
    - `OP_MINUS_ONE` push -1 onto the stack
    - `OP_INTEGER` pushes an 8-bit integer onto the stack
    - `OP_INTEGER_16` pushes a 16-bit integer onto the stack
    - `OP_CONSTANT_16` push a 16-bit indexed constant onto the stack
* New native functions:
    - `read()` reads a byte from `stdin` or `nil` if end of stream
    - `utf(byte, byte, byte, byte)` converts 1, 2, 3, or 4 bytes into a UTF string
    - `printerr(string)` prints a string to `stderr`
    - `exit(number)` exits with the specific exit code

These additions allow running [Lox.lox](https://github.com/mrjameshamilton/loxlox), an Lox interpreter written in Lox. In particular, Lox.lox introduces more constants than the original limit 255 per-chunk in the original clox implementation and requires the 4 native functions.

# Build

```shell
$ gcc src/*.src -O3 -o clox
```

# Run

```shell
$ ./clox examples/helloworld.lox
```
