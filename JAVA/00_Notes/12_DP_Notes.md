# 📘 Dynamic Programming (DP) – Complete Notes

---

# 🔹 1. What is Dynamic Programming?

Dynamic Programming (DP) is an optimization technique used when:

```text id="dp1"
1. Problem has overlapping subproblems  
2. Problem has optimal substructure  
```

👉 Store results to avoid recomputation

---

# 🔹 2. Why DP?

```text id="dp2"
Recursion → repeated work  
DP → store & reuse results  
```

---

## 🔸 Example (Fibonacci)

```java id="dp3"
int fib(int n){
    if(n <= 1) return n;
    return fib(n-1) + fib(n-2);
}
```

👉 Time: **O(2ⁿ)** ❌

---

## 🔸 DP Optimization

```java id="dp4"
int[] dp = new int[n+1];

dp[0] = 0;
dp[1] = 1;

for(int i = 2; i <= n; i++){
    dp[i] = dp[i-1] + dp[i-2];
}
```

👉 Time: **O(n)** ✅

---

# 🔹 3. DP Approaches

---

## 🔸 3.1 Top-Down (Memoization)

```java id="dp5"
int[] dp = new int[n+1];
Arrays.fill(dp, -1);

int solve(int n){
    if(n <= 1) return n;

    if(dp[n] != -1) return dp[n];

    return dp[n] = solve(n-1) + solve(n-2);
}
```

---

## 🔸 3.2 Bottom-Up (Tabulation)

```java id="dp6"
int[] dp = new int[n+1];

dp[0] = 0;
dp[1] = 1;

for(int i = 2; i <= n; i++){
    dp[i] = dp[i-1] + dp[i-2];
}
```

---

# 🔹 4. How to Solve DP Problems

```text id="dp7"
1. Identify state  
2. Write recurrence relation  
3. Define base case  
4. Build solution  
```

---

# 🔹 5. Common DP Patterns

---

## 🔸 5.1 1D DP

```java id="dp8"
int[] dp = new int[n+1];

for(int i = 1; i <= n; i++){
    dp[i] = dp[i-1] + 1;
}
```

---

## 🔸 5.2 2D DP

```java id="dp9"
int[][] dp = new int[n][m];

for(int i = 0; i < n; i++){
    for(int j = 0; j < m; j++){
        dp[i][j] = 0;
    }
}
```

---

## 🔸 5.3 Knapsack Pattern

```java id="dp10"
int[][] dp = new int[n+1][W+1];

for(int i = 1; i <= n; i++){
    for(int w = 0; w <= W; w++){
        if(weight[i-1] <= w){
            dp[i][w] = Math.max(
                value[i-1] + dp[i-1][w-weight[i-1]],
                dp[i-1][w]
            );
        } else {
            dp[i][w] = dp[i-1][w];
        }
    }
}
```

---

## 🔸 5.4 Longest Increasing Subsequence (LIS)

```java id="dp11"
int[] dp = new int[n];
Arrays.fill(dp, 1);

for(int i = 0; i < n; i++){
    for(int j = 0; j < i; j++){
        if(arr[j] < arr[i]){
            dp[i] = Math.max(dp[i], dp[j] + 1);
        }
    }
}
```

---

## 🔸 5.5 Longest Common Subsequence (LCS)

```java id="dp12"
int[][] dp = new int[n+1][m+1];

for(int i = 1; i <= n; i++){
    for(int j = 1; j <= m; j++){
        if(s1.charAt(i-1) == s2.charAt(j-1)){
            dp[i][j] = 1 + dp[i-1][j-1];
        } else {
            dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
        }
    }
}
```

---

# 🔹 6. DP Visualization (Table Filling)

```text id="dp13"
Example: LCS Table

      ""  A  B  C
""    0   0  0  0
A     0   1  1  1
B     0   1  2  2
C     0   1  2  3
```

---

# 🔹 7. Space Optimization

```java id="dp14"
int prev = 0, curr = 1;

for(int i = 2; i <= n; i++){
    int temp = curr;
    curr = prev + curr;
    prev = temp;
}
```

---

# 🔹 8. Time Complexity

| Approach  | Complexity    |
| --------- | ------------- |
| Recursion | O(2ⁿ)         |
| DP        | O(n) or O(n²) |

---

# 🔹 9. Common Problems

* Fibonacci
* Climbing Stairs
* 0/1 Knapsack
* Longest Common Subsequence
* Longest Increasing Subsequence
* Edit Distance

---

# 🔹 10. Common Mistakes

```text id="dp15"
❌ Wrong state definition  
❌ Missing base case  
❌ Incorrect transitions  
❌ Overcomplicating solution  
```

---

# 🔹 11. Interview Tips

```text id="dp16"
✔ Always start with recursion  
✔ Convert to memoization  
✔ Then optimize to tabulation  
✔ Look for overlapping subproblems  
```

---

# 🧠 Pattern Recognition Guide

```text id="dp17"
Subsequence → LCS / LIS  
Optimization → Knapsack  
Counting ways → Fibonacci / DP  
Grid problems → 2D DP  
```

---

# 🧠 Quick Revision

```text id="dp18"
DP → store results  
Top-down → recursion + memo  
Bottom-up → iteration  
State → dp[i]  
```

---

# 🔥 Final Insight

```text id="dp19"
DP = Recursion + Memory
```

👉 If recursion is slow → use DP

---
