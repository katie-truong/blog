---
layout: single
permalink: /reverse-a-linked-list
title: "Reverse a linked list"
---

There are two ways to reverse a linked list: the iterative way and the recursive way.

### 1. Iterative:

Reversing a linked list iteratively should be straightforward.

While traversing through the list, we assign the next node to the previous node. Since we don't want the next node to be overwritten, we store it in a temp variable and use it for the next iteration.

```
def reverse_linked_list(head):
    prev = None
    curr = head

    while (curr):
        temp = curr.next
        curr.next = prev
        prev = curr
        curr = temp

    return prev
```

**Complexity**:

- Time complexity: O(n)
- Space complexity: O(1)

### 2. Recursive:

```
def reverse_linked_list(head):
    if head == None or head.next == None:
        return head
    p = reverse_linked_list(head.next)
    head.next.next = head
    head.next = None
    return p
```

