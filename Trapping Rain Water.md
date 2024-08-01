# Trapping Rain Water

You are given an array non-negative integers heights which represent an elevation map. Each value `heights[i]` represents the height of a bar, which has a width of `1`.

Return the maximum area of water that can be trapped between the bars.

## Example
**Input:** 
```java
height = [0,2,0,3,1,0,1,3,2,1]
```
**Output:** 
```java
9
```




## Solution
```java
class Solution {
    public int trap(int[] height) {
        if (height == null || height.length == 0) {
            return 0;
        }

        int l = 0, r = height.length - 1;
        int leftMax = height[l], rightMax = height[r];
        int res = 0;
        while (l < r) {
            if (leftMax < rightMax) {
                l++;
                leftMax = Math.max(leftMax, height[l]);
                res += leftMax - height[l];
            } else {
                r--;
                rightMax = Math.max(rightMax, height[r]);
                res += rightMax - height[r];
            }
        }
        return res;
    }
}
```