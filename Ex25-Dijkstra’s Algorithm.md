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
