# 📘 Math Utilities in Java (DSA Friendly)

---

# 🔹 1. Why Math Utilities?

```text id="mu1"
Solve mathematical problems efficiently  
Used in number theory, CP, and DSA  
Optimize calculations  
```

---

# 🔹 2. Basic Math Methods (Math Class)

---

## 🔸 Common Functions

```java id="mu2"
Math.abs(x)        // absolute value  
Math.max(a, b)     // maximum  
Math.min(a, b)     // minimum  
Math.sqrt(x)       // square root  
Math.pow(a, b)     // a^b  
Math.ceil(x)       // round up  
Math.floor(x)      // round down  
```

---

## 🔸 Example

```java id="mu3"
System.out.println(Math.max(10, 20)); // 20
System.out.println(Math.sqrt(25));    // 5.0
```

---

# 🔹 3. Prime Number Check

---

## 🔸 Efficient Approach

```java id="mu4"
boolean isPrime(int n){
    if(n <= 1) return false;

    for(int i = 2; i * i <= n; i++){
        if(n % i == 0) return false;
    }
    return true;
}
```

👉 Time: **O(√n)**

---

# 🔹 4. GCD (Greatest Common Divisor)

---

## 🔸 Euclidean Algorithm

```java id="mu5"
int gcd(int a, int b){
    if(b == 0) return a;
    return gcd(b, a % b);
}
```

---

## 🔸 LCM

```java id="mu6"
int lcm(int a, int b){
    return (a * b) / gcd(a, b);
}
```

---

# 🔹 5. Fast Exponentiation (Binary Power)

---

## 🔸 Code

```java id="mu7"
long power(long a, long b){
    long res = 1;

    while(b > 0){
        if((b & 1) == 1){
            res *= a;
        }
        a *= a;
        b >>= 1;
    }
    return res;
}
```

👉 Time: **O(log n)**

---

# 🔹 6. Modular Arithmetic

---

## 🔸 Why Needed?

```text id="mu8"
Avoid overflow  
Used in competitive programming  
```

---

## 🔸 Properties

```text id="mu9"
(a + b) % m = (a % m + b % m) % m  
(a * b) % m = (a % m * b % m) % m  
```

---

## 🔸 Example

```java id="mu10"
int mod = 1000000007;

int sum = (a % mod + b % mod) % mod;
```

---

# 🔹 7. Sieve of Eratosthenes

---

## 🔸 Purpose

```text id="mu11"
Find all primes up to n
```

---

## 🔸 Code

```java id="mu12"
boolean[] prime = new boolean[n+1];
Arrays.fill(prime, true);

for(int i = 2; i * i <= n; i++){
    if(prime[i]){
        for(int j = i*i; j <= n; j += i){
            prime[j] = false;
        }
    }
}
```

👉 Time: **O(n log log n)**

---

# 🔹 8. Factorial

---

## 🔸 Iterative

```java id="mu13"
int fact(int n){
    int res = 1;

    for(int i = 1; i <= n; i++){
        res *= i;
    }
    return res;
}
```

---

# 🔹 9. Number of Digits

```java id="mu14"
int digits = (int)Math.log10(n) + 1;
```

---

# 🔹 10. Reverse a Number

```java id="mu15"
int rev = 0;

while(n > 0){
    rev = rev * 10 + n % 10;
    n /= 10;
}
```

---

# 🔹 11. Palindrome Number

```java id="mu16"
boolean isPalindrome(int n){
    int original = n;
    int rev = 0;

    while(n > 0){
        rev = rev * 10 + n % 10;
        n /= 10;
    }
    return rev == original;
}
```

---

# 🔹 12. Common Problems

* Prime numbers
* GCD & LCM
* Fast power
* Modular arithmetic
* Factorial
* Digit manipulation

---

# 🔹 13. Common Mistakes

```text id="mu17"
❌ Overflow in multiplication  
❌ Wrong modulo usage  
❌ Using slow power method  
❌ Not handling edge cases  
```

---

# 🔹 14. Interview Tips

```text id="mu18"
✔ Use fast exponentiation  
✔ Use modulo carefully  
✔ Use sqrt optimization  
✔ Remember common formulas  
```

---

# 🧠 Quick Revision

```text id="mu19"
GCD → Euclidean  
Power → log n  
Prime → √n  
Sieve → all primes  
```

---

# 🔥 Final Insight

```text id="mu20"
Math optimizations = faster solutions
```

👉 Use math to reduce time complexity

---
