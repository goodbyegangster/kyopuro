## 「組み合わせ」と「順列」と「直積集合（デカルト積）」を作成するライブラリ

### 組み合わせ

`itertools.combinations()` を利用する。第1引数に「選択対象データのiterable」を、第2引数に「選択数」を入れる。

例えば、[0, 1, 2, 3, 4] より、3つ選んだ組み合わせパターンを抽出する場合。つまり、5C3 の場合。

```python
from itertools import combinations

a = [0, 1, 2, 3, 4]
combination = combinations(a, 3)                        # combinations(iterable, 選択する数)
print(combination)
# <itertools.combinations object at 0x7fba3c0778b0>
print(list(combination))
# [(0, 1, 2), (0, 1, 3), (0, 1, 4), (0, 2, 3), (0, 2, 4), (0, 3, 4), (1, 2, 3), (1, 2, 4), (1, 3, 4), (2, 3, 4)]

pattern = []
for i, j, k in combinations(a, 3):
    pattern.append((i, j, k))

print(pattern)
# [(0, 1, 2), (0, 1, 3), (0, 1, 4), (0, 2, 3), (0, 2, 4), (0, 3, 4), (1, 2, 3), (1, 2, 4), (1, 3, 4), (2, 3, 4)]
```

[itertools.combinations()](https://docs.python.org/3.9/library/itertools.html#itertools.combinations)

### 順列

`itertools.permutations()` を利用する。第1引数に「選択対象データのiterable」を、第2引数に「選択数」を入れる。

例えば、[0, 1, 2, 3, 4] より、3つ選んだ順列のパターンを抽出する場合。つまり、5P3の場合。

```python
from itertools import permutations

a = [0, 1, 2, 3, 4]
permutation = permutations(a, 3)

print(permutation)
# <itertools.permutations object at 0x7f5dd80c9770>
print(list(permutation))
# [(0, 1, 2), (0, 1, 3), (0, 1, 4), (0, 2, 1), (0, 2, 3), (0, 2, 4), (0, 3, 1), (0, 3, 2), (0, 3, 4), (0, 4, 1), (0, 4, 2), (0, 4, 3), (1, 0, 2), (1, 0, 3), (1, 0, 4), (1, 2, 0), (1, 2, 3), (1, 2, 4), (1, 3, 0), (1, 3, 2), (1, 3, 4), (1, 4, 0), (1, 4, 2), (1, 4, 3), (2, 0, 1), (2, 0, 3), (2, 0, 4), (2, 1, 0), (2, 1, 3), (2, 1, 4), (2, 3, 0), (2, 3, 1), (2, 3, 4), (2, 4, 0), (2, 4, 1), (2, 4, 3), (3, 0, 1), (3, 0, 2), (3, 0, 4), (3, 1, 0), (3, 1, 2), (3, 1, 4), (3, 2, 0), (3, 2, 1), (3, 2, 4), (3, 4, 0), (3, 4, 1), (3, 4, 2), (4, 0, 1), (4, 0, 2), (4, 0, 3), (4, 1, 0), (4, 1, 2), (4, 1, 3), (4, 2, 0), (4, 2, 1), (4, 2, 3), (4, 3, 0), (4, 3, 1), (4, 3, 2)]

pattern = []
for i, j, k in permutations(a, 3):
    pattern.append((i, j, k))

print(pattern)
# [(0, 1, 2), (0, 1, 3), (0, 1, 4), (0, 2, 1), (0, 2, 3), (0, 2, 4), (0, 3, 1), (0, 3, 2), (0, 3, 4), (0, 4, 1), (0, 4, 2), (0, 4, 3), (1, 0, 2), (1, 0, 3), (1, 0, 4), (1, 2, 0), (1, 2, 3), (1, 2, 4), (1, 3, 0), (1, 3, 2), (1, 3, 4), (1, 4, 0), (1, 4, 2), (1, 4, 3), (2, 0, 1), (2, 0, 3), (2, 0, 4), (2, 1, 0), (2, 1, 3), (2, 1, 4), (2, 3, 0), (2, 3, 1), (2, 3, 4), (2, 4, 0), (2, 4, 1), (2, 4, 3), (3, 0, 1), (3, 0, 2), (3, 0, 4), (3, 1, 0), (3, 1, 2), (3, 1, 4), (3, 2, 0), (3, 2, 1), (3, 2, 4), (3, 4, 0), (3, 4, 1), (3, 4, 2), (4, 0, 1), (4, 0, 2), (4, 0, 3), (4, 1, 0), (4, 1, 2), (4, 1, 3), (4, 2, 0), (4, 2, 1), (4, 2, 3), (4, 3, 0), (4, 3, 1), (4, 3, 2)]
```

[itertools.permutations](https://docs.python.org/3.9/library/itertools.html#itertools.permutations)

### 直積集合（デカルト積）

`直積集合（デカルト積）` とは、複数の集合から要素を一つずつ取り出した組み合わせの集合、のこと。下記コードのトランプの例がわかりやすい。

[wikipedia - 直積集合](https://ja.wikipedia.org/wiki/%E7%9B%B4%E7%A9%8D%E9%9B%86%E5%90%88)

`itertools.product()` を利用する。

```python
# トランプのカード一覧を、直積集合を踏まえて作成してみる
from itertools import product

suits = ["spade", "club", "dia", "heart"]
ranks = [str(i) for i in range(1, 14)]

production = product(suits, ranks)
print(type(production))
# <class 'itertools.product'>
print(list(production))
# 4 * 13 = 52種類のパターンをタプルで返してくる
# [('spade', '1'), ('spade', '2'), ('spade', '3'), ('spade', '4'), ('spade', '5'), ('spade', '6'), ('spade', '7'), ('spade', '8'), ('spade', '9'), ('spade', '10'), ('spade', '11'), ('spade', '12'), ('spade', '13'), ('club', '1'), ('club', '2'), ('club', '3'), ('club', '4'), ('club', '5'), ('club', '6'), ('club', '7'), ('club', '8'), ('club', '9'), ('club', '10'), ('club', '11'), ('club', '12'), ('club', '13'), ('dia', '1'), ('dia', '2'), ('dia', '3'), ('dia', '4'), ('dia', '5'), ('dia', '6'), ('dia', '7'), ('dia', '8'), ('dia', '9'), ('dia', '10'), ('dia', '11'), ('dia', '12'), ('dia', '13'), ('heart', '1'), ('heart', '2'), ('heart', '3'), ('heart', '4'), ('heart', '5'), ('heart', '6'), ('heart', '7'), ('heart', '8'), ('heart', '9'), ('heart', '10'), ('heart', '11'), ('heart', '12'), ('heart', '13')]
```

`repeat` 引数を指定すると、処理対象の iterable を指定回だけ繰り返し利用する

```python
from itertools import product

A = [True, False]
production = product(A, repeat=3)

print(list(production))
# 2 ** 3 = 8種類のパターンをタプルで返してくる
# [(True, True, True), (True, True, False), (True, False, True), (True, False, False), (False, True, True), (False, True, False), (False, False, True), (False, False, False)]
```

[itertools.product()](https://docs.python.org/3.9/library/itertools.html#itertools.product)
