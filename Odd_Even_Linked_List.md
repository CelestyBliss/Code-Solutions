# **328. Odd Even Linked List**
`Medium`
### Question : 
Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the reordered list.<br><br>
The first node is considered odd, and the second node is even, and so on.<br><br>
Note that the relative order inside both the even and odd groups should remain as it was in the input.<br>
You must solve the problem in O(1) extra space complexity and O(n) time complexity.<br>

Example 1:<br>
Input: head = [1,2,3,4,5]<br>
Output: [1,3,5,2,4]<br>

Example 2:<br>
Input: head = [2,1,3,5,6,4,7]<br>
Output: [2,3,6,7,1,5,4]<br>

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
    public ListNode oddEvenList(ListNode head) {
        if(head == null || head.next == null){
            return head;
        }
        ListNode oddHead = head;
        ListNode evenHead = head.next;
        ListNode oddTail = oddHead;
        ListNode evenTail = evenHead;

        while(oddTail.next != null && oddTail.next.next != null){
                evenTail = oddTail.next;
                oddTail.next = oddTail.next.next;
                evenTail.next = evenTail.next.next;

                oddTail = oddTail.next;
                evenTail = evenTail.next;
        }
        oddTail.next = evenHead;
        return oddHead;
    }
}
```