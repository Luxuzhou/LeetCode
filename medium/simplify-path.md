# **题目地址**
https://leetcode-cn.com/problems/simplify-path/
# **题目描述**
```
以 Unix 风格给出一个文件的绝对路径，你需要简化它。或者换句话说，将其转换为规范路径。
在 Unix 风格的文件系统中，一个点（.）表示当前目录本身；此外，两个点 （..） 表示将目录切换到上一级（指向父目录）；两者都可以是复杂相对路径的组成部分。更多信息请参阅：Linux / Unix中的绝对路径 vs 相对路径
请注意，返回的规范路径必须始终以斜杠 / 开头，并且两个目录名之间必须只有一个斜杠 /。最后一个目录名（如果存在）不能以 / 结尾。此外，规范路径必须是表示绝对路径的最短字符串。

示例 1：
输入："/home/"
输出："/home"
解释：注意，最后一个目录名后面没有斜杠。

示例 2：
输入："/../"
输出："/"
解释：从根目录向上一级是不可行的，因为根是你可以到达的最高级。

示例 3：
输入："/home//foo/"
输出："/home/foo"
解释：在规范路径中，多个连续斜杠需要用一个斜杠替换。

示例 4：
输入："/a/./b/../../c/"
输出："/c"

示例 5：
输入："/a/../../b/../c//.//"
输出："/c"

示例 6：
输入："/a//b////c/d//././/.."
输出："/a/b/c"
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def simplifyPath(self, path: str) -> str:
        stack = []
        path = path.split("/")
        for item in path:
            if item == "..":
                if stack: stack.pop()
            elif item and item!= ".":
                stack.append(item)
        return "/" + "/".join(stack)
```
C++ Code:
```
class Solution {
public:
    string simplifyPath(string path) {
        path += "/";
        stack<string> st;
        string dir;
        for (auto c: path) {
            if (c == '/') {
                if (dir == ".." && !st.empty()) st.pop();
                else if (dir != ".." && dir != "." && !dir.empty()) st.push(dir);
                dir.clear();
                }
            else dir += c;
        }
        string res;
        while (!st.empty()) {
            auto t = st.top();
            st.pop();
            res += string(t.rbegin(), t.rend()) + "/";
        }
        reverse(res.begin(), res.end());
        if (res.empty()) res = "/";
        return res;
    }
};
```
