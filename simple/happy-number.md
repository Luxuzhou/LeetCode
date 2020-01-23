# **题目地址**
https://leetcode-cn.com/problems/happy-number/
# **题目描述**
```
编写一个算法来判断一个数是不是“快乐数”。
一个“快乐数”定义为：对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和，然后重复这个过程直到这个数变为 1，也可能是无限循环但始终变不到 1。如果可以变为 1，那么这个数就是快乐数。

示例: 
输入: 19
输出: true
解释: 
1^2 + 9^2 = 82
8^2 + 2^2 = 68
6^2 + 8^2 = 100
1^2 + 0^2 + 0^2 = 1
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def isHappy(self, n: int) -> bool:
        while n >= 10:
            n_l = list(int(i) for i in str(n))
            n = 0
            for num in n_l:
                n += num ** 2
        
        return n == 1 or n == 7
```
C++ Code:
```
class Solution {
public:
    int bitSquareSum(int n) {
        int sum = 0;
        while(n > 0) {
            int bit = n % 10;
            sum += bit * bit;
            n = n / 10;
        }
        return sum;
    }  
    bool isHappy(int n) {
        int slow = n, fast = n;
        do {
            slow = bitSquareSum(slow);
            fast = bitSquareSum(fast);
            fast = bitSquareSum(fast);
        }while (slow != fast);   
        return slow == 1;
    }
};
```
