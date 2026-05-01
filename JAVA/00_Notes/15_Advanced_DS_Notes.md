# 📘 Advanced Data Structures – Complete Notes

---

# 🔹 1. Why Advanced Data Structures?

Basic DS (Array, List, Stack, Queue) are not always efficient for:

* Range queries
* Dynamic updates
* Complex relationships

👉 Advanced DS helps optimize such problems

---

# 🔹 2. Segment Tree

---

## 🔸 What is Segment Tree?

A tree used for:

```text id="ads1"
Range Query + Point Update
```

---

## 🔸 Example

```text id="ads2"
Array: [1, 3, 5, 7]

Query → sum(1,3) = 3 + 5 + 7
```

---

## 🔸 Structure

```text id="ads3"
Each node stores range info
```

---

## 🔸 Operations

| Operation | Time     |
| --------- | -------- |
| Build     | O(n)     |
| Query     | O(log n) |
| Update    | O(log n) |

---

## 🔸 Code (Core Idea)

```java id="ads4"
int query(int node, int start, int end, int l, int r){
    if(r < start || end < l) return 0;

    if(l <= start && end <= r){
        return tree[node];
    }

    int mid = (start + end)/2;
    return query(2*node+1, start, mid, l, r) +
           query(2*node+2, mid+1, end, l, r);
}
```

---

# 🔹 3. Fenwick Tree (Binary Indexed Tree)

---

## 🔸 What is BIT?

Efficient for:

```text id="ads5"
Prefix sum + updates
```

---

## 🔸 Time Complexity

| Operation | Time     |
| --------- | -------- |
| Update    | O(log n) |
| Query     | O(log n) |

---

## 🔸 Code

```java id="ads6"
void update(int i, int val){
    while(i <= n){
        bit[i] += val;
        i += i & -i;
    }
}

int query(int i){
    int sum = 0;
    while(i > 0){
        sum += bit[i];
        i -= i & -i;
    }
    return sum;
}
```

---

# 🔹 4. Trie (Prefix Tree)

---

## 🔸 What is Trie?

Used for:

```text id="ads7"
Strings + prefix search
```

---

## 🔸 Structure

```text id="ads8"
Each node has 26 children (for lowercase)
```

---

## 🔸 Code

```java id="ads9"
class TrieNode {
    TrieNode[] children = new TrieNode[26];
    boolean isEnd;
}
```

---

## 🔸 Operations

* Insert
* Search
* StartsWith

---

# 🔹 5. Disjoint Set (Union-Find)

---

## 🔸 Use Cases

```text id="ads10"
Connectivity  
Cycle detection  
```

---

## 🔸 Code

```java id="ads11"
int find(int x){
    if(parent[x] != x){
        parent[x] = find(parent[x]);
    }
    return parent[x];
}
```

---

## 🔸 Optimization

```text id="ads12"
Path Compression  
Union by Rank  
```

---

# 🔹 6. LRU Cache

---

## 🔸 What is LRU?

```text id="ads13"
Least Recently Used removal
```

---

## 🔸 Implementation

* HashMap + Doubly Linked List

---

## 🔸 Complexity

```text id="ads14"
Get → O(1)  
Put → O(1)
```

---

# 🔹 7. Sparse Table

---

## 🔸 Use Case

```text id="ads15"
Static range queries (RMQ)
```

---

## 🔸 Time Complexity

| Operation | Time       |
| --------- | ---------- |
| Build     | O(n log n) |
| Query     | O(1)       |

---

# 🔹 8. Heavy Light Decomposition (HLD)

---

## 🔸 Use Case

```text id="ads16"
Tree queries optimization
```

---

## 🔸 Idea

```text id="ads17"
Break tree into chains
Use segment tree
```

---

# 🔹 9. Important Comparisons

| DS           | Best For                |
| ------------ | ----------------------- |
| Segment Tree | Range queries + updates |
| Fenwick Tree | Prefix sums             |
| Trie         | Strings                 |
| Union-Find   | Connectivity            |
| Sparse Table | Static queries          |
| LRU Cache    | Caching                 |

---

# 🔹 10. Common Problems

* Range Sum Query
* Kth Smallest Element
* Prefix Search
* Cycle Detection
* Network Connectivity
* Auto-complete

---

# 🔹 11. Common Mistakes

```text id="ads18"
❌ Wrong indexing (0 vs 1-based)  
❌ Forgetting updates  
❌ Overusing advanced DS  
```

---

# 🔹 12. Interview Tips

```text id="ads19"
✔ Use Segment Tree for dynamic range  
✔ Use BIT for prefix sums  
✔ Use Trie for strings  
✔ Use DSU for connectivity  
✔ Choose simplest DS first  
```

---

# 🧠 Quick Revision

```text id="ads20"
Segment Tree → range queries  
Fenwick → prefix sums  
Trie → strings  
DSU → connectivity  
```

---

# 🔥 Final Insight

```text id="ads21"
Advanced DS = optimization tools
```

👉 Use only when basic DS fails

---
