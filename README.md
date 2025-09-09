# The Last Courier’s Outpost
Time Limit: **2 seconds**  
Memory Limit: **512 MB**

Along a long, straight trade route marked at integer milestones $0$ through $m$, there are $n$ established courier outposts at positions $a_1, a_2, \dots, a_n$ (each $a_i$ is an integer in $[0, m]$). When a shipment request appears at milestone $T$ (an integer in $[0, m]$), exactly $k$ outposts are assigned to it: the ones with the smallest distances $| \text{position} - T |$. If multiple outposts tie for the last slot, the established (existing) outposts take precedence over the rookie; ties among existing outposts can be broken arbitrarily but consistently. A new rookie courier arrives and must choose a milestone $x \in [0, m]$ (integer) for his outpost. The rookie always loses ties against existing outposts.

Shipments don’t appear uniformly. There are $q$ forecasts; each forecast is a range update $(L, R, w)$ that adds $w$ to the expected weight of every shipment location $T$ with $L \leq T \leq R$. The total weight at each $T$ is the sum of all updates covering $T$.

For a chosen $x$, define the rookie’s score as the sum of weights of all $T \in [0, m]$ where the rookie would be selected among the $k$ assigned outposts (considering all $n$ existing outposts plus the rookie at $x$). Your task is to choose $x$ to maximize this score; if multiple $x$ achieve the same maximum, choose the smallest such $x$.

**Notes:**
- All positions and $T$ are integers.
- If $k \geq n + 1$, then the rookie is always selected for every $T$, regardless of $x$.


## Input Format
- The first line contains four integers $n, m, k, q$.  
- The second line contains $n$ integers $a_1, a_2, \dots, a_n$ ($0 \leq a_i \leq m$), the positions of existing outposts.  
- The next $q$ lines each contain three integers $L, R, w$, meaning add $w$ to every $T$ with $L \leq T \leq R$.  

## Output Format
- Print two integers: the maximum total weight the rookie can secure, and the smallest $x \in [0, m]$ achieving this maximum.  


## Constraints
- $1 \leq n \leq 2 \cdot 10^{5}$  
- $0 \leq m \leq 2 \cdot 10^{6}$  
- $1 \leq k \leq 2 \cdot 10^{5}$  
- $1 \leq q \leq 2 \cdot 10^{5}$  
- $0 \leq a_i \leq m$  
- $0 \leq L \leq R \leq m$  
- $1 \leq w \leq 10^{12}$  
- The total sum of weights over $T = 0..m$ is positive.  


## Examples

 - **Input:**
```
3 6 2 2
1 4 5
0 3 2
4 6 1
```

 - **Output:**
```
8 2
```

 - **Explanation:**
    - Build weights: $W(0..3)=2$, $W(4..6)=1$ from the two range updates.  
    - With existing $\{1,4,5\}$ and $k=2$, the $k$-th nearest distance is $D_2(T)=[4,3,2,2,1,1,2]$ for $T=0..6$.  
    - Rookie is picked at $T$ iff $|x-T|<D_2(T)$. This sum is maximized at $x=2$ (also $3$) with total $8$, so choose smallest $x=2$.

 - **Input:**
```
1 5 3 2
0
2 4 3
0 2 2
```

 - **Output:**
```
15 0
```

 - **Explanation:**
    - Here $k\ge n+1$ ($3\ge2$), so the rookie is chosen for **every** $T$, regardless of $x$.  
    - Total weight $\sum_T W[T]=15$; smallest optimal $x=0$.

 - **Input:**
```
3 6 1 2
2 4 4
0 6 1
5 6 10
```

 - **Output:**
```
22 5
```

 - **Explanation:**
    - Weights: baseline $+1$ on $T=0..6$ and extra $+10$ on $T=5,6$ → $W=[1,1,1,1,1,11,11]$.  
    - With existing $\{2,4,4\}$ and $k=1$, rookie must be strictly closer than the nearest existing: $|x-T|<D_1(T)$ where $D_1(T)=[2,1,0,1,0,1,2]$.  
    - Best is $x=5$, capturing heavy $T=5,6$ for total $22$ (smallest such $x$).   
