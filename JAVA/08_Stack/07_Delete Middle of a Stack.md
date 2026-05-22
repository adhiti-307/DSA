# Delete Middle of a Stack

## Problem Statement

Given a stack `s`, remove the middle element without using any additional data structure.

If the size is even, remove the **first middle element**.

---

# Examples

## Example 1

Input:

```text id="jlwm71"
[10, 20, 30, 40, 50]
```

Output:

```text id="jlwm72"
[10, 20, 40, 50]
```

Explanation:

```text id="jlwm73"
Middle element = 30
```

---

## Example 2

Input:

```text id="jlwm74"
[1, 2, 3, 4]
```

Output:

```text id="jlwm75"
[1, 3, 4]
```

Explanation:

```text id="jlwm76"
Middle elements are 2 and 3.
Delete the first middle element = 2.
```

---

# Approach

Use recursion.

### Idea

* Pop elements recursively until middle index is reached.
* Remove middle element.
* Push remaining elements back.

No extra data structure is used.

---

# Important Observation

Middle index:

```java id="jlwm77"
mid = (size / 2)
```

For even size:

* delete first middle

So for:

* size = 4
* delete index = 1 (0-based)

---

# Java Code

```java id="jlwm78"
import java.util.*;

class Solution {

    static void deleteMiddle(Stack<Integer> st, int curr, int mid) {

        // Middle element found
        if (curr == mid) {

            st.pop();
            return;
        }

        int top = st.pop();

        deleteMiddle(st, curr + 1, mid);

        st.push(top);
    }

    static void deleteMid(Stack<Integer> st) {

        int size = st.size();

        int mid = (size - 1) / 2;

        deleteMiddle(st, 0, mid);
    }

    public static void main(String[] args) {

        Stack<Integer> st = new Stack<>();

        st.push(10);
        st.push(20);
        st.push(30);
        st.push(40);
        st.push(50);

        deleteMid(st);

        System.out.println(st);
    }
}
```

---

# Dry Run

Input:

```text id="jlwm79"
[10, 20, 30, 40, 50]
```

Top:

```text id="jlwm80"
50
40
30
20
10
```

Middle index:

```text id="jlwm81"
2
```

Remove:

```text id="jlwm82"
30
```

Final Stack:

```text id="jlwm83"
[10, 20, 40, 50]
```

---

# Complexity

| Complexity | Value                |
| ---------- | -------------------- |
| Time       | O(N)                 |
| Space      | O(N) recursion stack |

---

# Important Interview Points

* No extra stack allowed.
* Recursion stack is allowed.
* For even size:

  * delete first middle
  * use:

```java id="jlwm84"
(size - 1) / 2
```

instead of:

```java id="jlwm85"
size / 2
```

---

# Related Problems

* Reverse Stack using Recursion
* Sort Stack using Recursion
* Insert at Bottom of Stack
* Implement Stack using Recursion

---

# Related LeetCode

[Min Stack](https://leetcode.com/problems/min-stack/?utm_source=chatgpt.com)
