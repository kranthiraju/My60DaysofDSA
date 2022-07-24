# Summary of Day-8

## 1. [Merge two sorted LinkedList](https://leetcode.com/problems/merge-two-sorted-lists/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

![](https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg)
## Approach :
* Create a merge node with store the answer.
* Which node value is less then move next to node, traverse both lists.

## Code :
```
ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
    ListNode *merge=NULL;
    if(!list1) return list2;
    else if(!list2) return list1;
    if(list1->val <= list2->val){
        merge=list1;
        merge->next=mergeTwoLists(list1->next,list2);
    }
    else{
        merge=list2;
        merge->next=mergeTwoLists(list1,list2->next);
    }
    return merge;
}
```

## Complexicty :
* **Time Complexity : *O(N+M)***
* **Space Complexity : *O(N+M)***

#
## 2. [Remove N-th node from back of LinkedList](https://leetcode.com/problems/merge-two-sorted-lists/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

![Remove N-th node from back of LinkedList](https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg)

## Approach :
* Count the number of node present in given linkedlist.
* Again traverse the linkedlist upto length-n. and next node is next of next node.

## Code :
```
ListNode* removeNthFromEnd(ListNode* head, int n) {
    ListNode *temp=head;
    int length=0;
    while(temp){
        length++;
        temp=temp->next;
    }
    temp=head;
    if(length==n) return head->next;
    n=length-n;

    for(int i=1;i<n;i++){
        temp=temp->next;
    }
    temp->next=temp->next->next;
    return head;
}
```

## Complexicty :
* **Time Complexity : *O(N+N)***
* **Space Complexity : *O(1)***
