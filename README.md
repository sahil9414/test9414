# Runes Between the Relics
Time Limit: **2 seconds**  
Memory Limit: **512 MB**

An archaeologist discovers a long mural etched with runic engravings in a single uninterrupted line. According to lore, pairs of rune sequences separated by a precise empty space mark entrances to hidden chambers. Your mission is to help locate the shortest mural panel that contains two target rune sequences $a$ and $b$ with a valid empty space (gap) between them. Either sequence may appear first, but they must not overlap.

You are given a string $s$ consisting of lowercase English letters. There are $q$ independent queries. Each query gives two non-empty patterns $a$ and $b$ and two integers $L$ and $R$.

For each query, find the minimum length of a substring of $s$ that contains one occurrence of $a$ and one occurrence of $b$ such that:
- The two chosen occurrences do not overlap.
- The number of characters strictly between the two occurrences (the gap) is between $L$ and $R$ inclusive.
- You may choose either order ($a$ before $b$ or $b$ before $a$), whichever yields the minimum.

If such a substring exists, print its minimum length; otherwise, print $-1$.

**Definitions:**
- Positions are $0$-based.
- An occurrence of pattern $p$ starting at index $i$ covers $[i, i + |p| - 1]$.
- Two occurrences do not overlap if these intervals are disjoint.
- If the left occurrence ends at $e$ and the right occurrence starts at $j$, the gap is $j - e - 1$.
- The minimal covering substring is from the left occurrence’s start to the right occurrence’s end.
- If $a = b$, you must choose two distinct, non-overlapping occurrences.
- Non-overlap is mandatory even when $L = 0$.


## Input Format
- The first line contains the string $s$ ($1 \leq |s| \leq 200000$), consisting of lowercase English letters.  
- The second line contains an integer $q$ ($1 \leq q \leq 100000$), the number of queries.  
- Each of the next $q$ lines contains a string $a$, a string $b$ ($1 \leq |a|, |b| \leq 10$), and integers $L$ and $R$ ($0 \leq L \leq R \leq |s|$), separated by spaces.  

## Output Format
- For each query, print a single integer — the minimum length of a valid substring, or $-1$ if none exists.


## Constraints
- $1 \leq |s| \leq 200000$  
- $1 \leq q \leq 100000$  
- $1 \leq |a|, |b| \leq 10$  
- $0 \leq L \leq R \leq |s|$  
- $s, a, b$ consist of lowercase English letters  
- Occurrences must be non-overlapping  


## Examples
 - **Input:**
```
stonefirewaterwind
6
fire water 0 1
stone wind 0 100
one fire 0 1
fire stone 0 100
fire water 1 1
water wind 0 0
```

 - **Output:**
```
9
18
7
9
-1
9
```

 - **Explanation:**
   - fire water 0 1 → pick fire [5..8], water [9..13]; gap $0\in[0,1]$, length $4+5+0=9$.
   - stone wind 0 100 → stone [0..4], wind [14..17]; gap $9\in[0,100]$, length $5+4+9=18$.
   - one fire 0 1 → one [2..4], fire [5..8]; gap $0$, length $3+4+0=7$.
   - fire stone 0 100 → stone [0..4], fire [5..8]; gap $0$, length $5+4+0=9$.
   - fire water 1 1 → no non-overlapping pair with gap in $[1,1]$ → $-1$.
   - water wind 0 0 → water [9..13], wind [14..17]; gap $0$, length $5+4+0=9$.

 - **Input:**
```
aaaaabaaaaa
4
aa aa 0 0
aa aa 1 1
a b 0 0
a a 4 7
```

 - **Output:**
```
4
5
2
6
```
 - **Explanation:**
    - aa aa 0 0 → [0..1] and [2..3]; gap $0$, length $2+2+0=4$.
    - aa aa 1 1 → [0..1] and [3..4]; gap $1$, length $2+2+1=5$.
    - a b 0 0 → a [4], b [5]; gap $0$, length $1+1+0=2$.
    - a a 4 7 → a [1] and a [6]; gap $4$, length $1+1+4=6$.

 - **Input:**
```
catcatdogcatdog
5
cat dog 0 0
dog cat 1 2
cat cat 0 3
at do 0 1
dog cat 0 3
```

 - **Output:**
```
6
-1
6
4
6
```
 - **Explanation:**
   - cat dog 0 0 → cat [3..5], dog [6..8]; gap $0$, length $3+3+0=6$.
   - dog cat 1 2 → no non-overlapping dog→cat with gap in $[1,2]$ → $-1$.
   - cat cat 0 3 → cat [0..2] and [3..5]; gap $0$, length $3+3+0=6$.
   - at do 0 1 → at [4..5], do [6..7]; gap $0$, length $2+2+0=4$.
   - dog cat 0 3 → dog [6..8], cat [9..11]; gap $0$, length $3+3+0=6$.


