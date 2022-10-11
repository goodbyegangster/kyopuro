# 貪欲法 (greedy algorithm)

### 貪欲法とは

貪欲法とは、

> 後先のことを考えず、その場その場での選択を繰り返していく

[アルゴ式 - 貪欲法](https://algo-method.com/descriptions/95)

> このアルゴリズムは問題の要素を複数の部分問題に分割し、それぞれを独立に評価を行い、評価値の高い順に取り込んでいくことで解を得るという方法である。動的計画法と異なり保持する状態は常に一つであり、一度選択した要素を再考する事は無い。

[Wikipedia 貪欲法](https://ja.wikipedia.org/wiki/%E8%B2%AA%E6%AC%B2%E6%B3%95)

### 典型

種類 `[100, 50, 10, 5, 1]` をもつコインがあるとき、`X` 円と合致する最小のコイン枚数は何枚となるか。

```python
X = int(input())
coins = [100, 50, 10, 5, 1]

rest = X
count_coin = [0 for _ in range(len(coins))]

for i in range(len(coins)):
    # q, mod = divmod(10, 3)
    # q...3, mod...1
    count_coin[i], rest = divmod(rest, coins[i])

print(sum(count_coin))
# 3
```
