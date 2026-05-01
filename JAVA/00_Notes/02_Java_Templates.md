# 📘 Java Templates for DSA

---

## 🔹 1. Basic Input Template (Scanner)

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] arr = new int[n];

        for(int i = 0; i < n; i++){
            arr[i] = sc.nextInt();
        }

        System.out.println("Input taken successfully");
    }
}
```

### ✅ When to use:

* Simple problems
* Small input size

### ⚠️ Limitation:

* Slow for large inputs

---

## 🔹 2. Fast Input Template (BufferedReader)

```java
import java.io.*;
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(br.readLine());

        String[] input = br.readLine().split(" ");
        int[] arr = new int[n];

        for(int i = 0; i < n; i++){
            arr[i] = Integer.parseInt(input[i]);
        }
    }
}
```

### ✅ When to use:

* Large input (competitive coding)
* Avoids TLE

---

## 🔹 3. Fast Input using StringTokenizer

```java
import java.io.*;
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(br.readLine());
        int[] arr = new int[n];

        StringTokenizer st = new StringTokenizer(br.readLine());

        for(int i = 0; i < n; i++){
            arr[i] = Integer.parseInt(st.nextToken());
        }
    }
}
```

### ✅ Faster than split()

---

## 🔹 4. Fast Output Template

```java
BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

bw.write("Hello World\n");
bw.flush();
```

---

## 🔹 5. Array Input & Output Template

```java
int[] arr = new int[n];

for(int i = 0; i < n; i++){
    arr[i] = sc.nextInt();
}

for(int x : arr){
    System.out.print(x + " ");
}
```

---

## 🔹 6. 2D Array Template

```java
int[][] matrix = new int[n][m];

for(int i = 0; i < n; i++){
    for(int j = 0; j < m; j++){
        matrix[i][j] = sc.nextInt();
    }
}
```

---

## 🔹 7. Binary Search Template

```java
int binarySearch(int[] arr, int target){
    int low = 0, high = arr.length - 1;

    while(low <= high){
        int mid = low + (high - low) / 2;

        if(arr[mid] == target) return mid;
        else if(arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}
```

---

## 🔹 8. DFS Template (Graph)

```java
void dfs(int node, boolean[] visited, ArrayList<ArrayList<Integer>> adj){
    visited[node] = true;

    for(int neighbor : adj.get(node)){
        if(!visited[neighbor]){
            dfs(neighbor, visited, adj);
        }
    }
}
```

---

## 🔹 9. BFS Template (Graph)

```java
void bfs(int start, ArrayList<ArrayList<Integer>> adj, int n){
    boolean[] visited = new boolean[n];
    Queue<Integer> q = new LinkedList<>();

    q.add(start);
    visited[start] = true;

    while(!q.isEmpty()){
        int node = q.poll();

        for(int neighbor : adj.get(node)){
            if(!visited[neighbor]){
                visited[neighbor] = true;
                q.add(neighbor);
            }
        }
    }
}
```

---

## 🔹 10. Priority Queue (Min Heap / Max Heap)

```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();

PriorityQueue<Integer> maxHeap = new PriorityQueue<>(
    (a, b) -> b - a
);
```

---

## 🔹 11. Custom Comparator (Sorting)

```java
Arrays.sort(arr, (a, b) -> a - b);
```

---

## 🔹 12. HashMap Template

```java
HashMap<Integer, Integer> map = new HashMap<>();

map.put(1, 10);
map.get(1);
map.containsKey(1);
```

---

## 🔹 13. HashSet Template

```java
HashSet<Integer> set = new HashSet<>();

set.add(1);
set.contains(1);
set.remove(1);
```

---

## 🔹 14. StringBuilder Template

```java
StringBuilder sb = new StringBuilder();

sb.append("Hello");
sb.reverse();
sb.toString();
```

---

## 🔹 15. Sliding Window Template

```java
int left = 0, sum = 0;

for(int right = 0; right < n; right++){
    sum += arr[right];

    while(sum > target){
        sum -= arr[left];
        left++;
    }
}
```

---

## 🔹 16. Prefix Sum Template

```java
int[] prefix = new int[n];
prefix[0] = arr[0];

for(int i = 1; i < n; i++){
    prefix[i] = prefix[i-1] + arr[i];
}
```

---

## 🔹 17. Fast Power (Binary Exponentiation)

```java
long power(long a, long b){
    long res = 1;

    while(b > 0){
        if((b & 1) == 1) res *= a;
        a *= a;
        b >>= 1;
    }
    return res;
}
```

---

## 🔹 18. GCD (Euclidean Algorithm)

```java
int gcd(int a, int b){
    if(b == 0) return a;
    return gcd(b, a % b);
}
```

---

# 🧠 Final Tips

```text
Use Scanner → small input  
Use BufferedReader → large input  
Use StringBuilder → string operations  
Use PriorityQueue → heap problems  
Use HashMap → frequency / lookup  
```

---

# 🔥 Must Remember

```text
Templates save time in contests  
Write once → reuse everywhere  
Practice using them regularly
```

# 🚀 Advanced Templates (DP, Union-Find, Segment Tree)

---

# 🔹 19. Dynamic Programming (DP Templates)

## ✅ 1D DP (Bottom-Up)

```java
int[] dp = new int[n + 1];
dp[0] = 0;

for(int i = 1; i <= n; i++){
    dp[i] = dp[i - 1] + 1;
}
```

---

## ✅ 1D DP (Top-Down / Memoization)

```java
int[] dp = new int[n + 1];
Arrays.fill(dp, -1);

int solve(int n){
    if(n == 0) return 0;
    if(dp[n] != -1) return dp[n];

    return dp[n] = solve(n - 1) + 1;
}
```

---

## ✅ 2D DP Template

```java
int[][] dp = new int[n][m];

for(int i = 0; i < n; i++){
    for(int j = 0; j < m; j++){
        dp[i][j] = 0;
    }
}
```

---

## ✅ Knapsack Pattern

```java
int[][] dp = new int[n + 1][W + 1];

for(int i = 1; i <= n; i++){
    for(int w = 0; w <= W; w++){
        if(weight[i-1] <= w){
            dp[i][w] = Math.max(
                value[i-1] + dp[i-1][w - weight[i-1]],
                dp[i-1][w]
            );
        } else {
            dp[i][w] = dp[i-1][w];
        }
    }
}
```

---

## ✅ LIS (Longest Increasing Subsequence)

```java
int[] dp = new int[n];
Arrays.fill(dp, 1);

for(int i = 0; i < n; i++){
    for(int j = 0; j < i; j++){
        if(arr[j] < arr[i]){
            dp[i] = Math.max(dp[i], dp[j] + 1);
        }
    }
}
```

---

# 🔹 20. Union-Find (Disjoint Set Union - DSU)

## ✅ With Path Compression + Union by Rank

```java
class DSU {
    int[] parent, rank;

    DSU(int n){
        parent = new int[n];
        rank = new int[n];

        for(int i = 0; i < n; i++){
            parent[i] = i;
        }
    }

    int find(int x){
        if(parent[x] != x){
            parent[x] = find(parent[x]);
        }
        return parent[x];
    }

    void union(int a, int b){
        int rootA = find(a);
        int rootB = find(b);

        if(rootA == rootB) return;

        if(rank[rootA] < rank[rootB]){
            parent[rootA] = rootB;
        } else if(rank[rootA] > rank[rootB]){
            parent[rootB] = rootA;
        } else {
            parent[rootB] = rootA;
            rank[rootA]++;
        }
    }
}
```

---

## ✅ Usage Example

```java
DSU dsu = new DSU(n);

dsu.union(1, 2);
dsu.union(2, 3);

if(dsu.find(1) == dsu.find(3)){
    System.out.println("Connected");
}
```

---

# 🔹 21. Segment Tree

## ✅ Build + Query + Update

```java
class SegmentTree {
    int[] tree;
    int n;

    SegmentTree(int[] arr){
        n = arr.length;
        tree = new int[4 * n];
        build(arr, 0, 0, n - 1);
    }

    void build(int[] arr, int node, int start, int end){
        if(start == end){
            tree[node] = arr[start];
        } else {
            int mid = (start + end) / 2;
            build(arr, 2*node+1, start, mid);
            build(arr, 2*node+2, mid+1, end);
            tree[node] = tree[2*node+1] + tree[2*node+2];
        }
    }

    int query(int node, int start, int end, int l, int r){
        if(r < start || end < l) return 0;

        if(l <= start && end <= r){
            return tree[node];
        }

        int mid = (start + end) / 2;
        int left = query(2*node+1, start, mid, l, r);
        int right = query(2*node+2, mid+1, end, l, r);

        return left + right;
    }

    void update(int node, int start, int end, int idx, int val){
        if(start == end){
            tree[node] = val;
        } else {
            int mid = (start + end) / 2;

            if(idx <= mid){
                update(2*node+1, start, mid, idx, val);
            } else {
                update(2*node+2, mid+1, end, idx, val);
            }

            tree[node] = tree[2*node+1] + tree[2*node+2];
        }
    }
}
```

---

# 🧠 When to Use What

```text
DP → optimization problems  
Union-Find → connectivity / cycle detection  
Segment Tree → range queries + updates  
```

---

# 🔥 Final Tip

```text
Don’t memorize blindly  
Understand pattern → reuse template  
```

---


---
