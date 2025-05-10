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

# Snippet 5: House Robber
Each of the n houses that are constructed in a line has some money in it. A burglar wants to take money from these homes, but he is unable to do so from two residences that are next to one other. Finding the most money that can be stolen is the challenge at hand.
Here, create a dp array to store the maximum loot at each house and fill the dp array using the bottom-up approach.
<pre>
def maxLoot(hval):
    n = len(hval)
  
    dp = [0] * (n + 1)

    dp[0] = 0
    dp[1] = hval[0]

    for i in range(2, n + 1):
        dp[i] = max(hval[i - 1] + dp[i - 2], dp[i - 1])

    return dp[n]

hval = [6, 7, 1, 3, 8, 2, 4]
print(maxLoot(hval))

</pre>

# Snippet 6: Subset Sum Problem
The aim is to determine whether there is a subset of the supplied array whose sum equals the given sum given an array arr[] of non-negative integers and a value sum. 
So we will create a 2D array of size (n + 1) * (sum + 1) of type boolean. The state dp[i][j] will be true if there exists a subset of elements from arr[0 . . . i] with sum = ‘j’. This means that if the current element has a value greater than the ‘current sum value’ we will copy the answer for previous cases and if the current sum value is greater than the ‘ith’ element we will see if any of the previous states have already computed the sum= j OR any previous states computed a value ‘j – arr[i]’ which will solve our purpose.
<pre>
def isSubsetSum(arr, sum):
    n = len(arr)

    dp = [[False] * (sum + 1) for _ in range(n + 1)]

    for i in range(n + 1):
        dp[i][0] = True

    for i in range(1, n + 1):
        for j in range(1, sum + 1):
            if j < arr[i - 1]:
                
                dp[i][j] = dp[i - 1][j]
            else:
                
                dp[i][j] = dp[i - 1][j] or dp[i - 1][j - arr[i - 1]]

    return dp[n][sum]


if __name__ == "__main__":
    arr = [3, 34, 4, 12, 5, 2]
    sum_value = 9

    if isSubsetSum(arr, sum_value):
        print("True")
    else:
        print("False")

</pre>

# Snippet 7: Minimum perfect squares
Given a positive integer n, the task is to find the minimum number of squares that sum to n. A number can always be represented as a sum of squares of other numbers. Because 1 is a square number and we can always break any number as (1*1 + 1*1 + 1*1 + … ). 

Maintain a dp[] table such that dp[i] stores the minimum perfect squares that sum to i.


Base Case: For i = 0 and i = 1, dp[i] = i

Recursive Case: For i > 1, dp[i] = min( 1 + dp[i – x2] ), for all x such that x * x <= i.

 <pre>
def minSquares(n):

    dp = [0] * (n + 1)
    
    dp[0] = 0
    dp[1] = 1
    
    for i in range(2, n + 1):
        dp[i] = i
        for x in range(1, int(i**0.5) + 1):
            dp[i] = min(dp[i], 1 + dp[i - x * x])
    
    return dp[n]
  
if __name__ == "__main__":
    n = 6
    print(minSquares(n))
</pre>


# Snippet 8:Longest Common Subsequence (LCS)
Given two strings, s1 and s2, the task is to find the length of the Longest Common Subsequence. If there is no common subsequence, return 0. A subsequence is a string generated from the original string by deleting 0 or more characters, without changing the relative order of the remaining characters.


There are two parameters that change in the recursive solution and these parameters go from 0 to m and 0 to n. So we create a 2D dp array of size (m+1) x (n+1). 


We first fill the known entries when m is 0 or n is 0.
Then we fill the remaining entries using the recursive formula.

<pre>
def lcs(S1, S2):
    m = len(S1)
    n = len(S2)

    dp = [[0] * (n + 1) for x in range(m + 1)]

    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if S1[i - 1] == S2[j - 1]:
                dp[i][j] = dp[i - 1][j - 1] + 1
            else:
                dp[i][j] = max(dp[i - 1][j],
                               dp[i][j - 1])

    return dp[m][n]

if __name__ == "__main__":
    S1 = "AGGTAB"
    S2 = "GXTXAYB"
    print(lcs(S1, S2))

</pre>















