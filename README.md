# LeetCode 191 - Number of 1 Bits

## Problem

Given a positive integer `n`, return the number of `1` bits in its binary representation.

This number is also called the **Hamming Weight**.

## Example

### Input

```text
n = 11
```

Binary representation:

```text
1011
```

There are three `1` bits.

### Output

```text
3
```

## Approach

This solution uses **bit manipulation**.

The important operation is:

```python
n = n & (n - 1)
```

This operation removes the **rightmost `1` bit** from `n`.

Every time this operation is performed, we increase the count by `1`.

We continue until `n` becomes `0`.

## Python Program

```python
class Solution:
    def hammingWeight(self, n):
        count = 0

        while n:
            n = n & (n - 1)
            count += 1

        return count
```

## How `n & (n - 1)` Works

Consider:

```text
n = 1011
```

Then:

```text
n - 1 = 1010
```

Perform AND:

```text
  1011
& 1010
------
  1010
```

The rightmost `1` has been removed.

Next:

```text
  1010
& 1001
------
  1000
```

Next:

```text
  1000
& 0111
------
  0000
```

The operation was performed three times.

Therefore:

```text
Number of 1 bits = 3
```

## Why This Method Is Efficient

Instead of checking every bit position, the algorithm directly removes one `1` bit during every iteration.

Therefore, the loop runs only as many times as there are `1` bits.

## Key Concept

The main bit manipulation trick is:

```python
n & (n - 1)
```

It removes the lowest/rightmost set bit.

This is a very useful technique in bit manipulation problems.

## Time Complexity

**O(k)**

Where `k` is the number of `1` bits in the binary representation.

In the worst case for a 32-bit integer, there can be 32 set bits, so it is effectively **O(1)**.

## Space Complexity

**O(1)**

Only a counter and the input integer are used.

## Difficulty

**Easy**

## Topics

* Bit Manipulation
* Binary Numbers
* Bitwise AND
* Hamming Weight
* Set Bits

## What I Learned

This problem helped me understand how bitwise operations can be used to count the number of `1` bits efficiently.

The most important trick is:

```text
n & (n - 1)
```

which removes one `1` bit from the number at every iteration.

## Author

T.Nandhini
