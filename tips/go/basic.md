# 基本 <!-- omit in toc -->

- [１行の入力（変数）](#１行の入力変数)
- [１行の入力（変数、キャスト含む）](#１行の入力変数キャスト含む)
- [１行で、複数値の入力（変数）](#１行で複数値の入力変数)
- [１行で、複数値の入力（スライス）](#１行で複数値の入力スライス)
- [複数行で入力（スライスの長さが分かる場合）](#複数行で入力スライスの長さが分かる場合)

## １行の入力（変数）

### コード

```go
package main

import (
	"fmt"
)

func main() {
	var S string
	fmt.Scan(&S)

	fmt.Println(S)
}
```

### 入力

```
mikochi
```

### 出力

```
mikochi
```

## １行の入力（変数、キャスト含む）

### コード

```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	var N int
	scanner := bufio.NewScanner(os.Stdin)
	scanner.Scan()
	fmt.Sscanf(scanner.Text(), "%d", &N)

	fmt.Printf("%d %T \n", N, N)
}
```

### 入力

```
5
```

### 出力

```
5 int
```

## １行で、複数値の入力（変数）

### コード

```go
package main

import "fmt"

func main() {
	var a, b, c int
	fmt.Scanf("%d %d %d", &a, &b, &c)

	fmt.Println(a)
	fmt.Println(b)
	fmt.Println(c)
}
```

### 入力

```
1 2 3
```

### 出力

```
1
2
3
```

## １行で、複数値の入力（スライス）

### コード

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strconv"
	"strings"
)

func main() {
	sc := bufio.NewScanner(os.Stdin)
	sc.Scan()
	inputs := strings.Split(sc.Text(), " ")

	var tmp []int
	for _, input := range inputs {
		t, _ := strconv.Atoi(input)
		tmp = append(tmp, t)
	}

	for _, value := range tmp {
		fmt.Printf("%T: %d\n", value, value)
	}
}
```

### 入力

```
1 2 3
```

### 出力

```
int: 1
int: 2
int: 3
```

## 複数行で入力（スライスの長さが分かる場合）

### コード

```golang
package main

import "fmt"

func main() {
	n := 5
	a := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&a[i])
	}

	fmt.Println(a)
}
```

### 入力

```
10
20
30
40
50
```

### 出力

```
[10 20 30 40 50]
```
