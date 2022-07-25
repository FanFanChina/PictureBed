## 题目

[4498.指针](https://www.acwing.com/problem/content/4501/)

## 解析

数据范围较小， 可以暴搜

sum：记录中间过程的读数变化

flag：记录返回时是否满足条件（判定方法：sum %360 == 0）

返回条件：枚举到最后一个度数的下一个

## 代码

```cpp
#include <bits/stdc++.h>
using namespace std;

const int N = 20;

int n, a[N];
bool flag;

void dfs(int i, int sum) {
    if(i == n + 1) {
        if(sum % 360 == 0) flag = true;
        return;
    }
    dfs(i + 1, sum + a[i]);
    dfs(i + 1, sum - a[i]);
}

int main() {
    scanf("%d", &n);
    for(int i = 1; i <= n; i ++ ) scanf("%d", &a[i]);
    dfs(1, 0);
    if(flag) puts("YES");
    else puts("NO");
    return 0;
}
```