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

** Fill notes here > Control Structures **

## C Functions:

- A function is a self-contained block or code which does a particular task.
- It contains statements that perform that particular task.
- It may take in input (information) in order to execute.
- It may also return information after it has finished running.

Note: 
1. Functions can call other functions and also call themselves.
2. C programming follows IMPERATIVE programming paradigm (C++ & Java follow OO paradigm. There is also a Functional Programming paradigm that is quite popular).

Advantages of functions:
- Breaks code into manageable units which are reusable.
- Helps keep code clean and readable.
- Can help with delegating work (as separate tasks).

### Library vs Functions:

- Libraries are essentially collections of functions. But, they are written by other developers and made available for us to use.
- `printf` and `scanf` are examples of readily available functions from the `stdio` library.
- User-defined functions (functions written by us) are the most useful parts of our own programs.

### Anatomy of a function:

Declaring a function: Announcing that a function exists, specifying the kind of input it takes and what output we should expect from it. (Signature of a function)

Definition of a function: Exactly what the function does. The meat of the function that contains all the statements of the function.

Call to a function: When we interact with a function (by passing it input) and ask it to accomplish its task (and wait for an output) it is referred to as a function 'call'.

Function Definition:
```
<return-type> <function-name>(<arguments-list>) {
	// Function Statements (Also known as the FUNCTION BODY)
}
```

- `<return-type>` : Type of information returned by the function. If function returns nothing then the return type is specified as `void`. Else, it is one of the C data types including user-defined types such as structs, pointers, etc.
- `<function-name>` : Way to identify a function in order to call it (so that it executes its statements). Function names can contain Letters of the alphabet(A-Z or a-z), Numbers(0-9) and Underscore(_) but it cannot start with a Number. Ex: `void echo_1_func()`, `int _convertToRs(int currency)`
- `<arguments-list>` : This is the list of the inputs expected by the function. Format: Data type followed by a name for the variable that is going to hold the passed value. It can be Zero or more and are separated by commas(,) while being enclosed within parentheses. Ex: `void _fun1(int num)`, `int add(int num1, int num2)`, `int floor(double _rawInput)`.

Note: 
1. In C, two functions cannot have the same name even they have different return types or different arguments list. In contrast, in C++ or Java, the functions can have the same name as long as their return types or argument(s) lists differ.
2. To return a value from within a function, use the `return` command to which we must pass a value. Ex: `return 5;`, `return num`. The value returned must match with the return type of the function.

The return-type, function-name and arguments-list constitute the 'function signature'.

Function Call:
```
...
int sum = add(a, b);
...
```

While calling a function:
- We are asking the function to accomplish its task.
- We can pass it arguments which must match those in the function signature or definiton in order, data types and number of arguments. (If pass by value then arguments are usually: Variables or literals)
- The returned value of the called function can be saved in a variable. The type of the variable holding the returned value should match the return type of the function. Ex: `float fun() { ... }` matches return type with `float x = fun();`

Function Declaration:
- Before we can call a function, it has to be declared first. It is like saying 'this functin exists and can be called by other code'.
```
<return-type> <function-name>(<arguments-list>);
```

Note: The arguments list in the declaration need not contain the associated variable names (Optional) (But, in the definition they should have names - known as formal parameters). Ex. of function declaration: `int sum(int, int);`, `int sum(int a, int b)` (with variable names).

Note:
1. Formal parameters - The variables in the arguments list in the function definition (Act as local variables - see scope).
2. Actual parameters - The actual values passed to the function through a function call. Ex: `int sum = add(a, 5);`. The formal parameters receive these particular values when the function is called/invoked.

### Putting it All Together:

We must: 
1. Declare a function.
2. Define a function.
3. Call a function. (In that order)

Ex:
```
int add(int, int);

int add(int a, int b) {
	return a + b;
}

int main() {
	...
	int sum = add(x, y);
	...
}
``` 

### Why have Separate Declarations and Definitions:

The reason is because the declarations usually go into Header Files (with `.h` extension) while the definitions go into Source Files(with `.c` extensions). Hence, they have to be separated.

### Parameter Passing: By-Value vs By-Reference:

In C, there are two ways by which we can pass data or inputs to a function:
1. Pass by Value, or
2. Pass by Reference

Pass by Value: Ex:
```
int main() {
	int a = 50, b = 100;
	func(a, b);
	printf("%d %d", a, b); // 50 100 (Unaffected by execution of 'func')
}
...
void func(int x, int y) { 
	printf("%d %d", x, y); // 50 100
	x = 1;
	y = 2;
	printf("%d %d", x, y); // 1 2
}
```

In pass by value, the actual parameter values are copied to the formal parameters. Changing formal parameter values inside the function will not affect the values of the values of the actual variables passed to it. (Note: Even if the formal and actual parameters have the same variable names, they are still different - formal parameters are local to the called function).

Pass by Reference: Uses pointers to achieve this. We pass the address of the location where the variables' values are stored. Therefore, changing the values of formal parameters will affect the actual parameters/values at the specified addresses (See pointers section).

## Storage Classes in C:

We can create variables with different 'settings' such as:
- Where the variable would be stored.
- Default value for the variable.
- Scope of the variable.
- Life of the variable.

These settings are governed by what is known as the variable's 'Storage Class'.

Tnere are 4 storage classes in C:
1. Automatic
2. Register
3. Static
4. External

### Automatic Storage Class:

- Where would the variable be stored? : In `Memory` (i.e Within the program's allocated space in the RAM while it is being executed by the CPU).
- Default Value for the Variable? : `Garbage Value` - random value (i.e Whatever value was at that memory location before it was assigned to the variable).
- Scope of the Variable? : `local` to the block (A set of curly braces {}) in which it is defined.
- Life of the Variable? : Till the `control` remains within the `block`.

This is the **default** storage class for any variable in C.

Explicitly defining an automatic variable: Use `auto` keyword during declarations (Although NOT using it is also automatic by default). Ex:
- `auto int a, b;` which is the same as `int a, b;`.

Scope of an Automatic Variable: Alive within a block({}) and lost/dead once control goes out of it. If two variables exist in different (nested) scopes, then the reference to the variable actually takes the nearest declaration (Within the closest scope). Ex:
```
int main() {
	auto int j = 1;
	{
		auto int j = 2;
		{
			auto int j = 3;
			printf("%d", j); // 3
		}
		printf("%d", j); // 2
	}
	printf("%d", j); // 1
}
```

Note: We can create random blocks too (with {}) and not just for functions or if/else/while/for etc.

### Register Storage Class:

- Where would the variable be stored? : In `CPU Registers` (This is the difference between automatic and register variables). Access to registers is much faster than access to memory locations used to store automatic variables.
- Default Value for the Variable? : `Garbage Value` - random value (i.e Whatever value was at that register location before it was assigned to the variable).
- Scope of the Variable? : `local` to the block (A set of curly braces {}) in which it is defined.
- Life of the Variable? : Till the `control` remains within the `block`.

With the main difference between automatic and register variables being Register v/s Memory storage locations, **everything else is the same**.

Note: Register storage classes are **almost never used** these days because:
1. Issues with multithreaded processes.
2. Modern compilers choose when to store variables in registers (Smart optimizations) - Therefore, it does not make sense to explicity define register variables.

Explicitly defining an register variable: Use `register` keyword. Ex: `register int x;`.

### Static Storage Class:

- Where would the variable be stored? : In `Memory` (Same as automatic variables)
- Default Value for the Variable? : `0` 
- Scope of the Variable? : `local` to the block (A set of curly braces {}) in which it is defined.
- Life of the Variable? : Value `persists` between different `function calls`.

Note: Static variable values don't disappear when the function is no longer active. In fact, the old values are remembered for successive function calls.

Explicitly defining an static variable: Use `static` keyword. Ex: `static int x;`. Ex:
```
int main() {
	int z;
	z = blah(2); // z = 2
	z = blah(2); // z = 4
	z = blah(2); // z = 8
}
int blah(int a) {
	static int x; // 0 by default
	x = x + a;
	return x;
}
```

If `x` was not static then the 3 calls to `blah()` would have yielded the value `2` all three times (Assuming the variable `x` was assigned a default value of `0` inside the function).

### External Storage Class:

- Where would the variable be stored? : In `Memory` (Same as automatic variables)
- Default Value for the Variable? : `0` 
- Scope of the Variable? : `Global`
- Life of the Variable? : Till `execution` does not come to an `end`.

External/Global variables are 'Omnipresent': That is, they are declared **outside functions**, yet are available to all functions that care to use them.

Usage: 
- Either declaring a variable outside any function, or 
- Declaring with an `extern` keyword inside a function.

Ex:
```
int x = 5; // global variable (outside any function)
int main() {
	extern int y; // y has not yet been defined outside the function but extern helps us to identify it.
	printf("%d %d", x, y);
}
int y = 31; // global variable. Used inside main() with the help of extern keyword
```

Note: 
1. If `extern` keyword was NOT being used inside the main() function then trying to access `y` inside it would have **caused an error** because the global declaration of `y` falls after the function definition. `extern` helps with idenitify global variables declared after the functions are defined.
2. Global variables vs Local variables(auto, static, register): Local variables of a function, when accessed inside it, take precedence over a global variable having the same name.

Ex:
```
int a = 5;
int main() {
	int a = 10;
	printf("%d", a); // 10 (Local 'a')
	anotherFunc();
}
void anotherFunc() {
	printf("%d", a); // 5 (Global 'a')
}
```

When to use external storage classes? 
- For variables being used (ubiquitously) by all functions of a program.
- Avoiding unnecessary passing of parameters between functions everytime. (But, nowadays function call overheads are not that great a concern because if faster CPU switching times & memory access speeds)

Caution: Declaring all or most of the variables as extern would amount to a lot of wastage of memory space - because the variables would remain alive throughout the program.





