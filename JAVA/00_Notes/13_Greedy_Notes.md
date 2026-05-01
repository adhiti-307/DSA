# 📘 Greedy Algorithms – Complete Notes

---

# 🔹 1. What is Greedy?

A Greedy algorithm makes the **best choice at the current step** with the hope of reaching a global optimum.

```text id="gr1"
Local Optimal Choice → Global Optimal Solution
```

---

# 🔹 2. When to Use Greedy?

Greedy works when:

```text id="gr2"
1. Greedy Choice Property  
2. Optimal Substructure  
```

👉 If choosing the best at each step leads to optimal solution → use greedy

---

# 🔹 3. Key Idea

```text id="gr3"
Sort → Pick → Move forward
```

👉 Most greedy problems involve **sorting first**

---

# 🔹 4. Common Greedy Patterns

---

## 🔸 4.1 Activity Selection

👉 Select maximum non-overlapping intervals

---

### ✅ Approach

```text id="gr4"
Sort by end time  
Pick first activity  
Select next with start ≥ previous end  
```

---

### ✅ Code

```java id="gr5"
Arrays.sort(arr, (a, b) -> a[1] - b[1]);

int count = 1;
int end = arr[0][1];

for(int i = 1; i < n; i++){
    if(arr[i][0] >= end){
        count++;
        end = arr[i][1];
    }
}
```

---

## 🔸 4.2 Fractional Knapsack

👉 Take items with highest value/weight ratio

---

### ✅ Approach

```text id="gr6"
Sort by value/weight ratio  
Take full items  
Take fraction if needed  
```

---

---

## 🔸 4.3 Minimum Coins

👉 Use largest denomination first

---

```text id="gr7"
Example: 121 → 100 + 20 + 1
```

---

## 🔸 4.4 Job Sequencing

👉 Maximize profit within deadlines

---

```text id="gr8"
Sort jobs by profit  
Assign to latest available slot  
```

---

## 🔸 4.5 Huffman Coding

👉 Minimize encoding length

---

```text id="gr9"
Use min heap  
Combine smallest frequencies  
```

---

# 🔹 5. Greedy vs DP

| Feature  | Greedy             | DP                  |
| -------- | ------------------ | ------------------- |
| Approach | Local choice       | Global optimization |
| Speed    | Fast               | Slower              |
| Accuracy | Not always correct | Always correct      |
| Example  | Activity selection | Knapsack            |

---

# 🔹 6. Important Problems

* Activity Selection
* Fractional Knapsack
* Coin Change (Greedy version)
* Job Scheduling
* Minimum Platforms
* Gas Station Problem

---

# 🔹 7. Time Complexity

```text id="gr10"
Mostly dominated by sorting → O(n log n)
```

---

# 🔹 8. Common Mistakes

```text id="gr11"
❌ Applying greedy where it doesn't work  
❌ Not sorting properly  
❌ Ignoring constraints  
```

---

# 🔹 9. How to Identify Greedy Problems

```text id="gr12"
✔ Problem asks for maximum/minimum  
✔ Choices are independent  
✔ No need to revisit previous decisions  
✔ Sorting helps  
```

---

# 🔹 10. Example Walkthrough

## Activity Selection

```text id="gr13"
Start: [1, 3, 0, 5, 8, 5]  
End:   [2, 4, 6, 7, 9, 9]

After sorting by end:

[1,2] → pick  
[3,4] → pick  
[5,7] → pick  
[8,9] → pick  

Total = 4 activities
```

---

# 🔹 11. Interview Tips

```text id="gr14"
✔ Always try greedy first (simple)  
✔ Verify with counterexample  
✔ If fails → switch to DP  
✔ Sorting is key  
```

---

# 🧠 Quick Pattern Guide

```text id="gr15"
Intervals → Activity selection  
Ratios → Knapsack  
Deadlines → Job scheduling  
Coins → Greedy coin change  
```

---

# 🧠 Quick Revision

```text id="gr16"
Greedy → choose best now  
Sort → important  
Works only when optimal structure exists  
```

---

# 🔥 Final Insight

```text id="gr17"
Greedy is fast but risky
```

👉 Always validate before using

---
