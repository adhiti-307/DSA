# 📘 Functions (Methods) in Java

---

# 🔹 1. What are Functions?

Functions (methods in Java) are **blocks of code** that perform a specific task and can be reused.

```text id="fn1"
Write once → use multiple times
```

---

# 🔹 2. Why Use Functions?

```text id="fn2"
✔ Code reuse  
✔ Better readability  
✔ Easier debugging  
✔ Modular programming  
```

---

# 🔹 3. Function Syntax

```java id="fn3"
returnType functionName(parameters){
    // code
    return value;
}
```

---

## 🔸 Example

```java id="fn4"
int add(int a, int b){
    return a + b;
}
```

---

# 🔹 4. Calling a Function

```java id="fn5"
int result = add(5, 3);
System.out.println(result);
```

---

# 🔹 5. Types of Functions

---

## 🔸 5.1 No Parameter, No Return

```java id="fn6"
void greet(){
    System.out.println("Hello");
}
```

---

## 🔸 5.2 Parameter, No Return

```java id="fn7"
void printSum(int a, int b){
    System.out.println(a + b);
}
```

---

## 🔸 5.3 No Parameter, With Return

```java id="fn8"
int getNumber(){
    return 10;
}
```

---

## 🔸 5.4 Parameter, With Return

```java id="fn9"
int multiply(int a, int b){
    return a * b;
}
```

---

# 🔹 6. Function Flow

```text id="fn10"
Main → Function call → Execute → Return → Continue
```

---

# 🔹 7. Pass by Value

Java uses **pass by value**

```java id="fn11"
void change(int x){
    x = 100;
}

int a = 10;
change(a);
System.out.println(a); // still 10
```

---

# 🔹 8. Function Overloading

Same function name with different parameters

```java id="fn12"
int add(int a, int b){
    return a + b;
}

double add(double a, double b){
    return a + b;
}
```

---

# 🔹 9. Recursion (Function Calling Itself)

```java id="fn13"
int fact(int n){
    if(n == 0) return 1;
    return n * fact(n - 1);
}
```

---

# 🔹 10. Scope of Variables

```java id="fn14"
int x = 10; // global (class level)

void func(){
    int y = 5; // local
}
```

---

# 🔹 11. Return Statement

```java id="fn15"
return value;
```

👉 Ends function execution

---

# 🔹 12. Void Functions

```java id="fn16"
void print(){
    System.out.println("Hello");
}
```

👉 No return value

---

# 🔹 13. Static Functions

```java id="fn17"
static void hello(){
    System.out.println("Hi");
}
```

👉 Called without object

---

# 🔹 14. Common Mistakes

```text id="fn18"
❌ Missing return statement  
❌ Wrong return type  
❌ Infinite recursion  
❌ Not passing correct arguments  
```

---

# 🔹 15. Interview Tips

```text id="fn19"
✔ Keep functions small  
✔ Use meaningful names  
✔ Avoid deep nesting  
✔ Use recursion carefully  
```

---

# 🧠 Quick Revision

```text id="fn20"
Function → reusable code  
Parameters → input  
Return → output  
```

---

# 🔥 Final Insight

```text id="fn21"
Functions = building blocks of programs
```

👉 Good functions → clean code

---
