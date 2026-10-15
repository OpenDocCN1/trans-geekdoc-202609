[1] "Operations Summary Report for the Year Ended March 31, 2021\n B C D E A Capacity H I J\n\n\n Capacity AEQ Tariff AEQ Tariff AEQ Tariff\n Capacity AEQ's Carried Actual Round AEQ Growth\n Routes Provided Utilization Fiscal Utilization Trips Revenue Fiscal Revenue Growth\n Fiscal 2021 Revenue Fiscal Revenue Fiscal 2020 Fiscal 2020 (C - F)\n (AEQ's) 2021 Note 2 (H - I)\n\n\n\n 1 (C / B) Fiscal 2020 2021 Note 2 2020 Note 2 2021 2021 2020 2021 2,239,426 1,557,909 69.6% 3,250.0 (811,527) $ 106,232,291 $ 152,416,489 (46,184,198)\n 2 84.1% 2,369,436 2,213.5 1,374,776 838,402 61.0% 68.8% 1,334,158 (495,756) 55,498,711 81,940,368 (26,441,657)\n 9 2,834.0 1,755,940 1,081,426 61.6% 65.9%

# FIGURE 8.4 BC Ferries page 11 from PDF file.

```
bcf_11 <- bcf[12]
```

bcf_11

[1] "Operations Summary Report for the Year Ended March 31, 2021\n\n K L M N O P\n Passenger\n Passenger Tariff Passengers % Sailings within 10 Min. (Note 3)\n Passenger Tariff Passengers Growth Passengers Revenue Fiscal Revenue Fiscal\n (N - ... ) Fiscal 2021 Fiscal 2021 (K - L) Fiscal 2020 2021 Note 2 2020 Note 2 ) YE Fiscal 2019 YE Fiscal 2020 YE Fiscal 2021\n\n 1 2,578,221 6,124,234 (3,546,013) 39,230,411 91,309,787 1,669,054 3,298,151 87.6% 87.2% 86.6% 2 1,669,054 3,298,151 (1,629,097) 25,150,326 48,775,753 (23,625,427) 81.8% 87.3% 86.2% 3 (4,001,646) 1,797,894 2,631,102 (833,208) 9,517,331 13,518,977 (4,001,646) 81.4% 88.0% 83.7% 30 1,158,810 1,652,801 (493,991) 378,372 23,970,199 (6,591,827) 85.3% 85.2% 80.6% Major Routes 7,203,979 13,706,288 (6,502,309) 91,276,440 177,574,716 (86,298,276) 84.3% 86.6% 84.3%\n\n 10 15,788 45,748 (29,960) 1,577,178

# FIGURE 8.5 BC Ferries page 12 from PDF file.

Now we have an object that is a single text string. All of the data we want is there, but it is going to take some finesse to extract the columns we want, and in a format that we can use.

Using the "\n" line break character, we can split this single value into as many lines as there are on the page.

```
# break into lines
bcf_11_lines <- bcf_11[[1]] |>
  strsplit(split = "\n")

# how many lines in the page?
length(bcf_11_lines[[1]])
```