# 📘 Stack & Queue – Complete Notes

---

# 🔹 1. Stack (LIFO)

A Stack is a linear data structure that follows:

```text
Last In → First Out (LIFO)
```

---

## 🔸 Example

```text id="st1"
Push: 10 → 20 → 30

Stack (top at right):
[10   20   30]

Pop → removes 30
[10   20]
```

---

# 🔹 2. Stack Operations

| Operation | Description     | Time |
| --------- | --------------- | ---- |
| push()    | Insert element  | O(1) |
| pop()     | Remove top      | O(1) |
| peek()    | Get top element | O(1) |
| isEmpty() | Check empty     | O(1) |

---

## 🔸 Implementation (Using Stack Class)

```java id="stk1"
Stack<Integer> st = new Stack<>();

st.push(10);
st.push(20);
st.pop();
st.peek();
```

---

## 🔸 Implementation (Using Array)

```java id="stk2"
int[] stack = new int[n];
int top = -1;

top++;
stack[top] = x;

int val = stack[top];
top--;
```

---

# 🔹 3. Important Stack Patterns

---

## 🔸 3.1 Balanced Parentheses

```java id="stk3"
Stack<Character> st = new Stack<>();

for(char c : s.toCharArray()){
    if(c == '(') st.push(c);
    else{
        if(st.isEmpty()) return false;
        st.pop();
    }
}
```

---

## 🔸 3.2 Next Greater Element

```java id="stk4"
Stack<Integer> st = new Stack<>();

for(int i = n-1; i >= 0; i--){
    while(!st.isEmpty() && st.peek() <= arr[i]){
        st.pop();
    }
    st.push(arr[i]);
}
```

---

## 🔸 3.3 Monotonic Stack

```text id="stmono"
Maintains increasing or decreasing order
Used for:
- Next greater/smaller element
- Histogram problems
```

---

## 🔸 3.4 Expression Evaluation

* Infix → Postfix
* Postfix evaluation

---

# 🔹 4. Queue (FIFO)

A Queue follows:

```text
First In → First Out (FIFO)
```

---

## 🔸 Example

```text id="q1"
Insert: 10 → 20 → 30

Queue:
Front → [10   20   30] ← Rear

Dequeue → removes 10
Front → [20   30]
```

---

# 🔹 5. Queue Operations

| Operation         | Description   | Time |
| ----------------- | ------------- | ---- |
| add() / offer()   | Insert        | O(1) |
| remove() / poll() | Remove        | O(1) |
| peek()            | Front element | O(1) |

---

## 🔸 Implementation

```java id="q2"
Queue<Integer> q = new LinkedList<>();

q.add(10);
q.add(20);

q.poll();
q.peek();
```

---

# 🔹 6. Types of Queue

---

## 🔸 6.1 Simple Queue

Basic FIFO structure

---

## 🔸 6.2 Circular Queue

```text id="cq1"
Reuses empty space

[1   2   3   _   _]
          ↑ reuse from front
```

---

## 🔸 6.3 Deque (Double Ended Queue)

```text id="dq1"
Insert/remove from both ends
```

```java id="dq2"
Deque<Integer> dq = new ArrayDeque<>();

dq.addFirst(10);
dq.addLast(20);
dq.removeFirst();
dq.removeLast();
```

---

## 🔸 6.4 Priority Queue (Heap)

```text id="pq1"
Elements processed based on priority
```

```java id="pq2"
PriorityQueue<Integer> pq = new PriorityQueue<>();

pq.add(5);
pq.add(1);
pq.add(3);
```

---

# 🔹 7. Queue Using Stack

```java id="q3"
Stack<Integer> s1 = new Stack<>();
Stack<Integer> s2 = new Stack<>();

void push(int x){
    s1.push(x);
}

int pop(){
    if(s2.isEmpty()){
        while(!s1.isEmpty()){
            s2.push(s1.pop());
        }
    }
    return s2.pop();
}
```

---

# 🔹 8. Time Complexity Summary

| Structure      | Operation     | Complexity |
| -------------- | ------------- | ---------- |
| Stack          | push/pop      | O(1)       |
| Queue          | add/remove    | O(1)       |
| Deque          | both ends     | O(1)       |
| Priority Queue | insert/remove | O(log n)   |

---

# 🔹 9. Common Problems

* Balanced Parentheses
* Next Greater Element
* Stock Span
* Sliding Window Maximum
* Implement Queue using Stack
* BFS (Queue usage)

---

# 🔹 10. Common Mistakes

```text id="miststq"
❌ Stack underflow (empty pop)  
❌ Queue overflow  
❌ Wrong push/pop order  
❌ Not checking empty condition  
```

---

# 🔹 11. Interview Tips

```text id="tipstq"
✔ Stack → LIFO problems  
✔ Queue → BFS / ordering problems  
✔ Use Deque for sliding window  
✔ Use PriorityQueue for sorting-like behavior  
```

---

# 🧠 Quick Revision

```text id="revstq"
Stack → LIFO  
Queue → FIFO  
Deque → both ends  
PriorityQueue → heap  
```

---

# 🔥 Final Insight

```text id="finstq"
Stack = reverse behavior  
Queue = ordered processing  
```

👉 Choose based on problem requirement

---
