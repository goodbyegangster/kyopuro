# 再帰関数 (recursive function)

- [再帰関数 (recursive function)](#再帰関数-recursive-function)
  - [漸化式と再帰関数](#漸化式と再帰関数)
    - [参考](#参考)
  - [コード](#コード)
    - [末尾再帰](#末尾再帰)
    - [メモ化](#メモ化)

## 漸化式と再帰関数

漸化式は再帰関数で表現することができる。

### 参考

複利計算を例とする。元金が１万円で、利率が１％である口座がある場合、元金は以下の通り推移する。

| 年数(n) |    元金(p) | 利率(r) |       利息 |   元利合計 |
| :-----: | ---------: | ------: | ---------: | ---------: |
|    0    |      10000 |       0 |          0 |      10000 |
|    1    |      10000 |    0.01 |        100 |      10100 |
|    2    |      10100 |    0.01 |        101 |      10201 |
|    3    |      10201 |    0.01 |     102.01 |   10303.01 |
|    4    |   10303.01 |    0.01 |   103.0301 | 10406.0401 |
|    5    | 10406.0401 |    0.01 | 104.060401 | 10510.1005 |

これは、以下の漸化式で表される。

```txt
・ f(n) = p                      (n = 0)  # 初年度は、当然元金が変わらない
・ f(n) = f(n-1) + (f(n-1) * r)  (n > 0)  # 翌年以降、前年の元金に利率が加味される
```

この計算は、以下の for 文で表現できる。

```python
p: float = 10000  # 元金
r: float = 0.01   # 利率
n: int = 5        # 期間

for _ in range(n):
    p = p + (p * r)

print(p)
# 10510.100501
```

一方で、以下の再帰関数としても表現できる。再帰関数内で、漸化式がそのまま出てくる。

```python
p: float = 10000  # 元金
r: float = 0.01   # 利率
n: int = 5        # 期間


def func(p, r, n):
    if n == 0:
        return p
    return func(p, r, n-1) + (func(p, r, n-1) * r)


print(func(p, r, n))
# 10510.100501
```

[漸化式と再帰 ― 数学 ×Python プログラミング入門](https://www.youtube.com/watch?v=D2jHia1wiHw)

## コード

フィボナッチ数列を例にする。フィボナッチ数列の以下の漸化式で定義される。

```txt
・F(0) = 0
・F(1) = 1
・F(n+2) = F(n) + F(n+1)
```

[フィボナッチ数](https://ja.wikipedia.org/wiki/%E3%83%95%E3%82%A3%E3%83%9C%E3%83%8A%E3%83%83%E3%83%81%E6%95%B0)

### 末尾再帰

`F(n+2) = F(n) + F(n+1)` の式を `F(n) = F(n-2) + F(n-1)` と変形させ、以下の再帰関数で表現できる。

```python
import sys
sys.setrecursionlimit(10 * 10000)


def fibonacci(x: int) -> int:
    if x <= 1:
        return x
    return (fibonacci(x-2) + fibonacci(x-1))


x = 10
print(fibonacci(x))
# 55
```

### メモ化

メモ化のテクニックを利用する。

> メモ化は、一度計算した再帰関数の結果を配列などに保存しておき、再度同じ関数の計算が必要になった際はそこから参照するテクニックです。これにより、同じ関数の計算結果を何度も再帰呼び出しを用いて計算してしまうことを避けることができます。

[アルゴ式 - Q4-4. フィボナッチ数列 (再帰-2)](https://algo-method.com/tasks/423/editorial)

```python
import sys
sys.setrecursionlimit(10 * 10000)


def fibonacci(x: int) -> int:
    if memo[x] != -1:            # 既に計算済のため、その結果を取得する
        return memo[x]
    if x <= 1:
        memo[x] = x
    if memo[x] == -1:            # 未計算のため、計算を行い、配列に結果を格納する
        memo[x] = fibonacci(x-2) + fibonacci(x-1)
    return memo[x]


x = 10
memo = [-1 for _ in range(x+1)]  # 計算結果を格納する配列を用意し、初期値を入れておく
print(fibonacci(x))
# 55
```
