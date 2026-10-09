```
func main() {
	config := `int Vlan1
				desc v1
! int Vlan2
			desc v2
`

	a := regexp.MustCompile("(?m)\n^!\$\n)")
	m := a.Split(config, -1)

	arr := [][]string{}

	for _, s := range m {
			s := strings.TrimSuffix(s, "\n")
			m := strings.Split(s, "\n")

			arr = append(arr, m)
	}

	fmt.Printf("%q\n", arr)
}
```

The output is shown with double quotes and brackets to demonstrate the result.

```
[["int Vlan1 " desc v1"]["int Vlan2 " desc v2]]
```