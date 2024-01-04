# Daily Leetcode Challenge Solutions

An attempt by me to apply my skills to help coding community.

## Always here to assist you guys.

## Today's 04-01-24 [Problem Link](https://leetcode.com/problems/minimum-number-of-operations-to-make-array-empty/description/)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to find the minimum number of operations required to transform the given array nums such that each unique element in the array appears three times or is removed completely. The allowed operations include adding or removing elements from the array.

# Approach
<!-- Describe your approach to solving the problem. -->
- Create an unordered map mp to store the frequency of each element in the array.
- Iterate through the array nums and update the frequency in the map mp.
- Initialize the variable ans to 0, which will represent the minimum number of operations.
- Iterate through the elements and their frequencies in the map mp. For each element:
- - If the frequency is 1, it means there is only one occurrence of the element, and it cannot be part of a valid transformation. In this case, return -1.
- - Calculate the number of operations required to make the frequency of the element a multiple of 3. Add this to the ans.
- Return the final value of ans, representing the minimum number of operations.

# Complexity
- Time complexity: $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->


- Space complexity: $$O(n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->


# Code
```
class Solution {
public:
    int minOperations(vector<int>& nums) {
        unordered_map<int , int> mp;
        for(int num : nums) ++mp[num];

        int ans = 0;
        for(auto [el , cnt] : mp) {
            if (cnt == 1) return -1;
            ans += cnt / 3 + (cnt % 3 > 0);
        }
        return ans;
    }
};
```
