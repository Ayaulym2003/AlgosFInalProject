# Snippet 1: Fibonacci Numbers Memoization Approach
Given a positive integer n, the task is to find the nth Fibonacci number.The Fibonacci sequence is a sequence where the next term is the sum of the previous two terms. The first two terms of the Fibonacci sequence are 0 followed by 1. The Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8, 13, 21
In the Top-down approach, a function with 2 parameters, n and memo table, is created. If n is in the table, function returns memo[n] and if n is less or equal to 1, function returns n which is 1 or 0. Fibonacci of previous 2 numbers is calculated and stored in a memo array. 
<pre>
  def fib(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fib(n-1, memo) + fib(n-2, memo)
    return memo[n]
print(fib(10))  # Output: 55
</pre>

# Snippet 2: Fibonacci Numbers Tabulation Approach
Given a positive integer n, the task is to find the nth Fibonacci number.The Fibonacci sequence is a sequence where the next term is the sum of the previous two terms. The first two terms of the Fibonacci sequence are 0 followed by 1. The Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8, 13, 21
In the Bottom-up approach, a function with 1 parameter, n, is created. If n is less or equal to 1, the function returns n which is 1 or 0. Then, we create an array with 0 and 1 and iterate from 2 till n+1 so that we go from bottom to up. After recursive calculation of Fibonacci numbers we append them to an array and return the array.
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
