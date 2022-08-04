# Summary of Day-14

## 1. [Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* By using Kadane's algorithm.
* Traverse the array and if element is zero then sum is zero else add element to sum and take maximum.
## Code :
```
int findMaxConsecutiveOnes(vector<int>& nums) {
    int sum=0,maxx=INT_MIN;
    for(int i=0;i<nums.size();i++){
        if(nums[i]==0){
            sum=0;
        }
        else{
            sum++;
        }
        maxx=max(maxx,sum);
    }
    return maxx;
}
```

## Complexicty :
* **Time Complexity : *O(N)***
* **Space Complexity : *O(1)***

#
## 2. [N meetings in one room](https://practice.geeksforgeeks.org/problems/n-meetings-in-one-room-1587115620/1)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Sort the pair with ending time.
* Make first meeting end at first element after sorted.
* Traverse the array, if start time is more than previous end time then increment meeting and endd make this ending time.
## Code :
```
static bool cmp(pair<int,int> a,pair<int,int> b){
    return a.second<b.second;
}
```
```
int maxMeetings(int start[], int end[], int n)
{
    // Your code here
    vector<pair<int,int>> v;
    for(int i=0;i<n;i++){
        v.push_back({start[i],end[i]});
    }

    sort(v.begin(),v.end(),cmp);

    int endd=v[0].second,meets=1;
    for(int i=1;i<n;i++){
        if(v[i].first > endd){
            meets++;
            endd=v[i].second;
        }
    }
    return meets;
}
```

## Complexicty :
* **Time Complexity : *O(N)+O(NlogN)+O(N)***
* **Space Complexity : *O(N)***

