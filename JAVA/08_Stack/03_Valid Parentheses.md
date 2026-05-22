# Valid Parentheses (Balanced Brackets)

## Problem Statement

Given a string `s` containing three types of brackets:

* `()`
* `{}`
* `[]`

Determine whether the expression is balanced or not.

An expression is balanced if:

* Every opening bracket has a corresponding closing bracket of the same type.
* Brackets are closed in the correct order.
* No closing bracket appears before its matching opening bracket.

---

## Examples

### Balanced

```text
[()()]{}
```

Explanation:

* Every opening bracket is closed correctly.
* Nesting order is valid.

---

### Not Balanced

```text
([{]})
```

Explanation:

* `]` appears before closing `{`.
* Nesting order is incorrect.

---

# Approach

Use a **Stack**.

### Steps

1. Traverse each character.
2. If it is an opening bracket:

   * push it into the stack.
3. If it is a closing bracket:

   * check top of stack.
   * if matching opening bracket exists → pop it.
   * otherwise return `false`.
4. At the end:

   * stack should be empty.

---

# Java Code

```java
import java.util.*;

public class Solution {

    public static boolean isBalanced(String s) {

        Stack<Character> st = new Stack<>();

        for (char ch : s.toCharArray()) {

            // Opening brackets
            if (ch == '(' || ch == '{' || ch == '[') {

                st.push(ch);
            }

            // Closing brackets
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

# Example Walkthrough

Input:

```text
([{}])
```

Stack Operations:

| Character | Stack |
| --------- | ----- |
| (         | (     |
| [         | ( [   |
| {         | ( [ { |
| }         | ( [   |
| ]         | (     |
| )         | empty |

Balanced ✔

---

# Complexity

| Operation | Complexity |
| --------- | ---------- |
| Time      | O(N)       |
| Space     | O(N)       |

---

# Important Interview Points

* Stack is the standard approach.
* Always check `isEmpty()` before `pop()`.
* Final stack must be empty.

---

# LeetCode Problem

[LeetCode - Valid Parentheses](https://leetcode.com/problems/valid-parentheses/?utm_source=chatgpt.com)
