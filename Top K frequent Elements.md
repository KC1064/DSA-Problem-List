# Top K Elements in List

Given an integer array `nums` and an integer `k`, return the `k` most frequent elements within the array.

The test cases are generated such that the answer is always unique.

You may return the output in any order.

## Example 1

**Input:** 
```java
nums = [1, 2, 2, 3, 3, 3]
k = 2
```

**Output:** 
```java
[2, 3]
```

## Example 2

**Input:** 
```java
nums = [7, 7]
k = 1
```

**Output:** 
```java
[7]
```

## Solution:

```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        List<Integer>[] count = new List[nums.length+1];
        HashMap <Integer,Integer> freqMap = new HashMap<>();

        for (int n : nums){
            freqMap.put(n,freqMap.getOrDefault(n,0)+1);
        }


        for (int i : freqMap.keySet()){
            int freq = freqMap.get(i);
            if(count[freq]==null){
                count[freq] = new ArrayList<>();
            }
            count[freq].add(i);
        }

        List<Integer> topK = new ArrayList<>();

        for(int i=count.length-1;i>=0 && topK.size() < k;i--){
            if(count[i]!= null){
                topK.addAll(count[i]);
            }
        }
        return topK.stream().mapToInt(i -> i).toArray();
    }
}
```


