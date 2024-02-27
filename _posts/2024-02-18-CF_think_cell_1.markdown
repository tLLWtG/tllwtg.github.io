---
layout:     post
title:      "Codeforces think-cell Round 1"
subtitle:   " \"Solutions of problem A-D\""
date:       2024-02-18 10:00:00
author:     "tLLWtG"
header-style: text
mathjax: true
catalog: true
tags:
    - Code
    - CP
---

> 题目链接[点这里](https://codeforces.com/contest/1930)

鉴定为最近码量最小的一场 CF(A~D)。

### CF1930A Maximise The Score

排序后两两取较小值累加。这样就尽可能的使大的数不被浪费。

```cpp
void solve()
{
    int n, ans = 0;
    cin >> n;
    vector<int> arr(2 * n);
    for (auto &x: arr)
        cin >> x;
    sort(all(arr));
    for (int i = 0; i < 2 * n; i += 2)
        ans += arr[i];
    cout << ans << endl;
}
```

### CF1930B Permutation Printing

找规律发现：奇偶和大小都错开排列是一种答案。（如 $8,1,6,3,4,5,2,7$）

```cpp
void solve()
{
    int n, cur;
    cin >> n;
    vector<int> arr(n + 1);
    if (n % 2 == 0)
    {
        cur = n;
        for (int i = 1; i <= n; i += 2)
            arr[i] = cur, cur -= 2;
        cur = 1;
        for (int i = 2; i <= n; i += 2)
            arr[i] = cur, cur += 2;
    }
    else
    {
        cur = n;
        for (int i = 1; i <= n; i += 2)
            arr[i] = cur, cur -= 2;
        cur = 2;
        for (int i = 2; i <= n; i += 2)
            arr[i] = cur, cur += 2;
    }
    for (int i = 1; i <= n; ++i)
        cout << arr[i] << " ";
    cout << endl;
}
```

### CF1930C Lexicographically Largest

> 看完 C 题我的第一想法是写棵线段树，再看一眼又觉得是平衡树（）

玩几个样例后得到结论：先将 $a[i]+i$ 从大到小排序，然后顺序输出（对应原序列的操作就是从右到左取数加入集合，这样损失是最小的）。注意输出时若当前数和上一个数相同，为避免被去重则需要减一（对应原序列的操作即先取较左边的数，再取较右边相同的数）。

```cpp
void solve()
{
    priority_queue<int> pq;
    int n, x;
    cin >> n;
    for (int i = 1; i <= n; ++i)
    {
        cin >> x;
        pq.push(x + i);
    }
    int last = 2e9 + 5, cur;
    for (int i = 1; i <= n; ++i)
    {
        cur = pq.top();
        pq.pop();
        if (cur >= last)
            cur = last - 1;
        last = cur;
        cout << cur << " ";
    }
    cout << endl;
}
```

### CF1930D1 Sum over all Substrings (Easy Version)

容易发现 $[l,r]$ 取 $[i-1,i]$ 或 $[i,i+1]$ 就一定能覆盖最优的情况。然后就贪心的让 $1$ 尽量靠后出现且不浪费（只有当本位对应数字为 $1$ 且上一位和这一位没取 $1$ 的时候，下一位才取 $1$。例：$01110$ 按这样贪心得到的答案就是 $00100$）。

```cpp
void solve()
{
    int n, ans = 0;
    string str;
    cin >> n >> str;
    function<int(string &s)> foo = [&](string &s)->int
    {
        s = '?' + s;
        int sz = s.size(), res = 0;
        vector<int> ok(sz + 1);
        for (int i = 1; i < sz; ++i)
            if (s[i] == '1')
            {
                if (ok[i - 1] == 0 && ok[i] == 0)
                    ok[i + 1] = 1;
            }
        for (int i = 1; i <= sz; ++i)
            res += ok[i];
        return res;
    };
    for (int i = 0; i < n; ++i)
        for (int j = i; j < n; ++j)
        {
            string s = str.substr(i, j - i + 1);
            ans += foo(s);
        }
    cout << ans << endl;
}
```

### CF1930D2 Sum over all Substrings (Hard Version)

> ~~D2 正在补。```(=´ω`=)```~~

定义 $dp[i]$ 是以 $i$ 为左端点的所有字符串的 $f$ 值之和，并且规定从右到左进行状态转移。

当前字符为 $0$ 时，不需要使用 $1$ ，即 $dp[i]=dp[i+1]$。若当前字符为 $1$，则将 $i+1$ 位置设为 $1$，这样可以兼顾 $i,i+1,i+2$ 位置上的 $1$，因此 $i$ 位置的状态就从 $i+3$ 位置的状态转移过来。由定义，这个位置作为左端点可以形成 $n-i+1$ 个字符串，所以最后的转移方程就是 $dp[i]=dp[i+3]+(n-i+1)$。

然后累加 $dp$ 数组中的值作为答案。

```cpp
void solve()
{
    ll n, ans = 0;
    string str;
    cin >> n >> str;
    str = '?' + str;
    vector<ll> dp(n + 2);
    for(int i = n; i >= 1; --i)
    {
        if (str[i] == '0')
            dp[i] = dp[i + 1];
        else
            dp[i] = dp[min<ll>(i + 3, n + 1)] + (n - i + 1);
    }
    for (int i = 1; i <= n; ++i)
        ans += dp[i];
    cout << ans << endl;
}
```