# Daily Leetcode Challenge Solutions

A attemp by me to apply my skills to help coding community.

## Always here to assist you guys.

## Today's 03-01-24 [Problem Link](https://leetcode.com/problems/number-of-laser-beams-in-a-bank/description/)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Simply multiply.

# Approach
<!-- Describe your approach to solving the problem. -->
- I kept track of indices of '0' '1' '2' 
- Iterated over whole rows of the array
- Calculated number of beams for each row
- Updated answer
# Complexity
- Time complexity : $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int numberOfBeams(vector<string>& bank) {
        int jawab = 0;      // to store answer
        int picheek = 0;    // to store number of '1' in previous state

        for( string r : bank){
                int ek = count_if(r.begin(), r.end(), [](char g) { return g == '1'; });
           // counting the number of '1' in current row
            if( ek != 0){             // number of beams will the product of current number of device and previous number of devices
                jawab += picheek*ek; // adding the product to answer
                picheek = ek;        // now, the current one will become the previous one to next row
            }
        }
        return jawab;
    }
};
```
