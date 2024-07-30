# Product of Array Except Self

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`.
The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in \(O(n)\) time and without using the division operation.

## Example 1

**Input:**
```java 
nums = [1, 2, 3, 4]
```

**Output:**
```java
[24, 12, 8, 6]
```

## Example 2

**Input:**
```java
nums = [-1, 1, 0, -3, 3]
```

**Output:**
```java
[0, 0, 9, 0, 0]
```


## Solution
```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int arr[] = new int[nums.length];
        int left = 1;
        int right = 1;

        for(int i=0;i<nums.length;i++){
            arr[i] = left;
            left *= nums[i];
        }

        for(int j = nums.length-1; j >= 0; j--){
            arr[j] *=right;
            right *= nums[j]; 
        }

        return arr;
    }
}  
```

