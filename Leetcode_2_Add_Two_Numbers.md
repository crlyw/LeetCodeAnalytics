# Add Two Numbers

#### Description

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

#### Example:

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
```

#### Tags
* Linked List
* Math

***

#### My original solutions

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        boolean addOne = false;
        ListNode l = new ListNode(Integer.MAX_VALUE);
        ListNode sentinel = l;
        while(l1!=null || l2!=null){
            if(l1!=null && l2!= null){
                int sum = 0;
                if(addOne){
                   sum = 1;
                }
                sum = sum + l1.val + l2.val;
                if(sum >= 10){
                    addOne = true;
                    l.next = new ListNode(sum - 10);
                    l = l.next;
                }else{
                    addOne = false;
                    l.next = new ListNode(sum);
                    l = l.next;
                }
                l1 = l1.next;
                l2 = l2.next;
                if(l1==null && l2==null){
                    if(addOne){
                        l.next = new ListNode(1);
                    }
                }
            }
            else if(l1!=null && l2==null){
                int sum = 0;
                if(addOne){
                    sum = 1;
                }
                sum = sum + l1.val;
                if(sum >= 10){
                    addOne = true;
                    l.next = new ListNode(sum - 10);
                    l = l.next;
                    l1 = l1.next;
                }else{
                    addOne = false;
                    l.next = new ListNode(sum);
                    l = l.next;
                    l1 = l1.next;
                }
                if(l1==null && l2==null){
                    if(addOne){
                        l.next = new ListNode(1);
                    }
                }
            }

            else if(l1==null && l2!=null){
                int sum = 0;
                if(addOne){
                    sum = 1;
                }
                sum = sum + l2.val;
                if(sum >= 10){
                    addOne = true;
                    l.next = new ListNode(sum - 10);
                    l = l.next;
                    l2 = l2.next;
                }else{
                    addOne = false;
                    l.next = new ListNode(sum);
                    l = l.next;
                    l2 = l2.next;
                }
                if(l1==null && l2==null){
                    if(addOne){
                        l.next = new ListNode(1);
                    }
                }
            }
        }
        return sentinel.next;
    }
}
```

#### Other people's solutions

```

```
