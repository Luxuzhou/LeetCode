# **题目地址**
https://leetcode-cn.com/problems/count-and-say/
# **题目描述**
```
「外观数列」是一个整数序列，从数字 1 开始，序列中的每一项都是对前一项的描述。前五项如下：

1.     1
2.     11
3.     21
4.     1211
5.     111221
1 被读作  "one 1"  ("一个一") , 即 11。
11 被读作 "two 1s" ("两个一"）, 即 21。
21 被读作 "one 2",  "one 1" （"一个二" ,  "一个一") , 即 1211。

给定一个正整数 n（1 ≤ n ≤ 30），输出外观数列的第 n 项。
注意：整数序列中的每一项将表示为一个字符串。

示例 1:
输入: 1
输出: "1"
解释：这是一个基本样例。

示例 2:
输入: 4
输出: "1211"
解释：当 n = 3 时，序列是 "21"，其中我们有 "2" 和 "1" 两组，"2" 可以读作 "12"，也就是出现频次 = 1 而 值 = 2；类似 "1" 可以读作 "11"。所以答案是 "12" 和 "11" 组合在一起，也就是 "1211"。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def countAndSay(self, n: int) -> str:
        ll = '1'  
        temp = ''
        count = 1
        time = 0
        while time < (n-1):
            for i in range(len(ll)):
                try:
                    if ll[i + 1] == ll[i]:
                        count += 1
                        continue
                    elif ll[i + 1] != ll[i]:
                        temp = temp + str(count) + str(ll[i])
                        count = 1
                        continue
                except IndexError:
                    temp = temp + str(count) + str(ll[i])
                    count = 1
            ll = temp
            temp = ''
            time += 1
        return ll
```
C++ Code:
```
class Solution {
public:
    string countAndSay(int n) {
        string s1 = "1", s2 = "";
        char itoa;
        if (n == 1) {return s1;}
        for (int i = 1; i < n; i++) {
            int count = 0;
            int len = s1.size();
            char c = s1[0];
            for (int j = 0; j < len; j++){
                if (s1[j] == c) {
                    count++;
                }
                else {
                    itoa = count + '0';
                    s2 += itoa;
                    s2 += c;
                    c = s1[j];
                    count = 1;
                }
                if(j == len - 1){
                    itoa = count + '0';
                    s2 += itoa;
                    s2 += c;
                }
            }
            s1 = s2;
            s2 = "";
        }
        return s1;
    }
};
```
