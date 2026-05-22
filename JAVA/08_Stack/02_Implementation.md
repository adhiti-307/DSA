# Stack in Java - Implementation

## Stack Using Array

```java
class StackArray {

    int[] arr;
    int top;
    int capacity;

    StackArray(int size) {
        arr = new int[size];
        capacity = size;
        top = -1;
    }

    void push(int x) {

        if (top == capacity - 1) {
            System.out.println("Stack Overflow");
            return;
        }

        arr[++top] = x;
    }

    int pop() {

        if (top == -1) {
            System.out.println("Stack Underflow");
            return -1;
        }

        return arr[top--];
    }

    int peek() {

        if (top == -1) {
            return -1;
        }

        return arr[top];
    }

    boolean isEmpty() {
        return top == -1;
    }
}
```

---

## Stack Using Linked List

```java
class Node {

    int data;
    Node next;

    Node(int data) {
        this.data = data;
    }
}

class StackLinkedList {

    Node top;

    void push(int x) {

        Node newNode = new Node(x);

        newNode.next = top;
        top = newNode;
    }

    int pop() {

        if (top == null) {
            return -1;
        }

        int val = top.data;
        top = top.next;

        return val;
    }

    int peek() {

        if (top == null) {
            return -1;
        }

        return top.data;
    }

    boolean isEmpty() {
        return top == null;
    }
}
```

---

## Stack Using Deque (Recommended)

```java
import java.util.*;

Deque<Integer> stack = new ArrayDeque<>();

stack.push(10);
stack.push(20);

System.out.println(stack.pop());
System.out.println(stack.peek());
```

---

## Applications of Stack

### 1. Balanced Parentheses

```java
import java.util.*;

public class Main {

    static boolean isBalanced(String s) {

        Stack<Character> st = new Stack<>();

        for (char ch : s.toCharArray()) {

            if (ch == '(' || ch == '{' || ch == '[') {
                st.push(ch);
            }
            else {

                if (st.isEmpty()) {
                    return false;
                }

                char top = st.pop();

                if ((ch == ')' && top != '(') ||
                    (ch == '}' && top != '{') ||
                    (ch == ']' && top != '[')) {

                    return false;
                }
            }
        }

        return st.isEmpty();
    }
}
```

---

## Monotonic Stack

Used in:
- Next Greater Element
- Largest Rectangle in Histogram
- Stock Span Problem

### Example

```java
Stack<Integer> st = new Stack<>();

for (int num : arr) {

    while (!st.isEmpty() && st.peek() < num) {
        st.pop();
    }

    st.push(num);
}
```

---

## Complexity

| Implementation | Push | Pop | Peek |
|---|---|---|---|
| Array | O(1) | O(1) | O(1) |
| Linked List | O(1) | O(1) | O(1) |

---

## Interview Tips

- Use `ArrayDeque` instead of `Stack` in production.
- Learn monotonic stack problems thoroughly.
- Understand recursion stack internally.
