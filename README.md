# Leetcode-643.-Maximum-Average-Subarray-I
# Description
You are given an integer array nums consisting of n elements, and an integer k.

Find a contiguous subarray whose length is equal to k that has the maximum average value and return this value. Any answer with a calculation error less than 10-5 will be accepted.
# Solution
In the given problem we have been given an integer array nums with an integer k . We need to find a continous subarray in the array nums which is of length integer k and has the maximum average value . Return the maximum average value.

This can be done by using sliding window technique , in which we use a window to compute an slid ethe window accross the array in a way that we dont have to recompute the values again and again. 

Example:

Input: nums = [1,12,-5,-6,50,3], k = 4

Output: 12.75000

<img width="453" height="587" alt="image" src="https://github.com/user-attachments/assets/9f570439-8b22-418f-bdfd-10fcff2c0484" />

#  Algorithm
1. Initialise a variable cur_sum as 0 , for calculating the sum of elements in a current window.
2. Use 2 for loops:
3. First for loop : builds the first window of size k . Add elements from 0th index to kth index in the cur_sum.
4. Create a max_avg variable which computes and stores the maximum average of the subarray.
5. Second for loop: slides the window across the rest of the array.
6. Add elements of the next window in cur_sum , but since the cur_sum also contains value of the previous window hence we need to remove the elements not present in the current window.
7. For this use cur_sum+=nums[i-k] . The i-k will remove the previous element which was in the previous window.
8. Again compute the avg .
9. Find max_avg by checking which value is greater in max_avg and avg variables.
10. Return the max_avg
# Code
class Solution:

    def findMaxAverage(self, nums: List[int], k: int) -> float:
        cur_sum=0
        n=len(nums)
        for i in range(k):
            cur_sum+=nums[i]
        max_avg=cur_sum/k

        for i in range(k,n):
            cur_sum+=nums[i]
            cur_sum-=nums[i-k]
            avg=cur_sum/k
            max_avg=max(avg,max_avg)
        return max_avg
# Complexity
Time Complexity:

First loop takes O(k).

Second loop takes O(n-k).

Total = O(k + (n-k)) = O(n)

So time complexity = O(n)

Space Complexity

You only use a few variables:

cur_sum, max_avg, avg, n.

No extra arrays or data structures.

So space complexity = O(1)
