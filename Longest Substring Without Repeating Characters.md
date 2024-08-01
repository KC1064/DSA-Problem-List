# Longest Substring Without Duplicate Characters

Given a string `s`, find the length of the longest substring without duplicate characters.

A substring is a contiguous sequence of characters within a string.

## Example 1

- **Input:** `s = "zxyzxyz"`
- **Output:** `3`
- **Explanation:** The string `"xyz"` is the longest without duplicate characters.

## Solution
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int lp = 0;
        int rp = 0;
        int res = 0;
        HashSet<Character> set = new HashSet<>(52);
        while(rp < s.length()){
            if(!set.contains(s.charAt(rp))){
                set.add(s.charAt(rp));
                rp++;
                res = Math.max(res,set.size());
            }else{
                set.remove(s.charAt(lp));
                lp++;
            }
        }
        return res;
    }
}
```