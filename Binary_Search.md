# **704. Binary Search**

### Question : 
Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.<br>

Example 1:<br>
Input: nums = [-1,0,3,5,9,12], target = 9<br>
Output: 4<br>
Explanation: 9 exists in nums and its index is 4<br>

Example 2:<br>
Input: nums = [-1,0,3,5,9,12], target = 2<br>
Output: -1<br>
Explanation: 2 does not exist in nums so return -1


### Java Solution(Using Recursion):
```java
class Solution {
    public int search(int[] nums, int target) {
        int s = 0;
        int e = nums.length-1;
        return bSearch(nums, target, s, e);
    }

    int bSearch(int[] nums, int target, int s, int e){
        if(s > e){
            return -1;
        }

        int m = s + (e - s)/2;

        if(target == nums[m]){
            return m;
        }

        if (target < nums[m]){
            return bSearch(nums, target, s, m-1);
        }

        return bSearch(nums, target, m+1, e);
    }
}
```