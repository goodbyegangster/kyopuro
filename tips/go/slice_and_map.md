# slice と map の使い方 <!-- omit in toc -->

- [slice in slice](#slice-in-slice)
- [map in slice](#map-in-slice)
- [slice in map](#slice-in-map)

## slice in slice

```go
	N := 3
```

```go
	var s1 [][]int
	for i := 0; i < N; i++ {
		s1 = append(s1, []int{i, i + 1, i + 2})
	}
	fmt.Println(s1)
	// [[0 1 2] [1 2 3] [2 3 4]]
```

```go
	var s2 [][]int
	for i := 0; i < N; i++ {
		row := []int{}
		for j := 0; j < N; j++ {
			row = append(row, i*j)
		}
		s2 = append(s2, row)
	}
	fmt.Println(s2)
	// [[0 0 0] [0 1 2] [0 2 4]]
```

```go
	s3 := make([][]int, N)
	for i := 0; i < N; i++ {
		s3[i] = make([]int, N)
		for j := 0; j < N; j++ {
			s3[i][j] = i * j
		}
	}
	fmt.Println(s3)
	// [[0 0 0] [0 1 2] [0 2 4]]
}
```

## map in slice

```go
	N := 3
```

```go
	var s1 []map[string]int
	for i := 0; i < N; i++ {
		s1 = append(s1, map[string]int{"a": i, "b": i + 1, "c": i + 2})
	}
	fmt.Println(s1)
	// [map[a:0 b:1 c:2] map[a:1 b:2 c:3] map[a:2 b:3 c:4]]
```

```go
	var s2 []map[int]int
	for i := 0; i < N; i++ {
		row := make(map[int]int)
		for j := 0; j < N; j++ {
			row[j] = j + 1
		}
		s2 = append(s2, row)
	}
	fmt.Println(s2)
	// [map[0:1 1:2 2:3] map[0:1 1:2 2:3] map[0:1 1:2 2:3]]
```

```go
	s3 := make([]map[int]int, N)
	for i := 0; i < N; i++ {
		s3[i] = make(map[int]int)
		for j := 0; j < N; j++ {
			s3[i][j] = j
		}
	}
	fmt.Println(s3)
	// [map[0:0 1:1 2:2] map[0:0 1:1 2:2] map[0:0 1:1 2:2]]
```

## slice in map

```go
	N := 3
```

```go
	m1 := make(map[int][]int)
	for i := 0; i < N; i++ {
		m1[i] = []int{i, i + 1, i + 2}
	}
	fmt.Println(m1)
	// map[0:[0 1 2] 1:[1 2 3] 2:[2 3 4]]
```

```go
	m2 := make(map[int][]int)
	for i := 0; i < N; i++ {
		for j := 0; j < N; j++ {
			m2[i] = append(m2[i], j)
		}
	}
	fmt.Println(m2)
	// map[0:[0 1 2] 1:[0 1 2] 2:[0 1 2]]
```
