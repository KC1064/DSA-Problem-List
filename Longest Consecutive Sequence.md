# Longest Consecutive Sequence

Given an array of integers `nums`, return the length of the longest consecutive sequence of elements. A consecutive sequence is a sequence of elements in which each element is exactly 1 greater than the previous element.

You must write an algorithm that runs in *O(n)* time.

## Example 1:

**Input:**

```java
nums = [2, 20, 4, 10, 3, 4, 5]
```

**Output:**

```java
4
```

**Explanation:** The longest consecutive sequence is `[2, 3, 4, 5]`.

## Example 2:

**Input:**

```java
nums = [0, 3, 2, 5, 4, 6, 1, 1]
```

**Output:**

```java
7
```

**Explanation:** The longest consecutive sequence is `[0, 1, 2, 3, 4, 5, 6]`.

## Solution:

```java
class Solution {
    public int longestConsecutive(int[] nums) {

        Set<Integer> numSet = new HashSet<>();
        for (int num : nums) {
            numSet.add(num);
        }

        int longestStreak = 0;

        for (int num : numSet) {
            if (!numSet.contains(num - 1)) {
                int currentNum = num;
                int currentStreak = 1;

                while (numSet.contains(currentNum + 1)) {
                    currentNum += 1;
                    currentStreak += 1;
                }

                longestStreak = Math.max(longestStreak, currentStreak);
            }
        }

        return longestStreak;
    }
}
```