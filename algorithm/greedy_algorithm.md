# 貪欲法 (greedy algorithm)

### 貪欲法とは

貪欲法とは、

> 後先のことを考えず、その場その場での選択を繰り返していく

[貪欲法 | アルゴ式](https://algo-method.com/descriptions/95)

> このアルゴリズムは問題の要素を複数の部分問題に分割し、それぞれを独立に評価を行い、評価値の高い順に取り込んでいくことで解を得るという方法である。動的計画法と異なり保持する状態は常に一つであり、一度選択した要素を再考する事は無い。

[貪欲法 | Wikipedia](https://ja.wikipedia.org/wiki/%E8%B2%AA%E6%AC%B2%E6%B3%95)

### 典型

種類 `[100, 50, 10, 5, 1]` をもつ硬貨があるとき、`X` 円と合致する最小のコイン枚数は何枚となるか。

```python
X = int(input())  # 176
coins = [100, 50, 10, 5, 1]

rest = X
coin_counts = [0 for _ in range(len(coins))]

for i in range(len(coins)):
    # > 問題の要素を複数の部分問題に分割し、それぞれを独立に評価を行い、評価値の高い順に取り込んでいくことで解を得る
    coin_counts[i], rest = divmod(rest, coins[i])  # 1, 76 = divmod(176, 100)

print(coin_counts)  # [1, 1, 2, 1, 1]
print(sum(coin_counts))  # 6
```
