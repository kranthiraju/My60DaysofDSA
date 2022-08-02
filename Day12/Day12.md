# Summary of Day-12

## 1. [3-Sum](https://leetcode.com/problems/3sum/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Sort the given array.
* Travese the array and low points to next of current element.
* high points to last element of array.
* compare nums[low]+nums[high] is equal to negative of current element.
* else move low pointer to right or high pointer to left.
## Code :
```
vector<vector<int>> threeSum(vector<int>& nums) {
    vector<vector<int>> v;
    sort(nums.begin(),nums.end());

    for(int i=0;i<nums.size()-2;i++){
        if(i==0 || (i>0 && nums[i]!=nums[i-1])){
            int lo=i+1,hi=nums.size()-1,sum=0-nums[i];
            while(lo<hi){
                if(nums[lo]+nums[hi]==sum){
                    v.push_back({nums[i],nums[lo],nums[hi]});

                    while(lo<hi && nums[lo]==nums[lo+1]) lo++;
                    while(lo<hi && nums[hi]==nums[hi-1]) hi--;

                    lo++;hi--;
                }
                else if(nums[lo]+nums[hi]<sum){
                    lo++;
                }
                else{
                    hi--;
                }
            }
        }
    }
    return v;
}
```

## Complexicty :
* **Time Complexity : *O(N^2)***
* **Space Complexity : *O(3k)***

#
## 2. [Trapping Rainwater](https://leetcode.com/problems/trapping-rain-water/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Take two arrays of size of given array as prefix, suffix.
* In prefix it stores the maximum value of left side from each element.
* In suffix it stores the maximum value of right side from each element.
* Traverse tha array, water stored in each height is minimum of prefix, suffix value of that index and subtract the current value and sum it up.


## Code :
```
int trap(vector<int>& height) {
    int water=0,n=height.size();
    int prefix[n],suffix[n];
    prefix[0]=height[0];

    for(int i=1;i<n;i++){
        prefix[i]=max(prefix[i-1],height[i]);
    }

    suffix[n-1]=height[n-1];
    for(int i=n-2;i>=0;i--){
        suffix[i]=max(suffix[i+1],height[i]);
    }

    for(int i=0;i<n;i++){
        water+=min(prefix[i],suffix[i])-height[i];
    }
    return water;
}
```

## Complexicty :
* **Time Complexity : *O(N+N+N)***
* **Space Complexity : *O(N+N)***
