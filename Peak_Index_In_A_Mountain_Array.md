# **852. Peak Index in a Mountain Array**
Problem description link: https://leetcode.com/problems/peak-index-in-a-mountain-array/description/
<br>
`MEDIUM`
### Java Solution
Approach: Binary Search <br>
`Time Complexity : O(log(n))`
```java
class Solution {
    public int peakIndexInMountainArray(int[] arr) {
        int s = 0;
        int e = arr.length - 1;

        while(s<e){
            int mid = s+(e-s)/2;
            if(arr[mid+1]<arr[mid]){
                e = mid;
            }
            else if(arr[mid+1]>arr[mid]){
                s = mid+1;
            }
            else{
                return mid;
            }
        }
        return s;
    }
}
```
## **Key Concept:** The numbers in the array are strictly increasing till the peak element and then decreasing. Hence, peak element probably lies where the right side element `m+1` is lesser than the middle element `m`.
