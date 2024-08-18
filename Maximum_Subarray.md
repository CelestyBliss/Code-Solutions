# **53. Maximum Subarray**
`Medium`
### Question : 
Given an integer array nums, find the subarray
 with the largest sum, and return its sum.

Example 1:<br>
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]<br>
Output: 6<br>
Explanation: The subarray [4,-1,2,1] has the largest sum 6.<br>

Example 2:<br>
Input: nums = [1]<br>
Output: 1<br>
Explanation: The subarray [1] has the largest sum 1.<br>

Example 3:<br>
Input: nums = [5,4,-1,7,8]<br>
Output: 23<br>
Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.<br>

### Java Solution:
```java
class Solution {
    public int maxSubArray(int[] nums) {
        //initialization
        int curr = 0; int maxTillNow = Integer.MIN_VALUE;
        
        for(int i=0; i<nums.length; i++){
            //updation
            curr += nums[i];

            if(curr>maxTillNow){
                maxTillNow = curr;
            }

            //ignoring negative contribution to the final sum
            if(curr < 0){
                curr = 0;
            }
        }
        return maxTillNow;
    }
}
```