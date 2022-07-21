# Summary of Day-7

## 1. [Reverse LinkedList](https://leetcode.com/problems/reverse-linked-list/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

![](https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg)
## Approach :
* Traverse the linkedlist.
* Change the arrow direction. By using two pointer approach.

## Code :
```
ListNode* reverseList(ListNode* head) {
    if(head==NULL || head->next==NULL){
        return head;
    }
    ListNode *temp=head,*prev=NULL,*next=NULL;

    while(temp!=NULL){
        next=temp->next;
        temp->next=prev;
        prev=temp;
        temp=next;
    }
    head=prev;

    return head;
}
```

## Complexicty :
* **Time Complexity : *O(N)***
* **Space Complexity : *O(1)***

#
## 2. [Middle element of LinkedList](https://leetcode.com/problems/middle-of-the-linked-list/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

![](https://assets.leetcode.com/uploads/2021/07/23/lc-midlist1.jpg)

![](https://assets.leetcode.com/uploads/2021/07/23/lc-midlist2.jpg)
## Approach :
* Traverse the linkedlist and count the no.of nodes.
* Traverse from start to length/2 and return the node.

## Code :
```
ListNode* middleNode(ListNode* head) {
    int len=0;
    ListNode *temp=head;
    while(temp){
        len++;
        temp=temp->next;
    }
    temp=head;
    for(int i=0;i<len/2;i++){
        temp=temp->next;
    }
    return temp;
}
```

## Complexicty :
* **Time Complexity : *O(N)+O(N)***
