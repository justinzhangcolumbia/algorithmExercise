preorder traversal
---
1. Non-Recursion

记忆方法就是把最左边的点的右child和左child依次放入stack，必须先放右child，这样的话stack最上面是左child，先pop出来的是左child，preorder是一路往左走，走到底，再返回上来
```
public List<Integer> preorderTraversal(TreeNode root) {
    Stack<TreeNode> stack = new Stack<TreeNode>();
    List<Integer> preorder = new ArrayList<Integer>();

    if (root == null) {
        return preorder;
    }

    stack.push(root);
    while (!stack.empty()) {
        TreeNode node = stack.pop();
        preorder.add(node.val);
        if (node.right != null) {
            stack.push(node.right);
        }
        if (node.left != null) {
            stack.push(node.left);
        }
    }
    return preorder;
}
```
2. Recursion
```
public ArrayList<Integer> preorderTraversal(TreeNode root) {
    ArrayList<Integer> result = new ArrayList<Integer>();
    traverse(root, result);
    return result;
}
// 把root为跟的preorder加入result里面
private void traverse(TreeNode root, ArrayList<Integer> result) {
    if (root == null) {
        return;
    }
    result.add(root.val);
    traverse(root.left, result);
    traverse(root.right, result);
}
```

inorder traversal
----
1. Non-Recursion

记忆方法是，inorder先要一路往左走，不记录这个过程中的点，走到底，记录第一个点，第二个while循环的作用就是走到整个tree的底部
```
public ArrayList<Integer> inorderTraversal(TreeNode root) {
    Stack<TreeNode> stack = new Stack<TreeNode>();
    ArrayList<Integer> result = new ArrayList<Integer>();
    TreeNode curt = root;
    while (curt != null || !stack.empty()) {
        while (curt != null) {
            stack.add(curt);
            curt = curt.left;
        }
        curt = stack.pop();
        result.add(curt.val);
        curt = curt.right;
    }
    return result;
}
```
2. Recursion
```
public ArrayList<Integer> preorderTraversal(TreeNode root) {
    ArrayList<Integer> result = new ArrayList<Integer>();
    traverse(root, result);
    return result;
}
// 把root为跟的preorder加入result里面
private void traverse(TreeNode root, ArrayList<Integer> result) {
    if (root == null) {
        return;
    }
    traverse(root.left, result);
    result.add(root.val);
    traverse(root.right, result);
}

```

postorder traversal
----
1. Non-Recursion
one stack solution(时间复杂度O(n)，空间复杂度是O(h), h是Tree的高度)
postorder始终要遵循左右中的顺序。
当pre和cur的关系是从上到下时（左右两种情况，pre=null就是root时候的情况），始终先放左边的child先，如果没有左边的child的再放右边的child。
当pre在cur的左边时，说明cur的左边已经遍历完了，要开始遍历cur的右边，所以检查一下cur有没有右child，有的话就放入stack。
当pre在cur的右边时，说明cur的左边和右边都已经遍历完了，只要把cur（三角的root）点放入result，并pop掉就可以了。
当pre和cur相等时，说明可能是cur是leaf可以放入result并pop，也可能是左边遍历完了没有右child，都是属于else，可以将结果放入result并pop。
```
public ArrayList<Integer> postorderTraversal(TreeNode root) {
    ArrayList<Integer> result = new ArrayList<Integer>();
    Stack<TreeNode> stack = new Stack<TreeNode>();
    TreeNode prev = null; // previously traversed node
    TreeNode curr = root;

    if (root == null) {
        return result;
    }

    stack.push(root);
    while (!stack.empty()) {
        curr = stack.peek();
        if (prev == null || prev.left == curr || prev.right == curr) { // traverse down the tree
            if (curr.left != null) {
                stack.push(curr.left);
            } else if (curr.right != null) {
                stack.push(curr.right);
            }
        } else if (curr.left == prev) { // traverse up the tree from the left
            if (curr.right != null) {
                stack.push(curr.right);
            }
        } else { // traverse up the tree from the right
            result.add(curr.val);
            stack.pop();
        }
        prev = curr;
    }

    return result;
}
```
two stack solution(时间复杂度相同，空间复杂度是O(n))
```
public ArrayList<Integer> postorderTraversal(TreeNode root) {
    ArrayList<Integer> result = new ArrayList<Integer>();
    Stack<TreeNode> stack1 = new Stack<TreeNode>();
    Stack<TreeNode> stack1 = new Stack<TreeNode>();
    if (root == null) {
        return result;
    }
    stack1.push(root);
    while (!stack1.empty()) {
        root = stack1.pop();
        stack2.push(root);
        if (root.left != null) {
            stack2.push(root.left);
        }
        if (root.right != null) {
            stack2.push(root.right);
        }
    }
    while (!stack2.empty()) {
        root = stack2.pop();
        result.add(root.val);
    }
    return result;
    
```
2. Recursion
```
public ArrayList<Integer> postorderTraversal(TreeNode root) {
    ArrayList<Integer> result = new ArrayList<Integer>();

    if (root == null) {
        return result;
    }

    result.addAll(postorderTraversal(root.left));
    result.addAll(postorderTraversal(root.right));
    result.add(root.val);

    return result;   
}
```

tree level traversal(BFS)
----
```
public List<List<Integer>> levelOrder(TreeNode root) {
    List result = new ArrayList();

    if (root == null) {
        return result;
    }

    Queue<TreeNode> queue = new LinkedList<TreeNode>();
    queue.offer(root);

    while (!queue.isEmpty()) {
        ArrayList<Integer> level = new ArrayList<Integer>();
        int size = queue.size();
        for (int i = 0; i < size; i++) {
            TreeNode head = queue.poll();
            level.add(head.val);
            if (head.left != null) {
                queue.offer(head.left);
            }
            if (head.right != null) {
                queue.offer(head.right);
            }
        }
        result.add(level);
    }

    return result;
}

```
