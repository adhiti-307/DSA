# 📘 Patterns & Tricks in DSA

---

## 🔥 Why Patterns Matter

Most DSA problems are **not new**—they follow **repeatable patterns**.

👉 If you recognize the pattern:

* You solve faster
* You avoid brute force
* You reduce mistakes

---

# 🔹 1. Two Pointer Technique

## 📌 When to Use:

* Array is **sorted**
* Need **pairs / subarrays**
* Reduce time from O(n²) → O(n)

---

## ✅ Template

```java
int left = 0, right = n - 1;

while(left < right){
    int sum = arr[left] + arr[right];

    if(sum == target){
        // found
        break;
    } else if(sum < target){
        left++;
    } else {
        right--;
    }
}
```

---

## 💡 Use Cases:

* Two Sum (sorted)
* Remove duplicates
* Container with most water

---

# 🔹 2. Sliding Window

## 📌 When to Use:

* Subarray / substring problems
* Contiguous range

---

## ✅ Fixed Window

```java
int windowSum = 0;

for(int i = 0; i < k; i++){
    windowSum += arr[i];
}

for(int i = k; i < n; i++){
    windowSum += arr[i];
    windowSum -= arr[i - k];
}
```

---

## ✅ Variable Window

```java
int left = 0, sum = 0;

for(int right = 0; right < n; right++){
    sum += arr[right];

    while(sum > target){
        sum -= arr[left];
        left++;
    }
}
```

---

## 💡 Use Cases:

* Longest substring
* Max sum subarray of size k

---

# 🔹 3. Prefix Sum

## 📌 When to Use:

* Range sum queries
* Repeated sum calculations

---

## ✅ Template

```java
int[] prefix = new int[n];
prefix[0] = arr[0];

for(int i = 1; i < n; i++){
    prefix[i] = prefix[i-1] + arr[i];
}
```

---

## 💡 Query

```java
sum(l, r) = prefix[r] - prefix[l-1]
```

---

# 🔹 4. Binary Search Pattern

## 📌 When to Use:

* Sorted array
* Searching efficiently

---

## ✅ Template

```java
int low = 0, high = n - 1;

while(low <= high){
    int mid = low + (high - low) / 2;

    if(arr[mid] == target) return mid;
    else if(arr[mid] < target) low = mid + 1;
    else high = mid - 1;
}
```

---

## 🔥 Binary Search on Answer

👉 Instead of searching value → search **answer range**

---

## 💡 Example:

* Minimum speed
* Maximum distance
* Allocate books

---

# 🔹 5. Fast & Slow Pointer

## 📌 When to Use:

* Linked List
* Cycle detection

---

## ✅ Template

```java
ListNode slow = head;
ListNode fast = head;

while(fast != null && fast.next != null){
    slow = slow.next;
    fast = fast.next.next;

    if(slow == fast){
        // cycle exists
    }
}
```

---

## 💡 Use Cases:

* Detect cycle
* Find middle node

---

# 🔹 6. Greedy Pattern

## 📌 When to Use:

* Local optimal → global optimal

---

## 💡 Strategy:

* Sort data
* Pick best option at each step

---

## 💡 Examples:

* Activity selection
* Fractional knapsack

---

# 🔹 7. Backtracking Pattern

## 📌 When to Use:

* All combinations / permutations

---

## ✅ Template

```java
void solve(){
    if(base case){
        return;
    }

    for(choices){
        // choose
        solve();
        // undo (backtrack)
    }
}
```

---

## 💡 Examples:

* N-Queens
* Sudoku
* Subsets

---

# 🔹 8. Recursion Pattern

## 📌 Key Idea:

Break problem into smaller parts

---

## ✅ Structure

```java
function(n){
    if(base case) return;

    return function(n-1);
}
```

---

# 🔹 9. Hashing Pattern

## 📌 When to Use:

* Frequency count
* Fast lookup

---

## ✅ Template

```java
HashMap<Integer, Integer> map = new HashMap<>();

for(int x : arr){
    map.put(x, map.getOrDefault(x, 0) + 1);
}
```

---

## 💡 Use Cases:

* Two Sum
* Duplicate detection

---

# 🔹 10. Monotonic Stack

## 📌 When to Use:

* Next greater / smaller element

---

## ✅ Template

```java
Stack<Integer> st = new Stack<>();

for(int i = 0; i < n; i++){
    while(!st.isEmpty() && arr[st.peek()] < arr[i]){
        st.pop();
    }
    st.push(i);
}
```

---

## 💡 Use Cases:

* Stock span
* Largest rectangle in histogram

---

# 🔹 11. Dynamic Programming Pattern

## 📌 When to Use:

* Overlapping subproblems
* Optimization problems

---

## 💡 Steps:

```text
1. Define state  
2. Define transition  
3. Base case  
4. Build solution  
```

---

# 🔹 12. Divide & Conquer

## 📌 When to Use:

* Break → solve → merge

---

## 💡 Examples:

* Merge Sort
* Quick Sort

---

# 🔥 13. Common Tricks

## ✅ Trick 1: Use modulo

```java
result = (a + b) % mod;
```

---

## ✅ Trick 2: Avoid overflow

```java
int mid = low + (high - low) / 2;
```

---

## ✅ Trick 3: Swap without temp

```java
a = a ^ b;
b = a ^ b;
a = a ^ b;
```

---

## ✅ Trick 4: Check even/odd

```java
if((n & 1) == 0)
```

---

# 🧠 Pattern Recognition Guide

```text
Sorted array → Binary Search / Two Pointer  
Subarray → Sliding Window / Prefix Sum  
Combinations → Backtracking  
Optimization → DP / Greedy  
Graph traversal → BFS / DFS  
```

---

# 🚀 Final Advice

```text
Don’t memorize problems  
Memorize patterns  
```

👉 Same pattern appears in multiple questions.

---

# 🔥 Golden Rule

```text
Identify pattern → apply template → optimize
```

---
