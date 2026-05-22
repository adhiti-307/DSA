# Implement Two Stacks in an Array

## Problem Statement

Create a data structure `twoStacks` that represents **two stacks using only one array**.

Both stacks should share the same array efficiently.

---

# Functions Supported

```text id="txjlwm"
push1(int x)  -> Push element into first stack
push2(int x)  -> Push element into second stack
pop1()        -> Pop element from first stack
pop2()        -> Pop element from second stack
```

---

# Idea

Use:

* one pointer from left side for Stack 1
* one pointer from right side for Stack 2

```text id="6jlwm9"
Stack1 --> <-- Stack2
```

Both stacks grow toward each other.

---

# Visualization

Array size = 10

```text id="psuzgm"
Index:
0 1 2 3 4 5 6 7 8 9

Stack1 grows →
Stack2 grows ←
```

---

# Initialization

```java id="zjlwm8"
top1 = -1
top2 = size
```

---

# Overflow Condition

When:

```java id="3jlwm1"
top1 + 1 == top2
```

No space remains.

---

# Java Implementation

```java id="jlwm92"
class TwoStacks {

    int[] arr;
    int size;

    int top1;
    int top2;

    TwoStacks(int n) {

        size = n;

        arr = new int[n];

        top1 = -1;
        top2 = n;
    }

    // Push into Stack 1
    void push1(int x) {

        if (top1 + 1 == top2) {

            System.out.println("Stack Overflow");
            return;
        }

        arr[++top1] = x;
    }

    // Push into Stack 2
    void push2(int x) {

        if (top1 + 1 == top2) {

            System.out.println("Stack Overflow");
            return;
        }

        arr[--top2] = x;
    }

    // Pop from Stack 1
    int pop1() {

        if (top1 == -1) {

            System.out.println("Stack 1 Underflow");
            return -1;
        }

        return arr[top1--];
    }

    // Pop from Stack 2
    int pop2() {

        if (top2 == size) {

            System.out.println("Stack 2 Underflow");
            return -1;
        }

        return arr[top2++];
    }
}
```

---

# Example

```java id="jlwm1k"
TwoStacks ts = new TwoStacks(10);

ts.push1(1);
ts.push1(2);

ts.push2(100);
ts.push2(200);

System.out.println(ts.pop1()); // 2
System.out.println(ts.pop2()); // 200
```

---

# Dry Run

After operations:

```java id="jlwmx2"
push1(1)
push1(2)
push2(100)
push2(200)
```

Array:

```text id="jlwmf3"
[1, 2, _, _, _, _, _, _, 200, 100]
```

---

# Complexity

| Operation | Complexity |
| --------- | ---------- |
| push1     | O(1)       |
| push2     | O(1)       |
| pop1      | O(1)       |
| pop2      | O(1)       |

---

# Advantages

* Better space utilization
* No fixed partition needed
* Both stacks dynamically share space

---

# Important Interview Points

* Both stacks grow toward each other.
* Overflow occurs only when pointers meet.
* Much more memory efficient than dividing array into halves.

---

# Related Problems

* Stack using Array
* Min Stack
* N Stacks in One Array
* Implement Queue using Stacks
* Implement Stack using Queues

---

# Related LeetCode

[Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/?utm_source=chatgpt.com)
