# Stack Expression Conversion & Evaluation in Java

## Table of Contents

1. Evaluate Reverse Polish Notation (Postfix Evaluation)
2. Postfix to Prefix Conversion
3. Prefix to Postfix Conversion
4. Infix to Postfix Conversion
5. Infix to Prefix Conversion
6. Why `ArrayDeque` is Better than `Stack`

---

# 1. Evaluate Reverse Polish Notation (Postfix Evaluation)

## Problem Statement

Evaluate a postfix expression.

---

## Example

Input:

```text
["2","1","+","3","*"]
```

Output:

```text
9
```

Explanation:

```text
(2 + 1) * 3
```

---

# Approach

Use a stack.

* Operand → push
* Operator:

  * pop two elements
  * apply operation
  * push result back

---

# Optimal Java Code

```java
import java.util.*;

class Solution {

    public int evalRPN(String[] tokens) {

        Deque<Integer> st = new ArrayDeque<>();

        for (String str : tokens) {

            switch (str) {

                case "+":
                    st.push(st.pop() + st.pop());
                    break;

                case "-": {

                    int b = st.pop();
                    int a = st.pop();

                    st.push(a - b);
                    break;
                }

                case "*":
                    st.push(st.pop() * st.pop());
                    break;

                case "/": {

                    int b = st.pop();
                    int a = st.pop();

                    st.push(a / b);
                    break;
                }

                default:
                    st.push(Integer.parseInt(str));
            }
        }

        return st.pop();
    }
}
```

---

# Complexity

| Time | Space |
| ---- | ----- |
| O(N) | O(N)  |

---

# LeetCode

[Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/?utm_source=chatgpt.com)

---

# 2. Postfix to Prefix Conversion

## Example

Input:

```text
AB+CD-*
```

Output:

```text
*+AB-CD
```

---

# Approach

* Operand → push
* Operator:

  * pop two strings
  * form:

```text
operator + op1 + op2
```

---

# Java Code

```java
import java.util.*;

class Solution {

    static boolean isOperator(char ch) {

        return ch == '+' || ch == '-' ||
               ch == '*' || ch == '/' ||
               ch == '^';
    }

    static String postfixToPrefix(String postfix) {

        Deque<String> st = new ArrayDeque<>();

        for (char ch : postfix.toCharArray()) {

            if (!isOperator(ch)) {

                st.push(ch + "");
            }

            else {

                String op2 = st.pop();
                String op1 = st.pop();

                st.push(ch + op1 + op2);
            }
        }

        return st.peek();
    }
}
```

---

# Complexity

| Time | Space |
| ---- | ----- |
| O(N) | O(N)  |

---

# 3. Prefix to Postfix Conversion

## Example

Input:

```text
*+AB-CD
```

Output:

```text
AB+CD-*
```

---

# Approach

Traverse from right to left.

---

# Java Code

```java
import java.util.*;

class Solution {

    static boolean isOperator(char ch) {

        return ch == '+' || ch == '-' ||
               ch == '*' || ch == '/' ||
               ch == '^';
    }

    static String prefixToPostfix(String prefix) {

        Deque<String> st = new ArrayDeque<>();

        for (int i = prefix.length() - 1; i >= 0; i--) {

            char ch = prefix.charAt(i);

            if (!isOperator(ch)) {

                st.push(ch + "");
            }

            else {

                String op1 = st.pop();
                String op2 = st.pop();

                st.push(op1 + op2 + ch);
            }
        }

        return st.peek();
    }
}
```

---

# Complexity

| Time | Space |
| ---- | ----- |
| O(N) | O(N)  |

---

# 4. Infix to Postfix Conversion

## Example

Input:

```text
(A+B)*C
```

Output:

```text
AB+C*
```

---

# Approach

Use:

* stack for operators
* precedence rules

---

# Java Code

```java
import java.util.*;

class Solution {

    static int precedence(char ch) {

        if (ch == '+' || ch == '-') return 1;
        if (ch == '*' || ch == '/') return 2;
        if (ch == '^') return 3;

        return -1;
    }

    static String infixToPostfix(String s) {

        StringBuilder ans = new StringBuilder();

        Deque<Character> st = new ArrayDeque<>();

        for (char ch : s.toCharArray()) {

            if (Character.isLetterOrDigit(ch)) {

                ans.append(ch);
            }

            else if (ch == '(') {

                st.push(ch);
            }

            else if (ch == ')') {

                while (!st.isEmpty() && st.peek() != '(') {
                    ans.append(st.pop());
                }

                st.pop();
            }

            else {

                while (!st.isEmpty() &&
                       precedence(st.peek()) >= precedence(ch)) {

                    ans.append(st.pop());
                }

                st.push(ch);
            }
        }

        while (!st.isEmpty()) {
            ans.append(st.pop());
        }

        return ans.toString();
    }
}
```

---

# Complexity

| Time | Space |
| ---- | ----- |
| O(N) | O(N)  |

---

# 5. Infix to Prefix Conversion

## Trick

1. Reverse infix
2. Swap brackets
3. Convert to postfix
4. Reverse answer

---

# Java Code

```java
import java.util.*;

class Solution {

    static int precedence(char ch) {

        if (ch == '+' || ch == '-') return 1;
        if (ch == '*' || ch == '/') return 2;
        if (ch == '^') return 3;

        return -1;
    }

    static String infixToPrefix(String s) {

        StringBuilder rev = new StringBuilder(s).reverse();

        // Swap brackets
        for (int i = 0; i < rev.length(); i++) {

            if (rev.charAt(i) == '(')
                rev.setCharAt(i, ')');

            else if (rev.charAt(i) == ')')
                rev.setCharAt(i, '(');
        }

        StringBuilder postfix = new StringBuilder();

        Deque<Character> st = new ArrayDeque<>();

        for (char ch : rev.toString().toCharArray()) {

            if (Character.isLetterOrDigit(ch)) {

                postfix.append(ch);
            }

            else if (ch == '(') {

                st.push(ch);
            }

            else if (ch == ')') {

                while (!st.isEmpty() && st.peek() != '(') {
                    postfix.append(st.pop());
                }

                st.pop();
            }

            else {

                while (!st.isEmpty() &&
                       precedence(st.peek()) >= precedence(ch)) {

                    postfix.append(st.pop());
                }

                st.push(ch);
            }
        }

        while (!st.isEmpty()) {
            postfix.append(st.pop());
        }

        return postfix.reverse().toString();
    }
}
```

---

# Complexity

| Time | Space |
| ---- | ----- |
| O(N) | O(N)  |

---

# 6. Why `ArrayDeque` is Better than `Stack`

## Prefer

```java
Deque<Integer> st = new ArrayDeque<>();
```

instead of:

```java
Stack<Integer> st = new Stack<>();
```

---

# Why?

## `Stack`

* legacy class
* synchronized
* slower

## `ArrayDeque`

* faster
* modern implementation
* recommended by Java documentation

---

# Important Interview Tips

* Expression problems are stack-heavy.
* Operand order matters.
* Always remember:

  * first popped → second operand
  * second popped → first operand

Especially for:

* subtraction
* division

---

# Related LeetCode Problems

* [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/?utm_source=chatgpt.com)
* [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/?utm_source=chatgpt.com)
