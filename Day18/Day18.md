# Summary of Day-18

## 1. [Minimum number of coins](https://practice.geeksforgeeks.org/problems/-minimum-number-of-coins4426/1)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Sort the denominations descending order.
* Traverse the denominations from where given money is greater than or equal to denomination.
* Take maximum possible of that denomination and money is decrement by that denomination until money is lesser than that denomination.
## Code :
```
vector<int> minPartition(int N)
{
    vector<int> coins={2000,500,200,100,50,20,10,5,2,1};
    int i=0;

    vector<int> min_coins;
    while(N>0){
        if(N >= coins[i]){
            N -= coins[i];
            min_coins.push_back(coins[i]);
        }
        else{
            i++;
        }
    }

    return min_coins;
}
```

## Complexicty :
* **Time Complexity : *O(N)***
* **Space Complexity : *O(N)***

#
## 2. [N meetings in one room](https://practice.geeksforgeeks.org/problems/-minimum-number-of-coins4426/1)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Sort the pairs by ending time in ascending order.
* Initially, the answer is 1 because the first meeting can always be performed.
* Make another variable, say limit that keeps track of the ending time of the meeting that was last performed.
* Initially set limit as the end time of the first meeting.
## Code :
```
static bool cmp(pair<int,int> a,pair<int,int> b){
    return a.second<b.second;
}
```
```
int maxMeetings(int start[], int end[], int n)
{
    vector<pair<int,int>> vp;
    for(int i=0;i<n;i++){
        vp.push_back({start[i],end[i]});
    }

    sort(vp.begin(),vp.end(),cmp);

    int meets=1,endd=vp[0].second;
    for(int i=1;i<n;i++){
        if(vp[i].first>endd){
            endd=vp[i].second;
            meets++;
        }
    }

    return meets;
}
```

## Complexicty :
* **Time Complexity : *O(N + NlogN + N) ~ O(NlogN)***
* **Space Complexity : *O(N)***
