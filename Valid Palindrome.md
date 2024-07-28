# Is Palindrome

## Problem Statement

Given a string `s`, return `true` if it is a palindrome, otherwise return `false`.

A palindrome is a string that reads the same forward and backward. It is also case-insensitive and ignores all non-alphanumeric characters.

### Examples

**Example 1:**

- **Input:** `s = "Was it a car or a cat I saw?"`
- **Output:** `true`
- **Explanation:** After considering only alphanumerical characters we have `"wasitacaroracatisaw"`, which is a palindrome.

**Example 2:**

- **Input:** `s = "tab a cat"`
- **Output:** `false`
- **Explanation:** `"tabacat"` is not a palindrome.

## Solution

```java
class Solution {
    public boolean isPalindrome(String s) {
        String s1 = s.toLowerCase();
        char[] arr = s1.toCharArray();
        int len = arr.length;
        
        int left = 0;
        int right = len - 1;
        
        while (left < right) {
            while (left < right && !Character.isLetterOrDigit(arr[left])) {
                left++;
            }
            while (left < right && !Character.isLetterOrDigit(arr[right])) {
                right--;
            }
            
            if (arr[left] != arr[right]) {
                return false;
            }
            
            left++;
            right--;
        }
        
        return true;
    }
}
```