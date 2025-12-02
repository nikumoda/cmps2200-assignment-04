# CMPS 2200 Assignment 4
## Answers

**Name:** Nikhil Modayur


- **1a.**

Maximum depth (height) of a d-ary heap with n elements is ⌊log_d n⌋, so O(log_d n).


- **1b.**

delete-min: O(d x log_d n) (per level compare among up to d children). Insert: O(log_d n) (swap up the tree).


- **1c.**

Using a d-ary heap in Dijkstra: |V| delete-min and up to |E| inserts/decrease-keys. Total work: O(|V| x d x log_d |V| + |E| x log_d |V|).

- **1d.**

With |E| = |V|^{1+ε}, choose d = |V|^{ε}. Then log_d |V| = 1/ε, giving total work O(|V| x |V|^{ε}/ε + |E|/ε) = O(|E|).


- **2a.**

With edges from image: 0→1 = −2, 0→2 = 2, 1→2 = 1.

APSP(i,j,0): same as direct edges (allowing 0 as intermediate does not improve any path). Distances: d01=−2, d02=2, d12=1, d00=d11=d22=0, others = ∞.

APSP(i,j,1): allowing vertex 1 as intermediate improves 0→2 via 0→1→2 to −1; all others unchanged. So d02=−1; d01=−2; d12=1; diagonals 0; others = ∞.

APSP(i,j,2): allowing vertex 2 as intermediate does not improve further; distances remain as for k=1.


- **2b.**

Yes. Floyd–Warshall recurrence: APSP(i,j,2) = min(APSP(i,j,1), APSP(i,2,1) + APSP(2,j,1)). More generally, APSP(i,j,1) relates similarly to k=0.


- **2c.**

Optimal substructure: APSP(i,j,k) = min(APSP(i,j,k−1), APSP(i,k,k−1) + APSP(k,j,k−1)).


- **2d.**

Distinct subproblems: n choices of k × n^2 pairs (i,j) = O(n^3). Work: O(n^3).


- **2e.**

Johnson’s: O(|V||E| log |E|). DP: O(|V|^3). DP preferable for dense graphs (|E| ≈ |V|^2), where O(|V|^3) ≤ O(|V|^3 log |V|).


- **3a.**

Yes. Any MST is a minimum bottleneck (MMET) spanning tree; MST minimizes the maximum edge weight by cut/cycle properties.


- **3b.**

Second-best MST: Build MST T. For each non-tree edge e=(u,v), add e to T to form a cycle; identify the maximum-weight edge on the u–v path in T and replace it with e to form candidate tree T_e. Among all candidates with total weight > weight(T), pick the minimum. Use LCA/segment tree to query max edge on a path.


- **3c.**

O(|E| log |V|) total: build MST in O(|E| log |V|), preprocess T for max-edge path queries in O(|V| log |V|), evaluate each of O(|E|−|V|+1) non-tree edges in O(log |V|).
