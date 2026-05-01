# 📘 Recursion & Backtracking – Complete Notes

---

# 🔹 1. What is Recursion?

Recursion is a technique where a function **calls itself** to solve a smaller version of the same problem.

---

## 📊 Visualization (Call Stack)

![Image](https://images.openai.com/static-rsc-4/9sg5IjcItPksbQW3TZnctv2mKwUxSz6Cn4Ouge7tdW3dvcdpMENl0mjsUlywxX0CNTLWLZRntWIh644ZtSR3jtnqUSCdvyMGC7pwb0t045Imp2vdrQxeCJeHpkJpnShODEygPNHlVDiDyEgk_Yppd1XQrtLP1nZboiFcqbsn276rrejJ5Cp-T9AU7BM7bqqu?purpose=fullsize)

---

## 🔸 Example: Factorial

```java id="k3d8v1"
int fact(int n){
    if(n == 0) return 1;
    return n * fact(n - 1);
}
```

---

## 🔹 2. Structure of Recursion

```text id="q8n2vt"
1. Base Case → stopping condition  
2. Recursive Call → smaller problem  
```

---

## 🔹 3. Recursion Tree (Concept)

Example: `f(3)`

```text id="m2k9fd"
f(3)
 ├── f(2)
 │    ├── f(1)
 │    │    └── f(0)
```

---

## 🔹 4. Types of Recursion

---

### 🔸 4.1 Direct Recursion

A function directly calls itself.

### ✅ Example

```java
void print(int n){
    if(n == 0) return;

    System.out.println(n);
    print(n - 1);
}
````

### 🔍 Flow

```text
print(3)
→ print(2)
→ print(1)
→ print(0) → stop
```

👉 Most common type of recursion

---

### 🔸 4.2 Indirect Recursion

Two or more functions call each other.

### ✅ Example

```java
void funA(int n){
    if(n <= 0) return;
    System.out.println("A: " + n);
    funB(n - 1);
}

void funB(int n){
    if(n <= 0) return;
    System.out.println("B: " + n);
    funA(n - 1);
}
```

### 🔍 Flow

```text
funA(3)
→ funB(2)
→ funA(1)
→ funB(0) → stop
```

👉 Useful in problems with alternating behavior

---

### 🔸 4.3 Tail Recursion

Recursive call is the **last operation** in the function.

👉 No work after recursive call

### ✅ Example

```java
void print(int n){
    if(n == 0) return;

    System.out.println(n);
    print(n - 1);
}
```

### 🔍 Why Important?

* Can be optimized (in some languages)
* Uses less stack space

---

### ❌ Not Tail Recursion

```java
int fact(int n){
    if(n == 0) return 1;

    return n * fact(n - 1);
}
```

👉 Multiplication happens after recursion → NOT tail recursion

---

### ✅ Convert to Tail Recursion

```java
int fact(int n, int result){
    if(n == 0) return result;

    return fact(n - 1, n * result);
}
```

---

### 🔸 4.4 Tree Recursion

Function makes **multiple recursive calls**

### ✅ Example

```java
void func(int n){
    if(n == 0) return;

    func(n - 1);
    func(n - 1);
}
```

### 🔍 Visualization

```text
func(3)
├── func(2)
│   ├── func(1)
│   └── func(1)
└── func(2)
    ├── func(1)
    └── func(1)
```

👉 Used in:

* Fibonacci
* Subsets
* Backtracking

---
```

---

# 🔹 5. Important Recursion Patterns

---

## 🔸 5.1 Linear Recursion

```java id="a6h1zp"
void print(int n){
    if(n == 0) return;
    print(n - 1);
}
```

---

## 🔸 5.2 Multiple Recursion Calls

```java id="z1w4rm"
void func(int n){
    if(n == 0) return;
    func(n - 1);
    func(n - 1);
}
```

---

## 🔸 5.3 Divide & Conquer

```java id="b7m2ks"
mergeSort(arr, l, r){
    mid = (l + r)/2;
    mergeSort(arr, l, mid);
    mergeSort(arr, mid+1, r);
}
```

---

# 🔹 6. Backtracking

Backtracking is a technique where:
👉 You try all possibilities
👉 Undo the choice if it fails

---

## 📊 Visualization

![Image](https://images.openai.com/static-rsc-4/u9L-lH3tPWpssZVo4vWuJ0M9soXkz9PGe2716H8lghHDFXsSeehkfncoYP0okUJLPdxCoeIsMXikZJPyWDMU4Acn5krN9R-XXx2At_AHMSJDzHOuZXGjlrqwOWgWy64bixinOHdO-iAqlsOAWbLg6-_hmgTeXJ8rfWbBpBstiaIfwSHbaFHvAdZDAuKjfxOM?purpose=fullsize)

---

## 🔸 Basic Idea

```text id="v8t3qp"
Choose → Explore → Undo
```

---

## 🔸 Template

```java id="r5x9jn"
void backtrack(){
    if(base case){
        return;
    }

    for(choice){
        // choose
        backtrack();
        // undo
    }
}
```

---

# 🔹 7. Classic Backtracking Problems

---

## 🔸 Subsets

```java id="u2d6wr"
void subsets(int i, List<Integer> curr){
    if(i == n){
        return;
    }

    curr.add(arr[i]);
    subsets(i+1, curr);

    curr.remove(curr.size()-1);
    subsets(i+1, curr);
}
```

---

## 🔸 Permutations

```java id="g9k1qb"
void permute(List<Integer> curr){
    if(curr.size() == n){
        return;
    }

    for(int i = 0; i < n; i++){
        if(used[i]) continue;

        used[i] = true;
        curr.add(arr[i]);

        permute(curr);

        curr.remove(curr.size()-1);
        used[i] = false;
    }
}
```

---

## 🔸 N-Queens

```java id="h2p7mv"
boolean isSafe(...){}

void solve(row){
    if(row == n){
        return;
    }

    for(int col = 0; col < n; col++){
        if(isSafe(row, col)){
            solve(row + 1);
        }
    }
}
```

---

# 🔹 8. Recursion vs Backtracking

| Feature            | Recursion | Backtracking |
| ------------------ | --------- | ------------ |
| Calls itself       | Yes       | Yes          |
| Explores all paths | No        | Yes          |
| Undo step          | No        | Yes          |
| Use case           | Factorial | N-Queens     |

---

# 🔹 9. Time Complexity

* Linear recursion → O(n)
* Tree recursion → O(2ⁿ)
* Backtracking → Exponential

---

# 🔹 10. Common Mistakes

```text id="t5c1wp"
❌ Missing base case  
❌ Infinite recursion  
❌ Not undoing changes in backtracking  
❌ Stack overflow  
```

---

# 🔹 11. Interview Tips

```text id="y4n8kb"
✔ Always define base case first  
✔ Think in tree structure  
✔ Dry run small input  
✔ Track state carefully  
```

---

# 🔹 12. When to Use

```text id="f2r6lg"
Recursion → smaller subproblems  
Backtracking → all combinations / possibilities  
```

---

# 🧠 Quick Revision

```text id="n7m3zx"
Recursion → function calls itself  
Base case → stopping point  
Backtracking → try + undo  
Tree structure → visualize calls  
```

---

# 🔥 Final Insight

```text id="q1z9xd"
If problem asks for ALL possibilities → use backtracking
```

---
