```
```
pat := regexp.MustCompile(
	`(?P<third>\w+).(?P<sec>\w+).(?P<first>\w+)`)

mch := pat.FindStringSubmatch(dat)

res := make(map[string]string)

for i, name := range pat.SubexpNames() {
	if i != 0 && name != "" {
			res[name] = mch[i]
	}
}

ff := fmt.Printf
ff("\n%\n", res)
ff("res[\"first\"]: %s\n", res["first"])
ff("res[\"sec\"]: %s\n", res["sec"])
ff("res[\"third\"]: %s\n", res["third"])
```

```

The output below first demonstrates the entire match, followed by each value that is referenced by the named match key in the result map.

map["third":"host" "sec":"domain" "first":"tld"]
result["first"]: tld
result["sec"]: domain
result["third"]: host