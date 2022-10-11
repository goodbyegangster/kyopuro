# 素数判定のアルゴリズム

## 考え方

ある整数 `N` が素数であるか判定するには、ある整数 `N` の平方根以下までの整数で試し割り、あまりを見ればよい。

## コード

```python
def is_prime(N: int) -> bool:
    if N < 2:
        return False
    i = 2
    while i * i <= N:
        if N % i == 0:
            return False
        i += 1
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
