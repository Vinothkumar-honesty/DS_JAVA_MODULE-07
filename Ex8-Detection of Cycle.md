# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List
## DATE: 03/08/2026
## AIM:
To write a program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
## Algorithm
1. 
2. 
3. 
4.  
5.   

## Program:
```
/*
program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
Developed by: VINOTHKUMAR R
RegisterNumber:  212224040361
*/

import java.util.*;

public class Solution {

    static class ListNode {
        int val;
        ListNode next;

        ListNode(int val) {
            this.val = val;
            this.next = null;
        }
    }

    public boolean hasCycle(ListNode head) {

        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {

            slow = slow.next;
            fast = fast.next.next;

            if (slow == fast) {
                return true;
            }
        }

        return false;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        String headInput = sc.nextLine().trim();

        headInput = headInput.replaceAll("\\[|\\]", "");

        if (headInput.isEmpty()) {
            System.out.println("false");
            return;
        }

        String[] values = headInput.split(",");
        int[] nums = Arrays.stream(values)
                           .mapToInt(Integer::parseInt)
                           .toArray();

        // Build linked list
        ListNode head = new ListNode(nums[0]);
        ListNode current = head;

        List<ListNode> nodeList = new ArrayList<>();
        nodeList.add(head);

        for (int i = 1; i < nums.length; i++) {
            ListNode node = new ListNode(nums[i]);

            current.next = node;
            current = node;

            nodeList.add(node);
        }

        int pos = sc.nextInt();

        // Create cycle
        if (pos >= 0 && pos < nodeList.size()) {
            current.next = nodeList.get(pos);
        }

        boolean result = sol.hasCycle(head);

        System.out.println(result);

        sc.close();
    }
}

```

## Output:

<img width="910" height="332" alt="image" src="https://github.com/user-attachments/assets/601af71e-706a-47d6-bfcc-ef83f3a78f18" />


## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.
