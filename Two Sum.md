
# Two Sum

Given an array of integers `nums` and an integer `target`, return the indices `i` and `j` such that `nums[i] + nums[j] == target` and `i != j`.
You may assume that every input has exactly one pair of indices `i` and `j` that satisfy the condition.
Return the answer with the smaller index first.

## Example 1:

**Input:**
```
nums = [3,4,5,6], target = 7
```

**Output:**
```
[0,1]
```

## Solution:
### 1. Brute Force
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{-1, -1};
    }
}
```

### 2. Optimal Solution
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            int num = nums[i];
            int diff = target - num;

            if (map.containsKey(diff)) {
                return new int[] { map.get(diff), i };
            }

            map.put(num, i);
        }

        return new int[] {-1,-1};
    }
}
```