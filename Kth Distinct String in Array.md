# Kth Distinct String in Array

A distinct string is a string that is present only once in an array.

Given an array of strings `arr`, and an integer `k`, return the `k`th distinct string present in `arr`. If there are fewer than `k` distinct strings, return an empty string `""`.

Note that the strings are considered in the order in which they appear in the array.

## Examples

### Example 1

**Input:** 
```java
arr = ["d", "b", "c", "b", "c", "a"]
k = 2
```

**Output:** 
```java
"a"
```

**Explanation:**
The only distinct strings in `arr` are `"d"` and `"a"`.  
`"d"` appears 1st, so it is the 1st distinct string.  
`"a"` appears 2nd, so it is the 2nd distinct string.  
Since `k == 2`, `"a"` is returned.

### Example 2

**Input:** 
```java
arr = ["aaa", "aa", "a"]
k = 1
```

**Output:** 
```java
"aaa"
```

**Explanation:**
All strings in `arr` are distinct, so the 1st string `"aaa"` is returned.

## Solution
```java
class Solution {
    public String kthDistinct(String[] arr, int k) {
        HashMap<String, Integer> map = new HashMap<>(arr.length);
        
        for (String s : arr) {
            map.put(s, map.getOrDefault(s, 0) + 1);
        }

        for (String s : arr) {
            if (map.get(s) == 1) {
                k--;
                if (k == 0) {
                    return s;
                }
            }
        }
        return "";
    }
}
```