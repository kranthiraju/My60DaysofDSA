# Summary of Day-11

## 1. [Palindrome LL](https://leetcode.com/problems/palindrome-linked-list/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

![](https://assets.leetcode.com/uploads/2021/03/03/pal1linked-list.jpg)

## Approach :
* Traverse the linkedList upto middle element.
* Reverse the linkedlist after middle element and traverse the given linkedlist again.
* If any dummy node and slow node is not equal then return false.

## Code :
```
ListNode* reverseLL(ListNode* head){
    ListNode *prev=NULL,*next=NULL;
    while(head!=NULL){
        next=head->next;
        head->next=prev;
        prev=head;
        head=next;
    }
    return prev;
}
bool isPalindrome(ListNode* head) {
    ListNode *slow=head,*fast=head,*dummy=head;

    while(fast->next && fast->next->next){
        slow=slow->next;
        fast=fast->next->next;
    }

    slow->next=reverseLL(slow->next);

    slow=slow->next;

    while(slow){
        if(dummy->val!=slow->val){
            return false;
        }
        dummy=dummy->next;
        slow=slow->next;
    }

    return true;
}
```

## Complexicty :
* **Time Complexity : *O(N/2)+O(N/2)+O(N/2)***
* **Space Complexity : *O(1)***

#
## 2. [Starting point of loop in a Linked List](https://leetcode.com/problems/linked-list-cycle-ii/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

## Approach :
* Traverse the LinkedList and store the nodes in map.
* If we enconutered the node is present in map then return it.

## Code :
```
ListNode *detectCycle(ListNode *head) {
    ListNode *temp=head;
    unordered_map<ListNode*,int> mp;
    while(temp){
        if(mp.find(temp)!=mp.end()){
            return temp;
        }
        mp[temp]++;
        temp=temp->next;
    }
    return NULL;
}
```

## Complexicty :
* **Time Complexity : *O(N)***
* **Space Complexity : *O(N)***
