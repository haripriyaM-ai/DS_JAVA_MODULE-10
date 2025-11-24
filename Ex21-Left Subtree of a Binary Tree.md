# Ex21 Count the Number of Nodes in the Left Subtree of a Binary Tree
## DATE:
## AIM:
To design and implement a java program that constructs a binary tree from given level order input and counts the number of nodes present in the left subtree of the root node

## Algorithm
1. Start
2. Read the number of nodes n
3. Read n values in level order and construct the binary tree using a queue
4. Store the root node
5. Traverse and count all nodes in the left subtree of the root using recursion:
      a. If node is null return 0
      b. Return 1 + countNodes(node.left) + countNodes(node.right)
6. Print the total count of nodes in the left subtree
7. Stop
 

## Program:
```java
/*
Program to constructs a binary tree from given level order input and counts the number of nodes 
Developed by: HARI PRIYA M 
RegisterNumber: 212224240047   
*/

import java.util.*;

public class Node {

    static class TreeNode {
        int data;
        TreeNode left, right;

        TreeNode(int data) {
            this.data = data;
            this.left = this.right = null;
        }
    }

    public static TreeNode buildTreeLevelOrder(int n, Scanner sc) {
        if (n == 0) return null;

        TreeNode root = new TreeNode(sc.nextInt());
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);

        int count = 1;

        while (!queue.isEmpty() && count < n) {
            TreeNode current = queue.poll();

            current.left = new TreeNode(sc.nextInt());
            queue.add(current.left);
            count++;

            if (count >= n) break;

            current.right = new TreeNode(sc.nextInt());
            queue.add(current.right);
            count++;
        }
        return root;
    }

    public static int countNodes(TreeNode node) {
        if (node == null)
            return 0;
        return 1 + countNodes(node.left) + countNodes(node.right);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of nodes: ");
        int n = sc.nextInt();

        System.out.println("Enter tree nodes in level order:");
        TreeNode root = buildTreeLevelOrder(n, sc);

        int leftCount = countNodes(root.left);

        System.out.println("Number of nodes in the left subtree: " + leftCount);

        sc.close();
    }
}

```

## Output:
<img width="486" height="282" alt="image" src="https://github.com/user-attachments/assets/b2b38f7b-3395-4183-8591-c1ca8cfa40f8" />



## Result:
The program has been successfully implemented and executed.
It correctly constructs the binary tree from level order input and counts the number of nodes in the left subtree of the root node.
