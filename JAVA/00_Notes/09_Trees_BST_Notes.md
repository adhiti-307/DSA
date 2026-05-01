# 📘 Trees & Binary Search Trees (BST) – Complete Notes

---

# 🔹 1. What is a Tree?

A Tree is a **hierarchical data structure** consisting of nodes connected by edges.

---

## 🔸 Basic Terminology

```text id="tree1"
Root → top node  
Parent → node having children  
Child → node derived from parent  
Leaf → node with no children  
Height → longest path from root to leaf  
Depth → distance from root  
```

---

## 🔸 Tree Representation

```text id="tree2"
        1
       / \
      2   3
     / \
    4   5
```

---

# 🔹 2. Types of Trees

* Binary Tree
* Binary Search Tree (BST)
* Complete Binary Tree
* Full Binary Tree
* Balanced Tree

---

# 🔹 3. Binary Tree

Each node has at most **2 children**

```text id="bt1"
Node
 /  \
L    R
```

---

# 🔹 4. Tree Traversals

---

## 🔸 4.1 Inorder (Left → Root → Right)

```text id="inorder"
4 → 2 → 5 → 1 → 3
```

```java id="tr1"
void inorder(Node root){
    if(root == null) return;

    inorder(root.left);
    System.out.print(root.data + " ");
    inorder(root.right);
}
```

---

## 🔸 4.2 Preorder (Root → Left → Right)

```text id="preorder"
1 → 2 → 4 → 5 → 3
```

```java id="tr2"
void preorder(Node root){
    if(root == null) return;

    System.out.print(root.data + " ");
    preorder(root.left);
    preorder(root.right);
}
```

---

## 🔸 4.3 Postorder (Left → Right → Root)

```text id="postorder"
4 → 5 → 2 → 3 → 1
```

```java id="tr3"
void postorder(Node root){
    if(root == null) return;

    postorder(root.left);
    postorder(root.right);
    System.out.print(root.data + " ");
}
```

---

## 🔸 4.4 Level Order (BFS)

```text id="levelorder"
1 → 2 → 3 → 4 → 5
```

```java id="tr4"
Queue<Node> q = new LinkedList<>();
q.add(root);

while(!q.isEmpty()){
    Node node = q.poll();
    System.out.print(node.data + " ");

    if(node.left != null) q.add(node.left);
    if(node.right != null) q.add(node.right);
}
```

---

# 🔹 5. Important Tree Problems

---

## 🔸 5.1 Height of Tree

```java id="ht1"
int height(Node root){
    if(root == null) return 0;

    return 1 + Math.max(height(root.left), height(root.right));
}
```

---

## 🔸 5.2 Diameter of Tree

```java id="dia1"
int diameter(Node root){
    if(root == null) return 0;

    int left = height(root.left);
    int right = height(root.right);

    return Math.max(left + right,
           Math.max(diameter(root.left), diameter(root.right)));
}
```

---

## 🔸 5.3 Lowest Common Ancestor (LCA)

```java id="lca1"
Node lca(Node root, Node p, Node q){
    if(root == null || root == p || root == q) return root;

    Node left = lca(root.left, p, q);
    Node right = lca(root.right, p, q);

    if(left != null && right != null) return root;

    return left != null ? left : right;
}
```

---

# 🔹 6. Binary Search Tree (BST)

A BST is a binary tree where:

```text id="bst1"
Left subtree < Root < Right subtree
```

---

## 🔸 Example

```text id="bst2"
        5
       / \
      3   7
     / \   \
    2   4   9
```

---

# 🔹 7. BST Operations

---

## 🔸 7.1 Search

```java id="bsts"
boolean search(Node root, int key){
    if(root == null) return false;

    if(root.data == key) return true;
    if(key < root.data) return search(root.left, key);

    return search(root.right, key);
}
```

---

## 🔸 7.2 Insertion

```java id="bsti"
Node insert(Node root, int key){
    if(root == null) return new Node(key);

    if(key < root.data)
        root.left = insert(root.left, key);
    else
        root.right = insert(root.right, key);

    return root;
}
```

---

## 🔸 7.3 Deletion

```java id="bstd"
Node delete(Node root, int key){
    if(root == null) return null;

    if(key < root.data)
        root.left = delete(root.left, key);
    else if(key > root.data)
        root.right = delete(root.right, key);
    else{
        if(root.left == null) return root.right;
        if(root.right == null) return root.left;

        Node min = findMin(root.right);
        root.data = min.data;
        root.right = delete(root.right, min.data);
    }
    return root;
}
```

---

# 🔹 8. Important BST Concepts

---

## 🔸 Inorder Traversal

```text id="bst3"
Always gives sorted order
```

---

## 🔸 Kth Smallest Element

Use inorder traversal

---

## 🔸 Validate BST

```java id="bstv"
boolean isValid(Node root, long min, long max){
    if(root == null) return true;

    if(root.data <= min || root.data >= max) return false;

    return isValid(root.left, min, root.data) &&
           isValid(root.right, root.data, max);
}
```

---

# 🔹 9. Time Complexity

| Operation | BST (Avg) | BST (Worst) |
| --------- | --------- | ----------- |
| Search    | O(log n)  | O(n)        |
| Insert    | O(log n)  | O(n)        |
| Delete    | O(log n)  | O(n)        |

---

# 🔹 10. Common Mistakes

```text id="misttree"
❌ Not handling null nodes  
❌ Incorrect traversal order  
❌ Ignoring BST property  
❌ Stack overflow in recursion  
```

---

# 🔹 11. Interview Tips

```text id="tiptree"
✔ Use recursion for trees  
✔ Draw tree before solving  
✔ Use inorder for BST problems  
✔ Think in terms of subtrees  
```

---

# 🧠 Quick Revision

```text id="revtree"
Tree → hierarchical  
Traversal → DFS/BFS  
BST → sorted property  
Inorder → sorted output  
```

---

# 🔥 Final Insight

```text id="fintree"
Tree problems = recursion + structure understanding
```

👉 Master traversal → solve most tree problems

---
