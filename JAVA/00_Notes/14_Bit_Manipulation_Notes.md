# 📘 Bit Manipulation – Complete Notes

---

# 🔹 1. What is Bit Manipulation?

Bit manipulation involves operating directly on the **binary representation** of numbers using bitwise operators.

---

# 🔹 2. Binary Basics

```text id="bm1"
Decimal → Binary

5  = 101  
10 = 1010  
```

---

# 🔹 3. Bitwise Operators

| Operator    | Symbol | Description         |
| ----------- | ------ | ------------------- |
| AND         | &      | Both bits must be 1 |
| OR          | |      | Any one bit is 1    |
| XOR         | ^      | Different bits      |
| NOT         | ~      | Flip bits           |
| Left Shift  | <<     | Multiply by 2       |
| Right Shift | >>     | Divide by 2         |

---

## 🔸 Examples

```text id="bm2"
5  = 101  
3  = 011  

AND → 001 (1)  
OR  → 111 (7)  
XOR → 110 (6)  
```

---

# 🔹 4. Important Bit Tricks

---

## 🔸 4.1 Check Even / Odd

```java id="bm3"
if((n & 1) == 0) → even
else → odd
```

---

## 🔸 4.2 Check Power of 2

```java id="bm4"
if(n > 0 && (n & (n - 1)) == 0)
```

---

## 🔸 4.3 Count Set Bits

```java id="bm5"
int count = 0;

while(n > 0){
    n = n & (n - 1);
    count++;
}
```

---

## 🔸 4.4 Get ith Bit

```java id="bm6"
(n >> i) & 1
```

---

## 🔸 4.5 Set ith Bit

```java id="bm7"
n | (1 << i)
```

---

## 🔸 4.6 Clear ith Bit

```java id="bm8"
n & ~(1 << i)
```

---

## 🔸 4.7 Toggle ith Bit

```java id="bm9"
n ^ (1 << i)
```

---

# 🔹 5. XOR Properties (Very Important)

```text id="bm10"
a ^ a = 0  
a ^ 0 = a  
a ^ b ^ a = b  
```

---

## 🔸 Example (Find Unique Element)

```java id="bm11"
int res = 0;

for(int x : arr){
    res ^= x;
}
```

---

# 🔹 6. Bit Masking

Used to represent subsets

---

## 🔸 Example

```text id="bm12"
n = 3 → subsets = 2^3 = 8

000 → {}  
001 → {a}  
010 → {b}  
011 → {a, b}  
```

---

## 🔸 Code

```java id="bm13"
for(int mask = 0; mask < (1 << n); mask++){
    for(int i = 0; i < n; i++){
        if((mask & (1 << i)) != 0){
            System.out.print(arr[i]);
        }
    }
}
```

---

# 🔹 7. Left & Right Shift

```text id="bm14"
n << 1 → n * 2  
n >> 1 → n / 2  
```

---

## 🔸 Example

```text id="bm15"
5 << 1 = 10  
5 >> 1 = 2  
```

---

# 🔹 8. Common Problems

* Single Number
* Missing Number
* Power of Two
* Subsets
* Bitwise AND of Range
* Count Bits

---

# 🔹 9. Time Complexity Advantage

```text id="bm16"
Bit operations → O(1)
```

👉 Much faster than arithmetic operations

---

# 🔹 10. Common Mistakes

```text id="bm17"
❌ Confusing AND & OR  
❌ Wrong shift direction  
❌ Not handling negative numbers  
```

---

# 🔹 11. Interview Tips

```text id="bm18"
✔ Use XOR for unique elements  
✔ Use (n & (n-1)) trick  
✔ Think in binary  
✔ Practice bit masking  
```

---

# 🧠 Quick Revision

```text id="bm19"
& → AND  
| → OR  
^ → XOR  
<< → multiply  
>> → divide  
```

---

# 🔥 Final Insight

```text id="bm20"
Bit Manipulation = speed + optimization
```

👉 Use when:

* Space needs to be minimized
* Performance is critical

---
