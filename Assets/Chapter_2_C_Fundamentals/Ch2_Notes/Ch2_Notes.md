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

1. First, I ran a program that looks at a text file formatted using `CLRF` and converts it into `LF`:

```bash
/Chapter_2_C_Fundamentals/Ch2_Code] ❱❱❱ dos2unix pun.c
dos2unix: converting file pun.c to Unix format...
[16:21:33] [cost 0.034s] dos2unix pun.c
```

However, this did not resolve this issue, as the same error was thrown when attempting to compile.

2. Opening the program in a Unix text editor

```bash
nano pun.c
```

Opening this file revealed it was blank, this command was run to see its file size:

```bash
/Chapter_2_C_Fundamentals/Ch2_Code] ❱❱❱ ls -l pun.c

-rwxrwxrwx 1 dom dom 0 Dec  6 16:21 pun.c
[16:24:29] [cost 0.012s] ls -l pun.c
```
As indicated in the output, this file was empty. I manually corrected this by copy and pasting the code into the Nano editor, and got the program to successfully compile and run, however this is not a lasting fix. 

3. Moving my Repository to the WSL File System

Moving my development into the Linux file system will prevent these types of errors as I am relying on Unix tools to build my program.

## 2.2 The General Form of a Simple Program

Taking a closer look a `pun.c`, we can generalize it a bit as simple C programs have the form:

```C
// directives
int main(void)
{
// statements
}
```

Notice how the *braces* `{...}` indicate where `main` begins and ends. C uses `{ and }` much in the same way that other languages use `begin` and `end`. This is an example of C's reliance on abbreviations and special symbols, one reason for the language's concise nature.

All C programs rely on **three key language features**:

-  Directives: Editing commands that modify the program prior to compilation.
-  Functions: Named blocks of executable code, e.x.: `main`.
-  Statements: Commands to be performed when the program is run.
  
### Directives

Before compilation, the C program is first edited by the *preprocessor* and commands intended for the preprocessor are called [Directives](). Directives as a topic will be more comprehensively in chapters 14 and 15, for our current purposes, we are only interested in the `#include` directive.

The `pun.c` program begins with this line:

```c
#include <stdio.h>
```
This directive states that the information of `<stdio.h>` is to be included into the program before compilation. `<stdio>` contains information from the standard I/O library.

C has a number of [Headers]() like `<stdio>` that contain some functionality from the standard library. This is a necessary inclusion as C contains no built-in *read* or *write* programs. This ability is accomplished by leveraging the standard library.

Directives always begin with a `#` character, distinguishing them from other items in a C program. By default, directives are one line long and there is no special marker (such as `;` as in JavaScript) to designate the end of a directive.

### Functions

Functions can be called *procedures* or *subroutines* - they are the building blocks from which programs are constructed. C programs are little more than *collections of functions*. All functions fall into the following two categories: those written by the programmer and those provided as part of the *C Implementation*. The latter of the two can be called [Library Functions]() - as they belong to the library of functions supplied by the compiler.

The term *Function* comes from mathematics, where a function is a rule for computing a value when given one or more arguments:

```latex
f(x) = x + 1
g(y,z) = y^2 - z^2
```
C uses the term more loosely. In C, a function is simply a series of statements that have been grouped together and given a name. Some compute a value, and others don't. Functions that do compute a value uses the `return` statement to specify what value is returned. 

For example, a function that adds 1 to its argument might execute the statement:

```c
return x + 1;
```

A function that computes the difference of the squares of its argument might look like this:

```c
return y * y - z * z;
```

C programs may consist of many functions, however the only mandatory function is `main`. This special function, `main`, gets automatically called when the program is executed. This will be our only function until [Chapter 9](). 

The `main` function returns a [status code]() that is given to the OS when the program terminates. 

Examining `pun.c` again:

```C
#include <stdio.h>

int main(void)
{
  printf("To C, or not to C: that is the question. \n");
  return 0;
}
```

The word `int` just before `main` indicates that the `main` function returns and integer value. 

The word `void` in parentheses indicates that `main` has no arguments. 

The statement `return 0` has two effects:

1. It causes the `main` function to terminate (ending the program).
2. It indicates that the `main` function returns a value of `0`.

We will discuss the `main` return value in more detail later, for now we need to know that value `0` indicates a normal program termination.  