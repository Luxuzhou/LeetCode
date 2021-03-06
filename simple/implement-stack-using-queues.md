# **题目地址**
https://leetcode-cn.com/problems/implement-stack-using-queues/
# **题目描述**
```
使用队列实现栈的下列操作：

push(x) -- 元素 x 入栈
pop() -- 移除栈顶元素
top() -- 获取栈顶元素
empty() -- 返回栈是否为空

注意:
你只能使用队列的基本操作-- 也就是 push to back, peek/pop from front, size, 和 is empty 这些操作是合法的。
你所使用的语言也许不支持队列。 你可以使用 list 或者 deque（双端队列）来模拟一个队列 , 只要是标准的队列操作即可。
你可以假设所有操作都是有效的（例如, 对一个空的栈不会调用 pop 或者 top 操作）。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
from queue import Queue

class MyStack:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.queue_push = Queue()

    def push(self, x: int) -> None:
        """
        Push element x onto stack.
        """
        self.queue_push.put(x)
        size = self.queue_push.qsize()
        while (size > 1):
            self.queue_push.put(self.queue_push.get())
            size -= 1

    def pop(self) -> int:
        """
        Removes the element on top of the stack and returns that element.
        """
        return self.queue_push.get()

    def top(self) -> int:
        """
        Get the top element.
        """
        top = self.queue_push.get()
        self.push(top)
        return top

    def empty(self) -> bool:
        """
        Returns whether the stack is empty.
        """
        return self.queue_push.empty()
```
C++ Code:
```
class MyStack {
    queue<int> nums;    
public:
    /** Initialize your data structure here. */
    MyStack() {
        //nothing to do
    }
    
    /** Push element x onto stack. */
    void push(int x) {
        nums.push(x);
        for(int i = 0; i < nums.size() - 1; i++){
            nums.push(nums.front());
            nums.pop();
        }
    }
    
    /** Removes the element on top of the stack and returns that element. */
    int pop() {
        int num = nums.front();
        nums.pop();
        return num;
    }
    
    /** Get the top element. */
    int top() {
        return nums.front();
    }
    
    /** Returns whether the stack is empty. */
    bool empty() {
        return nums.empty();
    }
};

/**
 * Your MyStack object will be instantiated and called as such:
 * MyStack* obj = new MyStack();
 * obj->push(x);
 * int param_2 = obj->pop();
 * int param_3 = obj->top();
 * bool param_4 = obj->empty();
 */
```
