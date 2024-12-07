# C Fundamentals

## Chapter Structure

- Section 2.1: A small sample C program.
- Section 2.2: Discussion on how to generalize the program.
- Section 2.3: How to comment your code.
- Section 2.4: Variables
- Section 2.5: Use of the `scanf` function to read data into variables.
- Section 2.6: Constants
- Section 2.7: C's rules for creating names or "Identifiers".
- Section 2.8: Rules for laying out a C program.

## 2.1 Writing a Simple Program

C requires little in the way of *boilerplate* code, a complete program can be as short as a few lines.

### Program: Printing a Pun

[To C, or not to C: that is the question...](Assets\Chapter_2_C_Fundamentals\Ch2_Code\pun.c)

#### Observations of `pun.c`

- The line `#include <stdio.h>` is used to call and include C's [Standard I/O Library.]()

- The program's executable goes inside `main`, representing the *main* program.

- The only line of code inside of `main` is the `printf` function called from the Standard I/O library.

- The code `\n` tells `printf` to add a new line after our string.

- The line `return 0;` tells the program to *return* a value of 0 to the OS when it terminates.

#### Compiling and Linking

Workflow for getting our C program to run.

First, we created the source code `pun.c`. Next we need to convert this program into something the machine can execute. In C this usually involves the following:

- **Preprocessing**: The program is fed into the [preprocessor](), which reads and obeys commands that begin with `#` (known as *directives*). Something like an editor, it can add or modify the program to make sure it runs correctly.

- **Compiling**: The modified program now is fed into the [compiler]() that translates the source code into machine instructions (*object code*).

- **Linking**: Finally, the [linker]() combines the object code with any additional code needed to yield a complete executable program. This includes library functions like `printf` that are used in the program.

Generally, this process is fully automated with the preprocessor usually integrated into the compiler. In [Unix Systems]() the compiler is usually named `cc`.

To compile and link the `pun.c` program in our environment, enter the following command into the terminal.

```bash
gcc pun.c -o pun
```

## WSL Issue Encountered

On my first attempt at running `pun.c` resulted in the following error:

```bash
Chapter_2_C_Fundamentals/Ch2_Code] ❱❱❱ gcc pun.c -o pun
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/11/../../../x86_64-linux-gnu/Scrt1.o: in function `_start':
(.text+0x1b): undefined reference to `main'
collect2: error: ld returned 1 exit status
[16:21:44] [cost 0.186s] gcc pun.c -o pun
```

The program as written in VSCode and was therefor saved with incorrect *Line Endings*. Line endings mark the end of a line in a text file and history has left us with two options that depend on your operating system.

### CLRF (Carriage Return + Line Feed)
- Represented as `\r\n`.
- Used by Windows
- Hold over from typewriters and ancient terminal designs where
  - `CR` (`\r`, ASCII 13) moves the cursor to the beginning of the current line.
  - `LF` (`\n`, ASCII 10) moves the cursor to the next line. 

### Steps to Fix

