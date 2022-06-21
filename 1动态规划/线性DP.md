[TOC]

```
​```c++

```



# 数字三角形模型

## 二维空间方法

```c++
const int N = 510, INF = -1e9;
int dp[N][N];
int n;
int main()
{
    cin >> n;
    for(int i = 0; i <= n; i++)
        for(int j = 0; j <= i+1; j++)
            dp[i][j] = INF;
    dp[0][0] = 0;
    int res = INF;
    for(int i = 1; i <= n; i ++)
        for(int j = 1; j <= i; j++)
        {
            scanf("%d", &dp[i][j]);
            dp[i][j] = max(dp[i-1][j-1],dp[i-1][j]) + dp[i][j];
            if(i == n) res = max(res, dp[n][j]);
        }

    cout << res << endl;
    return 0;
}
```

## 一维空间优化

```c++

```







# 最长上升子序列模型

## 长度较短的序列

```c++
int main()
{
    cin >> n;
    for(int i = 1; i <= n; i++) scanf("%d", &a[i]);
    
    for(int i = 1; i <= n; i++)
    {
        dp[i] = 1;
        for(int j = 1; j < i; j++)
        {
            if(a[i] > a[j])
                dp[i] = max(dp[i], dp[j]+1);
        }
    }
    int res = 0;
    for(int i = 1; i <= n; i++) res = max(dp[i],res);
    cout << res << endl;
    return 0;
}
```



## 长度较长的序列

```c++
const int N = 100010;

int n;
int a[N];
int q[N];

int main()
{
    scanf("%d", &n);
    for (int i = 0; i < n; i ++ ) scanf("%d", &a[i]);

    int len = 0;
    for (int i = 0; i < n; i ++ )
    {
        int l = 0, r = len;
        while (l < r)
        {
            int mid = l + r + 1 >> 1;
            if (q[mid] < a[i]) l = mid;
            else r = mid - 1;
        }
        len = max(len, r + 1);
        q[r + 1] = a[i];
    }

    printf("%d\n", len);
}
```



```c++

```



## 最长公共子序列

```c++
int main()
{
    cin >> n >> m;
    string a , b;
    cin >> a >> b;
    a = " " + a, b = " " + b;
    for(int i = 1; i <= n; i++)
        for(int j = 1; j <= m; j++)
        {
            dp[i][j] = max(dp[i-1][j], dp[i][j-1]);
            if(a[i] == b[j]) dp[i][j] = max(dp[i][j], dp[i-1][j-1] + 1);
        }
    
    cout << dp[n][m];
    return 0;
}
```