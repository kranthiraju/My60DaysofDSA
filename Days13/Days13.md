# Summary of Day-13

## 1. [Remove Duplicate from Sorted array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Traverse the array from 2nd element.
* check if two elements is eqaul then increment count.

## Code :
```
int removeDuplicates(vector<int>& nums) {
    int c=0;
    for(int i=1;i<nums.size();i++){
        if(nums[i]==nums[i-1]){
            c++;
        }
        else{
            nums[i-c]=nums[i];
        }
    }
    return nums.size()-c;
}
```

## Complexicty :
* **Time Complexity : *O(N)***
* **Space Complexity : *O(1)***
