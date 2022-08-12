# Summary of Day-19

## 1. [Subset Sum](https://practice.geeksforgeeks.org/problems/subset-sums2234/1)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Traverse through the array and for each index solve for two arrays, one where you pick the element
* Add the element to the sum or don’t pick and move to the next element, recursively, until the base condition.
* Here when you reach the end of the array is the base condition.

![](https://lh4.googleusercontent.com/f-cF0GX84YkT_9VaDr_8XpqbLOsbfbcIV8zqjoNmjloOS1LCG4MbO33O_2XLTO292CFoE47Ql1w3l6NPQjrrGs1D3R96uiNWuTFtW6m5LAsY2XGOT4eGvuaZ72ccI1UnwbLkG7fI)

## Code :
```
void solve(vector<int> arr,int ind,int sum,int n,vector<int> &ans){
    if(ind==n){
        ans.push_back(sum);
        return;
    }
    solve(arr,ind+1,sum+arr[ind],n,ans);
    solve(arr,ind+1,sum,n,ans);
}
```
```
vector<int> subsetSums(vector<int> arr, int N)
{
    vector<int> ans;
    solve(arr,0,0,N,ans);
    sort(ans.begin(),ans.end());
    return ans;
}
```

## Complexicty :
* **Time Complexity : *O(2^N)+O(2^N log(2^N))***
* **Space Complexity : *O(2^N)***
