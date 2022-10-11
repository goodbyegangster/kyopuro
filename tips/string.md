# Python の String 型はシーケンスである、ということ

String 型はシーケンスであるため、list のように処理できる。

## 参考

```python
# シーケンスのため、スライスで文字列を指定できる
X = "hololive"
print(X[1])

# リストに入れると、まるで２次元配列のように処理できる
Y = ["pekora", "mikochi", "suichan"]
print(Y[1][0])
# m

# アンパックして出力
print(*Y)
# pekora mikochi suichan

# list in list の２次元配列を作って処理すると、下記みたくなる
Y = [["pekora"], ["mikochi"], ["suichan"]]
print(Y[1][0])     # この場合、list in list の list が返る
# mikochi
print(Y[1][0][3])  # この場合、list in list の String から スライスを指定できる
# o
```
