# Evaluate Reverse Polish Notion

You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return an integer that represents the value of the expression.

**Note that:**

- The valid operators are '+', '-', '\*', and '/'.
- Each operand may be an integer or another expression.
- The division between two integers always truncates toward zero.
- There will not be any division by zero.
- The input represents a valid arithmetic expression in a reverse polish notation.
- The answer and all the intermediate calculations can be represented in a 32-bit integer.

## Example

### Example 1

**Input:**

```java
 tokens = ["2","1","+","3","*"]
```

**Output:**

```java
 9
```

**Explanation:** 
```sh
((2 + 1) \* 3) = 9
```
### Example 2

**Input:**

```java
tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
```

**Output:**

```java
 22
```

**Explanation:**
```sh
((10 _ (6 / ((9 + 3) _ -11))) + 17) + 5
= ((10 _ (6 / (12 _ -11))) + 17) + 5
= ((10 _ (6 / -132)) + 17) + 5
= ((10 _ 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
```

## Solution

```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> nums = new Stack<>();

        for(int i = 0; i < tokens.length; i++){
            String token = tokens[i];
            if(token.equals("+") || token.equals("-") || token.equals("*") || token.equals("/")){
                int b = nums.pop();
                int a = nums.pop();
                int result=0;
                switch(token){
                    case "+":
                        result = a + b;
                        break;
                    case "-":
                        result = a - b;
                        break;
                    case "*":
                        result = a * b;
                        break;
                    case "/":
                        result = a / b;
                        break;
                }
                nums.push(result);
            } else {
                nums.push(Integer.parseInt(token));
            }
        }

        return nums.pop();
    }
}
```
