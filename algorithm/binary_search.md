# 探索 (binary search)

## 二分探索とは

> ソート済みのリストや配列に入ったデータ（同一の値はないものとする）に対する検索を行うにあたって、 中央の値を見て、検索したい値との大小関係を用いて、検索したい値が中央の値の右にあるか、左にあるかを判断して、片側には存在しないことを確かめながら検索していく。

[wikipedia - 二分探索](https://ja.wikipedia.org/wiki/%E4%BA%8C%E5%88%86%E6%8E%A2%E7%B4%A2)

## 計算量

### 時間計算量

`N` 個のデータがある場合、`O(logN)` となる

## 実装イメージ

(1) 初期値として、以下の値を設定する

- left
  - 取りうる値の最小値
- right
  - 取りうる値の最大値
- mid
  - (left + right) // 2

(2) `比較対象の値` と `midの値` を比較して、正解でなかった側（left or right）を切り詰める

```python
if x < mid:             # x の値は mid より小さい場合
    right = mid         # True. right側を切り詰める
else:
    left = mid + 1      # False. left側を切り詰める。同時に mid は x でないので、+1をしておく
```

## コード

### 単純な二分探索

```python
# リスト A 内にある X 未満の個数を数える
X = 6
A = [0, 3, 4, 6, 8, 9]

left = 0
right = len(A)

while left < right:
    mid = (left + right) // 2
    if X <= A[mid]:
        right = mid
    else:
        left = mid + 1

print(left)
# 3
```
