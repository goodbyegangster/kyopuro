# 基本

## １行の入力（変数）

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

## １行の入力（スライス）

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
