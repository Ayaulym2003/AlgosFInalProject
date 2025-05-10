# ✅Topic: Dynamic Programming

Dynamic programming is a technique where an algorithmic problem is broken down into subproblems. It is a method of computer programming in which an algorithmic problem is first divided into smaller problems, the outcomes are saved, and then the smaller problems are optimized to find the overall solution, which typically involves determining the algorithmic query's maximum and minimum range. 

This method divides difficulties into more manageable, overlapping subproblems in order to solve them. In order to avoid having to compute the same problem again, the results are then saved in a table for later use. 

For instance, the results are kept and inserted into the equation later rather than being calculated anew when employing the dynamic programming technique to determine every conceivable outcome from a collection of values. Therefore, it saves time and produces faster results by requiring less work while working with lengthy, complex equations and processes.

Using dynamic programming to solve problems is more effective than just trying things until they work. But it only helps with problems that one can break up into smaller equations that will be used again at some point.

## How Does Dynamic Programming Work?

The way dynamic programming operates is by decomposing complicated issues into smaller, more manageable ones. Finding the best answers to these subproblems comes next. One technique that stores the results of these procedures is memorization, which eliminates the need to compute the related answers when they are later required. Saving answers reduces the amount of time needed to calculate previously encountered subproblems. 

There are two methods for achieving dynamic programming:

### Top-down approach (Memoization)
The top-down approach uses recursion and caching methods. It recursively solves subproblems and cache their results. But it has disadvantage because of recursion, which occupies more memory in call stack. 

### Bottom-up approach (Tabulation)
The bottom-up approach iteratively goes from bottom to up, that is, it solves subproblems first and then use their solutions to solve larger problems. 

## Suitability
There are two main signs that user can solve the problem with Dynamic Programming. When subproblems overlap and when there is optimal substructure.

### Subproblem Overlapping 
We refer to subproblems as overlapping when the solutions to the same subproblem are required more than once in order to resolve the primary issue. In this sign, solutions of subproblems are put into table so the users can reuse them instead of recalculating. 

### Optimal Substructure 
You can use DP if you can find best answer to the problem by taking best solutions of subproblems and putting them together. We see this when we have to find shortest path between two points. If we find path between p and w and w and t, then we can put them together and find distance between p to t.

## DP algorithms
There are many Dynamic programming algorithms. The most popular algorithms:

1. Greedy algorithms.

   We look for a local solution to find global answer. By looking for the best answers to the subproblems and merging the results of these subproblems, the approach finds the best solution to a given issue. 
3. Floyd-Warshall algorithm.

   This Algorithm is used to find shortest pathways. The possible paths through the graph for each pair of vertices are compared by this program. To find the shortest distance between two vertices in a chart, it iteratively optimizes an estimate of the shortest path between them. The pathways can be reconstructed with minor adjustments. 
5. Bellman Ford algorithm.

   Determines the shortest route from a particular source vertex to every other weighted digraph vertices. 

## Examples 
1. Fibbonacci numbers.

   F(n)=F(n−1)+F(n−2). Those, we can find the sequence by finding the sum of previous two numbers and recursively iterating through the values of n. 
3. The optimal Strategy of a game.

   We solve smaller subgames first using dynamic programming, and then we build up to determine the highest total you can achieve if you both play flawlessly.
5. Longest common subsequence.

   In order to determine the length of the longest common subsequence, we construct a table in which each cell has the best response for smaller segments of the strings. We then gradually fill it up.

## Takeways

- To save duplication of effort, Dynamic Programming divides problems into smaller subproblems, solves each one once, and stores the solutions.

- Top-down approach recursively solves subproblems and cache their results. While bottom-up solves subproblems first and then use their solutions to solve larger problems. 

- You can use DP when your code have overlapping subproblems and Optimal Substructure.

















