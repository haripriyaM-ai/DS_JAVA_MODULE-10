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
