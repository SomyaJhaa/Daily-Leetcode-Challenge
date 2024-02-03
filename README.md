
# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 03-02-24 
## [1043. Partition Array for Maximum Sum](https://leetcode.com/problems/partition-array-for-maximum-sum/description/?envType=daily-question&envId=2024-02-03)


**Intuition:**

The provided code uses dynamic programming to solve the problem. The idea is to iterate through the array from right to left, considering each element as the starting point of a subarray. For each starting point, it calculates the maximum value within the subarray of length at most k and updates the dynamic programming array `dp` to store the maximum sum after partitioning.

**Approach:**

1. Initialize a dynamic programming array `dp` of size n+1, where n is the length of the input array.
2. Iterate through the input array from right to left (using the variable `id`), considering each element as the starting point of a subarray.
3. For each starting point, iterate through the next k elements (or until the end of the array) to find the maximum value within the subarray.
4. Update `dp[id]` using the formula: `dp[id] = max(dp[id], (j-id+1)*maxVal + dp[j+1])`, where `(j-id+1)*maxVal` represents the sum of the maximum value within the subarray multiplied by the length of the subarray.
5. Return the final result stored in `dp[0]`, which represents the maximum sum after partitioning the array.

**Time Complexity:**

The time complexity of the provided code is O(n*k), where n is the length of the input array. This is because, for each element in the array, the algorithm considers the next k elements (or until the end of the array) to find the maximum value within the subarray.

**Space Complexity:**

The space complexity is O(n) as it uses a dynamic programming array of size n+1 (`dp`).



# Code
```
class Solution {
public:
    vector<int> dp;
    int n, k;

    int solve(int id, vector<int>& arr){
        if(id >= n) return 0;

        if(dp[id] != -1) return dp[id];

        int maxVal = 0, ans = 0;
        for(int j=id; j< min(n, id+k); j++){
            maxVal = max(maxVal, arr[j]);
            ans = max(ans, (j-id+1) * maxVal + solve(j+1, arr));
        }
        return dp[id] = ans;
    }
    int maxSumAfterPartitioning(vector<int>& arr, int k) {
        n = arr.size();
        this ->k = k;
        dp = vector<int>(n, -1);
        return solve(0, arr);
    }
};

Code 2
class Solution {
public:
    int maxSumAfterPartitioning(vector<int>& arr, int k) {
        int n = arr.size();
        vector<int> dp = vector<int>(n+1, 0);

        for(int id = n-1; id>=0; id--){
            int maxVal = 0;
            for(int j=id; j<min(n, id+k); j++){
                maxVal = max(maxVal, arr[j]);
                dp[id] = max(dp[id], (j-id+1)*maxVal + dp[j+1]);
            }
        }
        return dp[0];
    }
};

```