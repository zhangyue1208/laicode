##### Symmetric Binary Tree

Check if a given binary tree is symmetric.

**Examples**
```
        5
      /    \
    3        3
  /   \    /   \
1      4  4     1
```
is symmetric.
```
        5
      /    \
    3        3
  /   \    /   \
1      4  1     4
```
is not symmetric.

**Corner Cases**

* What if the given binary tree is null? Return an empty list in this case.

**How is the binary tree represented?**

* We use the level order traversal sequence with a special symbol "#" denoting the null node.

**For Example:**

The sequence [1, 2, 3, #, #, 4] represents the following binary tree:
```
    1
  /   \
 2     3
      /
    4
```

```java
/**
 * public class TreeNode {
 *   public int key;
 *   public TreeNode left;
 *   public TreeNode right;
 *   public TreeNode(int key) {
 *     this.key = key;
 *   }
 * }
 */
public class Solution {
    public boolean isSymmetric(TreeNode root) {
        if (root == null) {
            return true;
        }

        return isSymmetric(root.left, root.right);
    }

    public boolean isSymmetric(TreeNode node1, TreeNode node2) {
        if (node1 == null && node2 == null) {
            return true;
        } else if (node1 == null || node2 == null) {
            return false;
        } else if (node1.key != node2.key) {
            return false;
        }

        return isSymmetric(node1.left, node2.right) && isSymmetric(node1.right, node2.left);
    }
}
```