# Daily Temperatures

You are given an array of integers `temperatures` where `temperatures[i]` represents the daily temperatures on the `i-th` day.

Return an array `result` where `result[i]` is the number of days after the `i-th` day before a warmer temperature appears on a future day. If there is no day in the future where a warmer temperature will appear for the `i-th` day, set `result[i]` to `0` instead.

## Example 1:

**Input:**

```java
temperatures = [30, 38, 30, 36, 35, 40, 28]
```

**Output:**

```java
[1, 4, 1, 2, 1, 0, 0]
```

## Example 2:

**Input:**

```java
temperatures = [22, 21, 20]
```

**Output:**

```java
[0, 0, 0]
```

## Solution
```java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {

        int len = temperatures.length;
        int res[] = new int[len];
        Stack<Integer> stack = new Stack();

        for(int i=0;i<len;i++){
            while(!stack.isEmpty() && temperatures[stack.peek()] < temperatures[i]){
                int ele = stack.pop();
                res[ele] = i-ele;

            }
            stack.push(i);
        }
        return res;
    }
}
```