# **题目地址**
https://leetcode-cn.com/problems/4sum/
# **题目描述**
```
给定一个包含 n 个整数的数组 nums 和一个目标值 target，判断 nums 中是否存在四个元素 a，b，c 和 d ，使得 a + b + c + d 的值与 target 相等？
找出所有满足条件且不重复的四元组。

注意：
答案中不可以包含重复的四元组。

示例：
给定数组 nums = [1, 0, -1, 0, -2, 2]，和 target = 0。
满足要求的四元组集合为：
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        n = len(nums)
        if (not nums or n < 4):
            return []
        nums.sort()
        res = []
        for i in range(n-3):
            if (nums[i] + nums[i+1] + nums[i+2] + nums[i+3] > target):
                break
            if (nums[i] + nums[-1] + nums[-2] + nums[-3] < target):
                continue
            if (i > 0 and nums[i] == nums[i-1]):
                continue
            for j in range(i + 1, n - 2):
                if (nums[i] + nums[j] + nums[j+1] + nums[j+2] > target):
                    break
                if (nums[i] + nums[j] + nums[-1] + nums[-2] < target):
                    continue
                if (j - i > 1 and nums[j] == nums[j-1]):
                    continue
                L = j + 1
                R = n - 1
                while (L < R):
                    if (nums[i] + nums[j] + nums[L] + nums[R] == target):
                        res.append([nums[i], nums[j], nums[L], nums[R]])
                        while (L < R and nums[L] == nums[L + 1]):
                            L = L + 1
                        while (L < R and nums[R] == nums[R - 1]):
                            R = R - 1
                        L = L + 1
                        R = R - 1
                    elif (nums[i] + nums[j] + nums[L] + nums[R] > target):
                        R = R - 1
                    else:
                        L = L + 1
        return res
```
C++ Code:
```
class Solution{
    public: 
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        sort(nums.begin(), nums.end());
        vector<vector<int> > res;
        if (nums.size() < 4)
        return res;
        int a, b, c, d, _size = nums.size();
        for (a = 0; a <= _size - 4; a++) {
            if (a > 0 && nums[a] == nums[a-1]) continue;
            for (b = a + 1; b <= _size - 3; b++) {
                if (b > a + 1 && nums[b] == nums[b-1]) continue;
                c = b + 1, d = _size - 1;
                while(c < d) {
                    if (nums[a] + nums[b] + nums[c] + nums[d] < target)
                        c++;
                    else if (nums[a] + nums[b] + nums[c] + nums[d] > target)
                        d--;
                    else {
                        res.push_back({nums[a], nums[b], nums[c], nums[d]});
                        while (c < d && nums[c+1] == nums[c])
                            c++;
                        while (c < d && nums[d-1] == nums[d])
                            d--;
                        c++;
                        d--;
                    }
                }
            }
        }
        return res;
    }
};
```
