# How-to-Talk-Algorithm-Analysis

August 8, 2019

I appreciate comments. Shoot me an email at noel_s_cruz@yahoo.com!

Hire me!

Keeping Busy with Algorithm Analysis

An algorithm is a clearly specified set of simple instructions to be followed
to solve a problem. Once an algorithm is given for a problem and decided to be
correct, an important step is to determine how much in the way of resources,
such as time or space, the algorithm will require. An algorithm that solves a
problem but requires a year is hardly of any use. Likewise, an algorithm that
requires thousands of gigabytes of main memory is not currently useful on most
machines. As an aside, we have cloud servers which are not necessarily
supercomputers but simply commodity computers some even running Windows 7. We
only need to improve the throughput of processing data in cloud storage.

We need to establish a relative order among functions. Given two functions, 
there are usually points where one function is smaller than the other. So it 
does not make sense to claim, for instance, f(N) < g(N). Thus, we compare their
relative rates of growth. When we apply this to the analysis of algorithms, we
shall see why this is the important measure.

Although 1,000N is larger than N^2 for small values of N, N^2 grows at a faster
rate, and thus N^2 will eventually be the larger function. The turning point is
N = 1000 in this case.

This information is sufficient to arrange most of the common functions by growth
rate.

Constant

Logarithmic

Log-squared

Linear

Quadratic

Cubic

Exponential

Model

In order to analyze algorithms in a formal framework, we need a model of 
computation. Our model is basically a normal computer in which instructions are
executed sequentially. Our model has the standard repertoire of simple 
instructions, such as addition, multiplication, comparison and assignment, but,
unlike the case with real computers, it takes exactly one time unit to do
anything simple. We also assume infinite memory.

What to Analyze

The most important resource to analyze is generally the running time. Several
factors affect the running time of a program. Some, such as the compiler and
computer used, are obviously beyond the scope of any theoretical model, so,
although they are important, we cannot deal with them here. The other main
factors are the algorithm used and the input to the algorithm.

Typically, the size of the input is the main consideration. We define two
functions, Tavg(N) and Tworst(N), as the average and worst-case running time,
respectively, used by an algorithm on input of size N. Clearly, Tavg(N) <= 
Tworst(N). If there is more than one input, these functions may have more than
one argument.

Occasionally, the best-case performance of an algorithm is analyzed. However,
this is often of little interest, because it does not represent typical
behavior. Average-case performance often reflects typical behavior, while worst
case performance represents a guarantee for performance on any possible input.

Generally, the quantity required is the worst-case time, unless otherwise
specified. One reason for this is that it provides a bound for all input,
including particularly bad input, which an average-case analysis does not 
provide. The other reason is that average-case bounds are usually much more 
difficult to compute.

Running-Time Calculations

There are several ways to estimate the running time of a program. The previous
table was obtained empirically. If two programs are expected to take similar
times, probably the best way to decide which is faster is to code them both and
run them!

Generally, there are several algorithmic ideas, and we would like to eliminate
the bad ones early, so an analysis is usually required. Furthermore, the ability
to do an analysis usually provides insight into designing efficient algorithms. 
The analysis also generally pinpoints the bottlenecks, which are worth coding
carefully.

To simplify the analysis, we will adopt the convention that there are no 
particular units of time. Thus, we throw away leading constants. We will also
throw away low-order items, so what we are essentially doing is computing a
Big-Oh running time. Since Big-Oh is an upper bound, we must careful never to
underestimate the running time of the program. In effect, the answer provided is
a guarantee that the program will terminate within a certain time period. The 
program may stop earlier than this, but never later.

A Simple Example

   int sum( int n )
   
   {
   
     int partialSum;
     
1    partialSum = 0;

2    for( int i; i <= n; ++i )

3      partialSum += i*i*i;

4    return partialSum;

   }

The analysis of this fragment is simple. The declarations count for no time.
Lines 1 and 4 count for one unit each. Line 3 counts for four units per time
executed(two multiplications, one addition, and one assignment) and is 
executed N times, for a total of 4N units. Line 2 has the hidden costs of
initializing i, testing i <= , and incrementing i. The total cost of all these
is 1 to initialize, N+1 for all the tests, and N for all the increments, which
is 2N + 2. We ignore the costs of calling the function and returning, for a 
total of 6N + 4. Thus, we say that this function is O(N).

If we had to perform all this work every time we needed to analyze a program,
the task would quickly become infeasible. Fortunately, since we giving the 
answer in terms of Big-Oh, there are lots of shortcuts that can be taken without
affecting the final answer. For instance, line 3 is obviously an O(1) statement
(per execution), so it is silly to count precisely whether it is two, three, or
four units; it does not matter. Line 1 is obviously insignificant compared with
the for loop, so it is silly to waste time here. This leads to several general
rules.

General Rules

Rule 1 - FOR Loops

The running time of a for loop is at most the running time of the statements
inside the for loop(including tests) times the number of iterations.

Rule 2 - Nested Loops

Analyze these inside out. The total running time of a statement inside a group
of nested loops is the running time of the statement multiplied by the product
of the sizes of all the loops.

As an example, the following program fragment is O(N^2).

  for( i = 0; i < n; ++i )
  
    for( j = 0; j < n; ++j )
    
      ++k;
      
Rule 3 - Consecutive Statements

These just add (which means that the maximum is the one that counts; see rule 1)

As an example, the following fragment, which has O(N) work followed by O(N^2)
work, is also O(N^2).

   for( i = 0; i < n; ++i )
   
     a[i] = 0;
     
  for( i = 0; i < n; ++i )
  
    for( j = 0; j < n; ++j )
    
      a[i] += a[j] + 1 + j;
      
Rule 4 - If/Else

For the fragment

  if( condition )
  
    S1
    
  else
  
    S2
    
the running time of an if/else statement is never more than the running time of 
the test plus the larger of the running times of S1 and S2.

Clearly, this can be an overestimate in some cases, but it is never an 
underestimate.

I included some posts for reference.

https://github.com/noey2020/How-to-Talk-Recursion

https://github.com/noey2020/How-to-Talk-Linked-Lists

https://github.com/noey2020/How-to-Talk-Queues

https://github.com/noey2020/How-to-Talk-Stacks

https://github.com/noey2020/How-to-Talk-Lists-Stacks-and-Queues

https://github.com/noey2020/How-to-Talk-Linear-Regression

https://github.com/noey2020/How-to-Talk-Statistics-Pattern-Recognition-101

https://github.com/noey2020/How-to-Write-SPI-STM32

https://github.com/noey2020/How-to-Write-SysTick-Handler-for-STM32

https://github.com/noey2020/How-to-Write-Subroutines-in-C-Assembly-STM32

https://github.com/noey2020/How-to-Write-Multitasking-STM32

https://github.com/noey2020/How-to-Generate-Triangular-Wave-STM32-DAC

https://github.com/noey2020/How-to-Generate-Sine-Table-LUT

https://github.com/noey2020/How-to-Illustrate-Multiple-Exceptions-

https://github.com/noey2020/How-to-Blink-LED-using-Standard-Peripheral-Library

I appreciate comments. Shoot me an email at noel_s_cruz@yahoo.com!

Hire me!

Have fun and happy coding!
