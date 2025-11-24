# Ex22 Searching for a Book ID in a Binary Search Tree (BST)
## DATE:
## AIM:
To design and implement java program that constructs a Binary Search Tree (BST) using given Book IDs and checks whether a specific Book ID exists in the BST.
## Algorithm
1. Start
2. Read the number of Book IDs n
3. Create an empty Binary Search Tree
4. Insert each Book ID into the BST by comparing values:
      a. If tree is empty create root
      b. If new value is smaller insert in left subtree
      c. If new value is larger insert in right subtree
5. Read the Book ID key to be searched
6. Traverse the BST starting from the root:
      a. If root.data equals key return true
      b. If key is less than root.data move to left child
      c. If key is greater than root.data move to right child
7. If traversal ends return false
8. Display whether the Book ID exists in the BST
9. Stop


## Program:
```java
/*
Program to constructs a Binary Search Tree (BST) using given Book IDs 
Developed by: HARI PRIYA M 
RegisterNumber: 212224240047 
*/

import java.util.*;

public class Node {

    static class BSTNode {
        int data;
        BSTNode left, right;

        BSTNode(int data) {
            this.data = data;
            this.left = this.right = null;
        }
    }

    public static BSTNode insert(BSTNode root, int data) {
        if (root == null)
            return new BSTNode(data);
        if (data < root.data)
            root.left = insert(root.left, data);
        else
            root.right = insert(root.right, data);
        return root;
    }

    public static boolean search(BSTNode root, int key) {
        while (root != null) {
            if (root.data == key)
                return true;
            else if (key < root.data)
                root = root.left;
            else
                root = root.right;
        }
        return false;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        BSTNode root = null;

        System.out.print("Enter number of Book IDs: ");
        int n = sc.nextInt();

        System.out.println("Enter Book IDs:");
        for (int i = 0; i < n; i++) {
            root = insert(root, sc.nextInt());
        }

        System.out.print("Enter Book ID to search: ");
        int key = sc.nextInt();

        if (search(root, key))
            System.out.println("Book ID found in BST");
        else
            System.out.println("Book ID not found in BST");

        sc.close();
    }
}

```

## Output:
<img width="428" height="287" alt="image" src="https://github.com/user-attachments/assets/061e335d-ebe0-41c1-a39f-7057fcb36ff1" />



## Result:
The program has been successfully implemented and executed.
It constructs a Binary Search Tree from the given Book IDs and accurately determines whether a queried Book ID exists in the library system.
