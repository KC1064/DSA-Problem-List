# Two Sum II-Input Array Is Sorted

## Problem Statement

Given an array of integers `numbers` that is sorted in non-decreasing order, return the indices (1-indexed) of two numbers `[index1, index2]` such that they add up to a given target number `target` and `index1 < index2`. Note that `index1` and `index2` cannot be equal; therefore, you may not use the same element twice.

There will always be exactly one valid solution.

Your solution must use O(1) additional space.

### Example 1

**Input:** 
```plaintext
numbers = [1, 2, 3, 4]
target = 3
```

**Output:** 
```plaintext
[1, 2]
```

**Explanation:**
The sum of 1 and 2 is 3. Since we are assuming a 1-indexed array, `index1 = 1`, `index2 = 2`. We return `[1, 2]`.

## Solution
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int l = 0;
        int r = nums.length-1;

        while(l<r){
            int curSum = nums[l]+nums[r];
            if(curSum == target){
                return new int[]{l+1,r+1};
            }else if(curSum > target){
                r--;
            }
            else {
                l++;
            }
        }
        return new int[]{l+1,r+1};
    }
}
```