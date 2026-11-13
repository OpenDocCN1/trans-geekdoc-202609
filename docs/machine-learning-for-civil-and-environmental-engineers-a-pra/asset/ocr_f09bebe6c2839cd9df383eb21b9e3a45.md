```
if (r_ > 0.6265) {
    return(136)
}
if (r_ <= 0.6265) {
    return(125)
}
}
if (f_ <= 0.283) {
    if (a_mm_ > 812) {
    if (is.na(fc_mpa_)) {
    return(99.85714)
    }
    if (fc_mpa_ > 40) {
    if (fc_mpa_ > 43) {
    if (f_ > 0.045) {
    if (is.na(t)) {
    return(98.25)
    }
    if (t > 1) {
    if (f_ > 0.075) {
    if (a_mm_ > 1000) {
    if (a_mm_ > 1250) {
    return(106)
    }
    if (a_mm_ <= 1250) {
    return(105)
    }
    }
    if (a_mm_ <= 1000) {
    return(114)
    }
    }
    if (f_ <= 0.075) {
    return(101)
    }
    }
    if (t <= 1) {
    if (r_ > 0.4935) {
    if (r_ > 0.806) {
    if (r_ > 1.1945) {
    return(98)
    }
    if (r_ <= 1.1945) {
    return(100)
    }
    }
    if (r_ <= 0.806) {
    return(89)
    }
    }
    if (r_ <= 0.4935) {
    return(73)
    }
}
```