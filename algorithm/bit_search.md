# bit search（bit 全探索）

## bit 全探索とは

- ありえる組み合わせをすべて試す全探索の一種
- ２択によって決められる N 個の状態のすべての組み合わせを調べる
- イメージとしては
  - 「使う／使わない」を全探索する
  - 「選ぶ／選ばない」を全探索する

[こわくない bit 全探索 1 入門編: bit 全探索ってなに？【競プロ解説】 | Qiita](https://qiita.com/u2dayo/items/68e35815659b1041c3c2)

[【ゆっくり解説】bit 全探索 ABC182 C【競技プログラミング】 | Youtube](https://www.youtube.com/watch?v=umfbbrElhaM)

## 典型問題（部分和問題）

長さが `N` の数列（A とする） `{1, 2, ..., N}` がある。

その数列より複数の値を選択し、その合計（W とする）が `10` となるパターンは何種類あるか。

## 計算量

### 時間計算量

O(2^N)

## 実装方法

直積集合を利用する方法と、ビット演算を利用する方法がある。

### 直積集合を利用して実装

[itertools.product](https://docs.python.org/ja/3/library/itertools.html#itertools.product) を利用する。

```python
from itertools import product

N = 5                   # 数列内の値の数
A = [1, 2, 3, 4, 5]     # 数列
W = 10                  # 求める合計値
count = 0               # 合致するパターン数

# 数列内の値の数だけ、真偽値を利用した直積集合を用意する
# 下記のようなパターンが作成される
#  (True, True, True, True, True)
#  (True, True, True, True, False)
#  ...
#  (False, False, False, False, False)
for pattern in product((True, False), repeat=N):
    sum = 0
    for i in range(N):
        # Trueの時に、数列Aより合算値を求める
        if pattern[i]:
            sum += A[i]
    # 合算値を求める値と比較する
    if sum == W:
        count += 1

print(count)
# 3
# 以下のパターンが合致する
#  (True, True, True, True, False)
#  (True, False, False, True, True)
#  (False, True, True, False, True)
```

[こわくない bit 全探索 2 基本編 1: 簡単な例題で bit 全探索をやってみよう！【競プロ解説】 | Qiita](https://qiita.com/u2dayo/items/8c1601a61841540b4947)

### ビット演算を利用して実装

`bitシフト演算` と `bit論理積` を利用する。

```python
N = 5                   # 数列内の値の数
A = [1, 2, 3, 4, 5]     # 数列
W = 10                  # 求める合計値
count = 0

# 数列内の数分だけ、真偽値を利用した直積集合を用意する
# 下記のような、２進数のパターンが作成される
# 0b0
# 0b1
# 0b10
# 0b11
# 0b100
# ...
# 0b11111
#
# なお、 range(1 << 5) は、以下と同義となる
# - range(1 << 5)
# - range(2 ** 5)
# - range(32)
for bit in range(1 << N):
    sum = 0
    for i in range(N):
        # 2進数で用意されたパターンに対して、1の値を１桁ずつ増やした２進数をぶつけて、論理積をもとめる
        # range(N)で、数列内の値の数だけ繰り返されるので、(1 << i) は以下のパターンが作成される
        # 0b1
        # 0b10
        # 0b100
        # 0b1000
        # 0b10000
        if bit & (1 << i):
            sum += A[i]
    if sum == W:
        count += 1

print(count)
# 3
# 以下のパターンが合致する
#  0b1111
#  0b10110
#  0b11001
```

[こわくない bit 全探索 3 基本編 2: 2 進法を使って実装してみよう！【競プロ解説】 | Qiita](https://qiita.com/u2dayo/items/e321c66aa43e3a9b1b31)
