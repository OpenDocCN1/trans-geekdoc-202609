```
}

ipmask := ip.Mask(ipnet.Mask)

	for ip := ipmask; ipnet.Contains(ip); inc(ip) {
		fmt.Println(ip)
	}
}
```

The output below lists all IP addresses within the CIDR network, including the network and broadcast addresses.

+   1.1.1.0
1.1.1.1
1.1.1.2
1.1.1.3