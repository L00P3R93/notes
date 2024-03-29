## Data Structures and Algorithm [DSA]
### Introduction
- ```variables``` - placeholders representing data.

- ```data-types``` - set of data with predefined values: int, float, double, string.

- ```system-defined data-types``` - primitive data-types like int,float, etc.

- ```user-defined data-types``` - like ```Structures``` in C\C++ or ```Classes``` in Java.
#### Data Structure [DS]
- DS is a particular way of sorting and organizing data in a computer so that it can be used efficiently.
- A DS is a special format for organizing and storing data.
- Arrays, Files, Linked Lists, Queues, Trees, Graphs etc.
#### Data Structure Types
- ```Linear DS``` - Elements are accessed in a sequential order but it is not compulsory to store all elements sequentially. Linked Lists, Stacks and Queues.
- ```Non-Linear DS``` - Elements are stored/accessed in a non-linear order. Trees and Graphs.
#### Abstract Data Types [ADTs]
- Combining DS with their operations, which involves:
  - Declaration of data.
  - Declaration of operations.
- Commonly used ADTs include: Linked Lists, Stacks, Queues, Priority Queues, Binary Trees, Dictionaries, Disjoint Sets (Union and Find), Hash Tables, Graphs and many others.
#### Algorithm
- is the step-by-step unambiguous instructions to solve a given problem.
#### Analysis of Algorithms
The goal of the analysis of algorithms is to compare algorithms or solutions mainly in-terms of running time but also in-terms of other factors e.g. memory, developer effort etc.
#### Running Time Analysis
Process of determining how processing time increases as the size of the problem(input size) increases.

- ```Input Size``` - the number of elements in the input.

- Common types of inputs:
  - Size of an Array
  - Polynomial Degree
  - Number of elements in a matrix
  - Number of bits in the binary representation of the input.
  - Vertices and edges in a graph.

  #### Comparing Algorithms
- By expressing the running time of a given algorithm as a function of the input size *n* i.e. *f(n)* and comparing these different functions corresponding to running times.
#### Rate of Growth
 - The rate at which the running time increases as a function of input.
 - Commonly used Rates of Growth:

 | Time Complexity | Name | Example |
 | ----------- | ----------- | ----------- |
 | 1 | Constant | Adding an element to the front of a linked list |
 | logn | Logarithmic | Finding an element in a sorted array |
 | n | Linear | Finding an element in a unsorted array |
 | nlogn | Linear Logarithmic | Sorting n items by 'divide-and-conquer' - Mergesort |
 | n<sup>2</sup> | Quadratic | Shortest path between 2 nodes in a graph |
 | n<sup>3</sup> | Cubic | Matrix Multiplication |
 | 2<sup>n</sup> | Exponential | The Towers of Hanoi problem |

 #### Types of analysis
  1. Worst Case *(slowest time to complete)*  
    - Defines the input for which the algorithm takes a long time.
  2. Best Case *(fastest time to complete)*
    - Defines the input for which the algorithm takes the least time.
  3. Average Case
    - Provides a prediction about the running time of the algorithm.
    - Run algorithm many times, using many different inputs that come from some distribution that generates these inputs, compute the total running time and divide by number of trials.
    - Assumes that the input is random

    - ```Lower Bound <= Average Time <= Upper Bound```

  Representing the best, worst and average cases in the form of expressions:

  ```math
  f(n) = n^2 + 500, for worst case
  /sqrt{3}
  f(n) = n + 100n + 500, for best case
  ```
  #### Big-O Notation [Upper Bounding Function]
  - This notation gives the tight upper bound of the given function.
  - Generally, represented as ```f(n) = O[g(n)]```. This means that, at larger values of n, the upper bound of *f(n)* is *g(n)*.
  - O–notation defined as ```O[g(n)] = {f(n): there exist positive constants c and n~0 such that 0 ≤ f(n) ≤ cg(n) for all n > n~0}```.
  - g(n) is an asymptotic tight upper bound for f(n). Our objective is to give the smallest rate of growth g(n) which is greater than or equal to the given algorithms’ rate of growth /(n).

  #### Big-O Visualization
  - ```O[g(n)]``` is the set of functions with smaller or the same order of growth as ```g(n)```.

  #### Omega-Q Notation [Lower Bounding Function]
  - This notation gives the tighter lower bound of the given algorithm, represented as ```f(n) = Ω(g(n))```.
  - The Ω notation can be defined as ```Ω(g(n)) = {f(n): there exist positive constants c and $n~0$ such that 0 ≤ cg(n) ≤ f(n) for all $n ≥ n~0$}```.
  - g(n) is an asymptotic tight lower bound for f(n). Our objective is to give the largest rate of growth g(n) which is less than or equal to the given algorithm’s rate of growth f(n).
  #### Asymptotic Analysis
  - Algorithm analysis where the asymptotic curve of *g(n)* is used in approximating *f(n)* at higher values of *n*. In other terms, g(n) is the asymptotic curve for f(n).
  #### Guidelines for Asymptotic Analysis
  1. Loops:
    - Running time of a loop is, at most, the running time of statements inside the loop *(c)* multiplied by the number of iterations.

    ```console
    //Executes n times
    for(i=1; i<=2; i++){
      m = m + 2; //constant time, c
    }
    ```

    - Total time = ```c * n = cn = O(n)```
  2. Nested Loops
    - Analyzed from inside out. Total running time is the product of the sizes of all the loops.

    ```console
    //Outer loop executed n times
    for(i=1; i<=n; i++){
      //inner loop executes n times
      for(j=1; j<=n; j++){
        k = k + 1; //constant time
      }
    }

    Total time = c * n * n = cn^2 = O(n^2)
    ```
  3. Consecutive Statements
    - Add the time complexities of each statement.

    ```console
    x = x + 1; //constant time
    //executes n times
    for(i=1; i<=n; i++)
      m = m + 2; //constant time
    //outer loop executes n times
    for(i=1; i<=n; i++){
      //inner loop executed n times
      for(j=1; j<=n; j++){
        k = k + 1; //constant time
      }
    }

    Total time = c0 + c1n + c2n^2 = O(n^2)
    ```
  4. If-then-else statements
    - Worst-case running time: the test, plus either the then part or the else part.

    ```console
    //test: constant
    if(length() == 0){
      return false; //then part: constant
    }else{ //else part: (constant + constant) * n
      for(int n=0; n < length; n++)
        //another if: constant + constant (no else part)
        if(!list[n].equals(otherList[n]))
          return false; // constant
    }

    Total time = c0 + c1 + (c2 + c3) * n = O(n)
    ```

  5. Logarithmic Complexity
    - An Algorithm is *O(logn) if it takes a constant time to cut the problem size by a fraction.

    ```console
    for(i=1;i<=n;)
      i = i * 2;

    for(i=n; i>=1;)
      i = i/2;
    ```
