# 再帰関数の実行上限数を更新する

Python では、実行可能な再帰処理の上限が設定されている。上限に触れた場合、以下のエラーとなる。

> maximum recursion depth exceeded while calling a Python object

以下にて、`recursionlimit` のデフォルト値を更新できる。

```python
import sys
sys.setrecursionlimit(10 * 10000)
```
