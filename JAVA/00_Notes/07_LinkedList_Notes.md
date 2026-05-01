# 📘 Linked List – Complete Notes

---

# 🔹 1. What is a Linked List?

A Linked List is a **linear data structure** where elements (nodes) are connected using **pointers (references)** instead of contiguous memory.

---

## 📊 Visualization (Singly Linked List)

![Image](https://images.openai.com/static-rsc-4/GxZdx6d3Kelg2yN2BK5fRI2SFpVa9jdqa3Vj-0sjXSToyQ8WNJsr_sSskTQrTb5TZQSmB82UOPi1qPJiRPxcU6MrRrE-dkps0YBJPmR1ATZe3grt6jLmbh5TZB1Rhp2pWgp6CzSmcZSR2jxuhGn8viDe6gcShHEQ5NyUuUsKMPljvZr2xpYnPfvsALM_BDyK?purpose=fullsize)

```text id="l1viz1"
[10 | next] → [20 | next] → [30 | next] → null
```

---

# 🔹 2. Structure of Node

```java id="nodecls1"
class Node {
    int data;
    Node next;

    Node(int data){
        this.data = data;
        this.next = null;
    }
}
```

---

# 🔹 3. Types of Linked Lists

---

## 🔸 3.1 Singly Linked List

Each node points to the next node.

---

## 🔸 3.2 Doubly Linked List

Each node has two pointers:

* prev → previous node
* next → next node

---

## 🔸 3.3 Circular Linked List

Last node points back to the head.

---

## 📊 Visualization (Doubly & Circular)

![Image](https://images.openai.com/static-rsc-4/j8nLkO1lFe1Gc2Zw9q2mjQ-U4POKxAqJn3gvxxTuY_sGaqaEK9HAA_0RfRi0uV2ZIEHGyDEZx0a2c6rPJKxcUpWC6mDhwrEzglVJ4FcmVrhQEuJH7lXXcyLVWUgBfdIm_gCV1OzdEduCra6SC-lFQgxjD-7WTZ7sDzCFUYt-8iouhGDFOyZfws8eHym9KVaZ?purpose=fullsize)

---

# 🔹 4. Basic Operations

---

## 🔸 4.1 Traversal

```java id="trav1"
Node temp = head;

while(temp != null){
    System.out.print(temp.data + " ");
    temp = temp.next;
}
```

---

## 🔸 4.2 Insertion

### 👉 At Beginning

```java id="insbeg1"
Node newNode = new Node(val);
newNode.next = head;
head = newNode;
```

---

### 👉 At End

```java id="insend1"
Node temp = head;

while(temp.next != null){
    temp = temp.next;
}

temp.next = new Node(val);
```

---

### 👉 At Position

```java id="inspos1"
Node temp = head;

for(int i = 0; i < pos - 1; i++){
    temp = temp.next;
}

Node newNode = new Node(val);
newNode.next = temp.next;
temp.next = newNode;
```

---

## 🔸 4.3 Deletion

### 👉 From Beginning

```java id="delbeg1"
head = head.next;
```

---

### 👉 From End

```java id="delend1"
Node temp = head;

while(temp.next.next != null){
    temp = temp.next;
}

temp.next = null;
```

---

### 👉 From Position

```java id="delpos1"
Node temp = head;

for(int i = 0; i < pos - 1; i++){
    temp = temp.next;
}

temp.next = temp.next.next;
```

---

# 🔹 5. Important Patterns

---

## 🔸 5.1 Reverse Linked List

### 📊 Visualization

---

### ✅ Code

```java id="revll1"
Node prev = null;
Node curr = head;

while(curr != null){
    Node next = curr.next;
    curr.next = prev;

    prev = curr;
    curr = next;
}

head = prev;
```

---

## 🔸 5.2 Fast & Slow Pointer

Used to find:

* Middle node
* Cycle detection

---

### 📊 Visualization

![Image](https://images.openai.com/static-rsc-4/6vmcStpNPpU7tW6eR9xfse3hyUYi6ZiYAiWHaSfnNzpOyn18A_1qNHrahydceimYZgz7FuzzQp7Bzq9FWnvzIfdpu8MEGSYuJBWzhNpSRbOnZFLhHuMuu4AYek1GqqRY9hKDIv2F4zAg6WMSb3CzEzfJ_6O3rHKM50UxXGwR1If879jHmNTwaoss7fYileky?purpose=fullsize)

---

### ✅ Code

```java id="fastslow1"
Node slow = head;
Node fast = head;

while(fast != null && fast.next != null){
    slow = slow.next;
    fast = fast.next.next;
}
```

---

## 🔸 5.3 Cycle Detection (Floyd’s Algorithm)

```java id="cycle1"
Node slow = head;
Node fast = head;

while(fast != null && fast.next != null){
    slow = slow.next;
    fast = fast.next.next;

    if(slow == fast){
        return true;
    }
}
return false;
```

---

# 🔹 6. Time Complexity

| Operation        | Complexity |
| ---------------- | ---------- |
| Access           | O(n)       |
| Insertion (head) | O(1)       |
| Insertion (end)  | O(n)       |
| Deletion         | O(n)       |

---

# 🔹 7. Advantages

```text id="advll1"
✔ Dynamic size  
✔ Efficient insertion/deletion  
✔ No memory wastage  
```

---

# 🔹 8. Disadvantages

```text id="disll1"
❌ No random access  
❌ Extra memory for pointers  
❌ Traversal is slow  
```

---

# 🔹 9. Common Problems

* Reverse Linked List
* Detect Cycle
* Find Middle
* Merge Two Lists
* Remove Nth Node
* Intersection of Lists

---

# 🔹 10. Common Mistakes

```text id="mistll1"
❌ Losing reference of head  
❌ Null pointer exceptions  
❌ Incorrect pointer updates  
❌ Infinite loops  
```

---

# 🔹 11. Interview Tips

```text id="tipll1"
✔ Always draw diagram  
✔ Track prev, curr, next carefully  
✔ Use slow-fast pointer when needed  
✔ Handle edge cases (empty, single node)  
```

---

# 🧠 Quick Revision

```text id="revll2"
Linked List → nodes + pointers  
Reverse → change direction  
Fast/Slow → middle & cycle  
Insertion → pointer update  
```

---

# 🔥 Final Insight

```text id="finll1"
Linked List = pointer manipulation
```

👉 Master pointer handling → you master linked lists

---
