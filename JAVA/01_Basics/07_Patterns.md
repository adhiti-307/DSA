# 📘 Pattern Printing in Java

---

# 🔹 1. Why Pattern Problems?

```text id="pt1"
Improve logic building  
Understand nested loops  
Strengthen problem-solving  
```

---

# 🔹 2. Basic Idea

```text id="pt2"
Outer loop → rows  
Inner loop → columns  
```

---

# 🔹 3. Types of Patterns

* Square patterns
* Triangle patterns
* Pyramid patterns
* Number patterns
* Character patterns

---

# 🔹 4. Square Pattern

---

## 🔸 Example

```text id="pt3"
* * * *
* * * *
* * * *
* * * *
```

---

## 🔸 Code

```java id="pt4"
for(int i = 1; i <= 4; i++){
    for(int j = 1; j <= 4; j++){
        System.out.print("* ");
    }
    System.out.println();
}
```

---

# 🔹 5. Right Triangle Pattern

---

## 🔸 Example

```text id="pt5"
*
* *
* * *
* * * *
```

---

## 🔸 Code

```java id="pt6"
for(int i = 1; i <= 4; i++){
    for(int j = 1; j <= i; j++){
        System.out.print("* ");
    }
    System.out.println();
}
```

---

# 🔹 6. Inverted Triangle

---

## 🔸 Example

```text id="pt7"
* * * *
* * *
* *
*
```

---

## 🔸 Code

```java id="pt8"
for(int i = 4; i >= 1; i--){
    for(int j = 1; j <= i; j++){
        System.out.print("* ");
    }
    System.out.println();
}
```

---

# 🔹 7. Pyramid Pattern

---

## 🔸 Example

```text id="pt9"
   *
  * *
 * * *
* * * *
```

---

## 🔸 Code

```java id="pt10"
int n = 4;

for(int i = 1; i <= n; i++){
    for(int j = 1; j <= n - i; j++){
        System.out.print(" ");
    }
    for(int j = 1; j <= i; j++){
        System.out.print("* ");
    }
    System.out.println();
}
```

---

# 🔹 8. Number Pattern

---

## 🔸 Example

```text id="pt11"
1
1 2
1 2 3
1 2 3 4
```

---

## 🔸 Code

```java id="pt12"
for(int i = 1; i <= 4; i++){
    for(int j = 1; j <= i; j++){
        System.out.print(j + " ");
    }
    System.out.println();
}
```

---

# 🔹 9. Character Pattern

---

## 🔸 Example

```text id="pt13"
A
A B
A B C
A B C D
```

---

## 🔸 Code

```java id="pt14"
for(int i = 1; i <= 4; i++){
    char ch = 'A';
    for(int j = 1; j <= i; j++){
        System.out.print(ch + " ");
        ch++;
    }
    System.out.println();
}
```

---

# 🔹 10. Important Pattern Logic

---

## 🔸 Spaces + Stars

```text id="pt15"
Spaces decrease → stars increase
```

---

## 🔸 Formula

```text id="pt16"
Spaces = n - i  
Stars = i  
```

---

# 🔹 11. Advanced Pattern (Diamond)

---

## 🔸 Example

```text id="pt17"
   *
  * *
 * * *
  * *
   *
```

---

# 🔹 12. Common Mistakes

```text id="pt18"
❌ Wrong loop limits  
❌ Missing spaces  
❌ Incorrect print format  
❌ Not understanding row/column logic  
```

---

# 🔹 13. Interview Tips

```text id="pt19"
✔ Always dry run  
✔ Focus on pattern symmetry  
✔ Break into rows & columns  
✔ Practice regularly  
```

---

# 🧠 Quick Revision

```text id="pt20"
Outer loop → rows  
Inner loop → columns  
Spaces + elements → pattern  
```

---

# 🔥 Final Insight

```text id="pt21"
Pattern problems = loop mastery
```

👉 Master patterns → strong fundamentals

---
