# Minimum Window Substring Problem

## Problem Statement
Given two strings `s` and `t` of lengths `m` and `n` respectively, return the minimum window substring of `s` such that every character in `t` (including duplicates) is included in the window. If there is no such substring, return the empty string "".

The test cases will be generated such that the answer is unique.

### Examples

#### Example 1
- **Input:** s = "ADOBECODEBANC", t = "ABC"
- **Output:** "BANC"
- **Explanation:** The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.

#### Example 2
- **Input:** s = "a", t = "a"
- **Output:** "a"
- **Explanation:** The entire string s is the minimum window.

#### Example 3
- **Input:** s = "a", t = "aa"
- **Output:** ""
- **Explanation:** Both 'a's from t must be included in the window. Since the largest window of s only has one 'a', return empty string.

## Solution
```java
class Solution {
    public String minWindow(String s, String t) {
        HashMap<Character, Integer> map = new HashMap<>();

        if (s.length() < t.length()) {
            return "";
        }

        for (char c : t.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }

        int start = 0;
        int minLen = s.length() + 1;
        int match = 0;
        int subStr = 0;
        int count = map.size(); 
        for (int i = 0; i < s.length(); i++) {
            char right = s.charAt(i);

            if (map.containsKey(right)) {
                map.put(right, map.get(right) - 1);
                if (map.get(right) == 0) {
                    match++;
                }
            }

            while (match == count) {
                if (minLen > i - start + 1) {
                    minLen = i - start + 1;
                    subStr = start;
                }

                char del = s.charAt(start++);
                if (map.containsKey(del)) {
                    if (map.get(del) == 0) {
                        match--;
                    }
                    map.put(del, map.get(del) + 1);
                }
            }
        }

        return minLen > s.length() ? "" : s.substring(subStr, subStr + minLen);
    }
}
```