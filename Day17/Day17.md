# Summary of Day-17

## 1. [Fractional Knapsack](https://practice.geeksforgeeks.org/problems/fractional-knapsack-1587115620/1)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Sort the array of value per one unit of weight, according to weight.
* Pick up items with weight lesser than or equal to the current capacity of the knapsack.
* Calculate its value according to our current capacity and add this new value to our answer.
## Code :
```
static bool cmp(pair<int,double> a,pair<int,double> b){
    return a.second > b.second;
}
```
```
double fractionalKnapsack(int W, Item arr[], int n)
{
    vector<pair<int,double>> v;
    double pro=0;
    double fraction [n] = {0};

    for(int i=0;i<n;i++){
        v.push_back(make_pair(i,(double) arr[i].value/arr[i].weight));
    }

    sort(v.begin(),v.end(),cmp);

    for(auto i:v){
        if(arr[i.first].weight <= W){
            W -= arr[i.first].weight;
            fraction[i.first]=1;
        }
        else{
            fraction[i.first] = (double) W/arr[i.first].weight;
            W=0;
        }
    }
    for(int i=0;i<n;i++){
        pro += fraction[i]*arr[i].value;
    }

    return pro;
}
```

## Complexicty :
* **Time Complexity : *O(NlogN+N) O(NlogN)***
* **Space Complexity : *O(N)***
