# Snippet 1: Optimal Substructure

If the solution to a problem can be constructed from solutions to its subproblems, then the problem has an optimal substructure. For example, in Fibonacci we can combine the results from smaller numbers to solve the bigger one.

# Snippet 2: Overlapping Subproblems

When a problem involves overlapping subproblems, or when the same subproblem is handled more than once, DP performs best. By only resolving each subproblem once, DP saves time.

# Snippet 3: Memoization 

Avoiding recomputation by storing subproblem results in an array or dictionary during recursion. Recursive Fibonacci with a cache is one example.

# Snippet 4: Tabulation

Building array from base cases and filling it from 0 till the end. 

# Snippet 5: DP Array Initialization

Usually, in Python, array is created like:
<pre>
  dp = [0] * (n + 1)
</pre>

if it is 2D array:
<pre>
  dp = [[0] * (cols + 1) for _ in range(rows + 1)]
</pre>


# Snippet 6: 2D DP Array Initialization

For some problems like LCS, we need to create 2D arrays. In Python, 2D array is created:
<pre>
  dp = [[0] * (cols + 1) for _ in range(rows + 1)]
</pre>

# Snippet 7: Looping through array

In many DP problems we need rather recursion or array iteration. This is the code for iteration through array with loop and filling it:

<pre>
  for i in range(1, rows + 1):
    for j in range(1, cols + 1):
        dp[i][j] = max(dp[i-1][j], dp[i][j-1])
</pre>


