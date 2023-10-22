### [Q55: Jump Game](https://leetcode.cn/problems/jump-game/?envType=study-plan-v2&envId=top-interview-150)

You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.

### Q55: Solution:

```python3
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        max_reachable = 0
        for idx, num in enumerate(nums):
            if idx <= max_reachable:
                max_reachable = max(max_reachable, idx+num)
            else:
                break
        return max_reachable>=len(nums)-1
```


### [Q45: Jump Game II](https://leetcode.cn/problems/jump-game-ii/?envType=study-plan-v2&envId=top-interview-150)

You are given a 0-indexed array of integers nums of length n. You are initially positioned at nums[0].

Each element nums[i] represents the maximum length of a forward jump from index i. In other words, if you are at nums[i], you can jump to any nums[i + j] where:

0 <= j <= nums[i] and
i + j < n
Return the minimum number of jumps to reach nums[n - 1]. The test cases are generated such that you can reach nums[n - 1].

### Q45: Solution:


```python3:
class Solution:
    def jump(self, nums: List[int]) -> int:
        max_reachable = 0
        min_reach_step = [0]*len(nums)
        if len(nums) == 1:
            return 0

        step_maximal_flag_position = 0
        n_step_needed = 0
        for idx, num in enumerate(nums):
            if idx < step_maximal_flag_position:
                min_reach_step[idx] = n_step_needed
                max_reachable = max(num+idx, max_reachable)
            elif idx == step_maximal_flag_position:
                min_reach_step[idx] = n_step_needed
                n_step_needed+=1
                max_reachable = max(num+idx, max_reachable)
                step_maximal_flag_position = max_reachable
            else: # idx > step_maximal_flag_position
                print('this shold not happen')
        print(min_reach_step)
        return min_reach_step[-1]
```
