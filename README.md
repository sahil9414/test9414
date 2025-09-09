# Runes Between the Relics
Time Limit: **2 seconds**  
Memory Limit: **512 MB**

An archaeologist discovers a long mural etched with runic engravings in a single uninterrupted line. According to lore, pairs of rune sequences separated by a precise empty space mark entrances to hidden chambers. Your mission is to help locate the shortest mural panel that contains two target rune sequences \(a\) and \(b\) with a valid empty space (gap) between them. Either sequence may appear first, but they must not overlap.

You are given a string \(s\) consisting of lowercase English letters. There are \(q\) independent queries. Each query gives two non-empty patterns \(a\) and \(b\) and two integers \(L\) and \(R\).

For each query, find the minimum length of a substring of \(s\) that contains one occurrence of \(a\) and one occurrence of \(b\) such that:
- The two chosen occurrences do not overlap.
- The number of characters strictly between the two occurrences (the gap) is between \(L\) and \(R\) inclusive.
- You may choose either order (\(a\) before \(b\) or \(b\) before \(a\)), whichever yields the minimum.

If such a substring exists, print its minimum length; otherwise, print \(-1\).

**Definitions:**
- Positions are 0-based.
- An occurrence of pattern \(p\) starting at index \(i\) covers \([i, i + |p| - 1]\).
- Two occurrences do not overlap if these intervals are disjoint.
- If the left occurrence ends at \(e\) and the right occurrence starts at \(j\), the gap is \(j - e - 1\).
- The minimal covering substring is from the left occurrence’s start to the right occurrence’s end.
- If \(a = b\), you must choose two distinct, non-overlapping occurrences.
- Non-overlap is mandatory even when \(L = 0\).


## Input Format
- The first line contains the string \(s\) (\(1 \leq |s| \leq 200000\)), consisting of lowercase English letters.  
- The second line contains an integer \(q\) (\(1 \leq q \leq 100000\)), the number of queries.  
- Each of the next \(q\) lines contains a string \(a\), a string \(b\) (\(1 \leq |a|, |b| \leq 10\)), and integers \(L\) and \(R\) (\(0 \leq L \leq R \leq |s|\)), separated by spaces.  

## Output Format
- For each query, print a single integer — the minimum length of a valid substring, or \(-1\) if none exists.


## Constraints
- \[1 \leq |s| \leq 200000\]  
- \(1 \leq q \leq 100000\)  
- \(1 \leq |a|, |b| \leq 10\)  
- \(0 \leq L \leq R \leq |s|\)  
- \(s, a, b\) consist of lowercase English letters  
- Occurrences must be non-overlapping  


## Examples
 - **Input:**
