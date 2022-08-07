# Summary of Day-15

## 1. [Minimum No.of platforms](https://practice.geeksforgeeks.org/problems/minimum-platforms-1587115620/1#)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* sort the arriving and depature time.
* If arriving time is less than depature time then add platform.
* If arriving time is greater than depature time then remove platform.

## Code :
```
int findPlatform(int arr[], int dep[], int n)
{
    int plats=1,maxx=1;
    sort(arr,arr+n);
    sort(dep,dep+n);
    int i=1,j=0;

    while(i<n && j<n){
        if(arr[i]<=dep[j]){
            plats++;
            i++;
        }
        else if(arr[i]>dep[j]){
            plats--;
            j++;
        }
        maxx=max(maxx,plats);
    }

    return maxx;
}
```

## Complexicty :
* **Time Complexity : *O(NlogN)+O(NlogN)+O(N)***
* **Space Complexity : *O(1)***
