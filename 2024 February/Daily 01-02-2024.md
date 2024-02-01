
# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 01-02-24 
## [2966. Divide Array Into Arrays With Max Difference](https://leetcode.com/problems/divide-array-into-arrays-with-max-difference/description/?envType=daily-question&envId=2024-02-01)


**Intuition:**

The given code aims to divide the input array `nums` into one or more arrays of size 3, such that the difference between any two elements in one array is less than or equal to `k`. The approach used in the code is to sort the array and then iterate through it in chunks of three, checking the conditions for a valid division. If the conditions are met, the current chunk is added to the result. If not, an empty vector is returned.

**Approach:**

1. Sort the input array `nums`.
2. Initialize a 2D vector `answer` to store the result.
3. Iterate through the sorted array in chunks of three.
4. For each chunk, check the conditions for a valid division.
5. If the conditions are met, add the current chunk to the result.
6. If the conditions are not met for any chunk, return an empty vector.
7. Return the result.

**Time Complexity:**

The time complexity is dominated by the sorting step, which is O(n log n), where n is the size of the input array `nums`. The iteration through the sorted array is O(n), so the overall time complexity is O(n log n).

**Space Complexity:**

The space complexity is O(n/3) for the `answer` vector, as each valid chunk is added to the result. In big-O notation, this simplifies to O(n). Additionally, the space complexity of the sorting operation is O(log n). Therefore, the overall space complexity is O(n).



# Code
```

class Solution {
public:
    vector<vector<int>> divideArray(vector<int>& nums, int k) {
        sort(nums.begin(), nums.end());
        int m = nums.size();
        vector<vector<int>> answer(m / 3, vector<int>(3, 0));

        for (int i = 0; i <= m - 3; i += 3) {
            int ri = i / 3;
            vector<int> t(3, 0);
            t[0] = nums[i];
            t[1] = nums[i + 1];
            t[2] = nums[i + 2];

            if ((t[2] - t[1] > k) || (t[2] - t[0] > k) || (t[1] - t[0] > k)) {
                return vector<vector<int>>();  // Returning an empty vector in case conditions are not met
            }
            answer[ri] = t;
        }
        return answer;
    }
};

```