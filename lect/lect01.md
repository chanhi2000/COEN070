# lect01

## OBJECT ORIENTED PROGRAMMING
- abbreviated: *OOP*
- used for many modern programs
- program is viewed as interacting objects
    - each object contains algorithms to describe its behavior
    - program design phase involves **designing objects** and **their algorithms**


## CHARACTERISTICS: OOP
- #### ENCAPSULATION
    - information hiding
    - objects contain their own data and algorithms
- #### INHERITANCE
    - writing reusable code
    - objects can inherit characteristics from other objects
- #### POLYMORPHISM
    - a single name can have multiple meanings depending on its context.


## INTRODUCTION TO C++
- where did C++ come from?
    - derived from the C language
    - C was derived from the B langauge
    - B was derived from the BCPL language
- why the '++'?
    - ++ is an operator in C++ and results in a cute pun


## C++ HISTORY
- C is developed by **Dennis Richie** at AT&T Bell Labs in the 1970s.
    - used to maintain UNIX systems
    - many commercial applications are written in C.
- C++ developed by **Bjarne Stroustrup** at AT&T Bell Labs in the 1980s.
    - overcame several shortcomings of C
    - incorporated OOP.
    - C remains a subset of C++


## HELLO WORLD.
```cpp
#include <iostream>
using namespace std;

int main()
{
	cout << "Hello World!" << endl;
	cout << "Welcome to C++ Programming" << endl;

	return 0;
}
```

## PROGRAM LAYOUT
- compiler accepts almost any pattern of line breaks and indentation
- programers format programs so they are easy to read.
    - place opening brace '{' and closing brace '}' on a line by themselves.
    - indent statements
    - use only one statement per line.
- variables are declared before they are used.
    - typically variables are declared at the beginning of the program.
    - statements (not always lines) end with a semi-colon.
- include directives `#include <iostream>`
    - tells compiler where to find information about items used in the program
    - `iostream` is a library containing definitions of `cin` and `cout`.
- `using namespace std;`
    - tells the compiler to use names in `iostream` in a "standard" way.
- to begin the main function of the program
    ```
    int main()
    {
    ```
- to end the main function
    ```
    	return 0;
    }
    ```
	- main function ends with a return statement.


## I/O STREAMS
- I/O refers to program input and output
    - input is delivered to your program via a stream object
    - input can be from
        - keyboard
        - file
    - output is delivered to the output device via a stream object
    - output can be to
        - the screen
        - file


## `cin` AND `cout` STREAMS
- `cin`
    - input stream connnected to the keyboard
- `cout`
    - output stream connected to the screen.
- `cin` and `cout` deviend in the iostream library.
    - use include directive: `#include <iostream>`
- you can declare your own streams to use with files.


## DECLARING AN INPUT-FILE STREAM VARIABLE
- input-file streams are of type `ifstream`
- type `ifstream` is defined in the `fstream` library
    - you must use the `include` and using directives
    ```cpp
    #include <fstream>
    using namespace std;
    ```
- declare an input-file stream variable using
    ```cpp
    ifstream in_stream;
    ```

## DECLARING AN OUTPUT-FILE STREAM VARIABLE
- output-file streams are of type `ofstream`
- type `ofstream` is defined in the `fstream` library
    - you must use the `include` and using directives
    ```cpp
    #include <fstream>
    using namespace std;
    ```
- declare an input-file stream variable using
    ```cpp
    ofstream out_stream;
    ```

## CONNECTING TO A FILE
- once a stream variable is declared, connect it to a file (initialization)
    - connecting a stream to a file = opening the file.
    - use the open function of the stream object.



## USING THE INPUT STREAM
- once connected to a file, the input-stream variable can be used to produce input just as you would use `cin` with the extraction operator.
- i.e.
    ```cpp
    int one_number, another_number;
    in_stream >> one_number >> another_number;
    ```

## USING THE OUTPUT STREAM
- an output-stream works similarly to the input-stream
- i.e.
    ```cpp
    ofstream out_stream;
    out_stream.open("outfile.dat");

    out_stream << "one number = "
               << one_number
               << "another number = "
               << another_number;
    ```

## SIMPLE FILE INPUT/OUTPUT
```cpp
// reads three numbers from the file infile.dat,
// sums the nubmers, and writes the sums to the file
// outfile.dat (a better version of this program will be given
// in Display 5.2.)

#include <fstream>

int main()
{
    using namespace std;
    ifstream in_stream;
    ofstream out_stream;

    in_stream.open("infile.dat");
    out_stream.open("outfile.dat");

    int first, second, thrid;
    in_stream >> first >> second >> thrid;
    out_stream << "The sum of the first 3\n"
               << "numbers in infile.dat\n"
               << "is " << (first + second + third)
               << endl;
    in_stream.close();
    out_stream.close();

    return 0;
}
```


## FILE I/O WITH CHECKS AN OPEN
```cpp
// reads three numbers from the file infile.dat,
// sums the nubmers, and writes the sums to the file
// outfile.dat
#include <fstream>
#include <iostream>
#include <cstdlib>

int main()
{
    using namespace std;
    ifstream in_stream;
    ofstream out_stream;

    in_stream.open("infile.dat");
    if ( in_stream.fail() ) {
        cout << "input file opening failed.\n";
        exit(1);
    }

    out_stream.open("outfile.dat");
    if ( out_stream.fail() ) {
        cout << "Output file opening failed.\n";
        exit(1);
    }
    // ...
}
```


## IO: keyboard monitor
```cpp
#include <iostream>

int main()
{
    using namespace std;


}
```


## THE END OF THE FILE
- **example**: to calculate the average of the numbers in a file.

```cpp
double next, sum = 0;
int count = 0;
while( in_stream >> next ) {
    sum = sum + next;
    count++;
}

double average = sum / count;
```

## HOW TO TEXT END OF FILE
- we have seen two methods
    - `while ( in_stream >> next )`
    - `wihle ( !in_stream.eof() )`
- which should be used?
    - in general, use `eof` when input is treated as text and using a member function `get` to read input.
    - in general, use the extraction operator method when processing numeric data.


## INSERTION & EXTRACTION OPERATORS
- `<<` : insertion operator, applied to an output stream
- `>>` : extraction operator, applied to an input stream
- **example**:
```cpp
int n;
cout << "Enter a number: ";
cin >> n;
cout << "You have entered: " << n << '\n';
```
- where `cout` is the standard output (monitor) and `cin` is the standard input (keyboard).


## PROGRAM ERRORS
- #### syntax errors
    - vioilation of the grammar rules of the language
    - discovered by the compiler
        - error messages may not always show correct location of erros
- #### run-time errors
    - error conditions detected by the computer at run-time
- #### logic errors
    - errors in the program's algorithm
    - most difficult to diagnose
    - computer does not recognize an error.


## FIX BUGS
- compiler for syntax errors
- debugger for the rest.


## THE STANDARD `STRING` CLASS
- the `string` class allows the programmer to treat strings as a basic data type.
- the `string` class is defined in the `string` library and the names are in the standard `namespace`
    - to use the `string` class you need these lines:
    ```cpp
    #include <string>
    using namespace std;
    ```


## ASSIGNMNET OF STRINGS
- variables of type `string` can be assigned with the `=` operator.
    - **example**:
    ```cpp
    string s1, s2, s3;
    //...
    s3 = s2;
    ```
- quoted strings (i.e. C-strings) are **type cast** to type string.
    - **example**:
    ```cpp
    string s1 = "Hello Mom!";
    ```


## USING `+` WITH STRINGS
- variables of type `string` can be concatenated with the `+` operator.
    - **example**:
    ```cpp
    string s1, s2, s3;
    //...
    s3 = s1 + s2;
    ```
    - if `s3` is not large enough to contain `s1 + s2`, **more space is allocated**.


## COMPARISON OF STRINGS
- comparison operators work with `string` objects.
    - objectes are compared using lexicographic order (alphabetical ordering using the order of symbols in the ASCII character set.)
    - `==` returns true if two string objects contain the same characters in the same order.
    - `<`, `>`, `<=`, `>=` can be used to compare string objects


## `STRING` CONSTRUCTORS
- The default `string` **constructor** initializes the `string` to the empty string
- Another `string` constructor takes a C-string argument
    - **example**:
    ```cpp
    string parse; // empty string
    string noun("ants"); // a string version of "ants"
    ```

## MIXING `STRING`s AND C-STRINGS
- it is natural to work with strings in the following manner
```cpp
string phrase = "I love" + adjective + " " + noun + "!";
```
> it is not so easy for C++! It must either convert the null-terminated C-strings, e.g. "I love", to `string`s, or it must use an overloaded `+` operator that works with strings and C-strings.


## MEMBER FUNCTION `length`
- the `string` class member function `length` returns the number of characters in the `string` object:
    - **example**:
    ```cpp
    int n = string_var.length();
    ```

## `string` PROCESSING
- the string class allows the same operations we used with C-strings... and more
    - characters in a string object can be accessed as if they are in an array.
        - `last_name[i]` provides access to a single character as in an array
        - index value are **not** checked for validity!


## MEMBER FUNCTION `at`
- `at` is an alternative to using `[]`'s to access characters in a string.
    - `at` checks for valid index values.
    - **example**:
    ```cpp
    string str("Mary");
    ```
    - **example#02**:
    ```cpp
    cout << str[6] << endl;
    ```
    is equivalent to
    ```cpp
    cout << str.at(6) << endl;
    ```
    - **example#03**:
    ```cpp
    str[2] = 'X';
    ```
    is equivalent to
    ```cpp
    str.at(2) = 'X';
    ```


## MEMBER FUNCTIONS OF THE STANDARD CLASS `string`
- #### CONSTRUCTORS
| 1   | 2   |
|-----|-----|
| 0:2 | 1:2 |
| 0:3 | 1:3 |
| 0:4 | 1:4 |









