# Summary of Day-10

## 1. [Delete a given node (O(1)solution)](https://leetcode.com/problems/delete-node-in-a-linked-list/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

![](https://assets.leetcode.com/uploads/2020/09/01/node1.jpg)
## Approach :
* Replace the value of deleted node with next node value.
* Next pointer of deleted node is next of next node.

## Code :
```
void deleteNode(ListNode* node) {
    node->val=node->next->val;
    node->next=node->next->next;
}
```

## Complexicty :
* **Time Complexity : *O(1)***
* **Space Complexity : *O(1)***

#
## 2. [Find Intersection point in Y LL](https://leetcode.com/problems/intersection-of-two-linked-lists/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

![](https://assets.leetcode.com/uploads/2021/03/05/160_example_1_1.png)
## Approach :
* Make both linkedlists contains same length.
* Then traverse both linkedlists at same time ,if both nodes are equal then return it.
## Code :
```
int lengthLL(ListNode *head){
    ListNode *temp=head;
    int length=0;
    while(temp){
        length++;
        temp=temp->next;
    }
    return length;
}
```
```
ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
    ListNode *temp1=headA,*temp2=headB;
    int len1=lengthLL(temp1);
    int len2=lengthLL(temp2);
    int dis=0;

    if(len1<len2){
        dis=len2-len1;
        temp1=headA;
        temp2=headB;
    }
    else{
        dis=len1-len2;
        temp1=headB;
        temp2=headA;
    }

    for(int i=0;i<dis;i++){
        temp2=temp2->next;
    }

    while(temp1 && temp2){
        if(temp1==temp2){
            return temp1;
        }
        temp1=temp1->next;
        temp2=temp2->next;
    }

    return NULL;
}
```

## Complexicty :
* **Time Complexity : *O(2max(length of list1,length of list2))+O(abs(length of list1-length of list2))+O(min(length of list1,length of list2))***
* **Space Complexity : *O(1)***

#
## 3. [Detect Cycle in LL](https://leetcode.com/problems/linked-list-cycle/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

## Approach :
* Take slow,fast nodes which points to head of given linkedlist.
* slow it goes next pointer of its,fast it goes next of next pointer of its.
* slow and fast are equals then return true.
## Code :
```
bool hasCycle(ListNode *head) {
    ListNode *slow=head,*fast=head;

    while(fast && fast->next){
        slow=slow->next;
        fast=fast->next->next;
        if(slow==fast){
            return true;
        }
    }
    return false;
}
```

## Complexicty :
* **Time Complexity : *O(N)***
* **Space Complexity : *O(1)***
