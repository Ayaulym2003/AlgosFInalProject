# Problem 1: Fibonacci Numbers 
Problem Statement
Given a positive integer n, the task is to find the nth Fibonacci number.The Fibonacci sequence is a sequence where the next term is the sum of the previous two terms. The first two terms of the Fibonacci sequence are 0 followed by 1. The Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

Example:

Input: n = 2   
Output: 1   
Explanation: 1 is the 2nd number of Fibonacci series.

Input: n = 5   
Output: 5   
Explanation: 5 is the 5th number of Fibonacci series.

## 🔹 Hints

Hint 1: 

Hint 2:

## 🔹 Brute Force Idea

We can use recursion to solve this problem because any Fibonacci number n depends on previous two Fibonacci numbers. Therefore, this approach repeatedly breaks down the problem until it reaches the base cases.

<pre>
def nth_fibonacci(n):
    if n <= 1:
        return n
      
    return nth_fibonacci(n - 1) + nth_fibonacci(n - 2)

n = 5
result = nth_fibonacci(n)
print(result)
</pre>

## 🔹 Optimized Idea

We can optimize the idea by adding Dynamic programming. Tabulation approach iteratively builds up the solution by calculating Fibonacci numbers from the bottom up. In the this approach, a function with 1 parameter, n, is created. If n is less or equal to 1, the function returns n which is 1 or 0. Then, we create an array with 0 and 1 and iterate from 2 till n+1 so that we go from bottom to up. After recursive calculation of Fibonacci numbers we append them to an array and return the array.

Time Complexity: O(n), the loop runs from 2 to n, performing a constant amount of work per iteration.

## 🔹 Code Fragment
<pre>
def fib(n):
    if n <= 1:
        return n
    dp = [0, 1]
    for i in range(2, n+1):
        dp.append(dp[i-1] + dp[i-2])
    return dp[n]
print(fib(10))  # Output: 55
</pre>

# Problem 2: 
Problem Statement
There are n stairs, and a person standing at the bottom wants to climb stairs to reach the top. The person can climb either 1 stair or 2 stairs at a time, the task is to count the number of ways that a person can reach at the top. 

Input: n = 1                                                                                                                            
Output: 1   
Explanation: There is only one way to climb 1 stair.     

Input: n = 2  
Output: 2   
Explanation: There are two ways to reach 2th stair: {1, 1} and {2}.  

Input: n = 4   
Output: 5   
Explanation: There are five ways to reach 4th stair: {1, 1, 1, 1}, {1, 1, 2}, {2, 1, 1}, {1, 2, 1} and {2, 2}. 

## 🔹 Hints

Hint 1: 

Hint 2:

## 🔹 Brute Force Idea

This problem is just like Fibonacci numbers. A person can reach nth stair either from (n-1)th stair or (n-2)th stair. Thus, for each stair n, we calculate the number of ways to reach the (n-1)th and (n-2)th stairs, and add them to get the total number of ways to reach the nth stair. This gives us the following recurrence relation:   
countWays(n) = countWays(n-1) + countWays(n-2)

## 🔹 Optimized Idea

We can optimize the idea by adding Dynamic programming. Tabulation approach iteratively builds up the solution by calculating Fibonacci numbers from the bottom up. In the this approach, a function with 1 parameter, n, is created. If n is less or equal to 1, the function returns n which is 1 or 0. Then, we create an array with 0 and 1 and iterate from 2 till n+1 so that we go from bottom to up. After recursive calculation of Fibonacci numbers we append them to an array and return the array.

Time Complexity: O(n), the loop runs from 2 to n, performing a constant amount of work per iteration.

## 🔹 Code Fragment
<pre>
def fib(n):
    if n <= 1:
        return n
    dp = [0, 1]
    for i in range(2, n+1):
        dp.append(dp[i-1] + dp[i-2])
    return dp[n]
print(fib(10))  # Output: 55
</pre>


# Snippet 3: Climbing stairs with Tabulation approach

There are n stairs, and a person standing at the bottom wants to climb stairs to reach the top. The person can climb either 1 stair or 2 stairs at a time, the task is to count the number of ways that a person can reach at the top.
In the Bottom-up approach, a function with 1 parameter, n, is created. An array of length n+1, filled with 0s, is created and the first 2 elements are set to 1. After, we iterate through the array from the second element to the end and the elements in the array are replaced with the sum of previous 2 elements.
<pre>
def countWays(n):
    dp = [0] * (n + 1)
  
    dp[0] = 1
    dp[1] = 1
    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]; 
  
    return dp[n]
n = 4
print(countWays(n))
</pre>

# Snippet 4: Count Valid Parenthesis
Given a number n, the task is to find the number of valid parentheses expressions of that length. 
Algorithm:
Using a combinatorial method that is tuned to minimize computational steps by utilizing the symmetry C(n,k) = C(n,n-k), determine the binomial coefficient C(2n,n). 
Calculate the nth Catalan number as C(2n,n)/(n+1) using the binomial coefficient. This shows how many possible arrangements there are for parenthetical pairs.
Verify if n is odd; if it is, return 0 and have balanced parentheses.
To get the total number of valid balanced parentheses arrangements of length n, calculate the (n/2)th Catalan number for even n.
<pre>
def binomialCoeff(n, k):
    res = 1
    if k > n - k:
        k = n - k
    for i in range(k):
        res *= (n - i)
        res //= (i + 1)

    return res

def catalan(n):
    c = binomialCoeff(2 * n, n)
    return c // (n + 1)

def findWays(n): 
    if n & 1:
        return 0
    return catalan(n // 2)

if __name__ == "__main__":
    n = 6
    print(findWays(n))
</pre>
