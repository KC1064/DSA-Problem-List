# Make Two Arrays Equal By Reversing Substring

You are given two integer arrays of equal length `target` and `arr`. In one step, you can select any non-empty subarray of `arr` and reverse it. You are allowed to make any number of steps.

Return true if you can make `arr` equal to `target` or false otherwise.

## Examples

### Example 1:

**Input:**
```java
target = [1,2,3,4]
arr = [2,4,1,3]
```
**Output:**
```java
true
```

**Explanation:** 
You can follow the next steps to convert `arr` to `target`:
1. Reverse subarray [2,4,1], `arr` becomes [1,4,2,3]
2. Reverse subarray [4,2], `arr` becomes [1,2,4,3]
3. Reverse subarray [4,3], `arr` becomes [1,2,3,4]

There are multiple ways to convert `arr` to `target`; this is not the only way to do so.

### Example 2:
**Input:**
```java
target = [7]
arr = [7]
```
**Output:**
```java
true
```
**Explanation:** 
`arr` is equal to `target` without any reverses.

### Example 3:
**Input:**
```java
target = [3,7,9]
arr = [3,7,11]
```
**Output:**
```java
false
```
**Explanation:** 
`arr` does not have value `9` and it can never be converted to `target`.

## Solution

```java
class Solution {
    public boolean canBeEqual(int[] target, int[] arr) {
        HashMap<Integer, Integer> map = new HashMap<>();

        for (int num : target) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        for (int num : arr) {
            if (map.containsKey(num)) {
                if (map.get(num) == 1) {
                    map.remove(num);
                } else {
                    map.put(num, map.get(num) - 1);
                }
            } else {
                return false;
            }
        }

        return map.isEmpty();
    }
}
```