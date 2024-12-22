# 素数判定のアルゴリズム

## 考え方

ある整数 `N` が素数であるかを判定するには、`N` の平方根以下の整数で試し割りを行い、余りが 0 でないかを確認すればよい。

## コード

```python
def is_prime(N: int) -> bool:
    if N < 2:
        return False
    x = 2
    while x * x <= N:
        if N % x == 0:
            return False
        x += 1
    return True

if __name__ == "__main__":
    for i in range(10):
        print(f"{i}: 素数" if is_prime(i) else f"{i}: Not 素数")
        # 0: Not 素数
        # 1: Not 素数
        # 2: 素数
        # 3: 素数
        # 4: Not 素数
        # 5: 素数
        # 6: Not 素数
        # 7: 素数
        # 8: Not 素数
        # 9: Not 素数
```
