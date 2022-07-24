# Summary of Day-2

## 1. [Search in a 2D matrix](https://leetcode.com/problems/search-a-2d-matrix/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Given that matrix is in sorted order.
* So, traverse all rows and check if target in between first and last of that row.
* If target is present in between then traverse that row and check the target on that row.

## Code :
```
bool searchMatrix(vector<vector<int>>& matrix, int target) {
        for(int i=0;i<matrix.size();i++){
            if(matrix[i][0]<=target && matrix[i][matrix[i].size()-1]>=target){
                for(int j=0;j<matrix[i].size();j++){
                    if(matrix[i][j]==target){
                        return true;
                    }
                }
            }
        }
        return false;
    }
```

## Complexity :
* **Time Complexity : *O(N^2)***

#
## 2. [Pow(X,n)](https://leetcode.com/problems/powx-n/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Take a double variable(ans) to store the answer, take a long long variable(m) to store copy of 'n'.
* Check if m is negative then make it postive by multiply with '-1'.
* Keep on iterating until m is greater than zero, now if m is an odd power then multiply x with ans, reduce m by 1. Else multiply x with itself and divide m by two.
* Check if n is negative then return the ans as 1/ans else return ans.

## Code :
```
double myPow(double x, int n) {
        double ans=1.0;
        long long m=n;
        if(m<0) m= -1 * m;
        while(m){
            if(m%2){
                ans*=x;
                m-=1;
            }
            else{
                x*=x;
                m/=2;
            }
        }
        if(n<0) ans=(double)(1.0) / (double)(ans);
        return ans;
    }
```

## Complexity :
* **Time Complexity : *O(logN)***
* **Space Complexity : *O(1)***

#
## 3. [Majority elements (>N/2 times)](https://leetcode.com/problems/majority-element/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Take a map of elements of the given array with key as element and value as count.
* On same time check whether that value of that element in map is more than N/2.
* If Yes then return that element.

## Code :
```
int majorityElement(vector<int>& nums) {
        unordered_map<int,int> mp;
        for(int i=0;i<nums.size();i++){
            mp[nums[i]]++;
            if(mp[nums[i]]>nums.size()/2){
                return nums[i];
            }
        }
        return 0;
    }
```

## Complexity :
* **Time Complexity : *O(NlogN)***
* **Space Complexity : *O(N)***
