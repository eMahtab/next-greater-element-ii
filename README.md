# Next greater element II
## https://leetcode.com/problems/next-greater-element-ii

Given a circular integer array nums (i.e., the next element of nums[nums.length - 1] is nums[0]), return the next greater number for every element in nums.

The next greater number of a number x is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, return -1 for this number.

```
Example 1:

Input: nums = [1,2,1]
Output: [2,-1,2]
Explanation: The first 1's next greater number is 2; 
The number 2 can't find next greater number. 
The second 1's next greater number needs to search circularly, which is also 2.

Example 2:

Input: nums = [1,2,3,4,3]
Output: [2,3,4,-1,4]
``` 

## Constraints:

1. 1 <= nums.length <= 10^4
2. -10^9 <= nums[i] <= 10^9

# Implementation 1 : O(n^2)
```java
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        if(nums == null)
            return nums;
        int index = 0;
        int[] result = new int[nums.length];
        for(int i = 0; i < nums.length; i++) {
            int j = (i+1) % nums.length; // Don't forget % nums.length
            while(j != i) {
                if(nums[j] > nums[i]) {
                    result[index++] = nums[j];
                    break;
                }
                j = (j+1) % nums.length; // Don't forget % nums.length
            }
            if(j == i)
                result[index++] = -1;
            
        }
        return result;
    }
}
```

