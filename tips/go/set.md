# go で set 型を利用する

go には set 型は用意されていない。しかしながら、map 型を利用することで、同じようなことを実現できる。

map 型の Key では重複を許さないので、Value に空の値を入れて利用してあげれば良い。

```golang
package main

import "fmt"

func main() {
	set := map[string]struct{}{}

	set["Mikochi"] = struct{}{}
	set["Sui-chan"] = struct{}{}
	set["Fubuki-chan"] = struct{}{}
	set["Mikochi"] = struct{}{}

	fmt.Println(set)
    // map[Fubuki-chan:{} Mikochi:{} Sui-chan:{}]
}
```
