# deque

deque(double-ended queue) 両極端キュー。先頭または末尾で要素を追加・削除できるキューのこと。

## 実装方法

以下の実装方法がある。

- 動的配列
- 双方向連結リスト

## Python の collections.deque

Python 標準ライブラリ内の [collections.deque](https://docs.python.org/ja/3.13/library/collections.html#collections.deque) は、双方向連結リストとして実装されている。

## Go の container.list

deque という名前ではないが、双方向連結リストである [container.list](https://pkg.go.dev/container/list) を deque として利用できる。
