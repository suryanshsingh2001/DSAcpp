# Sliding Window

## Brute Force
```
#include<bits/stdc++.h>
using namespace std;
int maxSumSubarray(vector<int> &a, int k)
{
    int maxSum = INT_MIN;
    int n = a.size();
	
    if(n < k) return -1;
    for(int i = 0; i < n - k + 1; i++) {
        int curr = 0;
        for(int j = 0; j < k; j++) {
            curr += a[i+j];
        }
        maxSum = max(maxSum, curr);
    }
    return maxSum;
}
int main()
{
    vector<int> a{100, 200, 300, 400 };
    int k = 5;
    cout <<  maxSumSubarray(a, k);
}
```

## Optimized Approach

```
#include<bits/stdc++.h>
using namespace std;
int maxSumSubarray(vector<int> &a, int k)
{
   int n = a.size();
   if(n < k) return -1;
   
   int maxSum = 0;
   //first windows sum
   for(int i = 0; i < k; i++) {
       maxSum += a[i];
   }
   //next windows
   int windowSum = maxSum;
   for(int i = k; i < n; i++) {
       windowSum += a[i] - a[i - k];
       maxSum = max(maxSum, windowSum);
   }
   return maxSum;
}
int main()
{
    vector<int> a{1, 4, 2, 10, 2, 3, 1, 0, 20 };
    int k = 4;
    cout <<  maxSumSubarray(a, k);
    
}
```
