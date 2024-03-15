# **PALINDROME LINKED LIST**

### Question : 
Given the head of a singly linked list, return true if it is a 
palindrome or false otherwise.

Example 1:<br>
Input: head = [1,2,2,1]<br>
Output: true<br>

Example 2:<br>
Input: head = [1,2]<br>
Output: false

### Java Solution: (Using Array(Extra Space))
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {

    public boolean isPalindrome(ListNode head) {
        ListNode temp = head;
        int size = 0;
        while(temp != null){
            size ++;
            temp = temp.next;
        }
        ListNode temp1 = head;
        int arr[] = new int[size];
        int i = 0;
        while(temp1 != null){
            arr[i] = temp1.val;
            i++;
            temp1 = temp1.next;
        }
        int middle = Math.floorDiv(size,2);
        for (int j=0; j<middle; j++){
            if(arr[j]!=arr[size-j-1]){
                return false;
            }
        }
        return true;
    }
}
```
### Java Solution: (Without using Extra Space)
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {

    public ListNode reverse(ListNode head){
        ListNode prev = null;
        ListNode curr = head;

        while(curr != null){
            ListNode next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
    public ListNode findMiddle(ListNode head){
        if(head == null || head.next == null){
            return head;
        }
        //using fast and slow pointers
        ListNode fast = head;
        ListNode slow = head;
        while (fast.next != null && fast.next.next != null){
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }       
    public boolean isPalindrome(ListNode head) {
        //1. Find middle node
        ListNode middle = findMiddle(head);
        //2. Find the first node from last
        ListNode secondHalfStart = reverse(middle.next);
        //3. Compare from both the ends
        ListNode firstHalfStart = head;
        while(secondHalfStart != null){
            if(firstHalfStart.val != secondHalfStart.val){
                return false;
            }

            secondHalfStart = secondHalfStart.next;
            firstHalfStart = firstHalfStart.next;
        }
        return true;
    }
}
```