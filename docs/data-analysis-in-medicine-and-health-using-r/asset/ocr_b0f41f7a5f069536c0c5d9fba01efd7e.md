```
## smoke_yrs : chr "15-19" "20-24" "25-29" "30-34" ...
## cigar_day : num 0 0 0 0 0 0 0 5.2 ...
## person_yrs : int 10366 8162 5969 4496 3512 1421 1201 1121 826 3121 ...
## case : int 1 0 0 0 0 0 0 2 0 ...
```

# 10.5.3 Data exploration

For descriptive statistics, we use epidis::codebook as before.

```
epiDisplay::codebook(smoke)

##
##
##
## smoke_yrs :
## A character vector
##
## ==========
## cigar_day :
## obs. mean median s.d. min. max.
## 63 17.271 15.9 12.913 0 40.8
##
## ==========
## person_yrs :
## obs. mean median s.d. min. max.
## 63 2426.444 1826 2038.143 104 10366
##
## ==========
## case :
## obs. mean median s.d. min. max.
## 63 2.698 1 3.329 0 12
##
## ==========
```

In addition, we are also interested to look at the observed rates,

```
smoke%>% mutate(rate = round(case/person_yrs, 4))
```

```
## smoke_yrs cigar_day person_yrs case rate
## 1 15-19 0.0 10366 1 0.0001
## 2 20-24 0.0 8162 0 0.0000
## 3 25-29 0.0 5969 0 0.0000
## 4 30-34 0.0 4496 0 0.0000
## 5 35-39 0.0 3512 0 0.0000
```