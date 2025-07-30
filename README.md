# 2411.-Smallest-Subarrays-With-Maximum-Bitwise-OR

Link: https://leetcode.com/problems/smallest-subarrays-with-maximum-bitwise-or/submissions/1716499312/?envType=daily-question&envId=2025-07-29


## Approach: Enumeration
# Intuition
For the elements nums[i] in the array, their range is [0,10 
9
 ], and they can contain up to 31 binary bits.

For the bit-th binary digit:

If it is 1, then after performing a bitwise OR operation with any number, this binary bit remains 1, so it has no effect.

If it is 0, then we need to find the smallest j such that j>i and the bit-th binary digit of nums[j] is 1. This way, we can achieve the maximum value through bitwise OR operations. Note that such a j may not exist.

Therefore, we can traverse the array nums in descending order of index, while using an array pos to record the most recent position where each binary bit was set to 1 (if no such position exists, it is initialized to −1). When we reach nums[i], for its bit-th binary digit:

If it is 1, we update pos[bit] to i.

If it is 0 and pos[bit] is not −1, then to obtain the maximum bitwise OR value with i as the left boundary, the right boundary must be at least pos[bit].

In this way, we can sequentially determine the minimum right boundary for each i as the left boundary, and thus obtain the minimum length of the subarray.


# Complexity Analysis
Let n be the length of the array nums, and let C be the range of elements in the array nums.

Time complexity: O(n×logC).

We enumerate the binary bits of each element, and each element has logC binary bits.

Space complexity: O(logC)

This is the space required for the array pos.
