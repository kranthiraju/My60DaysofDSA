# Summary of Day-5

## 1. [Longest subarray with sum zero](https://practice.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Store the prefix sum and index in hashmap.
* traverse the array and add array element to sum.
* If sum is zero then update max.
* Else if sum exist in hashmap it means subarray with equal sum, so we update our max by taking maximum of max and current_index - value of sum in hashmap.
* Else insert sum to hashmap as value of index.

## Code :
```
int maxLen(vector<int>&A, int n)
{
    int maxx=0,sum=0;
    unordered_map<int,int> mp;
    for(int i=0;i<n;i++){
        sum+=A[i];
        if(sum==0){
            maxx=max(maxx,i+1);
        }
        else if(mp.find(sum)!=mp.end()){
            maxx=max(maxx,i-mp[sum]);
        }
        else{
            mp[sum]=i;
        }
    }
    return maxx;
}
```

## Complexicty :
* **Time Complexity : *O(N)***
* **Space Complexity : *O(N)***

#
## 2. [Count number of subarrays with given Xor K](https://www.codingninjas.com/codestudio/problems/1115652?topList=striver-sde-sheet-problems&utm_source=striver&utm_medium=website)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Store prefix xor in hashmap with no.of occurence as value.
* Traverse the array , xor the array elements to xo.
* If xo is equal to given integer then increment the count.
* If xo^x is exist in hashmap then increment then count by value of that key in hashmap.
* And increment the occurence of xor value.

## Code :
```
int subarraysXor(vector<int> &arr, int x)
{
    int count=0,xo=0;
    unordered_map<int,int> mp;
    for(int i=0;i<arr.size();i++){
        xo^=arr[i];
        if(xo==x){
            count++;
        }
        if(mp.find(xo^x)!=mp.end()){
            count+=mp[xo^x];
        }
        mp[xo]++;
    }
    return count;
}
```

## Complexicty :
* **Time Complexity : *O(N)***
* **Space Complexity : *O(N)***
