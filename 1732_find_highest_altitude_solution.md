# 1732. Find the Highest Altitude

## Java Solution

```java
class Solution {
    public int largestAltitude(int[] gain) {
        int max = 0;
        int current = 0;

        for (int i = 0; i < gain.length; i++) {
            current += gain[i];
            max = Math.max(max, current);
        }

        return max;
    }
}
```

## Explanation

- Start with altitude `0`
- Keep track of the **current altitude**
- Track the **maximum altitude** reached during the trip
- For each value in `gain`, update the current altitude and compare it with the maximum

## Example

For `gain = [-5,1,5,0,-7]`:

- Altitudes: `0, -5, -4, 1, 1, -6`
- Highest altitude = `1`

## Time Complexity

- `O(n)`

## Space Complexity

- `O(1)`
