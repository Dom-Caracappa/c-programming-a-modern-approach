# Introducing C


## Origins

C is a by-product of the **UNIX Operating System**, developed at Bell Laboratories by *Ken Thompson*, *Dennis Richie*, and other Bell Researchers.

UNIX, like most operating systems of its era, was written in [Assembly Language](), a *low-level* language, making debugging and enhancement to existing code base difficult. As UNIX development was suffering from these issues, it was decided that a *higher-level* language was needed to continue UNIX development. 

First, in 1969, Thompson designed a small language called **B**, based on **BCPL**, a **systems programming language* developed in the mid-1960's. Richie and others joined the UNIX project and development in the B Language continued.

The next year, Bell Labs outfitted the UNIX project with a PDP-11, a *16-bit minicomputer*, which provided features allowing for easier *general-purpose* computing, such as wide peripherals support, easy *direct memory access*, and an innovative *instruction set*. 

The hope was this new powerful hardware could work with the B Language's abstraction of Assembly, and a portion of UNIX was rewritten in B. However by 1971, it became clear to researchers the PDP-11 was ill-suited with the current incarnation of the B Language, so then began project by Richie to *extend* the language, creating what he called **NB**, or, *"New B"*. As this new language continued to diverge from its origin, it was eventually renamed the "C Programming Language".  

By 1973, C was stable enough that UNIX was completely rewritten in the new language. This change in code base also provided a new feature: *portability*. No longer was an operating system a bespoke piece of programming, unique to segregated computer architectures. Now, if a researcher wanted to test UNIX on a new machine, they just needed to write a *C Compiler* for that hardware's instruction set, and UNIX will run on that machine. 

## Standardization

The C Language continued to evolve into the late 1970's, during which time the first book on C was published. This still foundational text, *The C Programming Language*, written by the Bell Lab researchers Brian Kernighan and Dennis Richie, released in 1978, became the defacto standard of the language. 

For the remainder 70's, the population of C programmers was limited to the world of UNIX, a proprietary and at times expensive licensed software that found little footing outside academia and industry. The next decade however would see C expanding past the walled UNIX garden, and into areas where efficiency, portability, and *close-to-the-hardware* capabilities. 

During this period operating systems such as **Windows 1.0** and **Amiga OS** were written in C, along with *database management systems* like original releases of both **Oracle Database** and **MySQL**. Compilers by Microsoft were written in the language as were early versions of **GCC (GNU Compiler Collection)** were developed in C, as were early networking protocols and applications such as the **TCP/IP** stack, both applications greatly benefiting from the language's portability. 

The early video game industry of the 1980's saw C's efficiency and *close to the metal* nature, ideal for development in graphics programming and engine development. Early Nintendo and Sega games were written in C, as was *Doom* and *Wolfenstein 3d* in the next decade. In 1992, the **OpenGL Library**, an influential open standard graphics API, was implemented in C, allowing it to be used wherever the language ran. 

Lastly, C was instrumental in the early development of **scientific computing** and **high-performance research applications**, where performance and precision are paramount. Scientific computing often requires extensive mathematical operations, such as matrix manipulations, differential equations, and statistical analyses. Libraries like BLAS (Basic Linear Algebra Subprograms) and LAPACK (Linear Algebra PACKage) were implemented in C, making it a go-to language for numerical computing and linear algebra. Before Python became the standard tool for data science, it was C and implementations like CERN's **ROOT System**, that provided complex data visualizations, 3d-simulations, other high-performance applications. 

Beyond all these specialized applications, C was also being introduced to users all around the world via the popular IBM PC Platform - the original predecessor of all modern PCs. 

Difficulties presented themselves as the language's popularity continued to grow. Maybe the most issue was the lack of a "C Standard" - as new programmers learned the language, they relied primarily on the K&R book, which while responsible for teaching the C Language to the wider world beyond Bell Labs, could be a tad *fuzzy*, allowing for different interpreters to execute different blocks of code differently, undermining the power of portability and utility of the language. To further complicate matters, the K&R book was not always careful to separate was was UNIX and what was the C Language, causing users to conflate features of the two. Finally, the language had grown a great deal since the original publishing of the K&R text, and thus not formally documented anywhere. Affirmative action was needed by the C Language community to correct these long-suffering issues of the language, perfect portability among different platforms and professionalize its use.

The development of a U.S. standard for C began in 1983 under the auspices of the *American National Standards Institute (ANCI)* and finally completed in 1988, with formal approval in December 1989 as **ANCI Standard X3.159-1989**. In the next year, the standard was approved by the *International Organization for Standardization (ISO)* as international standard **ISO/ICE 9899:1990** - this version is referred to as **C89** or **C90** to distinguish it from *K&R C*.

## C the Living Language

The **C99** standard - released in 1999 - was an attempt to modernize the language with the creation of [inline functions]() for performance, [variable-lengths arrays]() for flexibility in memory use, the `long long int` type for extended precision, new data types and boolean types, as well as `//` single-line comments. The update also improved *floating-point operations*, making C more useful for scientific and engineering applications. 

**C11** - released in 2011 - improved portability and safety. C11 introduced a standard way of handling concurrency with thread-local storage and atomic operations, enhancing performance in multi-core environments. [Static assertions]() allow for compile-time error checking, [anonymous unions]() made structures more flexible and readable.The update added support for UTF-16 and UTF-32, expanding use for internationalization of word processor applications. [Optional bounds checking]() were aimed at increasing safety, these checking functions help catch buffer overflows.

**C17/C18** focused mostly on stability by  bug fixes and addressing ambiguities/inconsistancies in C11.  

**C23** was designed to bring modern coding advancements into the C Language. New [keywords]() such as `typeof` (to simplify [type checking]()) and enhanced `constexpr` capabilities to evaluate expressions at compile time. C23 expanded the [Standard Library]() with new mathematical functions and other utility improvements with the idea of making the language more versatile and accessible to new users. Improved Unicode support created more openings to international use and improved its [string manipulation]() functionality.

## Modern Context of C

Systems Programming and Embedded Applications: C remains the go-to language for systems programming, embedded applications, and operating systems because of its efficiency, control over hardware, and small runtime footprint. Interoperability with other languages is a core feature of C, and the language's stable [ABI (Application Binary Interface)]() allows it to interface with other languages and environments, making it integral in environments like Linux, where it underpins many core libraries. C’s newer standards continue to evolve cautiously, balancing new language features and compatibility with existing codebases, ensuring that C remains relevant for both new and legacy applications.