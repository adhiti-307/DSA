# 📘 Loops in Java

---

# 🔹 1. What are Loops?

Loops are used to **execute a block of code repeatedly**.

```text id="l1"
Repeat until condition becomes false
```

---

# 🔹 2. Types of Loops

* for loop
* while loop
* do-while loop

---

# 🔹 3. for Loop

---

## 🔸 Syntax

```java id="l2"
for(initialization; condition; update){
    // code
}
```

---

## 🔸 Example

```java id="l3"
for(int i = 0; i < 5; i++){
    System.out.println(i);
}
```

👉 Output:

```text id="l4"
0 1 2 3 4
```

---

## 🔸 Flow

```text id="l5"
Init → Condition → Execute → Update → Repeat
```

---

# 🔹 4. while Loop

---

## 🔸 Syntax

```java id="l6"
while(condition){
    // code
}
```

---

## 🔸 Example

```java id="l7"
int i = 0;

while(i < 5){
    System.out.println(i);
    i++;
}
```

---

# 🔹 5. do-while Loop

---

## 🔸 Syntax

```java id="l8"
do{
    // code
}while(condition);
```

---

## 🔸 Example

```java id="l9"
int i = 0;

do{
    System.out.println(i);
    i++;
}while(i < 5);
```

---

## 🔸 Key Difference

```text id="l10"
do-while executes at least once
```

---

# 🔹 6. Loop Comparison

| Loop     | Condition Check | Execution       |
| -------- | --------------- | --------------- |
| for      | Before          | 0 or more times |
| while    | Before          | 0 or more times |
| do-while | After           | At least once   |

---

# 🔹 7. Nested Loops

---

## 🔸 Example

```java id="l11"
for(int i = 1; i <= 3; i++){
    for(int j = 1; j <= 3; j++){
        System.out.print("* ");
    }
    System.out.println();
}
```

👉 Output:

```text id="l12"
* * *
* * *
* * *
```

---

# 🔹 8. break Statement

Used to exit loop

```java id="l13"
for(int i = 0; i < 5; i++){
    if(i == 3) break;
    System.out.println(i);
}
```

---

# 🔹 9. continue Statement

Skips current iteration

```java id="l14"
for(int i = 0; i < 5; i++){
    if(i == 2) continue;
    System.out.println(i);
}
```

---

# 🔹 10. Infinite Loop

```java id="l15"
while(true){
    // runs forever
}
```

---

# 🔹 11. Loop Patterns (Important)

---

## 🔸 Counting Loop

```java id="l16"
for(int i = 0; i < n; i++)
```

---

## 🔸 Reverse Loop

```java id="l17"
for(int i = n-1; i >= 0; i--)
```

---

## 🔸 Step Loop

```java id="l18"
for(int i = 0; i < n; i += 2)
```

---

# 🔹 12. Time Complexity Insight

```text id="l19"
Single loop → O(n)  
Nested loop → O(n²)  
```

---

# 🔹 13. Common Mistakes

```text id="l20"
❌ Infinite loops  
❌ Off-by-one errors  
❌ Wrong condition  
❌ Missing update  
```

---

# 🔹 14. Interview Tips

```text id="l21"
✔ Dry run loops carefully  
✔ Check boundary conditions  
✔ Use meaningful variables  
✔ Avoid unnecessary loops  
```

---

# 🧠 Quick Revision

```text id="l22"
for → fixed iterations  
while → condition-based  
do-while → at least once  
```

---

# 🔥 Final Insight

```text id="l23"
Loops = foundation of problem solving
```

👉 Master loops → master logic

---
