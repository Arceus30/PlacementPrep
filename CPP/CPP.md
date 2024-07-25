# CPP

#### 1. [Basic Sheet](https://quickref.me/cpp)

#### 2. [Ascii Codes](https://quickref.me/ascii-code)

#### 3. Input Output

```c++
#include<iostream>
#include <fstream>
int main(){
    int v_name;

    // input without whitespace, '\t', '\n'.
    std::cin>>v_name;

    // input to be stored in object v_name and '$' acts as a custom delimeter.
    getline(std::cin, v_name,'$');

    std::cout<<v_name<<endl;
}
filehandling(){

    // file stream object
    std::ofstream outputFile;
    std::ifstream inputFile;

    // Open a file
    outputFile.open("example.txt");
    inputFile.open("example.txt");

    // Check if the file opened successfully
    if (!outputFile.is_open()) {
        std::cerr << "Error opening file!" << std::endl;
    }

    // Write data to the file
    outputFile << "Hello, world!" << std::endl;
    outputFile << "This is a test file." << std::endl;

    // Read data from the file
    std::string line;
    while (std::getline(inputFile, line)) {
        std::cout << line << std::endl;
    }

    // Close the file
    outputFile.close();
    inputFile.close();
}
```

#### 4. Datatypes

-   [GFG](https://www.geeksforgeeks.org/cpp-data-types/)
-   Negative numbers are stored after taking 2's complement
-   **Type Casting**
    -   Implicit :- casting done by compilier automatically. bool => char => short int => int => unsigned int => long => unsigned long => long long => float => double => long double.
    -   Explicit :- `datatype var_name = (type) expression`

#### 5. Operators

-   Arithematic Operators (Not included in the reference file above): + , - , \* , / , % , ++ (Pre and Post) , -- (Pre and Post)

#### 6. [Functions (GFG)](https://www.geeksforgeeks.org/functions-in-cpp/)

#### 7. [Lambda Expressions (GFG)](https://www.geeksforgeeks.org/lambda-expression-in-c/)

#### 8. [Pointers (GFG)](https://www.geeksforgeeks.org/cpp-pointers/)

#### 9. Time Complexity

| Input Length | Worst Accepted Time Complexity | Usually type of solutions                                       |
| ------------ | ------------------------------ | --------------------------------------------------------------- |
| 10 -12       | O(N!)                          | Recursion and backtracking                                      |
| 15-18        | O(2<sup>N</sup> \_ N)          | Recursion, backtracking, and bit manipulation                   |
| 18-22        | O(2<sup>N</sup> \_ N)          | Recursion, backtracking, and bit manipulation                   |
| 30-40        | O(2<sup>N/2</sup> \* N)        | Meet in the middle, Divide and Conquer                          |
| 100          | O(N<sup>4</sup>)               | Dynamic programming, Constructive                               |
| 400          | O(N<sup>3</sup>)               | Dynamic programming, Constructive                               |
| 2K           | O(N<sup>2</sup> \* log N)      | Dynamic programming, Binary Search, Sorting, Divide and Conquer |
| 10K          | O(N<sup>2</sup>)               | Dynamic programming, Graph, Trees, Constructive                 |
| 1M           | O(N\* log N)                   | Sorting, Binary Search, Divide and Conquer                      |
| 100M         | O(N), O(log N), O(1)           | Constructive, Mathematical, Greedy Algorithms                   |

#### 10. [Error Handling (GFG)](https://www.geeksforgeeks.org/exception-handling-c/)

#### 11. [OOPS](OOPS/OOPS.md)

#### 12. [Data Structures](Data%20Structures/DataStructures.md)

#### 13. [Algorithms](Algorithms/Algorithms.md)
