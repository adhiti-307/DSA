# 📘 Strings – Complete Notes

---

# 🔹 1. What is a String?

A String is a sequence of characters.

In Java:

* Strings are **immutable** (cannot be changed)
* Stored in **String Pool**

---

## 📊 Visualization

![Image](https://images.openai.com/static-rsc-4/JacE8dYH9K1wR_8OSNmmSBQaMkkBH28B_QxQgoYhmv1O6_ENQG6I9DEqzoVD7pTOh_8G565T3fMz2SNB3gMBuQlC7fD3sUQlKE2rNLrxiePmt7jmTkJebbV49dM58_DuJHtE1V7C9EiDb5PQQOonsc-CXgehrgbl3Z_G8VTG3lHeTk1TonEoYBk5c7d8PRlo?purpose=fullsize)

```text id="d7m9aa"
String:   H   E   L   L   O
Index:    0   1   2   3   4
```

---

# 🔹 2. String Declaration

```java id="y3f0j8"
String s1 = "Hello";          // String literal
String s2 = new String("Hi"); // Object
```

---

# 🔹 3. Important String Methods

```java id="m3j2k8"
s.length()
s.charAt(i)
s.substring(start, end)
s.equals(s2)
s.equalsIgnoreCase(s2)
s.toLowerCase()
s.toUpperCase()
s.trim()
```

---

# 🔹 4. String Immutability

```java id="n0t1xp"
String s = "Hello";
s.concat("World");
```

👉 Original string remains unchanged

---

# 🔹 5. StringBuilder (Mutable String)

Used for efficient string operations

```java id="p8u2al"
StringBuilder sb = new StringBuilder("Hello");

sb.append(" World");
sb.reverse();
sb.toString();
```

👉 Faster than String in loops

---

# 🔹 6. Common Patterns in Strings

---

## 🔸 6.1 Frequency Count (Hashing)

```java id="r2jk3m"
int[] freq = new int[26];

for(char c : s.toCharArray()){
    freq[c - 'a']++;
}
```

---

## 🔸 6.2 Palindrome Check

```java id="x5m2rq"
int left = 0, right = s.length() - 1;

while(left < right){
    if(s.charAt(left) != s.charAt(right)){
        return false;
    }
    left++;
    right--;
}
return true;
```

---

## 🔸 6.3 Anagram Check

```java id="f7t9yb"
int[] freq = new int[26];

for(char c : s1.toCharArray()) freq[c - 'a']++;
for(char c : s2.toCharArray()) freq[c - 'a']--;

for(int x : freq){
    if(x != 0) return false;
}
return true;
```

---

## 🔸 6.4 Sliding Window (Strings)

```java id="v9k3lp"
Set<Character> set = new HashSet<>();

int left = 0, maxLen = 0;

for(int right = 0; right < s.length(); right++){
    while(set.contains(s.charAt(right))){
        set.remove(s.charAt(left));
        left++;
    }
    set.add(s.charAt(right));
    maxLen = Math.max(maxLen, right - left + 1);
}
```

---

## 🔸 6.5 Two Pointer (Strings)

```java id="w1d8az"
int left = 0, right = s.length() - 1;

while(left < right){
    // compare or modify
    left++;
    right--;
}
```

---

# 🔹 7. Important String Problems

* Reverse a String
* Check Palindrome
* Longest Substring Without Repeating Characters
* Valid Anagram
* Group Anagrams
* Longest Palindromic Substring

---

# 🔹 8. String Comparison

```java id="t4y7qw"
s1.equals(s2)      // correct
s1 == s2           // compares reference
```

---

# 🔹 9. Conversion Techniques

```java id="u6z9kt"
char[] arr = s.toCharArray();
String str = new String(arr);

int num = Integer.parseInt("123");
String s = String.valueOf(123);
```

---

# 🔹 10. Common Tricks

```java id="h3k8wd"
// Check vowel
if("aeiou".indexOf(c) != -1)

// Toggle case
char ch = (char)(c ^ 32)

// Reverse using StringBuilder
new StringBuilder(s).reverse().toString()
```

---

# 🔹 11. Time Complexity

| Operation            | Complexity |
| -------------------- | ---------- |
| Access char          | O(1)       |
| Concatenation        | O(n)       |
| StringBuilder append | O(1)       |
| Substring            | O(n)       |

---

# 🔹 12. Common Mistakes

```text id="8z1tgm"
❌ Using == for string comparison  
❌ Using String in loops (slow)  
❌ Not handling case sensitivity  
❌ Ignoring whitespace issues  
```

---

# 🔹 13. Interview Tips

```text id="k3p7lm"
✔ Use StringBuilder for modifications  
✔ Think in sliding window for substrings  
✔ Use hashing for frequency problems  
✔ Always check edge cases  
```

---

# 🧠 Quick Revision

```text id="r9u2ye"
String → immutable  
StringBuilder → mutable  
Palindrome → two pointer  
Substring → sliding window  
Frequency → hashing  
```

---

# 🔥 Final Insight

```text id="b4n8lp"
Most string problems = pattern recognition
```

👉 Master:

* Sliding Window
* Two Pointer
* Hashing

---
