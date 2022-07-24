# Summary of Day-9

## 1. [Add two numbers as LinkedList](https://leetcode.com/problems/add-two-numbers/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

![](https://assets.leetcode.com/uploads/2020/10/02/addtwonumber1.jpg)
## Approach :
* Take a dummy node, ans node.
* Traverse the nodes till both will end. Take sum of value of current nodes and carry as sum/10. And add node of sum%10 to dummy node.

## Code :
```
ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
    ListNode *ans=new ListNode(),*temp=ans;
    int carry=0;

    while(l1 || l2 || carry){
        int sum=0;
        if(l1){
            sum+=l1->val;
            l1=l1->next;
        }
        if(l2){
            sum+=l2->val;
            l2=l2->next;
        }

        sum+=carry;
        carry=sum/10;
        ListNode *node=new ListNode(sum%10);
        temp->next=node;
        temp=temp->next;
    }
    return ans->next;
}
```

## Complexicty :
* **Time Complexity : *O(N)***
* **Space Complexity : *O(N)***
