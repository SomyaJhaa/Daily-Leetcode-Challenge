# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 23-02-24 [Problem Link](https://leetcode.com/problems/cheapest-flights-within-k-stops/description/?envType=daily-question&envId=2024-02-23)
## 787. Cheapest Flights Within K Stops

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
This problem involves finding the cheapest price to travel from a source city to a destination city with a constraint on the maximum number of stops allowed. This can be solved using Dijkstra's algorithm, which is a graph search algorithm that finds the shortest paths between nodes in a graph.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialized the Graph :**
   - Created an adjacency list to represent the graph, where each node contained a list of neighboring nodes and their corresponding weights.

**Initialized the Data Structures :**
   - Created a priority queue (minHeap) to store information about the current distance, current node, and remaining stops.
   - Initialized a 2D array (`dist`) to store the minimum distances from the source to each node with a specific number of stops remaining.

**Dijkstra's Algorithm :**
   - Initialized the distance from the source to itself with the maximum number of stops allowed to be 0.
   - Added the source node to the priority queue with the initial distance.
   - Performed the main loop of Dijkstra's algorithm :
     - Popped the node with the minimum distance from the priority queue.
     - If the current node is the destination, returned the minimum cost.
     - If the remaining stops are 0, skipped to the next iteration.
     - Relaxation step : Updated the distances to neighbors and added them to the priority queue if a shorter path is found.

**Result :**
   - If the destination is not reachable within the allowed stops, returned -1.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)

# Complexity
- Time complexity : $O((V + E) * log(V))$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$V$ : number of nodes
$E$ : number of edges in the graph

- Space complexity : $O(V + E)$ 
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Static variables for graph, minHeap, and distance matrix
    static List<Pair<Integer, Integer>>[] graph;
    static Queue<int[]> minHeap;
    static int[][] dist;

    // Main function to find the cheapest price using Dijkstra's algorithm
    public int findCheapestPrice(int n, int[][] flights, int src, int dst, int k) {
        
        // Initializing the graph as an adjacency list
        graph = new List[n];
        for (int i = 0; i < n; i++)
            graph[i] = new ArrayList<>();

        // Populating the graph with flight information
        for (int[] flight : flights) {
            int u = flight[0];
            int v = flight[1];
            int w = flight[2];
            graph[u].add(new Pair<>(v, w));
        }

        // Initializing the minHeap with a custom comparator for Dijkstra's algorithm
        minHeap = new PriorityQueue<>(Comparator.comparingInt(a -> a[0]));

        // Initializing the distance matrix with maximum values
        dist = new int[graph.length][k + 2];
        for (int[] row : dist)
            Arrays.fill(row, Integer.MAX_VALUE);

        // Setting the distance from source to source with k stops remaining to 0
        dist[src][k + 1] = 0;
        minHeap.offer(new int[]{dist[src][k + 1], src, k + 1});

        // Calling the helper function to perform Dijkstra's algorithm
        return helperDijkstra(src, dst, k);
    }

    // Helper function for Dijkstra's algorithm
    private static int helperDijkstra(int src, int dst, int k) {
        // Main loop for Dijkstra's algorithm
        while (!minHeap.isEmpty()) {
            int d = minHeap.peek()[0];
            int u = minHeap.peek()[1];
            int stops = minHeap.poll()[2];

            // If the destination is reached, returning the minimum cost
            if (u == dst)
                return d;

            // If no more stops allowed, skipping to the next iteration
            if (stops == 0)
                continue;

            // Relaxation step - update distances to neighbors
            for (Pair<Integer, Integer> pair : graph[u]) {
                int v = pair.getKey();
                int w = pair.getValue();
                if (d + w < dist[v][stops - 1]) {
                    dist[v][stops - 1] = d + w;
                    minHeap.offer(new int[]{dist[v][stops - 1], v, stops - 1});
                }
            }
        }

        // If the destination is not reachable within allowed stops, returning -1
        return -1;
    }
}
```