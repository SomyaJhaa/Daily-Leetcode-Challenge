# Daily Leetcode Challenge Solutions

An attempt by me to apply my skills to help coding community.

## Always here to assist you guys.

## Today's 05-01-24 [Problem Link](https://leetcode.com/problems/longest-increasing-subsequence/description/)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Binary search

# Approach
<!-- Describe your approach to solving the problem. -->
- Initialize an empty vector lis to represent the current LIS.
- Iterate through each element num in the input array nums.
- For each element, check if the lis is empty or if the current element is greater than the last element of lis. If true, append the current element to lis.
- If the current element is not greater than the last element of lis, - find the position where the current element can be inserted in lis while maintaining the sorted order. This can be done using the lower_bound function.
- Replace the element at the found position with the current element.
- Continue this process for all elements in nums.
- The size of the final lis vector represents the length of the LIS.
Return the length of the LIS.

# Complexity
- Time complexity: $$O(nlogn)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ --> 

# Code
```
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        vector<int> lis;

        for (int num : nums) {
            if (lis.empty() || num > lis.back()) {
                lis.push_back(num);
            } else {
                auto it = lower_bound(lis.begin(), lis.end(), num);
                *it = num;
            }
        }

        return lis.size();
    }
};
```
