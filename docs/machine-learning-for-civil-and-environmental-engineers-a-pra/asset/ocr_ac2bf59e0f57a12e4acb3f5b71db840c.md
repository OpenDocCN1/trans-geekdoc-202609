```
```
}
if (f_ > 0.407) {
    if (a_mm_ > 919) {
        if (f_ > 0.825) {
            if (f_ > 1.95) {
                return(98)
            }
            if (f_ <= 1.95) {
                if (f_ > 1.15) {
                    return(76)
                }

                if (f_ <= 1.15) {
                    return(95)
                }
            }
        }
    }
    if (f_ <= 0.825) {
        if (f_ > 0.575) {
            return(65)
        }
        if (f_ <= 0.575) {
            return(76)
        }
    }
}
if (a_mm_ <= 919) {
    if (f_ > 1.096) {
        if (f_ > 2.372) {
            return(61)
        }
        if (f_ <= 2.372) {
            return(53)
        }
    }
    if (f_ <= 1.096) {
        return(40)
    }
}
if (f_ <= 0.407) {
    if (is.na(r_)) {
        return(100.66667)
    }

    if (r_ > 1.672) {
        if (r_ > 2.232) {
            return(155)
        }

        if (r_ <= 2.232) {
            return(134)
        }
    }

}
if (r_ <= 1.672) {
    if (f_ > 0.283) {
```
```