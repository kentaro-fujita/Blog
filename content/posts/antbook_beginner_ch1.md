---
title: "Atcoder版!蟻本(初級編) in Python 1章"
date: 2020-07-17T00:56:09+09:00
draft: false
katex: true
tags: []
categories: []
---

# 1章をPythonで解く

https://qiita.com/drken/items/e77685614f3c6bf86f44の問題をPythonで解いていくシリーズです．

## 1 いざチャレンジ!でもその前に --- 準備編
### 1-1 プログラミングコンテストって何？
* 例題 1-1-1 くじびき
{{< highlight python >}}
n, m = map(int, input().split())
k = list(map(int, input().split()))

for a in range(n):
    for b in range(n):
        for c in range(n):
            for d in range(n):
                if k[a] + k[b] + k[c] + k[d] == m:
                    print("Yes")
                    exit()
print("No")
{{< /highlight >}}

* [JOI 2007 本選 C ダーツ](https://atcoder.jp/contests/joi2008ho/tasks/joi2008ho_c)
{{< highlight python >}}
from bisect import bisect_right

n, m = map(int, input().split())
p = [0] + [int(input()) for _ in range(n)]
p.sort()

l = [p[i]+p[j] for i in range(n+1) for j in range(i, n+1) if p[i]+p[j] <= m]
l.sort()

ans = 0
for x in l:
    y = l[bisect_right(l, m - x) - 1]
    ans = max(ans, x + y)

print(ans)
{{< /highlight >}}

### 1-6 気軽にウォーミングアップ
* 例題 1-6-1 三角形
{{< highlight python >}}
n = int(input())
a = list(map(int, input().split()))

ans = 0
for i in range(n):
    for j in range(i+1, n):
        for k in range(j+1, n):
            if a[i] + a[j] > a[k] and a[j] + a[k] > a[i] and a[k] + a[i] > a[j]:
                ans = max(ans, a[i]+a[j]+a[k])

print(ans)
{{< /highlight >}}

* [ARC 004 A 2点間距離の最大値](https://atcoder.jp/contests/arc004/tasks/arc004_1)
{{< highlight python >}}
n = int(input())
xy = [list(map(int, input().split())) for _ in range(n)]

ans = 0
for i in range(n):
    for j in range(n):
        xi, yi = xy[i]
        xj, yj = xy[j]
        ans = max(ans, ((xi-xj)**2 + (yi-yj)**2)**(1/2))

print(ans)
{{< /highlight >}}

* [ABC 051 B Sum of Three Integers](https://atcoder.jp/contests/abc051/tasks/abc051_b)
{{< highlight python >}}
k, s = map(int, input().split())

ans = 0
for x in range(k+1):
    for y in range(k+1):
        z = s - x - y
        if 0 <= z <= k:
            ans += 1

print(ans)
{{< /highlight >}}

* [ABC 085 C Otoshidama](https://atcoder.jp/contests/abc085/tasks/abc085_c)
{{< highlight python >}}
k, s = map(int, input().split())

ans = 0
for x in range(k+1):
    for y in range(k+1):
        z = s - x - y
        if 0 <= z <= k:
            ans += 1

print(ans)
{{< /highlight >}}

* 例題 1-6-2 [Ants(POJ No.1852)](http://poj.org/problem?id=1852)
{{< highlight python >}}
t = int(input())

ans = []
for _ in range(t):
    l, n = map(int, input().split())
    x = list(map(int, input().split()))

    res1 = 0
    res2 = 0
    for i in range(n):
        res1 = max(res1, min(x[i], l-x[i]))
        res2 = max(res2, max(x[i], l-x[i]))
    ans.append([res1, res2])

for a in ans:
    print(*a)
{{< /highlight >}}