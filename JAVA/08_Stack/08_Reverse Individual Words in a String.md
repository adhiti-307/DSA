# Reverse Individual Words in a String

## Problem Statement

Given a string `str`, reverse every individual word while preserving the original word order.

---

# Examples

## Example 1

Input:

```text id="jlwm91"
Hello World
```

Output:

```text id="jlwm92"
olleH dlroW
```

Explanation:

* `Hello` → `olleH`
* `World` → `dlroW`

---

## Example 2

Input:

```text id="jlwm93"
Geeks for Geeks
```

Output:

```text id="jlwm94"
skeeG rof skeeG
```

---

# Approach 1: Using Stack

## Idea

* Traverse characters.
* Push characters of a word into stack.
* When space appears:

  * pop all characters from stack
  * append them to answer.
* Append spaces normally.

---

# Java Code (Using Stack)

```java id="jlwm95"
import java.util.*;

class Solution {

    static String reverseWords(String str) {

        Deque<Character> st = new ArrayDeque<>();

        StringBuilder ans = new StringBuilder();

        for (char ch : str.toCharArray()) {

            // Word character
            if (ch != ' ') {

                st.push(ch);
            }

            // Space encountered
            else {

                while (!st.isEmpty()) {
                    ans.append(st.pop());
                }

                ans.append(' ');
            }
        }

        // Last word
        while (!st.isEmpty()) {
            ans.append(st.pop());
        }

        return ans.toString();
    }

    public static void main(String[] args) {

        String str = "Hello World";

        System.out.println(reverseWords(str));
    }
}
```

---

# Dry Run

Input:

```text id="jlwm96"
Hello World
```

### Stack for "Hello"

```text id="jlwm97"
o
l
l
e
H
```

Pop all:

```text id="jlwm98"
olleH
```

Final Output:

```text id="jlwm99"
olleH dlroW
```

---

# Complexity

| Complexity | Value |
| ---------- | ----- |
| Time       | O(N)  |
| Space      | O(N)  |

---

# More Optimal Approach (Recommended)

Instead of stack:

* use two pointers
* reverse each word directly

This avoids explicit stack usage.

---

# Optimal Java Code

```java id="jlwm100"
class Solution {

    static String reverseWords(String str) {

        String[] words = str.split(" ");

        StringBuilder ans = new StringBuilder();

        for (String word : words) {

            ans.append(new StringBuilder(word).reverse())
               .append(" ");
        }

        return ans.toString().trim();
    }
}
```

---

# Complexity

| Complexity | Value |
| ---------- | ----- |
| Time       | O(N)  |
| Space      | O(N)  |

---

# Important Interview Points

* Stack approach demonstrates LIFO usage clearly.
* `StringBuilder.reverse()` is simpler and preferred in Java.
* Preserve original word order.
* Only reverse characters inside each word.

---

# Related Problems

* Reverse String
* Reverse Words in a String
* Reverse Stack using Recursion
* Valid Parentheses

---

# Related LeetCode

[LeetCode - Reverse Words in a String III](https://leetcode.com/problems/reverse-words-in-a-string-iii/?utm_source=chatgpt.com)
