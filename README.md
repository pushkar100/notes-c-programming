# C Programming Notes

## C Program Format:

A C program is first converted to machine language for execution by a C Compiler. The compiler expects a certain (strict) structure for the C program to follow - Standard format.

C files must be saved in a file whose extension is `.c` (Ex: `hello.c`)

Basic Format:
```
#include <stdio.h>
int main() {
    // Your code ...
}
```

### What is `#include <stdio.h>`

`#` prefixed lines are known as Preprocessor Directives: They give some instructions to the compiler.

`#include` is a preprocessor directive that asks the compiler to 'Include' the mentioned source before executing the current program further.

`#include <stdio.h>` : 'stdio.h' is a file that is a library of functions mainly to do with 'standard input output'. This library is included in most C programs in order to display/receive input. It is a Standard Library available to all programs.

Examples of functions contained in `stdio.h`:
- scanf() : Function used to scan or receive input. (Read in input from user)
- printf() : Function used to print or display the output. (Outputs to screen)

### What is `int main()`:

`main()` : It is a type of function. 

A function is a block of code that takes in input & produces output. It can be called by other pieces of code (Ex: Called from other functions). A 'function body' refers to the set of statements inside the function (Within {}) that gets executed when that particular function is called.

`main()` : It is a special type of function. When a C program is run, it starts executing from the first line of the main() function. Hence, `main()` is a **mandatory** function in all C programs. It takes NO inputs & produces an Integer (int) output.  

### C Comments:

Comments are sections of code that are not executed or compiled. These are for the programmers to document parts of the code - to help with debudding later or for when multiple developers work on the same code.

- `// This is a single line comment` : Single line comments start with `//` and to the end of the line.
- `/* Some comment */` : This is used as a block or multiline comment. 

```
/* This
is also a 
multiline comment
*/
```

### Variables:

Variables are containers that store values of different types of data. Ex: `int a = 5;` declares a variable 'a' to be an integer variable and initialises it to hold the value 5 (5 is an integer value).

## C Data Types:

Data types define what is the type of the value that we are dealing with. Literals and variables in the C program are classified based on their type.

### Integer Data Types:

`int` is the keyword for Integer Data Types.

There are 3 main integer data types. 
- `short`: Usually about 2 bytes long on most systems.
- `int`  : Usually about 2 or 4 bytes long on most systems. (Minimum 2 bytes)
- `long` : Usually about 4 or 8 bytes long on most systems. (Minimum 4 bytes)

The range of values for each type:
- The range of values for any integer type is `-2^(n - 1)` to `2^(n - 1) - 1` where n is the number of bits assigned to that data type.
- The reason it is not `2^n` is because 1 bit will be used to represent the sign of the value(+/-). (Most systems follow 2's - complement representation)
- Ex: Range for `short` is `-2^15` to `2^15 - 1` since short is 2 bytes, which is 16 bits. (-32768 to 32767)

#### What happens of you exceed the limits of the ranges:

You get wrong values. Ex: 32767 + 1 will give you -32768 in `short` type. Ex2: 32767 + 10 will give you -32758 in `short` type.

Condition is called `Overflow`.

#### Syntax for `short` declaration:

To declare a short integer 'a': `short int a;` or simply `short a;`

#### Syntax for `int` declaration:

To declare a integer 'a': `int a;`

#### Syntax for `long` declaration:

To declare a long integer 'a': `long int a;` or simply `long a;`

#### Unsigned Integers:

We know that one bit in every integer type is kept to save the sign of the value. What if we know that the integer is always going to be **positive** only? In that case we can tell the compiler to free the greatest bit from saving the sign of the integer and effectively increase the range of the data type from `0` to `2^n - 1` where n is the number of bits for that type.

Keyword used to define only positive integers: `unsigned`

Examples:
- `unsigned short a;` : is having a range between 0 and 65535.
- `unsigned int a;` : an unsigned integer.
- `unsigned long a;` : an unsigned long integer.

Note:
1. The total values in the unsigned range is the same as in the signed range. Only difference is that the range starts from 0 in unsigned and moves in the positive direction.
2. The default is `signed` but we do not have to prefix it before any integer data type (since it's the default).

### Floating Point Data Types:

There a 3 Floating point data types:
- `float` : Usually holds 4 bytes of data
- `double` : Usually holds 8 bytes of data
- `long double` : Usually holds 10 bytes of data

These data types store their values in Scientific Notation (Mantissa & Exponent form). Reason: Storing decimal pointed values is somewhat complicated.

#### Declaration Syntaxes:
- `float a;` 
- `double a;` 
- `long double a;` 

### Text Data Types:

In C, we use the `char` data type to store a single character.

Ex:
- `char a, b, c;`
- `char a = 'A';`

A character data type is only 1 byte long. The character must be enclosed withing **Single Quotes**. 

#### How can we store a character?:

Since machines can only store numeric values, stored in binary, how can we represent text/symbols/characters?

The characters are actually mapped to integers which are then stored in binary in the computer whenever we use `char`. The mappings are defined by standards such as `ASCII` and nowadays (on more modern systems)by `UTF-8`. Therefore, we can replace the character with the corresponding integer associated with it while storing it. Ex:
- `char a = 'A';` : Stores the character 'A'
- `char a = 65;` : Also stores the character 'A' since it is mapped to the integer 70 in the ASCII table.

Note: 
1. `char` can be thought of as a subset to the `short` integer type since it can hold 1 byte(8 bits) or 256 integer values (0 to 255) and the symbol stored in it maps to one of these integer values.
2. Hence, **Arithmetic Operations** can be performed on following data types: INTEGERS, FLOATING POINTS & CHARACTERS. **Imp!** 

Ex:
```
char x, y;
int z;
x = 'a'; // Integer equivalent is 97
y = 'b'; // Integer equivalent is 98
z = x + y; // Will be 97 + 98 = 195
printf("%d", z); // 195
printf("%c %c", x, y); // 97 98 => %c is a formatter to char type. (Reverse map to char)
```


