# **206. Reverse Linked List**

### Question : 
Given the head of a singly linked list, reverse the list, and return the reversed list.

Example 1:<br>
Input: head = [1,2,3,4,5]<br>
Output: [5,4,3,2,1]<br>

Example 2:<br>
Input: head = [1,2]<br>
Output: [2,1]<br>

Example 3:<br>
Input: head = []<br>
Output: []

### Java Solution:
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
    public ListNode reverseList(ListNode head) {
        if (head == null || head.next == null){
            return head;
        }
        //using three pointer approach
        ListNode prev = head;
        ListNode curr = head.next;
        while(curr != null){
            ListNode next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next; 
        }
        head.next = null;
        head = prev;
        return head;
    }  
}
```