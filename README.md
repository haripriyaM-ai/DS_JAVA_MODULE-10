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
It constructs a Binary Search Tree from the given Book IDs and accurately determines whether a queried Book ID exists in the library system.# Ex22 Searching for a Book ID in a Binary Search Tree (BST)
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
# Ex23 Breadth-First Search (BFS) Traversal of a City Junction Map
## DATE:
## AIM:
To design and implement a java program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph, and find all reachable locations from a given source junction.
## Algorithm
1. Start
2. Read the number of junctions (vertices) and roads (edges)
3. Create a graph using adjacency lists
4. For each road, add an edge between source and destination
5. Read the source junction for BFS traversal
6. Initialize a visited array and an empty queue
7. Mark the source as visited and enqueue it
8. While queue is not empty:
      a. Dequeue a node and display it
      b. For each adjacent unvisited node:
            i. Mark it visited
            ii. Enqueue it
9. Stop after all reachable nodes are processed


## Program:
```java
/*
Program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph
Developed by: HARI PRIYA M 
RegisterNumber: 212224240047  
*/

import java.util.*;

public class Node {

    static class Graph {
        int vertices;
        ArrayList<LinkedList<Integer>> adj;

        Graph(int v) {
            vertices = v;
            adj = new ArrayList<>();
            for (int i = 0; i < v; i++) {
                adj.add(new LinkedList<>());
            }
        }

        void addEdge(int src, int dest) {
            adj.get(src).add(dest);
        }

        void BFS(int start) {
            boolean[] visited = new boolean[vertices];
            Queue<Integer> queue = new LinkedList<>();

            visited[start] = true;
            queue.add(start);

            System.out.println("Reachable locations from source " + start + ":");
            while (!queue.isEmpty()) {
                int node = queue.poll();
                System.out.print(node + " ");

                for (int next : adj.get(node)) {
                    if (!visited[next]) {
                        visited[next] = true;
                        queue.add(next);
                    }
                }
            }
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of junctions: ");
        int v = sc.nextInt();

        Graph g = new Graph(v);

        System.out.print("Enter number of roads: ");
        int e = sc.nextInt();

        System.out.println("Enter road connections (src dest):");
        for (int i = 0; i < e; i++) {
            int src = sc.nextInt();
            int dest = sc.nextInt();
            g.addEdge(src, dest);
        }

        System.out.print("Enter source junction: ");
        int start = sc.nextInt();

        g.BFS(start);

        sc.close();
    }
}


```

## Output:
<img width="511" height="476" alt="image" src="https://github.com/user-attachments/assets/280fd3b8-e6b3-4cf4-9d48-85579244d40d" />



## Result:
The program has been successfully implemented and executed.
It performs Breadth-First Search (BFS) traversal on a city junction map and correctly lists all reachable locations from the given source node.

# Ex24 Shortest Path and Reachability in a Heritage Town using BFS
## DATE:
## AIM:
To design and implement a java program that, given a map of attractions in a heritage town connected by walking paths, recommends:
The shortest number of paths (minimum hops) from a starting attraction to a target attraction.
The number of reachable attractions from the same starting point using Breadth-First Search (BFS)


## Algorithm
1. Start
2. Read the number of attractions (vertices) and paths (edges)
3. Create a graph using adjacency lists
4. Add each walking path between attractions
5. Read the starting attraction and target attraction
6. To find minimum hops:
      a. Use BFS and maintain a distance array initialized as -1
      b. Set distance[start] = 0 and enqueue start
      c. While queue is not empty, update distance for each neighbor
      d. Stop when target is reached
7. To count reachable attractions:
      a. Use BFS with a visited array starting from the start node
      b. Count all visited nodes until BFS completes
8. Display minimum hops and reachable attraction count
9. Stop
   

## Program:
```java
/*
Program to determine Shortest Path and Reachability in a Heritage Town using BFS
Developed by: HARI PRIYA M 
RegisterNumber: 212224240047   
*/

import java.util.*;

public class Node {

    static class Graph {
        int vertices;
        ArrayList<LinkedList<Integer>> adj;

        Graph(int v) {
            vertices = v;
            adj = new ArrayList<>();
            for (int i = 0; i < v; i++) {
                adj.add(new LinkedList<>());
            }
        }

        void addEdge(int src, int dest) {
            adj.get(src).add(dest);
            adj.get(dest).add(src);
        }

        int shortestPath(int start, int target) {
            boolean[] visited = new boolean[vertices];
            int[] distance = new int[vertices];
            Arrays.fill(distance, -1);

            Queue<Integer> q = new LinkedList<>();
            visited[start] = true;
            distance[start] = 0;
            q.add(start);

            while (!q.isEmpty()) {
                int node = q.poll();
                if (node == target)
                    return distance[node];

                for (int next : adj.get(node)) {
                    if (!visited[next]) {
                        visited[next] = true;
                        distance[next] = distance[node] + 1;
                        q.add(next);
                    }
                }
            }
            return -1;
        }

        int reachableCount(int start) {
            boolean[] visited = new boolean[vertices];
            Queue<Integer> q = new LinkedList<>();
            visited[start] = true;
            q.add(start);
            int count = 1;

            while (!q.isEmpty()) {
                int node = q.poll();
                for (int next : adj.get(node)) {
                    if (!visited[next]) {
                        visited[next] = true;
                        q.add(next);
                        count++;
                    }
                }
            }
            return count;
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of attractions: ");
        int v = sc.nextInt();

        Graph g = new Graph(v);

        System.out.print("Enter number of walking paths: ");
        int e = sc.nextInt();

        System.out.println("Enter paths (source destination):");
        for (int i = 0; i < e; i++) {
            int src = sc.nextInt();
            int dest = sc.nextInt();
            g.addEdge(src, dest);
        }

        System.out.print("Enter starting attraction: ");
        int start = sc.nextInt();

        System.out.print("Enter target attraction: ");
        int target = sc.nextInt();

        int shortest = g.shortestPath(start, target);
        int reach = g.reachableCount(start);

        if (shortest != -1)
            System.out.println("Minimum hops to reach target: " + shortest);
        else
            System.out.println("Target not reachable");

        System.out.println("Total reachable attractions: " + reach);

        sc.close();
    }
}

```

## Output:
<img width="492" height="467" alt="image" src="https://github.com/user-attachments/assets/31329706-fc6c-47a1-99b3-4a4c28136629" />



## Result:
The program has been successfully implemented and executed.
It correctly computes:
The shortest number of paths (minimum hops) between two attractions.
The total number of reachable attractions from a given starting point using BFS traversal.

# Ex25 Finding the Fastest Route to a Charging Station using Dijkstra’s Algorithm
## DATE:
## AIM:
To design and implement a java program that helps an electric vehicle (EV) find the shortest travel time from its current block to the nearest charging station using Dijkstra’s shortest path algorithm.
## Algorithm
1. Start
2. Read number of blocks (vertices) and roads (edges)
3. Create a weighted graph using adjacency lists
4. Input all road connections and travel time between blocks
5. Read the EV's current block and target charging station
6. Initialize a distance array with infinity and set distance[start] = 0
7. Use a min-priority queue to always extract the node with the minimum distance
8. Update travel time to adjacent nodes if a shorter path is found
9. Continue until the priority queue becomes empty or the target is reached
10. Output the minimum travel time or unreachable message
11. Stop
 

## Program:
```java
/*
Program to find the Fastest Route to a Charging Station using Dijkstra’s Algorithm
Developed by: HARI PRIYA M 
RegisterNumber: 212224240047  
*/

import java.util.*;

public class Node {

    static class Pair {
        int v, w;
        Pair(int v, int w) {
            this.v = v;
            this.w = w;
        }
    }

    static class Graph {
        int vertices;
        ArrayList<ArrayList<Pair>> adj;

        Graph(int v) {
            vertices = v;
            adj = new ArrayList<>();
            for (int i = 0; i < v; i++) {
                adj.add(new ArrayList<>());
            }
        }

        void addEdge(int src, int dest, int wt) {
            adj.get(src).add(new Pair(dest, wt));
            adj.get(dest).add(new Pair(src, wt));
        }

        int dijkstra(int start, int target) {
            int[] dist = new int[vertices];
            Arrays.fill(dist, Integer.MAX_VALUE);
            dist[start] = 0;

            PriorityQueue<Pair> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a.w));
            pq.add(new Pair(start, 0));

            while (!pq.isEmpty()) {
                Pair curr = pq.poll();
                int node = curr.v;
                int d = curr.w;

                if (node == target) return d;

                for (Pair p : adj.get(node)) {
                    if (d + p.w < dist[p.v]) {
                        dist[p.v] = d + p.w;
                        pq.add(new Pair(p.v, dist[p.v]));
                    }
                }
            }
            return -1;
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of blocks: ");
        int v = sc.nextInt();

        Graph g = new Graph(v);

        System.out.print("Enter number of roads: ");
        int e = sc.nextInt();

        System.out.println("Enter road details (src dest time):");
        for (int i = 0; i < e; i++) {
            g.addEdge(sc.nextInt(), sc.nextInt(), sc.nextInt());
        }

        System.out.print("Enter current block of EV: ");
        int start = sc.nextInt();

        System.out.print("Enter charging station block: ");
        int target = sc.nextInt();

        int ans = g.dijkstra(start, target);

        if (ans != -1)
            System.out.println("Fastest travel time to charging station: " + ans);
        else
            System.out.println("Charging station unreachable");

        sc.close();
    }
}

```

## Output:
<img width="570" height="522" alt="image" src="https://github.com/user-attachments/assets/3e3f05dd-df65-479d-b0be-7f5709f32965" />



## Result:
The program has been successfully implemented and executed.
It uses Dijkstra’s algorithm to determine the shortest travel time from the EV’s current location to the nearest charging station and correctly handles cases where no station is reachable.
