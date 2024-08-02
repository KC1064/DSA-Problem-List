# Permutation String

You are given two strings `s1` and `s2`.

Return `true` if `s2` contains a permutation of `s1`, or `false` otherwise. That means if a permutation of `s1` exists as a substring of `s2`, then return `true`.

Both strings only contain lowercase letters.

## Examples:

### Example 1:
**Input:**
```java
s1 = "abc"
s2 = "lecabee"
```

**Output:**
```java
true
```

**Explanation:**
The substring `"cab"` is a permutation of `"abc"` and is present in `"lecabee"`.

### Example 2:

**Input:**
```java
s1 = "abc"
s2 = "lecaabee"
```

**Output:**
```java
false
```

## Solution

**1.Using HashMap**
```java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        if (s1.length() > s2.length()) {
            return false;
        }

        HashMap<Character, Integer> s1Map = new HashMap<>();
        for (char c : s1.toCharArray()) {
            s1Map.put(c, s1Map.getOrDefault(c, 0) + 1);
        }

        HashMap<Character, Integer> s2Map = new HashMap<>();
        for (int i = 0; i < s1.length(); i++) {
            char c = s2.charAt(i);
            s2Map.put(c, s2Map.getOrDefault(c, 0) + 1);
        }

        if (s1Map.equals(s2Map)) {
            return true;
        }


        for (int i = s1.length(); i < s2.length(); i++) {
            
            char newChar = s2.charAt(i);
            s2Map.put(newChar, s2Map.getOrDefault(newChar, 0) + 1);

            char oldChar = s2.charAt(i - s1.length());
            if (s2Map.get(oldChar) == 1) {
                s2Map.remove(oldChar);
            } else {
                s2Map.put(oldChar, s2Map.get(oldChar) - 1);
            }

            if (s1Map.equals(s2Map)) {
                return true;
            }
        }

        return false;
    }
}
```
**2. Using Array**
```java
class Solution {
    public boolean allZeros(int nums[]) {
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                return false;
            }
        }
        return true;
    }

    public boolean checkInclusion(String s1, String s2) {
        int len1 = s1.length();
        int len2 = s2.length();

        if (len1 > len2) {
            return false;
        }

        int[] count = new int[26];

        for (int i = 0; i < len1; i++) {
            count[s1.charAt(i) - 'a']++;
            count[s2.charAt(i) - 'a']--;
        }

        if (allZeros(count)) {
            return true;
        }

        for (int i = len1; i < len2; i++) {
            count[s2.charAt(i) - 'a']--;
            count[s2.charAt(i - len1) - 'a']++;
            if (allZeros(count)) {
                return true;
            }
        }

        return false;
    }
}
```