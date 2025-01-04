# 「標準入力」を「文字列入力」に入れ替える方法

```golang
package main

import (
	"os"
)

func mockStdin(input string) (clean func()) {
	temp, _ := os.CreateTemp("", "mock")
	temp.Write([]byte(input))
	temp.Seek(0, 0)

	os.Stdin = temp

	return func() {
		temp.Close()
		os.Remove(temp.Name())
	}
}

func gen() string {
	return `
`
}

func main() {
	clean := mockStdin(gen())
	defer clean()

}
```
