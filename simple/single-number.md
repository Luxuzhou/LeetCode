# **题目地址**
https://leetcode-cn.com/problems/single-number/
# **题目描述**
```
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

说明：
你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

示例 1:
输入: [2,2,1]
输出: 1

示例 2:
输入: [4,1,2,1,2]
输出: 4
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        res = nums[0]
        for num in nums[1:]:
            res ^= num
        return res
```
C++ Code:
```
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int ret = 0;
        int len = nums.size();
        for (int i = 0; i < len; i++) {
            ret = nums[i] ^ ret;
        }
        return ret;
    }
};
```
