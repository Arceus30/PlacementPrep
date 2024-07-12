# CPP

**Input Output**

```c++
#include<iostream> // library containing input output objects stored inside the namespace 'std'
#include <fstream> // library containing file handling objects stored inside the namespace 'std'
int main(){
    int v_name;
    std::cin>>v_name; // it takes a continuous input without whitespace, '\t', '\n'.
    getline(std::cin, v_name,'$'); // it takes input to be stored in object v_name and '$' acts as a custom delimeter.
    std::cout<<v_name<<endl; // it is used to display output on the screen, endl is used to move to next line
}

filehandling(){
    std::ofstream outputFile; // output file stream object
    std::ifstream inputFile; // input file stream object

    outputFile.open("example.txt"); // Open a file for writing
    inputFile.open("example.txt"); // Open a file for reading

    // Check if the file opened successfully
    if (!outputFile.is_open()) {
        std::cerr << "Error opening file!" << std::endl;
        return 1; // Exit the program with an error code
    }

    // Write data to the file
    outputFile << "Hello, world!" << std::endl;
    outputFile << "This is a test file." << std::endl;

    // Read data from the file and print it to the console
    std::string line;
    while (std::getline(inputFile, line)) {
        std::cout << line << std::endl;
    }

    // Close the file
    outputFile.close();
    inputFile.close();
}
```

**PreProcessor**

-   `#if`, `#elif`, `#else`: Preprocessor version of condition statements
-   `#endif`: Used to end an `#if`
-   `#define`: Defines a text macro.
-   `#undef`: Un-defines a text macro
-   `#include`: Includes a source file

**Datatypes**

| DataType      | Size (bytes) |          | Range                               |
| ------------- | ------------ | -------- | ----------------------------------- |
| short int     | 2            | signed   | -2<sup>15</sup> to 2<sup>15</sup>-1 |
|               |              | unsigned | 0 to 2<sup>16</sup>-1               |
| int           | 4            | signed   | -2<sup>31</sup> to 2<sup>31</sup>-1 |
|               |              | unsigned | 0 to 2<sup>32</sup>-1               |
| long long int | 8            | signed   | -2<sup>63</sup> to 2<sup>63</sup>-1 |
|               |              | unsigned | 0 to 2<sup>64</sup>-1               |
| float         | 4            |          | -3.4×10^38 to 3.4×10^38             |
| double        | 8            |          | -1.7×10^308 to1.7×10^308            |
| long double   | 16           |          | -1.1×10^4932 to1.1×10^4932          |
| signed char   | 1            | signed   | -128 to 127                         |
|               |              | unsigned | 0 to 255                            |
| wchar_t       | 2 or 4 bytes |          | 1 wide character                    |
| bool          | 1 byte       |          | True or False (0 or 1)              |

-   Negative numbers are stored after taking 2's complement
-   **Type Casting**
    -   Implicit :- The compilier will automatically converts datatype from low size to higher size. bool => char => short int => int => unsigned int => long => unsigned long => long long => float => double => long double.
    -   Explicit :- We have to specify to which datatype we want to convert. `(type) expression`

**operators**

-   Arithematic Operators: + , - , \* , / , % , ++ (Pre and Post) , -- (Pre and Post)
-   Relational Operators: == , != , < , > , <= , >=
-   Bitwise Operatos: ~ , & , | , ^ , << , >>
-   Logical Operatos: ! , && , ||
-   Assignment Operators: += , -= , \*= , /= , %=

-   if we use left-shift operator such that the leftmost bit becomes the set bit(i.e. = 1), then that number will be perceived as negative number
-   XOR of a number with itself = 0 and XOR of any number with 0 is that number itself
-   **Modular Arithmetic**
    -   (a+b) % m = (a%m + b%m) %m
    -   (a-b) % m = (a%m - b%m) %m
    -   (a*b) % m = (a%m * b%m) %m
    -   (a/b) % m = (a \* (inverse of b if exists)) %m

**Conditions**

-   `if (cond) {}`
-   `if (cond) {} else {}`
-   `if (cond1) {} else if (cond2) {} else {}`
-   ```cpp
      if (cond1) {
          if (cond2) {}
      }
    ```
-   ```c++
      switch(val){
          case cond1:
          case cond2:
          default:
      }
    ```
-   Ternary Operator: `res = cond ? s1(cond is true): s2(cond is false);`

**Loops**

-   `for(initialize; cond; increment) {}`
-   ```cpp
      //initialize
      while(cond) {
          increment
      }
    ```
-   ```cpp
      initialize;
      do{
          increment
      }while(cond)
    ```
-   `continue` skips that particular iteration and continues the loop
-   `break` end the iterations and break the loop

**Functions**

-   `return_type function_name (parameter_type parameter_name){ //body }`
-   Function Declaration: `return_type function_name(parameter_list);`
-   Types of parameters
    -   Formal Parameter: parameters received by the function
    -   Actual Parameter: parameters passed to the function
-   Function with Default Parameters: `return_type function_with_defaults(type parameter1,type parameter2 = default_value2) {}`
-   Ways to pass the parameter
    -   `return_type function_name (parameter_type parameter_name){ //body }`
        Pass by Value: values of actual parameters are copied to the function’s formal parameters. Actual and formal parameters are stored in different memory locations so any changes made in the functions are not reflected in the actual parameters of the caller
    -   `return_type function_name (parameter_type & parameter_name){ //body }`
        Pass by reference: Both actual and formal parameters refer to the same locations, so any changes made inside the function are reflected in the actual parameters of the caller.
-   Lambda Function: `auto lambda_function = [](parameters) -> return_type {};`

**Pointers**

-   & is reference operator or address operator it returns the address of that var object
-   stores the address of the variable and `*` is used to dereference that address and access the value
-   Size of pointer = 8bytes ( address occupies 8bytes of storage)
-   & is reference operator or address operator it returns the address of that var object
-   ```cpp
      return_type variable_name = val;
      return_type * pointer_name = & variable_name;
      pointer_name --> address of variable_name
      * pointer_name --> value at address of variable_name
    ```

**Time Complexity**
| Input Length | Worst Accepted Time Complexity | Usually type of solutions |
| - | - | - |
| 10 -12 | O(N!) | Recursion and backtracking |
| 15-18 | O(2<sup>N</sup> _ N) | Recursion, backtracking, and bit manipulation |
| 18-22 | O(2<sup>N</sup> _ N) | Recursion, backtracking, and bit manipulation |
| 30-40 | O(2<sup>N/2</sup> \* N) | Meet in the middle, Divide and Conquer |
| 100 | O(N<sup>4</sup>) | Dynamic programming, Constructive |
| 400 | O(N<sup>3</sup>) | Dynamic programming, Constructive |
| 2K | O(N<sup>2</sup> \* log N) | Dynamic programming, Binary Search, Sorting, Divide and Conquer
| 10K | O(N<sup>2</sup>) | Dynamic programming, Graph, Trees, Constructive |
| 1M | O(N\* log N) | Sorting, Binary Search, Divide and Conquer |
| 100M | O(N), O(log N), O(1) | Constructive, Mathematical, Greedy Algorithms |

**Error Handling**

-   `try { throw SomeExceptionType("Error message");} catch( ExceptionName e1 ) {} `
-   `catch(...)`: catches all types of exceptions
-   Implicit type conversion doesn't happen for primitive types
-   If an exception is thrown and not caught anywhere, the program terminates abnormally.
-   try/catch blocks can be nested. Also, an exception can be re-thrown using “throw; “.
-   When an exception is thrown, all objects created inside the enclosing try block are destroyed before the control is transferred to the catch block.
