# 643. Maximum Average Subarray I

## Problem
You are given an integer array `nums` consisting of `n` elements, and an integer `k`.

Find a contiguous subarray whose length is equal to `k` that has the maximum average value and return this value. Any answer with a calculation error less than `10^-5` will be accepted.

## Examples

### Example 1
**Input:** `nums = [1,12,-5,-6,50,3]`, `k = 4`  
**Output:** `12.75000`  
**Explanation:** Maximum average is `(12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75`

### Example 2
**Input:** `nums = [5]`, `k = 1`  
**Output:** `5.00000`

## Constraints
- `n == nums.length`
- `1 <= k <= n <= 10^5`
- `-10^4 <= nums[i] <= 10^4`

## Java Solution

```java
class Solution {
    public double findMaxAverage(int[] nums, int k) {
        int windowSum = 0;

        // Calculate sum of first window
        for (int i = 0; i < k; i++) {
            windowSum += nums[i];
        }

        int maxSum = windowSum;

        // Slide the window across the array
        for (int i = k; i < nums.length; i++) {
            windowSum += nums[i] - nums[i - k];
            maxSum = Math.max(maxSum, windowSum);
        }

        return (double) maxSum / k;
    }
}
```

## Approach
Use the **sliding window** technique:

- First, compute the sum of the first `k` elements.
- Then slide the window one element at a time:
  - Add the new element entering the window.
  - Subtract the element leaving the window.
- Track the maximum window sum.
- Return `maxSum / k` as the maximum average.

## Time Complexity
- `O(n)`

## Space Complexity
- `O(1)`
