# **题目地址**
https://leetcode-cn.com/problems/contains-duplicate-ii/
# **题目描述**
```
给定一个整数数组和一个整数 k，判断数组中是否存在两个不同的索引 i 和 j，使得 nums [i] = nums [j]，并且 i 和 j 的差的绝对值最大为 k。

示例 1:
输入: nums = [1,2,3,1], k = 3
输出: true

示例 2:
输入: nums = [1,0,1,1], k = 1
输出: true

示例 3:
输入: nums = [1,2,3,1,2,3], k = 2
输出: false
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        hash={}
        for i in range(len(nums)):
            if (nums[i] not in hash):
                hash[nums[i]] = i
            else:
                if (i - hash[nums[i]] <= k):
                    return True
                else:
                    hash[nums[i]] = i
        return False
```
C++ Code:
```
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        unordered_map<int,int> map;
        for (int i =0; i < nums.size(); i++) {
            if (map.count(nums[i]) != NULL && i - map[nums[i]] <= k) return true;
            map[nums[i]] = i;
        }
        return false;
    }
};
```
