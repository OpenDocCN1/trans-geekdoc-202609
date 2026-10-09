```
"bgp.tmpl", "ntp.tmpl")
tmpl["base.tmpl"] = template.Must(files, nil)
_ = tmpl["base.tmpl"].ExecuteTemplate(
  os.Stdout, "base", config)
}
```

The output below shows the combined data and templates.

```
hostname router1

router 1234
  router-id 4.4.4.4
  neighbor 1.1.1.1 remote-as 1
  neighbor 2.2.2.2 remote-as 2

ntp source-interface Loopback0
ntp server 11.11.11.11 prefer
ntp server 22.22.22.22
```