# Reverse a String Using Stack

## Problem Statement

Given a string `s`, reverse the string using a **Stack** data structure.

---

## Example

Input:

```text id="5o1tgn"
hello
```

Output:

```text id="y7c9ea"
olleh
```

---

# Approach

A Stack follows the **LIFO (Last In First Out)** principle.

### Idea

1. Push all characters into the stack.
2. Pop characters one by one.
3. The popped order forms the reversed string.

---

# Java Code

```java id="2kqx0t"
import java.util.*;

public class Solution {

    public static String reverseString(String s) {

        Stack<Character> st = new Stack<>();

        // Push characters into stack
        for (char ch : s.toCharArray()) {
            st.push(ch);
        }

        StringBuilder ans = new StringBuilder();

        // Pop characters
        while (!st.isEmpty()) {
            ans.append(st.pop());
        }

        return ans.toString();
    }

    public static void main(String[] args) {

        String s = "hello";

        System.out.println(reverseString(s));
    }
}
```

---

# Dry Run

Input:

```text id="jigbt9"
abc
```

### Step 1: Push into stack

```text id="ivjlwm"
Top
c
b
a
```

### Step 2: Pop elements

```text id="xb40ft"
c → b → a
```

Result:

```text id="o0gbo9"
cba
```

---

# Complexity

| Complexity | Value |
| ---------- | ----- |
| Time       | O(N)  |
| Space      | O(N)  |

---

# Optimized Version Using ArrayDeque

`ArrayDeque` is preferred over `Stack` in modern Java.

```java id="h1d04w"
import java.util.*;

public class Solution {

    public static String reverseString(String s) {

        Deque<Character> st = new ArrayDeque<>();

        for (char ch : s.toCharArray()) {
            st.push(ch);
        }

        StringBuilder ans = new StringBuilder();

        while (!st.isEmpty()) {
            ans.append(st.pop());
        }

        return ans.toString();
    }
}
```

---

# Important Interview Points

* Stack reverses order naturally because of LIFO.
* `StringBuilder` is used for efficient string concatenation.
* `ArrayDeque` is faster than `Stack`.

---

# LeetCode Related Problem

[LeetCode - Reverse String](https://leetcode.com/problems/reverse-string/?utm_source=chatgpt.com)
