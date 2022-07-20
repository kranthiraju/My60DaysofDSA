# Summary of Day-6

## 1. [Longest Substring without repeat](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

### 🚨Disclaimer : Don’t jump directly to the solution, try it out yourself first.

## Approach :
* Counting the elements and maintaining the frequency of each and every element in vector.
* We will store unity by talking the latest index of every element.

## Code :
```
int lengthOfLongestSubstring(string s) {
    vector<int> mp(256,-1);

    int left=0,right=0;
    int maxlen=0;

    while(right<s.size()){
        if(mp[s[right]]!=-1){
            left=max(mp[s[right]]+1,left);
        }
        mp[s[right]]=right;
        maxlen=max(maxlen,right-left+1);
        right++;
    }
    return maxlen;
}
```

## Complexicty :
* **Time Complexity : *O(N)***
* **Space Complexity : *O(N)***
