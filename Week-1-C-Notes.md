# Week 1 Summary
Week 1 teaches you about C, a minimal but powerful programming language. Due to it's speed, portability, and memory control - you start working in a Linux command-line environment instead of a GUI. Basic shell commands (`ls`, `cd`, `make`, `./program`) are like the grag-and-drop in Scratch.

For the C program:
- `#include` directives for libraries.
- Must have a `main` function, with statements terminated with a semicolon formed inside curly braces.
- Create variables of fundamental types (`int`, `char`, `string`, etc.).
- Gather user input with CS50's helpers (`get_int`, `get_string`).
- Control execution using conditionals, loops, and tailored custom functions.
- Errors compiling should be considered learning moments, and tools like `help50` should be used as needed for human-readable diagnostics and `debug50` for step-by-step debugging.

---

# Week 1 Problem Set and Solution

TO DO: Insert problem statement
*Solution in private repo to respect CS50's Academic Honest Policy.*

---

# Week 1 Notes

## Why use C?
C is **small, fast, and close to the hardware**.  
It forces you to think explicitly about memory and types.

---

## Development Environment

| Command | Purpose                                   | Example        |
| :------ | :---------------------------------------- | :------------- |
| `cd`    | Change directory                          | `cd pset1`     |
| `ls`    | List files                                | `ls -1`        |
| `mkdir` | Make directory                            | `mkdir hello`  |
| `code .`| Open VS Code in the current folder        | `code .`       |
| `rm`    | Remove file                               | `rm a.out`     |

---

## Compiling

```bash
make hello
./hello
```

*Build stages:* **Pre-processing → Compiling → Assembling → Linking**

---

## Debugging Help

| Tool       | Example Command     | Purpose                                             |
| :--------- | :------------------ | :-------------------------------------------------- |
| `help50`   | `help50 make hello` | Show human-friendly explanations of compiler errors |
| `debug50`  | `debug50 ./hello`   | Step through code with breakpoints                  |
| `valgrind` | `valgrind ./hello`  | Detect memory errors                                |

---

## Anatomy of a C Program

```c
// comment describing program
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    string name = get_string("Name: ");
    printf("hello, %s\n", name);
}
```

| Part           | Purpose                               |
| -------------- | ------------------------------------- |
| `#include …`   | Copy declarations into your file      |
| `int main`     | Function where execution begins       |
| `{ … }`        | Block of statements                   |
| `string`       | CS50 alias for `char *`               |
| `printf`       | Print formatted output                |

---

## Data Types & Variables

| Type   | Typical Size | Format Specifier | Range / Notes                                      |
| :----- | :----------- | :--------------- | :------------------------------------------------- |
| `bool` | 1 byte       | `%i`             | `true`, `false`; need `<stdbool.h>` (included by `<cs50.h>`) |
| `char` | 1 byte       | `%c`             | ASCII character                                    |
| `int`  | 4 bytes      | `%i`             | ±2 147 483 647 (32-bit)                            |
| `long` | 8 bytes      | `%li`            | ±9 223 372 036 854 775 807 (64-bit)                |
| `float`| 4 bytes      | `%f`             | ~7 decimal digits                                  |
| `double`| 8 bytes     | `%lf`            | ~15 decimal digits                                 |
| `string`| varies      | `%s`             | CS50 alias for `char *`                            |

```c
int x = 5;
x = x + 1;     // 6
x++;           // 7
int y = x / 2; // integer division -> 3
```

---

## Conditionals

```c
if (x < y)
{
    // …
}
else if (x > y)
{
    // …
}
else
{
    // …
}
```

Operators: `<` `<=` `>` `>=` `==` `!=` (note: equality uses `==`, **not** `=`)  
Logical operators: `&&` (and), `||` (or), `!` (not)

Example:

```c
if (grade >= 90 && grade <= 100)
{
    printf("A\n");
}
```

---

## Loops

### `while`

```c
while (counter < 3)
{
    printf("meow\n");
    counter++;
}
```

### `for`

```c
for (int i = 0; i < 3; i++)
{
    printf("meow\n");
}
```

### `do … while` (executes at least once)

```c
int n;
do
{
    n = get_int("Positive number: ");
}
while (n < 1);
```

Pick the construct that makes intent clearest.

---

## Functions

Why? Reuse code and improve readability.

```c
int square(int n);   // declaration (prototype)

int main(void)
{
    printf("%i\n", square(5));
}

int square(int n)    // definition
{
    return n * n;
}
```

Guidelines:  
* One purpose per function  
* Keep functions short (≈ 20 lines)  
* Give meaningful names  

---

## CS50 Library Functions (Week 1 subset)

| Function            | Prompts the user for… | Returns |
| :------------------ | :-------------------- | :------ |
| `get_string(prompt)`| a line of text        | `string`|
| `get_int(prompt)`   | integer               | `int`   |
| `get_long(prompt)`  | long integer          | `long`  |

Use these helpers instead of unsafe `scanf`.

---

## Style Checklist (abridged)

* One statement per line  
* Curly brace on its own line  
* 4 spaces per indent (no tabs)  
* Comment **why**, not **what**  
* Descriptive variable names (`height`, not `h`)  
* Run `style50` before submitting  

---

## Problem Set 1 Overview

| Task          | Key Concepts          | Tips                                             |
| :------------ | :-------------------- | :----------------------------------------------- |
| Mario (Less)  | loops, conditionals   | Left-aligned half-pyramid of bricks              |
| Mario (More)  | nested loops          | Two half-pyramids, gap of two spaces             |
| Cash          | greedy algorithm      | Work in cents to avoid floating-point imprecision|
| Credit        | Luhn’s algorithm      | Move right-to-left; identify card type by prefix & length |

General advice:  
1. Start with pseudocode in comments.  
2. Implement incrementally; compile early and often.  
3. Use `check50` only after you’re confident.  
4. If stuck, rubber-duck debug or ask on the course’s Q&A.  

---

## Submission Workflow

1. Ensure files are in the correct folder (`pset1/`, etc.).  
2. Run `style50 mario.c` → fix style issues.  
3. Run `check50 cs50/problems/2024/x/mario/more` (adjust URL).  
4. Submit with `submit50 cs50/problems/2024/x/mario/more`.  
5. Repeat for each program.  

---

## Quick Cheat Sheet

| Snippet                       | Purpose                        |
| :---------------------------- | :----------------------------- |
| `printf("x = %i\n", x);`      | Print integer                  |
| `scanf("%i", &x);`            | Read integer (**unsafe—prefer `get_int`**) |
| `// …` or `/* … */`           | Comments                       |
| `#define PI 3.14159`          | Constant macro                 |
| `char c = getchar();`         | Read single character          |
| `break;` / `continue;`        | Jump out / skip within loops   |
| `return 0;`                   | Exit `main` successfully       |
