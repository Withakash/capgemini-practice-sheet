# Highest Peak — Altitude Sum Problem

Alice (or a hiker) visits a sequence of checkpoints with given altitudes.
A **peak** is defined as a contiguous subarray that first strictly increases and then strictly decreases (both increasing and decreasing parts must be non-empty). The shape is like a mountain (increasing then decreasing). The **altitude sum** of a peak is the sum of the values in that subarray.

Given the number of checkpoints `N` and an integer array `arr` of length `N` representing altitudes at each checkpoint, find and return the **maximum altitude sum** of any subarray that forms a valid peak (an increasing-then-decreasing contiguous subarray). If no such peak exists, return `0`.

---

## Input
- `input1`: Integer `N` — number of checkpoints.
- `input2`: Integer array `arr` of length `N` — altitudes.

## Output
- An integer representing the maximum altitude sum for any valid peak subarray, or `0` if none exists.

---

## Notes / Clarifications
- A valid peak subarray must have length at least 3 (at least one increasing step and one decreasing step).
- Increasing and decreasing should be **strict** (no equal adjacent elements allowed inside the strictly increasing or strictly decreasing parts).
- You must consider **contiguous** subarrays only.

---

## Examples

**Example 1**
```
input1: 7
input2: [1, 2, 3, 4, 3, 2, 1]
Output: 16
```
**Explanation:** The whole array `[1,2,3,4,3,2,1]` is a valid peak (strictly increases to 4, then strictly decreases). Sum = 1+2+3+4+3+2+1 = 16.

---

**Example 2**
```
input1: 8
input2: [5, 1, 2, 3, 2, 1, 6, 7]
Output: 9
```
**Explanation:** The subarray `[1,2,3,2,1]` is a valid peak with sum 1+2+3+2+1 = 9. Other segments are not valid peaks or have smaller sums.

---

## Constraints
- `3 <= N <= 10^5` (typical)
- Altitudes can be positive integers (or non-negative depending on problem variant)
- Aim for an algorithm that works in O(N) time and O(1) extra space (besides input/output).

---

## Approach (Hint)
- For each index, you can expand left while strictly increasing (towards left) and expand right while strictly decreasing (towards right) to identify a peak centered at that index — but naive expansion for every index is O(N^2).
- A linear O(N) solution uses two passes:
  1. Compute `inc[i]` = length of strictly increasing run ending at `i` (or sum of that run).
  2. Compute `dec[i]` = length of strictly decreasing run starting at `i` (or sum of that run).
  3. For every index `i` that can be the peak (inc[i] > 0 and dec[i] > 0), consider the sum of the subarray covered and take maximum.

---

## Sample Python Implementation (O(N))

```python
def max_peak_sum(arr):
    n = len(arr)
    if n < 3:
        return 0

    # prefix sums for quick subarray sum queries
    pref = [0] * (n + 1)
    for i in range(n):
        pref[i+1] = pref[i] + arr[i]

    # inc[i] = length of strictly increasing sequence ending at i (count of elements)
    inc_len = [1] * n
    for i in range(1, n):
        if arr[i] > arr[i-1]:
            inc_len[i] = inc_len[i-1] + 1
        else:
            inc_len[i] = 1

    # dec_len[i] = length of strictly decreasing sequence starting at i
    dec_len = [1] * n
    for i in range(n-2, -1, -1):
        if arr[i] > arr[i+1]:
            dec_len[i] = dec_len[i+1] + 1
        else:
            dec_len[i] = 1

    max_sum = 0
    # A valid peak must have inc_len[i] >= 2 and dec_len[i] >= 2 (so peak length >= 3)
    for i in range(n):
        if inc_len[i] >= 2 and dec_len[i] >= 2:
            left = i - inc_len[i] + 1
            right = i + dec_len[i] - 1
            s = pref[right+1] - pref[left]
            if s > max_sum:
                max_sum = s

    return max_sum
```

---

## Edge Cases
- Flat arrays like `[1,1,1,1]` → no valid peak → return `0`.
- Arrays with multiple peaks → return maximum sum among them.
- Single steep peaks vs wide shallow peaks — use sums rather than lengths.

---

## Author / Source
This problem is commonly seen in online assessment platforms and resembles Capgemini/Metti style hands-on programming questions.
