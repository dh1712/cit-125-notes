# Chapter 9: Value-Returning Functions

## Objectives
* Raise a number to a power using the `pow` function
* Return the square root of a number using the `sqrt` function
* Generate random numbers
* Create and invoke a function that returns a value
* Pass information _by value_ to a function
* Write a function prototype
* Understand a variable's scope and lifetime


## Functions
* A function is a block of code that performs a task
* Every C++ program contains at least one function (main)
	* Most contain many functions
* Some functions are built-in functions (part of C++): defined in language libraries
* Others, called program-defined functions, are written by programmers; defined in a program
* Functions allow for blocks of code to be used many times in a program without having to duplicate code
* Functions also allow large, complex programs to be broken down into small, manageable sub-tasks
* Each sub-task is solved by a function, and thus different people can write different functions
* Many functions can then be combined into a single program
* Typically, `main` is used to call other functions, but any function can call any other function


## Value-Returning Functions
* All functions are either value-returning or void
* All __value-returning functions__ perform a task and then return precisely one value
* In most cases, the value is returned to the statement that called the function
* Typically, a statement that calls a function assigns the return value to a variable
	* However, a return value could also be used in a comparison or calculation or could be printed to the screen
	
## The `pow` Function
* The __pow function__ is a convenient tool to raise a number to a power __(exponentiation)__
* The `pow` function raises a number to a power and returns the result as a `double` number
* Syntax is `pow (x, y)`, in which `x` is the base and `y` is the exponent
* At least one of the two arguments must be a `double`
* Program must contain the `#include <cmath>` directive to use the `pow` function


## How to Use the `pow` Function

### Syntax
```cpp
pow(x, y)
```
Note that the `pow` function requires the `#include <cmath>` directive.

### Example 1
```cpp
double cube = 0.0;
cube = power(4.0, 3);
```
The assignment statements assigns the number `64.0`, which is `4.0` raised to the third power, to the `cube` variable.

### Example 2
```cpp
cout << pow(100, 0.5);
```
The statement displays the number `10`, which is `100` raised to the `0.5` power.  The `pow (100, 0.5)` expression is equivalent to finding the square root of the number `100`.

### Example 3
```cpp
double area = 0.0;
double radius = 5.0;
area = 3.14 * pow(radius, 2);
```
The assignment statement raises the value stored in the `radius` variable to the second power, giving `25.0`.  It then multiplies the `25.0` by `3.14` and assigns the product `78.5` to the `area` variable.


## The `sqrt` Function
* The `sqrt` function is a built-in value-returning function that returns a number's square root as a `double`
* Definition contained in `cmath` library
	* Program must contain `#include <cmath>` to use it
* Syntax: `sqrt(x)`, in which `x` is a `double` or `float`
	* Here, `x` is an __actual argument__, which is an item of information a function needs to perform its task
* Actual arguments are passed to a function when called


## How to Use the `sqrt` Function

### Syntax
```cpp
sqrt(x)
```
Note that the `pow` function requires the `#include <cmath>` directive.

### Example 1
```cpp
double squareRoot = 0.0;
squareRoot = sqrt(100.0);
```
The `sqrt` function finds the square root of the `double` number `100.0` and then returns the result (the `double` number `10.0`) to the assignment statement, which assigns the return value to the `squareRoot` variable.

### Example 2
```cpp
double num = 0.0;
cout << "Enter a number: ";
cin >> num;
cout << sqrt(num);
```
The `sqrt` function finds the square root of the `double` number stored in the `num` variable and then returns the result to the `cout` statement, which displays the return value on the computer screen.


## The Hypotenuse Program
* Program that calculates and displays the length of a right triangle hypotenuse
* Program uses Pythagorean theorem
	* Requires squaring and taking square root
* `pow` function can be used to square
* `sqrt` function can be used to take square root
* Both are built-in value-returning functions

### Pythagorean Theorem
The theorem states that the length of a right triangle's hypotenuse is equal to the square root of the sum of the squares of the lengths of the triangle's two adjacent sides.  In other words, the hypotenuse's length is equal to the square root of the following sum: (side a length)^2 + (side b length)^2.

### Example
```cpp
//Hypotenuse.cpp - displays the length of a right triangle's hypotenuse

#include <iostream>
#include <iomanip>
#include <cmath>
using namespace std;

int main()
{
	double sideA = 0.0;
	double sideB = 0.0;
	double sumSquares = 0.0;
	double hypotenuse = 0.0;
	
	// Get lengths of two sides
	cout << "Side A length: ";
	cin >> sideA;
	cout << "Side B length: ";
	cin >> sideB;
	
	// Calculate the hypotenuse length
	sumSquares = pow(sideA, 2) + pow(sideB, 2);
	hypotenuse = sqrt(sumSquares);
	
	// Display the hypotenuse length
	cout << fixed << setprecision(1);
	cout << "Hypotenuse length: " << hypotenuse << endl;
	
	return 0; 
}
```


## Random number generators in C++
* C++ provides a pseudo-random number generator
	* Produces a sequence of numbers that meet certain statistical requirements for randomness
	* Numbers chosen uniformly from finite set of numbers
	* Not truly random but sufficient for practical purposes
	
## How to Use the `rand` Function
* Random number generator in C++: `rand` function
	* Returns an integer between `0` and `RAND_MAX`, inclusive
	* `RAND_MAX` is a built-in constant (>= 32767)
	* Initialize the random number generator each time, otherwise it will produce the same sequence

### Syntax
```cpp
rand()
```
Note that the `rand` function _may_ require the `#include <cstdlib>` directive.
Doesn't require any actual arguments, but parentheses are still required.

### Example 1
```cpp
int randomNum = 0;
randomNum = rand();
```
The `rand` function generates a random integer that is greater than or equal to `0` but less than or equal to `RAND_MAX`.  It then returns the random integer to the assignment statement, which assigns it to the `randomNum` variable.

### Example 2
```cpp
cout << rand();
```
The `rand` function generates a random integer that is greater than or equal to `0` but less than or equal to `RAND_MAX`.  It then returns the random integer to the `cout` statement, which displays it on the computer screen.

### Example 3
```cpp
int tripleNum = 0;
tripleNum = rand() * 3;
```
The `rand` function generates a random integer that is greater than or equal to `0` but less than or equal to `RAND_MAX`.  It then requires the random integer to the assignment statement, which multiplies it by 3 and assigns the result to the `tripleNum` variable.

### How to Generate Random Integers Within a Specific Range
```cpp
lowerBound + rand() % (upperBound - lowerBound + 1)
```
This allows ranges other than `0` to `RAND_MAX` to be used.
The range is `upperBound` to `lowerBound`.

#### Example 1
```cpp
cout << 1 + rand() % (6 - 1 + 1);
```
This will display a random integer 1 through 6 on the computer screen.

#### Example 2
```cpp
cout << 10 + rand() % (100 - 10 + 1);
```
This will display a random integer 10 through 100 on the computer screen.


## How to Use the `srand` Function
* Use `srand` function (a void function) to initialize random number generator

### Syntax
```cpp
srand(seed)
```
Where `seed` is an integer actual argument that represents the starting point of the generator.
Commonly initialized using the `time` function.
Ensures unique sequences of numbers for each program run.

### Example 1
```cpp
int x = 0;
cout << "Enter an integer: ";
cin >> x;
srand(x);
cout << rand() << endl;
```
The 'srand' function initializes the random number generator using the integer entered by the user.  The `cout` statement displays a random integer that will be greater than or equal to `0` but less than or equal to `RAND_MAX`.

### Example 2
```cpp
srand(static_cast<int>(time(0)));
cout << rand() << endl;
```
The `srand` function initializes the random number generator using the value returned by the `time` function after it has been converted to the `int` data type.  The `cout` statement displays a random integer that will be greater than or equal to `0` but less than or equal to `RAND_MAX`.

### Example 3
```cpp
int randNum = 0;
srand(static_cast<int>(time(0)));
randNum = 1 + rand() % (10 - 1 + 1);
```
The `srand` function initializes the random number generator using the value returned by the `time` function after it has been converted to the `int` data type.  The assignment statement assigns a random integer that is greater than or equal to `1` but less than or equal to `10` to the `randNum` variable.

## How to Use the `time` Function
* Use `time` as a value-returning function that returns the current time in number of seconds since January 1, 1970
	* Returns a `time_t` object, so must be cast to an integer before passing to `srand`
	* Program must contain `#include <ctime>` directive to use it
	
## Example Random Number Generator - The Guessing Game Program
* The program generates a random number from 1 to 10 and then allows the user as many choices as needed to guess the number.
* The `srand`, `time`, and `rand` functions are all utilized in the program.

```cpp
// GuessingGame.cpp

#include <iostream>
#include <ctime>

// Your compiler may require this directive to use the rand and srand functions
#include <cstdlib>

using namespace std;

int main()
{
	int randomNumber = 0;
	int numberGuess = 0;
	
	// Generate a random number from 1 through 10
	srand(static_cast<int>(time(0)));
	randomNumber = 1 + rand() % (10 - 1 + 1);
	
	// Get first guess from user
	cout << "Guess a number from 1 through 10: ";
	cin >> numberGuess;
	
	while (numberGuess != randomNumber)
	{
		cout << "Sorry, guess again: ";
		cin >> numberGuess;
	}
	// end while
	
	// Confirms correct answer
	cout << endl << "Yes, the number is "
		<< randomNumber << "." << endl;
		
	return 0;
}
```


## Creating Program-Defined Value-Returning Functions
* A program-defined value-returning function definition is composed of a header and a body
* Header (first line) contains return data type, name of function, and an optional `parameterList`
	* Rules for function names are same as for variables
	* Good idea to use meaningful names that describe function's purpose
	* Memory locations in `parameterList` are called __formal parameters__
		* Each stores an item of information passed to the function when it is called
* Function body contains instructions for performing the function's assigned task
* Surrounded by braces `{ }`
* Last statement is usually the `return` statement
	* Returns one value (much match return data type in function header)
* After `return` statement is processed, program execution continues in calling function
* God idea to include comment (such as `\\end of functionName`) to mark end of function

### Syntax
```cpp
returnDataType functionName([parameterList])
{
// one or more statements go here

return expression;
}
```

### Example 1
```cpp
int getRandomNumber()
{
	int randInteger = 0;
	randInteger = 1 + rand() % (10 - 1 + 1);
	return randInteger;
}
```
The function generates a random integer from `1` through `10` and then returns the random integer.

### Example 2
```cpp
double getRectangleArea(double len, double wid)
{
	return len * wid;
}
```
The function calculates the area of a rectangle and then returns the result as a `double` number.

### Example 3
```cpp
double getSubtotal(int sold, double costPerItem)
{
	double subtotal = 0.0;
	subtotal = sold * costPerItem;
	return subtotal;
}
```
The function calculates the subtotal and then returns the result as a `double` number.


## Calling a function
* A function must be called (invoked) to perform its task
* `main` is automatically called when program is run
* Other functions must be called by a statement
* Value-returning functions are typically called from statements that:
	* Assign the return value to a variable
	* Use the return value in a calculation or comparison
	* Display the return value
* A call to a void function is an independent statement because void functions do not return values
* C++ allows you to pass either a variable's value or its address to a function
* Passing a variable's value is referred to as __passing *by value*__
* Passing a variable's address is referred to as __passing *by reference*__
* Default is passing *by value*
* Number, data type, and ordering of actual arguments must match the formal parameters in function header
	* Names do not need to match (different names are better)

### Syntax
```cpp
functionName ([argumentList]);
```
* argumentList is a list of actual arguments (if any)
* An actual argument can be a variable, named constant, literal constant, or keyword

### Example 1
```cpp
num1 = getRandomNumber();
```
The assignment statement calls the `getRandomNumber` function and then assigns the function's return value to the `num1` variable.

### Example 2
```cpp
cout << getRectangleArea(7.25, 21.0);
```
The `cout` statement calls the `getRectangleArea` function, passing it the `double` numbers `7.75` and `21.0`.
It then displays the function's return value on the computer screen.

### Example 3
```cpp
salesTax = getSubtotal(quantity, itemPrice) * 0.05;
```
The assignment statement calls the `getSubtotal` function, passing it the integer stored in the `quantity` variable and the `double` number stored in the `itemPrice` variable.
It then multiplies the function's return value by the `double` number `0.05` and stores the result in the `salesTax` variable.

## Example Function - The Savings Account Program
* The program allows the user to enter the initial deposit made into a savings account and the annual interest rate
* The program displays the amount of money in the account at the end of `1` through `3` years, assuming no additional deposits or withdrawals are made.

### `main` Function
```cpp
int deposit = 0;
double interestRate = 0.0;
double acctBalance = 0.0;

cout << "Deposit: ";
cin >> deposit;
cout << "Rate (in decimal form): ";
cin >> interestRate;

for (int year = 1; year < 4; year += 1)
{
	acctBalance = getBalance(deposit, interestRate, year);
	
	cout << "Year " << year << ": $" << acctBalance << endl;
}
```

### `getBalance` Function
```cpp
int amount;
double rate;
int y;

double balance = 0.0;

balance = amount * pow((1 + rate), y);

return balance;
```

### Completed Program
```cpp
// Savings.cpp - displays the account balance at the end of 1 through 3 years

#include <iostream>
#include <iomanip>
#include <cmath>
using namespace std;

// Function prototype
double getBalance (int amount, double rate, int y);

int main()
{
	int deposit = 0;
	double interestRate = 0.0;
	double acctBalance = 0.0;
	
	cout << "Deposit: ";
	cin >> deposit;
	cout << "Rate (in decimal form): ";
	cin >> interestRate;
	
	cout << fixed << setprecision(2);
	for (int year = 1; year < 4; year += 1)
	{
		acctBalance = getBalance(deposit, interestRate, year);
		cout << "Year " << year << ": $" << acctBalance << endl;
	}
	
	return 0;
}

double getBalance(int amount, double rate, int y)
{
	double balance = 0.0;
	
	balance = amount * pow((1 + rate), y);
	
	return balance;
}
```


## Function Prototypes
* When a function definition appears below the `main` function, you must enter a function prototype above the `main` function
* A __function prototype__ is a statement that specifies the function's name, data type of its return value, and data type of each of its formal parameters (if any)
	* Names for the formal parameters are not required
* Programmers usually place function prototypes at beginning of program, after the `#include` directives

### Syntax
```cpp
returnDataType functionName([parameterList]);
```

### Example 1 (with the optional names)
```cpp
double getBalance (int amount, double rate, int y);
```

### Example 2 (without the optional names)
```cpp
double getBalance(int, double, int);
```


## The Scope and Lifetime of a Variable
* A variable's __scope__ indicates where in the program the variable can be used
* A variable's __lifetime__ indicates how long the variable remains in the computer's internal memory
* Both scope and lifetime are determined by where you declare the variable in the program
* Variables declared within a function and those that appear in a function's `parameterList` have a local scope and are referred to as local variables
* __Local variables__ can be used only by the function in which they are declared or in whose `parameterList` they appear
	* They remain in internal memory until the function ends
* __Global variables__ are declared outside of any function in the program
	* They remain in memory until the program ends
* Any statement can use a global variable
* Declaring a variable as global can allow unintentional errors to occur
	* For example, a function that should not have access to the variable inadvertently changes the variable's contents
* You should avoid using global variables unless necessary
* If more than one function needs to access the same variable, it is better to create a local variable in one function and pass it to other functions that need it

## Summary
* Functions:
	* Allow programmers to avoid duplicating code
	* Allow for large, complex programs to be broken into small, manageable tasks
* Some functions are built into the language, and others are program-defined
* All functions are either value-returning or void
* A value-returning function returns one value
	* The value is returned to the statement that called the function
* A `void` function returns no value
* Use the `sqrt` function to find the square root of a number
* Use the `pow` function to raise a number to a power
* Items in parentheses in a function call are called actual arguments
* The `rand` function is used to generate random numbers
	* Returns an integer between `0` and `RAND_MAX`
* `srand` function is used to initialize `rand` function
	* `time` function is usually used as seed (starting point)
* Function definition composed of header and body
* Header specifies function name, return data type, and formal parameter names and types (if any)
	* Data types and ordering of formal parameters must match data types and ordering of actual arguments
* Body contains instructions for performing the function's assigned task
	* Surrounded by braces `{ }`
* `return` statement returns the result of an expression to the calling function
* You call a function by including its name and actual arguments (if any) in a statement
* Variables in C++ are passed _by value_ by default
* A function prototype must be provided for each function defined below the _main_ function
* Scope of a variable indicates where in the program it can be used
* Lifetime of a variable indicates how long it will stay in internal memory
* Local variables can be used only within the function in which they are declared or in whose `parameterList` they appear
	* They remain in memory until the function ends
* Global variables can be used anywhere
	* They remain in memory until the program ends
* If more than one memory location has the same name, position of the statement in which the name is used determines which location is used