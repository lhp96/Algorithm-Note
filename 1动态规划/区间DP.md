## 石子合并

> 前缀和 + 区间
>
> `dp[l][r] = min(dp[l][r], dp[l][k] + dp[k+1][r] +(s[r] - s[l-1]));`

```c++
const int N = 310, INF = 1e9;
int w[N], s[N];
int dp[N][N];
int n;
int main()
{
    cin >> n;
    for(int i = 1; i <= n; i++) cin >> w[i];
    for(int i = 1; i <= n; i++) s[i] = s[i-1]+w[i];
    
    for(int len = 2; len <= n; len++)
        for(int l = 1; l + len - 1 <= n; l++)
        {
            int r = l + len -1;
            dp[l][r] = INF;
            for(int k = l; k < r; k++)
            {
                dp[l][r] = min(dp[l][r], dp[l][k] + dp[k+1][r] +(s[r] - s[l-1]));
            }
        }
        
    cout << dp[1][n];
    return 0;
}
```

