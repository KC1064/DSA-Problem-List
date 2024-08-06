# MinStack

Design a stack that supports `push`, `pop`, `top`, and retrieving the minimum element in constant time.

## Class Definition
Implement the `MinStack` class:

- `MinStack()`: Initializes the stack object.
- `void push(int val)`: Pushes the element `val` onto the stack.
- `void pop()`: Removes the element on the top of the stack.
- `int top()`: Gets the top element of the stack.
- `int getMin()`: Retrieves the minimum element in the stack.

You must implement a solution with \( O(1) \) time complexity for each function.

## Example

### Example 1
- **Input:**
  ```
  ["MinStack","push","push","push","getMin","pop","top","getMin"]
  [[],[-2],[0],[-3],[],[],[],[]]
  ```
- **Output:**
  ```
  [null,null,null,null,-3,null,0,-2]
  ```

- **Explanation:**
  ```java
  MinStack minStack = new MinStack();
  minStack.push(-2);
  minStack.push(0);
  minStack.push(-3);
  minStack.getMin(); // return -3
  minStack.pop();
  minStack.top();    // return 0
  minStack.getMin(); // return -2
  ```


## Solution
```java
class MinStack {
    Stack<Integer> stack;
    Stack<Integer> min_stack;

    public MinStack() {
        stack = new Stack<>();
        min_stack = new Stack<>();
    }
    
    public void push(int val) {
        if(min_stack.isEmpty() || val <= min_stack.peek()){
            min_stack.push(val);
        }
        stack.push(val);
    }
    
    public void pop() {
        if(stack.peek().equals(min_stack.peek())){
            min_stack.pop();
        }
        stack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
        return min_stack.peek();
    }
}
```
