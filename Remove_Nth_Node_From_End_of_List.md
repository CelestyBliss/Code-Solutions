# **19. Remove Nth Node From End of List**

### Question : 
Given the head of a linked list, remove the nth node from the end of the list and return its head.

 

**Example 1:**<br>
Input: head = [1,2,3,4,5], n = 2<br>
Output: [1,2,3,5]<br>

**Example 2:**<br>
Input: head = [1], n = 1<br>
Output: []<br>

**Example 3:**
Input: head = [1,2], n = 1<br>
Output: [1]


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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if(head.next == null){
            return null;
        }

        ListNode curr = head;
        int size = 0;
        //find size
        while (curr != null){
            curr = curr.next;
            size ++;
        }

        if(n == size){ //nth node from last => delete the head. Hence the list starts from head.next
            return head.next;
        }

        ListNode prev = head;
        //pos of node to be deleted from last from front = size-n+1
        //prev node of the node to be deleted is at (size - n) from front
        int prevNodePos = size-n;
        //traversal to prev node of the node to be deleted
        for (int i=1; i<prevNodePos; i++){
            prev = prev.next;
        }
        prev.next = prev.next.next;
        return head;
    }
}
```