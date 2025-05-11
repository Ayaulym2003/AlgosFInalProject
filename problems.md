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

Hint 1: Think about how you can compute F(n) by knowing F(n-1) and F(n-2).

Hint 2: Try not to repeat yourself and recompute the same numbers many times. Try storing already computed numbers in one list. 

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
</pre>

# Problem 2: Climbing Stairs
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

Hint 1: Think about how you can reach selected stair and try to memorize the ways for future use.

Hint 2: Try to use Dynamic Programming bottom-up approach. Calculate from the bottom to upper stairs. 

## 🔹 Brute Force Idea

This problem is just like Fibonacci numbers. A person can reach nth stair either from (n-1)th stair or (n-2)th stair. Thus, for each stair n, we calculate the number of ways to reach the (n-1)th and (n-2)th stairs, and add them to get the total number of ways to reach the nth stair. This gives us the following recurrence relation:   
countWays(n) = countWays(n-1) + countWays(n-2)

## 🔹 Optimized Idea

We can optimize the idea by adding Dynamic programming. Tabulation approach iteratively builds up the solution by calculating stairs from the bottom up. In the this approach, a function with 1 parameter, n, is created. We create an array to store all ways to reach
nth stair and set the first 2 elements as 1, because there is one way to reach the first stair and one way to stay on the ground. The, to fill the array, we iterate through array from 2nd stair till the end, and store the sum of (n-1)th and (n-2)th values in nth cell. For example, we have [1,1,0,0] and to reach 3rd stair person can move from 1st 2 steps and from 2nd stair 1 step, so it is 2 ways to reach the 3rd step. 

## 🔹 Code Fragment
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

# Problem 3: Longest Common Subsequence (LCS)
Problem Statement
Given two strings, s1 and s2, the task is to find the length of the Longest Common Subsequence. If there is no common subsequence, return 0. A subsequence is a string generated from the original string by deleting 0 or more characters, without changing the relative order of the remaining characters.

For example, subsequences of “ABC” are “”, “A”, “B”, “C”, “AB”, “AC”, “BC” and “ABC”. In general, a string of length n has 2n subsequences.

Example:

Input: s1 = “ABC”, s2 = “ACD”  
Output: 2  
Explanation: The longest subsequence which is present in both strings is “AC”.  

Input: s1 = “AGGTAB”, s2 = “GXTXAYB”  
Output: 4  
Explanation: The longest common subsequence is “GTAB”.  

## 🔹 Hints

Hint 1: Use 2D list, count the number of matches and store them in a list. 

Hint 2: If the last letter of the strings match, store them and go to next 2 letters. If they do not match, skip one of them and compare with the next one. 

## 🔹 Brute Force Idea

The basic idea is to compare two strings, s1 and s2. There can be two cases:

- If the substrings match, recall the function with m-1 and n-1 substrings where m and n are the lengths of the strings.
- If the substrings does not match, recall the function 2 times with m-1 and n substrings and m and n-1.

If both strings are empty return 0.

<pre>
def lcsRec(s1, s2, m, n):
    if m == 0 or n == 0:
        return 0

    if s1[m - 1] == s2[n - 1]:
        return 1 + lcsRec(s1, s2, m - 1, n - 1)

    else:
        return max(lcsRec(s1, s2, m, n - 1), lcsRec(s1, s2, m - 1, n))

def lcs(s1,s2):
    m = len(s1)
    n = len(s2)
    return lcsRec(s1,s2,m,n)
</pre>

## 🔹 Optimized Idea

We can optimize the idea by adding Dynamic programming. 

There are two parameters that change in the recursive solution and these parameters go from 0 to m and 0 to n. So we create a 2D dp array of size (m+1) x (n+1).  

- We first fill the known entries when m is 0 or n is 0.
- Then we fill the remaining entries using the recursive formula.

## 🔹 Code Fragment
<pre>
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if S1[i - 1] == S2[j - 1]:
                dp[i][j] = dp[i - 1][j - 1] + 1
            else:
                dp[i][j] = max(dp[i - 1][j],
                               dp[i][j - 1])

    return dp[m][n]
</pre>
