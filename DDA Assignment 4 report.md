##### DDA 6050 Assignment 4 116020372 Zhu Yulin



#### Q1 

Idea: Find the longest harmonic substring including the first letter, then invert the rest of the string and add them to the front of the input string.

To find the longest harmonious substring including the first letter: first find the index of the center of that. If the input string is `s` and its length is n, start from s[n/2 - 1] and check whether it can be used as the center of the harmonious substring, if not, subtract one more until you find the index of the center of the harmonious substring. Note that the length of the substring could be odd and even, which need to be thought separately.

Time complexity: $O(n^2)$. $T(n) = n + (n - 2) + (n - 4) + ... +  1 = 1/2 * n * n - 1/2 * n * 1/2 * n = 1/4*n^2 = O(n^2)$



#### Q2

Disjoint set union is used to record the nodes are connected.

First, execute Kruskal algorithm to obtain the value of the minimum spanning tree. Then enumerate each edge, determine whether it is a key edge. If not, then determine whether it is a pseudo-key edge.

To determine whether it is a key edge, first remove this edge, then use Kruskal algorithm. if the whole graph is not connected and there is no minimum spanning tree, or the whole graph is connected and the corresponding minimum spanning tree has a weight value, which is strictly greater than value, then the edge is a key edge.

After excluding an edge as a key edge, we then determine whether it is a pseudo-key edge. In the process of computing the minimum spanning tree, this edge is considered first. If the minimum spanning tree can be generated and the final minimum spanning tree weight is the same as the value obtained at the beginning, then this edge is a pseudo-key edge.

Time complexity: $O(m^2⋅α(n))$, where n is the number of nodes and m the number of edges. The time complexity of sorting all edges is $O(mlogm)$. The time complexity of one Kruskal algorithm is $O(m⋅α(n))$. At most $2m+1$ times Kruskal's algorithm needs to be executed, the time complexity is $O(m^2α(n))$, which is greater than the time complexity of sorting in an asymptotic sense.



#### Q3

First, convert the graph into a bipartite graph by splitting each point into two points, input point and output point. Set the start point of the bipartite graph, which leads to each split input point, and set the end point of the bipartite graph, which leads to each split output point.

Fold Fulkerson algorithm is used to obtain the max flow of the bipartite graph from the start point to the end point, and BFS algorithm is used to find a way from start point to the end point in each turn in the Fulkerson algorithm. The final answer is number of point of the input minus the max flow of the bipartite graph.

Time complexity: $O((m + 2n) * f)$, where m is number of edges, n is the number of nodes and f is the maxflow. Time complexity of Fold Fulkerson algorithm is  $O(E * f)$. While there is an augmenting path, a loop is executed. In the worst situation, each loop may add 1 unit flow. For this question, we add 2n edges with the bipartite graph, therefore the number of total edges of the bipartite graph is m + 2n.



#### Q4

In Kruskal's algorithm, the minimum spanning tree selects the edge with the lowest cost each time. So the weight of the edge that affects whether the target edge is definite or not must be smaller than the target edge. Therefore, we only consider edges whose weight is less than or equal to the target edge. A new graph only contains the edges which weight is smaller than the target edge is build, and the weight of each edge of it is equal to target weight - edge weight + 1. The maximum flow of this new graph is equal to the steps of the revision.

Time complexity: $O(t * f)$, where t is the weight rank of target edge and f is the maxflow. Time complexity of Fold Fulkerson algorithm is  $O(E * f)$. While there is an augmenting path, a loop is executed. In the worst situation, each loop may add 1 unit flow. For this question, we only considered the edges weight smaller than the target edge. In the worst case, the weight of t is the biggest in all edges, the time will be $O(E * f)$
