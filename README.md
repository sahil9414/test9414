# Spiral Archipelago — Twin Portals
Time Limit: **2 seconds**  
Memory Limit: **512 MB**

The Spiral Archipelago is built in tiers. Tier $k$ contains $S[k]$ islands labeled $1$ through $S[k]$. The sizes follow:  
- $S[0] = 1$, $S[1] = 2$, and for $k \geq 2$, $S[k] = S[k-1] + S[k-2]$.

The tier- $k$ archipelago $A(k)$ is constructed as follows:
- $A(k)$ has $S[k]$ islands labeled $1..S[k]$.
- For $k \geq 2$, let $m = S[k-1]$ and $r = m + 1$.  
  - Islands $1..m$ form a copy of $A(k-1)$ (labels unchanged).  
  - Islands $r..S[k]$ form a copy of $A(k-2)$ (with labels increased by $m$).  
  - Two additional bidirectional edges (twin portals) are added:  
    - $(1, r)$ and $(m, r)$.  
- All edges (both inherited from the sub-archipelagos and the two portals) are bidirectional and have unit cost.

You are given $t$ travel requests on a fixed tier $n$ archipelago $A(n)$. For each request, given two distinct islands $a$ and $b$ ($1 \leq a, b \leq S[n]$), determine:
- $d$: the minimal number of edges between $a$ and $b$;  
- $c$: the number of distinct shortest paths between $a$ and $b$, modulo $1\,000\,000\,007$.

Input constraints guarantee that $a$ and $b$ are valid islands in $A(n)$.


## Input Format
- The first line contains two integers $t$ and $n$.  
- Each of the next $t$ lines contains two integers $a$ and $b$ — the endpoints of a query.  


## Output Format
- For each query, output two integers $d$ and $c$:  
  - $d$ is the minimum number of edges between $a$ and $b$ in $A(n)$,  
  - $c$ is the number of distinct shortest paths between $a$ and $b$ modulo $1\,000\,000\,007$.  


## Constraints
- $1 \leq t \leq 100000$  
- $1 \leq n \leq 1000$  
- $1 \leq a, b \leq \min(S[n], 10^{16}),\ a \neq b$  
- $S[0] = 1,\ S[1] = 2,\ S[k] = S[k-1] + S[k-2]$ for $k \geq 2$  
- All edges are undirected and have unit length  
- Output $c$ modulo $1\,000\,000\,007$  


## Examples
 - **Input:**
```
3 3
2 5
1 5
4 5
```

 - **Output:**
```
3 2
2 1
1 1
```

 - **Explanation:** (input: $3\ 3$ with queries $(2,5)$, $(1,5)$, $(4,5)$)
   - In $A(3)$: left is $A(2)$ (triangle on $\{1,2,3\}$), right is $A(1)$ (edge $4$–$5$); portals $(1,4)$ and $(3,4)$.
   - $(2,5)$ has two shortest routes via $4$: $2\!\to\!1\!\to\!4\!\to\!5$ and $2\!\to\!3\!\to\!4\!\to\!5$ $\Rightarrow d=3,\ c=2$.
   - $(1,5)$ uses $(1,4)$ then $(4,5)$ $\Rightarrow d=2,\ c=1$; $(4,5)$ are neighbors $\Rightarrow d=1,\ c=1$.


 - **Input:**
```
6 4
1 8
2 7
3 5
1 4
6 8
2 3
```

 - **Output:**
```
2 1
3 1
2 1
1 1
1 1
1 1
```

 - **Explanation:** (input: $6\ 4$ with queries $(1,8)$, $(2,7)$, $(3,5)$, $(1,4)$, $(6,8)$, $(2,3)$)
    - In $A(4)$: left is $A(3)$ on $\{1..5\}$, right is $A(2)$ (triangle) on $\{6,7,8\}$; portals $(1,6)$ and $(5,6)$.
    - $(1,8)$ goes $1\!\to\!6\!\to\!8$ $\Rightarrow d=2,\ c=1$; $(2,7)$ goes via $1$: $2\!\to\!1\!\to\!6\!\to\!7$ $\Rightarrow d=3,\ c=1$.
    - Neighbors give $(1,4)$, $(6,8)$, $(2,3)$ each $d=1,\ c=1$; $(3,5)$ uses $3\!\to\!4\!\to\!5$ $\Rightarrow d=2,\ c=1$.


