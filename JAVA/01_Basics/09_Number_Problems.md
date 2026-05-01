# 📘 Number Problems (DSA Basics)

---

# 🔹 1. Why Number Problems?

```text id="np1"
Builds logic foundation  
Used in loops, math, and recursion  
Frequently asked in interviews  
```

---

# 🔹 2. Reverse a Number

---

## 🔸 Example

```text id="np2"
Input: 1234  
Output: 4321  
```

---

## 🔸 Code

```java id="np3"
int rev = 0;

while(n > 0){
    int digit = n % 10;
    rev = rev * 10 + digit;
    n /= 10;
}
```

---

# 🔹 3. Palindrome Number

---

## 🔸 Example

```text id="np4"
121 → true  
123 → false  
```

---

## 🔸 Code

```java id="np5"
int original = n;
int rev = 0;

while(n > 0){
    rev = rev * 10 + n % 10;
    n /= 10;
}

return rev == original;
```

---

# 🔹 4. Armstrong Number

---

## 🔸 Example

```text id="np6"
153 → 1³ + 5³ + 3³ = 153  
```

---

## 🔸 Code

```java id="np7"
int sum = 0, temp = n;

while(temp > 0){
    int d = temp % 10;
    sum += d * d * d;
    temp /= 10;
}

return sum == n;
```

---

# 🔹 5. Count Digits

---

## 🔸 Code

```java id="np8"
int count = 0;

while(n > 0){
    count++;
    n /= 10;
}
```

---

## 🔸 Shortcut

```java id="np9"
int digits = (int)Math.log10(n) + 1;
```

---

# 🔹 6. Sum of Digits

```java id="np10"
int sum = 0;

while(n > 0){
    sum += n % 10;
    n /= 10;
}
```

---

# 🔹 7. Check Prime

```java id="np11"
for(int i = 2; i * i <= n; i++){
    if(n % i == 0) return false;
}
return true;
```

---

# 🔹 8. GCD (HCF)

```java id="np12"
int gcd(int a, int b){
    if(b == 0) return a;
    return gcd(b, a % b);
}
```

---

# 🔹 9. LCM

```java id="np13"
int lcm(int a, int b){
    return (a * b) / gcd(a, b);
}
```

---

# 🔹 10. Factorial

```java id="np14"
int fact = 1;

for(int i = 1; i <= n; i++){
    fact *= i;
}
```

---

# 🔹 11. Fibonacci Series

---

## 🔸 Example

```text id="np15"
0 1 1 2 3 5 8
```

---

## 🔸 Code

```java id="np16"
int a = 0, b = 1;

for(int i = 0; i < n; i++){
    System.out.print(a + " ");
    int c = a + b;
    a = b;
    b = c;
}
```

---

# 🔹 12. Power of Number

```java id="np17"
int res = 1;

while(b > 0){
    if((b & 1) == 1){
        res *= a;
    }
    a *= a;
    b >>= 1;
}
```

---

# 🔹 13. Strong Number

---

## 🔸 Example

```text id="np18"
145 → 1! + 4! + 5! = 145  
```

---

# 🔹 14. Perfect Number

---

## 🔸 Example

```text id="np19"
6 → 1 + 2 + 3 = 6  
```

---

# 🔹 15. Common Patterns

```text id="np20"
Digit extraction → n % 10  
Remove digit → n / 10  
Reverse logic → rev = rev * 10 + digit  
```

---

# 🔹 16. Common Mistakes

```text id="np21"
❌ Not handling 0  
❌ Overflow in factorial  
❌ Wrong loop condition  
❌ Ignoring negative numbers  
```

---

# 🔹 17. Interview Tips

```text id="np22"
✔ Practice digit manipulation  
✔ Use math shortcuts  
✔ Optimize loops  
✔ Handle edge cases  
```

---

# 🧠 Quick Revision

```text id="np23"
%10 → last digit  
/10 → remove digit  
Prime → √n  
GCD → recursion  
```

---

# 🔥 Final Insight

```text id="np24"
Number problems = logic + math
```

👉 Strong basics → easy coding problems

---
