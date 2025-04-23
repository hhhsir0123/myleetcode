
# 2025-04-23
https://www.acwing.com/problem/content/description/50/

```python
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        # 首先可以想到贪心，看到最大值可以想到dp
        # dp[i]以i结尾的最大值
        # dp[i] = max(dp[i-1] + nums[i], nums[i])
        m = -float('inf')
        n = len(nums)
        dp = [0] * n
        for i in range(n):
            if i > 0:
                dp[i] = max(nums[i], dp[i-1] + nums[i])
            else:
                dp[i] = nums[i]
            m = max(dp[i], m)
        return m
```



