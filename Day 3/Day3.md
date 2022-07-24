# Summary of Day-3

## 1. [Grid Unique Paths](https://leetcode.com/problems/unique-paths/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Take a dummy matrix of size m*n fill with -1.
* We recursively move from (0,0) to (m-1,n-1).
* If we encountered negative index then return 0.
* If we encountered our end point return 1.
* Whenever we returning the answers we store them in dummy matrix and whenerver we making a recursive call we simple check if that state is already visited or not.

## Code :
```
int paths(int i,int j,int m,int n,vector<vector<int>> &dp){
    if(i==m-1 && j==n-1){
        return 1;
    }
    if(i==m || j==n){
        return 0;
    }
    if(dp[i][j]!=-1){
        return dp[i][j];
    }
    return dp[i][j]=paths(i,j+1,m,n,dp)+paths(i+1,j,m,n,dp);
}

int uniquePaths(int m, int n) {
    vector<vector<int>> dp(m+1,vector<int>(n+1,-1));
    int num=paths(0,0,m,n,dp);
    if(m==1 && num==1){
        return num;
    }
    return dp[0][0];
}
```

## Complexity :
* **Time Complexity : *O(MxN)***
* **Space Complexity : *O(MxN)***

