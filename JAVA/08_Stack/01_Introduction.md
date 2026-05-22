# Stack in Java - Introduction

## What is a Stack?

A Stack is a linear data structure that follows the **LIFO (Last In First Out)** principle.

- The last inserted element is removed first.
- Similar to a stack of plates.

---

## Real Life Examples

- Browser history
- Undo/Redo operations
- Function call stack
- Expression evaluation

---

## Basic Operations

| Operation | Description |
|---|---|
| push() | Insert element |
| pop() | Remove top element |
| peek() | Get top element |
| isEmpty() | Check if stack is empty |
| size() | Number of elements |

---

## Stack Using Java Collections Framework

Java provides a built-in `Stack` class inside:

```java
import java.util.Stack;
```

---

## Creating a Stack

```java
Stack<Integer> stack = new Stack<>();
```

---

## Push Operation

```java
stack.push(10);
stack.push(20);
stack.push(30);
```

Stack:

```text
30
20
10
```

---

## Pop Operation

```java
stack.pop();
```

Removes:

```text
30
```

---

## Peek Operation

```java
stack.peek();
```

Returns top element without removing it.

---

## isEmpty()

```java
stack.isEmpty();
```

Returns:
- `true` if empty
- `false` otherwise

---

## Complete Example

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Stack<Integer> stack = new Stack<>();

        stack.push(10);
        stack.push(20);
        stack.push(30);

        System.out.println(stack);

        System.out.println(stack.peek());

        System.out.println(stack.pop());

        System.out.println(stack);

        System.out.println(stack.isEmpty());
    }
}
```

---

## Time Complexity

| Operation | Complexity |
|---|---|
| push | O(1) |
| pop | O(1) |
| peek | O(1) |

---

## Important Notes

- `Stack` class is legacy.
- `Deque` is preferred in modern Java.
- Still widely used in coding interviews.

