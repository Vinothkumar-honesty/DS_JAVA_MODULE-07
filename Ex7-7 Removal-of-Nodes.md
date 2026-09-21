# Ex7 Removal of Nodes with a Specific Value from a Linked List
## DATE: 01/08/2026
## AIM:
To write a java  program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm


1.Move head forward until it reaches a node whose value is not equal to val. 

2.If the list becomes empty, return null. 

3.Start from the new head and traverse the list using a pointer (current).

4.If current.next contains val, skip that node 

5.Otherwise, move to the next node. Continue until the end, then return the modified head.


## Program:
```
/*
program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
Developed by: VINOTHKUMAR R
RegisterNumber:  212224040361
*/

import java.util.*;

class ListNode {
    int val;
    ListNode next;

    ListNode(int val) {
        this.val = val;
    }
}

class Solution {
    public ListNode removeElements(ListNode head, int val) {

        // Remove matching nodes from the beginning
        while (head != null && head.val == val) {
            head = head.next;
        }

        // Remove matching nodes from the remaining list
        ListNode current = head;

        while (current != null && current.next != null) {
            if (current.next.val == val) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }

        return head;
    }
}

public class Main {

    public static ListNode buildList(int[] arr) {
        if (arr.length == 0)
            return null;

        ListNode head = new ListNode(arr[0]);
        ListNode current = head;

        for (int i = 1; i < arr.length; i++) {
            current.next = new ListNode(arr[i]);
            current = current.next;
        }

        return head;
    }

    public static String listToString(ListNode head) {
        List<Integer> result = new ArrayList<>();

        while (head != null) {
            result.add(head.val);
            head = head.next;
        }

        return result.toString();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String input = scanner.nextLine().replaceAll("\\s", "");

        int[] nums = Arrays.stream(input.split(","))
                           .mapToInt(Integer::parseInt)
                           .toArray();

        int val = scanner.nextInt();

        ListNode head = buildList(nums);

        Solution solution = new Solution();

        ListNode updated = solution.removeElements(head, val);

        System.out.println(listToString(updated));

        scanner.close();
    }
}
```

## Output:

<img width="915" height="306" alt="image" src="https://github.com/user-attachments/assets/ea4a945c-3e78-49bd-a8b0-23cd7a03a78c" />


## Result:
The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.
