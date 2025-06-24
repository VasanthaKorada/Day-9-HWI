1.Job Scheduling with max profits 
---------------------------------------
```cpp
#include<bits/stdc++.h>
using namespace std;
int main(){
     int n;
    cin >> n;
    vector<vector<int>> v(n, vector<int>(3));
    for (int i = 0; i < n; i++) {
        cin >> v[i][0] >> v[i][1] >> v[i][2];
    }

  sort(v.begin(), v.end(), [](const vector<int>& a, const vector<int>& b) {
        return a[1] < b[1];
    });
    vector<int>dp(n);
    for(int i=0;i<n;i++){
        dp[i]=v[i][2];
        
    }
    
    for(int i=1;i<n;i++){
        for(int j=0;j<i;j++){
            if(v[i][0]>=v[j][1]){
                dp[i]=max(dp[i],v[i][2]+dp[j]);
            }
        }
    }
cout<<*max_element(dp.begin(),dp.end());
    
}
```
2.Robot path finding in matrix*
--------------------------------
```cpp
#include<bits/stdc++.h>
using namespace std;
int possible(int i,int j,int n,int m,vector<vector<int>>& v){
    if(i>=n || j>=m){
        return 0;
    }
if(v[i][j]!=1)
return 0;
if (i==n-1 and j==m-1)
return 1;
return possible(i+1,j,n,m,v) || possible(i,j+1,n,m,v);
}
int main(){
    int n,m;
    cin>>n>>m;
    vector<vector<int>>v(n,vector<int>(m+1));
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            cin>>v[i][j];
        }
    }
    cout<<possible(0,0,n,m,v);
    ```
3.Number of possible paths for the above sum
--------------------------------------
```cpp
#include <bits/stdc++.h>
using namespace std;

int possible(int i, int j, int n, int m, vector<vector<int>>& v, vector<vector<int>>& dp) {
   
    if (i >= n || j >= m) return 0;
   
    if (v[i][j] == 0) return 0;
    
    if (i == n - 1 && j == m - 1) return 1;
    
    if (dp[i][j] != -1) return dp[i][j];
    dp[i][j] = possible(i + 1, j, n, m, v, dp) + possible(i, j + 1, n, m, v, dp);
    return dp[i][j];
}
int main() {
    int n, m;
    cin >> n >> m;
    vector<vector<int>> v(n, vector<int>(m));
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            cin >> v[i][j];
        }
    }
    vector<vector<int>> dp(n, vector<int>(m, -1));
    cout << possible(0, 0, n, m, v, dp) << "\n";
    return 0;
```
4.ISLAND problem
-----------------------------
```cpp
#include<bits/stdc++.h>
using namespace std;
void numberofislands(int n,int m,int i,int j,vector<vector<int>>& v){
    if(i>=n || j>=m || i<0 ||j<0 || v[i][j]!=1)
    return ;
   if(v[i][j]==1){
       v[i][j]=2;
   }
 numberofislands(n, m, i + 1, j, v);
    numberofislands(n, m, i - 1, j, v);
    numberofislands(n, m, i, j + 1, v);
    numberofislands(n, m, i, j - 1, v);
}
int main(){
     int n, m;
    cin >> n >> m;
    int c=0;
     vector<vector<int>> v(n, vector<int>(m));
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            cin >> v[i][j];
        }
    }
         for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
          if(v[i][j]==1){
          numberofislands(n,m,i,j,v);
          c++;
        }
        }
         }
     cout << c;
}
```
