# Summary of Day-4

## 1. [2-sum Problem](https://leetcode.com/problems/two-sum/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* By using hashmap. we will use hashmap to find if target-nums[i] exists for each value of given array.
* If we found target-nums[i] in map, return the index and value of target-nums[i] in map.

## Code :
```
vector<int> twoSum(vector<int>& nums, int target) {
    unordered_map<int,int> mp;

    for(int i=0;i<nums.size();i++){
        mp[nums[i]]=i;
    }

    for(int i=0;i<nums.size();i++){
        if(mp[target-nums[i]]!=0 && mp[target-nums[i]]!=i){
            return {i,mp[target-nums[i]]};
        }
    }
    return {};
}
```

## Complexicty :
* **Time Complexity : *O(N+N)***
* **Space Complexity : *O(N)***

#
## 2. [4-sum Problem](https://leetcode.com/problems/4sum/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Sort the given array. Use 2-pointer approach.
* Now,we can fix two-pointer , one left another at end of array as right.
* If nums[left]+nums[right] < target then move left pointer towards right to maximize the sum. Else if sum > target then move right pointer towards left to minimize the sum.
* In order to avoid duplicates , we can jump the duplicates because taking duplicates will result in repating quads.

## Code :
```
vector<vector<int>> fourSum(vector<int>& nums, int target) {
    vector<vector<int>> ans;
    if(nums.empty()) return ans;

    sort(nums.begin(),nums.end());
    int n=nums.size();
    for(int i=0;i<n;i++){
        long long int t=target-nums[i];
        for(int j=i+1;j<n;j++){
            long long int target1=t-nums[j];

            int left=j+1;
            int right=n-1;

            while(left<right){
                if(nums[left]+nums[right] < target1){
                    left++;
                }
                else if(nums[left]+nums[right] > target1){
                    right--;
                }
                else{
                    vector<int> qrad;
                    qrad={nums[i],nums[j],nums[left],nums[right]};
                    ans.push_back(qrad);

                    while(left<right && nums[left]==q[2]) left++;
                    while(left<right && nums[right]==q[3]) right--;
                }
            }

            while(j+1<n && nums[j+1]==nums[j]) j++;
        }
        while(i+1<n && nums[i+1]==nums[i]) i++;
    }
    return ans;
}
```

#
## 3. [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Sort the given array.Traverse the array.
* if arr[i]==arr[i-1]+1 then increment the count variable.
* Else reset the count to 1 and store the max of ans,count in ans.

## Code :
```
int longestConsecutive(vector<int>& nums) {
    int ans=0,count=1;
    if(nums.empty()) return 0;
    sort(nums.begin(),nums.end());

    for(int i=1;i<nums.size();i++){
        if(nums[i]==nums[i-1]) continue;
        if(nums[i]-nums[i-1]==1){
            count++;
        }
        else{
            ans=max(count,ans);
            count=1;
        }
    }
    return max(ans,count);
}
```

## Complexicty :
* **Time Complexity : *O(NlogN)***
* **Space Complexity : *O(1)***
