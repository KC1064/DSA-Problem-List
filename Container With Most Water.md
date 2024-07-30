# Max Water Container Problem

You are given an integer array `heights` where `heights[i]` represents the height of the \(i\)th bar.

You may choose any two bars to form a container. Return the maximum amount of water a container can store.

## Example 1

**Input:**
``` java
height = [1,7,2,5,4,7,3,6]
```

**Output:**
```java
36
```

### Example 2

**Input:**
```java
height = [2,2,2]
```

**Output:**
```java
4
```

## Solution:
```java
class Solution {
    public int maxArea(int[] height) {
        int i = 0, j = height.length - 1, max = 0;
        while (i <= j) {
            if (height[i] <= height[j]) {
                max = Math.max(height[i] * (j - i), max);
                i++;
            } else {
                max = Math.max(height[j] * (j - i), max);
                j--;
            }
        }

        return max;

    }
}
```