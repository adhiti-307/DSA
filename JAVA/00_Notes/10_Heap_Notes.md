# 📘 Heap (Priority Queue) – Complete Notes

---

# 🔹 1. What is a Heap?

A Heap is a **complete binary tree** that follows a specific property:

```text id="heap1"
Min Heap → parent ≤ children  
Max Heap → parent ≥ children  
```

---

# 🔹 2. Structure of Heap

Heaps are usually implemented using **arrays**

---

## 🔸 Array Representation

```text id="heap2"
Index:   0   1   2   3   4   5
Value:  10  20  30  40  50  60
```

---

## 🔸 Parent / Child Relation

```text id="heap3"
Parent(i)      = (i - 1) / 2  
Left Child(i)  = 2*i + 1  
Right Child(i) = 2*i + 2  
```

---

# 🔹 3. Types of Heap

---

## 🔸 3.1 Min Heap

```text id="minheap"
        10
       /  \
     20    30
    /  \
   40  50
```

👉 Smallest element at root

---

## 🔸 3.2 Max Heap

```text id="maxheap"
        50
       /  \
     40    30
    /  \
   10  20
```

👉 Largest element at root

---

# 🔹 4. Heap Operations

---

## 🔸 4.1 Insertion (Heapify Up)

```text id="heapins"
Step 1: Insert at last position  
Step 2: Compare with parent  
Step 3: Swap until heap property satisfied  
```

---

## 🔸 Example

```text id="heapins2"
Insert 5 into Min Heap

Before:
[10   20   30]

After insert:
[10   20   30   5]

Heapify Up:
[10   5   30   20]
[5   10   30   20]
```

---

## 🔸 4.2 Deletion (Heapify Down)

```text id="heapdel"
Step 1: Replace root with last element  
Step 2: Remove last element  
Step 3: Swap with smaller/larger child  
```

---

## 🔸 Example

```text id="heapdel2"
Remove root (Min Heap)

Before:
[5   10   30   20]

After replace:
[20   10   30]

Heapify Down:
[10   20   30]
```

---

# 🔹 5. Priority Queue in Java

---

## 🔸 Min Heap (Default)

```java id="pq1"
PriorityQueue<Integer> pq = new PriorityQueue<>();

pq.add(10);
pq.add(5);
pq.add(20);

pq.poll();  // removes smallest
```

---

## 🔸 Max Heap

```java id="pq2"
PriorityQueue<Integer> pq = new PriorityQueue<>(
    (a, b) -> b - a
);
```

---

# 🔹 6. Heap Sort

---

## 🔸 Steps

```text id="hs1"
1. Build heap  
2. Extract root  
3. Heapify  
```

---

## 🔸 Code (Conceptual)

```java id="hs2"
void heapify(int[] arr, int n, int i){
    int largest = i;
    int left = 2*i + 1;
    int right = 2*i + 2;

    if(left < n && arr[left] > arr[largest])
        largest = left;

    if(right < n && arr[right] > arr[largest])
        largest = right;

    if(largest != i){
        swap(arr, i, largest);
        heapify(arr, n, largest);
    }
}
```

---

# 🔹 7. Important Heap Problems

---

## 🔸 Top K Elements

```text id="heapk"
Use min heap of size k
```

---

## 🔸 Kth Largest Element

```text id="heapk2"
Maintain heap of size k
```

---

## 🔸 Merge K Sorted Arrays

```text id="heapmerge"
Use min heap
```

---

## 🔸 Sliding Window Maximum

```text id="heapwin"
Use max heap or deque
```

---

# 🔹 8. Time Complexity

| Operation  | Complexity |
| ---------- | ---------- |
| Insert     | O(log n)   |
| Delete     | O(log n)   |
| Peek       | O(1)       |
| Build Heap | O(n)       |

---

# 🔹 9. Common Mistakes

```text id="mistheap"
❌ Wrong parent/child index  
❌ Not maintaining heap property  
❌ Confusing min vs max heap  
```

---

# 🔹 10. Interview Tips

```text id="tipheap"
✔ Use heap for top-k problems  
✔ Prefer PriorityQueue in Java  
✔ Understand heapify process  
✔ Combine with greedy approach  
```

---

# 🧠 Quick Revision

```text id="revheap"
Heap → complete binary tree  
Min Heap → smallest at root  
Max Heap → largest at root  
PriorityQueue → heap implementation  
```

---

# 🔥 Final Insight

```text id="finheap"
Heap = efficient selection of min/max
```

👉 Use heap when:

* You need **top K elements**
* You need **frequent min/max**

---
