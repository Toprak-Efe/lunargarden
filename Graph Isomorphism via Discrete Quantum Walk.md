
> [!REFERENCE] Main Article
> https://iopscience.iop.org/article/10.1088/1751-8113/41/7/075303
# Graph Properties
## Diameter
The diameter of a graph is the longest path that connects two vertices with the minimal amount of edges traversed, in other words, it is **the longest shortest path**.
## Girth
The length shortest path in a graph where you end up on the same vertex you started without repeating any vertices is called girth. A graph without any cyclic paths is called an acyclic graph, and it has infinite girth. A square has a girth of 4, a triangle has a girth of 3, a tree has infinite girth and so on.
## Degree
The degree of a vertex is the number of edges connected to that vertex.
## Regularity
A graph is **regular** if every vertex has the same degree. A graph where every vertex has a degree of $k$, is called a $k$-regular graph. A square is a $2$-regular graph.

> [!DEFINITION] Strongly Regular Graphs
> * A strongly regular graph is a regular graph with specific additional properties related to the number of common neighbors between pairs of vertices.
> * More precisely, a strongly regular graph with parameters $(n, k, λ, μ)$ has:
> 	  - $n$ vertices
> 	  - $k$-regular
> 	  - Every two adjacent vertices have $\lambda$ neighbours.
> 	  - Every two non-adjacent vertices have $\mu$ common neighbours.
> * These graphs have a very uniform structure, making them interesting in areas like combinatorics and network theory.
> * They are highly symmetrical.
> * They are used in the construction of error correcting codes, and in the designs of experiments.
## Isomorphism
Two graphs are isomorphic if they have the same structure, even if their vertex labels are different.

> [!EXPLANATION] Meaning
> Essentially, two graphs are isomorphic if you can relabel the vertices of one graph to make it identical to the other. It's a way of saying that the graphs are "the same" in terms of their connections, even if they look different visually. To prove isomorphism, you need to find a bijection (a one-to-one and onto mapping) between the vertex sets of the two graphs that preserves adjacency. For example, a square and a 4 vertex hour glass is isomorphic because you can rotate the top edge of the hourglass to get a square back.
## Automorphism
An automorphism of a graph is a permutation (a rearrangement) of its vertices that preserves the graph's structure. In simpler terms, it's a way to relabel the vertices so that the connections (edges) between them remain exactly the same.

## Vertex-transitive Graphs
