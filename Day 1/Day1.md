# Summary of Day-1

## 1. [Repeat and missing number](https://www.codingninjas.com/codestudio/problems/873366?topList=striver-sde-sheet-problems&utm_source=striver&utm_medium=website)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Map the all elements of the array.
* Traverse the loop from 1 to N.
* If map[i]==0 then missing number is i.
* If map[i]>1 then repeating number is i.

## Code :
```
pair<int,int> missingAndRepeating(vector<int> &arr, int n)
{
    int r=0,m=0;
    unordered_map<int,int> mp;
    for(int i=0;i<n;i++){
        mp[arr[i]]++;
    }
    for(int i=1;i<=n;i++){
        if(mp[i]==0) m=i;
        else if(mp[i]==2) r=i;
    }

    return {m,r};
}
```

## Complexity :
* **Time Complexity : *O(N)***
* **Space Complexity : *O(N)***

#
## 2. [Count Inversion of array](https://www.codingninjas.com/codestudio/problems/615?topList=striver-sde-sheet-problems&utm_source=striver&utm_medium=website)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* By using Merge Sort.

## Code :
```
long long merge(long long arr[],long long temp[],int start,int mid,int end){
    long long inv_count=0;

    int i=start,j=mid,k=start;

    while((i<=mid-1) && (j<=end)){
        if(arr[i]<=arr[j]){
            temp[k++]=arr[i++];
        }
        else{
            temp[k++]=arr[j++];
            inv_count += (mid-i);
        }
    }

    while(i<=mid-1){
        temp[k++]=arr[i++];
    }
    while(j<=end){
        temp[k++]=arr[j++];
    }

    for(i=start;i<=end;i++){
        arr[i]=temp[i];
    }
    return inv_count;
}

long long mergesort(long long arr[],long long temp[],int start,int end){
    int mid=(start+end)/2;
    long long inv_count=0;

    if(start<end){
        inv_count += mergesort(arr,temp,start,mid);
        inv_count += mergesort(arr,temp,mid+1,end);

        inv_count += merge(arr,temp,start,mid+1,end);
    }

    return inv_count;
}
long long getInversions(long long *arr, int n){
    long long temp[n];
    return mergesort(arr,temp,0,n-1);
}
```

## Complexity :
* **Time Complexity : *O(NlogN)***
