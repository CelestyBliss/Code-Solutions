# **1431. Kids With the Greatest Number of Candies**

### Question : 
There are n kids with candies. You are given an integer array candies, where each candies[i] represents the number of candies the ith kid has, and an integer extraCandies, denoting the number of extra candies that you have.<br><br>
Return a boolean array result of length n, where result[i] is true if, after giving the ith kid all the extraCandies, they will have the greatest number of candies among all the kids, or false otherwise.<br><br>
Note that multiple kids can have the greatest number of candies.<br><br>
Example 1:<br>
Input: candies = `[2,3,5,1,3]`, extraCandies = 3<br>
Output: `[true,true,true,false,true]`<br> 
Explanation: <br>If you give all extraCandies to:
- Kid 1, they will have 2 + 3 = 5 candies, which is the greatest among the kids.
- Kid 2, they will have 3 + 3 = 6 candies, which is the greatest among the kids.
- Kid 3, they will have 5 + 3 = 8 candies, which is the greatest among the kids.
- Kid 4, they will have 1 + 3 = 4 candies, which is not the greatest among the kids.
- Kid 5, they will have 3 + 3 = 6 candies, which is the greatest among the kids.

### Java Solution:
```java
class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        List<Boolean> list = new ArrayList<Boolean>(); 
        for(int i=0; i<candies.length; i++){
            if(candies[i]+extraCandies >= findMax(candies) ){
                list.add(true);
            }
            else{
                list.add(false);
            }
        }
        return list;
    }
    static int findMax(int[] arr){
        int max = arr[0];
        for(int i = 0; i<arr.length; i++){
            if(arr[i] > max){
                max = arr[i];
            }
        }
        return max;
    }
}  
```