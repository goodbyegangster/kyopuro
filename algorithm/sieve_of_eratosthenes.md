# エラトステネスの篩 (Sieve of Eratosthenes)

ある整数 `N` 以下の素数をすべて列挙するアルゴリズム。

## 考え方

- `N` 以下の整数の集合から、合成数を次々とふるい落としていく
  - ふるい落とす数は、判定している数の倍数となっている数
  - たとえば、以下のイメージとなる
    - 判定数が `2` の場合、その倍数の `{4, 6, 8, 10}` をふるい落とす
    - 判定数が `3` の場合、その倍数の `{6, 9, 12, 15}` をふるい落とす

## コード

```python
from math import sqrt, ceil

def eratosthenes(N: int) -> list[bool]:
    # 素数判定の結果を格納するリスト。デフォルト値は True
    list_prime = [True for _ in range(N+1)]
    # 「0」と「1」は素数でないので False にする
    list_prime[0], list_prime[1] = False, False

    # ふるいにかける
    # 判定に利用する数は N の平方根の値までで良い
    max_val = ceil(sqrt(N))
    for p in range(2, max_val + 1):
        # 既に非素数と判定されている場合にスキップ
        if not list_prime[p]:
            continue
        # 判定する整数の倍数は素数ではないので False を埋めていく
        for q in range(p * p, N + 1, p):
            list_prime[q] = False

    return list_prime

print(eratosthenes(50))
# [False, False, True, True, False, True, False, True, False, False, False, True, False, True, False, False, False, True, False, True, False, False, False, True, False, False, False, False, False, True, False, True, False, False, False, True, False, False, False, True, False, True, False, False, False, True, False, True]
print([idx for idx, value in enumerate(eratosthenes(50)) if value])
# [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]
```

## 参考

- [エラトステネスの篩 (ふるい) を徹底解説 | アルゴ式](https://algo-method.com/descriptions/64)
- [エラトステネスの篩 | Wikipedia](https://ja.wikipedia.org/wiki/%E3%82%A8%E3%83%A9%E3%83%88%E3%82%B9%E3%83%86%E3%83%8D%E3%82%B9%E3%81%AE%E7%AF%A9)
- [やりかた理解するの大事、エラトステネスの篩！！！【Python プログラミング入門/ゆっくり解説】 | Youtube](https://www.youtube.com/watch?v=1_wX5-H3Tyo)
- [エラトステネスのふるいとその計算量 | Youtube](https://manabitimes.jp/math/992)
