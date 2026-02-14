---
author: Jash Ambaliya
pubDatetime: 2026-02-14T16:00:00+05:30
title: "CSES — Weird Algorithm (Collatz Conjecture)"
description: "A detailed breakdown of the CSES Weird Algorithm problem — understanding the Collatz Conjecture, discussing approaches, and walking through a clean C++ solution."
tags: ["competitive-programming", "cses", "cpp", "math"]
featured: true
draft: false
---

## Problem Statement

**Source:** [CSES Problem Set — Weird Algorithm](https://cses.fi/problemset/task/1068)

Given a positive integer $n$, apply the following rules repeatedly until $n$ becomes $1$:

- If $n$ is **even**, divide it by $2$
- If $n$ is **odd**, multiply it by $3$ and add $1$

Print all the values of $n$ during the process.

**Example:** For $n = 3$:

$$3 \rightarrow 10 \rightarrow 5 \rightarrow 16 \rightarrow 8 \rightarrow 4 \rightarrow 2 \rightarrow 1$$

**Constraints:** $1 \le n \le 10^6$

---

## The Math Behind It — Collatz Conjecture

This problem is based on the famous **Collatz Conjecture** (also known as the $3n + 1$ problem). The conjecture states that no matter what positive integer you start with, the sequence will **always** eventually reach $1$.

Despite being incredibly simple to state, this conjecture remains **unproven** — it's one of the great unsolved problems in mathematics. Mathematician Paul Erdős once said:

> "Mathematics may not be ready for such problems."

The conjecture has been verified computationally for all integers up to $2^{68}$, but no general proof exists.

---

## Approach 1: Direct Simulation (Optimal)

Since the problem just asks us to simulate the process, the straightforward approach is the best one:

1. Print $n$
2. While $n \neq 1$:
   - If $n$ is even → $n = n / 2$
   - If $n$ is odd → $n = 3n + 1$
   - Print $n$

### Time Complexity

There's no known closed-form for how many steps the sequence takes, but empirically the number of steps is roughly $O(\log n)$ on average. For $n \le 10^6$, the maximum sequence length is around $525$ steps (for $n = 837799$), so this is very fast.

### Important: Integer Overflow

Even though $n \le 10^6$, intermediate values in the sequence can exceed $2^{31} - 1$ (the max value of a 32-bit int). For example, starting from $n = 113383$, the sequence peaks at $2,482,111,348$ — which overflows a 32-bit integer.

**Always use `long long`** for this problem.

### C++ Solution

```cpp
#include <iostream>
using namespace std;

int main() {
    long long n;
    cin >> n;

    while (n != 1) {
        cout << n << " ";
        if (n % 2 == 0)
            n /= 2;
        else
            n = 3 * n + 1;
    }
    cout << 1 << endl;

    return 0;
}
```

---

## Approach 2: Using Bitwise Operations

We can make the solution slightly more efficient by using bitwise operations:

- `n & 1` checks if $n$ is odd (faster than `n % 2`)
- `n >>= 1` divides by 2 (equivalent to `n /= 2`)

```cpp
#include <iostream>
using namespace std;

int main() {
    long long n;
    cin >> n;

    while (n != 1) {
        cout << n << " ";
        if (n & 1)
            n = 3 * n + 1;
        else
            n >>= 1;
    }
    cout << 1 << endl;

    return 0;
}
```

This doesn't change the asymptotic complexity but is a micro-optimization that's common in competitive programming.

---

## Approach 3: Precomputed / Memoized (Overkill Here)

If you had to answer **multiple queries** (e.g., print sequence lengths for many values of $n$), you could memoize results. For this particular problem it's unnecessary since there's only one query, but it's worth knowing the technique:

```cpp
#include <iostream>
#include <unordered_map>
using namespace std;

unordered_map<long long, int> memo;

int collatzLength(long long n) {
    if (n == 1) return 0;
    if (memo.count(n)) return memo[n];

    int steps;
    if (n % 2 == 0)
        steps = 1 + collatzLength(n / 2);
    else
        steps = 1 + collatzLength(3 * n + 1);

    memo[n] = steps;
    return steps;
}

int main() {
    long long n;
    cin >> n;

    // For this problem, just simulate and print
    while (n != 1) {
        cout << n << " ";
        n = (n % 2 == 0) ? n / 2 : 3 * n + 1;
    }
    cout << 1 << endl;

    return 0;
}
```

---

## Key Takeaways

| Point | Detail |
|---|---|
| **Use `long long`** | Intermediate values exceed 32-bit range |
| **Simple simulation** | No fancy algorithm needed — just follow the rules |
| **Bitwise tricks** | `n & 1` and `n >>= 1` are minor optimizations |
| **Collatz Conjecture** | Unproven but assumed to always terminate |
| **CSES Difficulty** | Introductory — great first problem to start the set |

This is the very first problem in the CSES Problem Set and a perfect warm-up. The real challenge isn't the code — it's remembering to use `long long`! 🚀
