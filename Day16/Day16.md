# Summary of Day-16

## 1. [Job Sequencing](https://practice.geeksforgeeks.org/problems/job-sequencing-problem-1587115620/1#)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Sort the jobs in descending order of profit.
* If the maximum deadline is x, make an array of size x .Each array index is set to -1 initially as no jobs have been performed yet.
* For every job check if it can be performed on its last day.
* If possible mark that index with the job id and add the profit to our answer.
* If not possible, loop through the previous indexes until an empty slot is found.

## Code :
```
vector<int> JobScheduling(Job arr[], int n)
{
    // your code here
    sort(arr,arr+n,cmp);
    int maxi=arr[0].dead;

    for(int i=0;i<n;i++){
        maxi=max(maxi,arr[i].dead);
    }

    int slot[maxi+1];

    for(int i=0;i<=maxi;i++){
        slot[i]=-1;
    }

    int countJobs=0,jobJobs=0;
    for(int i=0;i<n;i++){
        for(int j=arr[i].dead;j>0;j--){
            if(slot[j]==-1){
                slot[j]=i;
                countJobs++;
                jobJobs+=arr[i].profit;
                break;
            }
        }
    }
    return {countJobs,jobJobs};
}
```

## Complexicty :
* **Time Complexity : *O(NlogN)+O(NM)***
* **Space Complexity : *O(M)***
