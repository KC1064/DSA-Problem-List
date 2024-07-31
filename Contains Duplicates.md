# Duplicate Integer

Given an integer array `nums`, return `true` if any value appears more than once in the array; otherwise, return `false`.

## Examples
**Input:** 
```java
nums = [1, 2, 3, 3]
```
**Output:** 
```java
true
```

## Solution

```java
class Solution {
    public boolean hasDuplicate(int[] nums) {
        HashMap <Integer,Integer> map = new HashMap<>();

        for (int n : nums){
            if(map.containsKey(n)){
                return true;
            }else{
                map.put(n,map.getOrDefault(n,0)+1);
            }
        }

        return false;
    }
}
```
