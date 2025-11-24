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
