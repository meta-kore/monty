# monty

An interpreter for Monty ByteCodes files, written in C. It reads a `.m` file one instruction at a time and runs it against a stack or a queue, both held in the same doubly linked list.

```
$ cat example.m
push 1
push 2
push 3
pall
add
pall

$ ./monty example.m
3
2
1
5
1
```

## Build

```sh
gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o monty
./monty file.m
```

## Opcodes

| Opcode | What it does |
|---|---|
| `push n` | Push the integer `n` |
| `pall` | Print every value, top first |
| `pint` | Print the top value |
| `pop` | Remove the top value |
| `swap` | Swap the top two values |
| `add` `sub` `mul` `div` `mod` | Arithmetic on the top two values; the result replaces them |
| `nop` | Do nothing |
| `pchar` | Print the top value as an ASCII character |
| `pstr` | Print the stack as a string, until a zero or a non-ASCII value |
| `rotl` `rotr` | Rotate the stack to the top or to the bottom |
| `stack` `queue` | Switch between LIFO and FIFO behaviour |

Lines that start with `#` are not instructions. A bad instruction, an empty stack or a division by zero stops the run with an error and a line number.

## Layout

```
main.c                  Read the file, dispatch each line
get_opcodes.c           Opcode table
opcode_instructions*.c  The instructions themselves
doubly_functions.c      Doubly linked list helpers
malloc_functions.c      Allocation helpers
str_functions.c         String helpers
monty.h                 Types and prototypes
bf/                     Brainfuck programs from the same project
```

## Notes

Built as a project for ALX Africa Software Engineering.
