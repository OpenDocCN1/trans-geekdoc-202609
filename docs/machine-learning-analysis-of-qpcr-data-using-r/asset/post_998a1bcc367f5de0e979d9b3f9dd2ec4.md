
a common option (Döring et al., 2019). The ROI (in this case, a file that contains the sequence for E. coli Stx2) is loaded into an R object. The specifics of the primers (such as length of the oligonucleotides and of the amplicon, position of the amplicon with respect to the reference sequence, and Tₘ of the oligonucleotides) are stored in an xml file. The easiest approach to personalize the design is to download a ready-made xml file from the openPrimeR website and then modify specific items.

### Listing 2.1
```r
library("openPrimeR")
fasta.file <- "stx.fa"
seq.df <- read_templates(fasta.file)
settings.xml <- system.file("extdata", "settings",
    "C_Taq_PCR_high_stringency.xml", package = "openPrimeR")
settings <- read_settings(settings.xml)
```

After all this, it is possible to design the primers. The specific conditions for the computation of the primer include a maximum length in the range 18-25 nucleotides and no mismatches between primers and template. The found primers are then written to local file for later use and this file is read back into memory to show the result.

### Listing 2.1 (continuation)
```r
constraints(design.settings)[["primer_length"]] <- c("min" = 18, "max" = 25)
conOptions(design.settings)[["allowed_mismatches"]] <- 0
primer_set <- design_primers(
  seq.df,
  mode.directionality = "both",
  settings,
  init.algo = "naive",
  opti.algo = "Greedy",
  required.cvg = 1,
  timeout = Inf,
  max.degen = 16,
  conservation = 1,
  sample.name = NULL,
  cur.results.loc = NULL,
  primer.df = NULL,
  updateProgress = NULL
)
write_primers(primer_set$opti, "stx_primers.fasta")
primer.df <- read_primers("stx_primers.fasta", fw.id = "_fw")
```

```r
> print(primer.df[, c("ID", "Forward", "Reverse")])
```

| ID | Forward | Reverse |
|---|---|---|
| 1-1| (stx|2:21|_fw | tgaagaagatgtttatggcg |  |
| 1-1| (stx|8:26|_rev |  | agtaacggttgcagattcc |

That is, the optimal forward primer for the sequence *E. coli* Stx2 target is 5′- TGAAGAAGATGTTTATGGCG-3′ and the paired reverse primer is 5′- AGTAACGGTTGCAGATTCC-3′. By repeating this procedure, the primers 5′- TTTGCCGACTGGGCTGTGCGG-3′ and 5′-CTCCGGTGTAAGTCAGGGCT-3′ are found for the DNA-pol. It is good practice to design at least three primer sets for each target and test them even in combination.

## Elements of Quantification

The qPCR does not directly count the molecules present in a sample, but instead allows one to estimate such number by associating the light produced by a sample with the copies of the target. Such association can be either absolute or relative. Absolute quantification provides an actual copy number (or load) of the target whereas the relative quantification gives the ratio between the target and a reference. Specifically, indicating with ΔCqS the difference between the Cq of the sample and a reference target, respectively, and ΔCqC the difference between the Cq of the calibrator and a reference target, respectively, it is possible to obtain the normalized expression ratio R_S between sample and calibrator (an untreated sample) (Livak and Schmittgen, 2001; Green and Sambrook, 2018):

R_S = E^{-ΔΔCq}. (2.1a)

where ΔΔCq = ΔCqs – ΔCqC, and E = 2. Using the E. coli O:157 example, let’s assume that the Cq of a sample treated for instance with UV irradiation to activate the expression of Stx2 (Yue et al., 2012) is 18 cycles. The Cq of the untreated sample is 24 and that of the reference gene is 22. It follows that ΔCqs is –4 cycles, ΔCqC is 2 cycles, and ΔΔCq is –6. Subsequently, R_S is 2^(-6) = 2^6 = 64; thus, the expression of Stx2 in UV-treated samples is 64 times that in the untreated cells.

Equation 2.1a is equivalent to (Pfaffl, 2001):

R_S = E_S^{ΔCq_s}/E_R^{ΔCq_c}. (2.1b)

Equation 2.1b takes into account the actual efficiency of amplification of the PCR. On the other hand, absolute quantification aims at calculating the actual number of target molecules in a given sample and its procedure will be described in the following paragraphs. In both absolute and relative quantification, though, light emission is converted into a digital value. There are two main systems for extracting light emission from vessels:

- Take a snapshot of all the reactions at once at each amplification cycle and then extrapolate the emission from each reaction. The PCR is typically carried out in a 96-well plate with conical bottom-wells; the optical apparatus takes a single picture of the top of the plate. The software then processes the fluorescence signal from each well.
- Record the light produced by each reaction independently. This is accomplished by placing the reaction vessels on a carousel that passes, at each rotation, in front of a laser optical apparatus. This system is commercialized as Rotor-gene™ by Qiagen and LightCycler™ by Roche.

In both cases, the end result is a table of numbers referring to the light emission of each sample at each amplification cycle. It should be kept in mind that the reported molecules (either probes or intercalators) increased their luminescence when in contact with the amplicons — either because they actually bind the DNA or because the DNA-pol has released the fluorophore. On the other hand, however, they emit light even when not in contact with the amplicons. For instance, SYBR Green™ increases its

luminescence over 2000 times after binding to the DNA, which means there is a background light that is two thousand-fold lower than the PCR-related signal. Such background is a noise that reduces the sensitivity of the PCR, and can be observed in the lower insert of Figure 1.2.

It is possible to relate the initial loads N₀ of two sample A and B as follows (Kubista et al., 2006):

N₀ᴬ/N₀ᴮ = (1 + E)^{CqA - CqB} = (1 + E)^{ΔCq}.  (2.2)

When the efficiency of amplification of the PCR is 1 (100%), then the base becomes 2^{ΔCq}. In the example, the difference in Cq between the UV-treated and UV-untreated samples is six, the ratio between their load is 2⁶ = 64.

It is possible to relate the quantity of ROI N_t at a given amplification cycle t to the initial amount of target N₀ with the equation (Rutledge and Côté, 2003):

N₀ = N_t (E+1)^{-t}.  (2.3)

Equation 2.3 can be linearized by converting to logarithms:

log(N₀) = log(N_t) - log(E+1) t =
= - log(E+1) t + log(N_t).  (2.4)

From Equation 2.3, the slope of the curve is -log(E+1) and the intercept is log(N_t). The curve needed to generate this curve is practically obtained by serially diluting a stock of a nucleic acids measured with an accurate method. Such series goes under the name of standard dilution and the resulting Cqs are used to generate a standard curve, that is a linear regression model. The interval between the lowest and highest dilutions should be within the dynamic range of the assay, that is the minimal and maximal amounts that the assay can accurately measure. A sample with unknown load can be quantified by interpolation using such a curve. This is possible because each reaction’s Cq is described by this equation (Rutledge and Côté, 2003):

Cqₙ = s × log(N₀) + I  (2.5)

where I (intercept) is the ideal Cq obtained if there was only one copy of target in the reaction and s is the slope obtained from fitting a line (or more

properly: a curve) on the standard curve’s values. Using s, it is possible to calculate the efficiency of the PCR:

$E = 10^{-1/s} - 1$  (2.6)

Let’s generate a standard curve with the following commands.

### Listing 2.2
```r
A1 <- PCR(10, d, K, r)
A2 <- PCR(100, d, K, r)
A3 <- PCR(1000, d, K, r)
A4 <- PCR(10000, d, K, r)
A5 <- PCR(100000, d, K, r)
A6 <- PCR(1000000, d, K, r)
cq_1 <- find_cycle(A1, 1:45, 37)
cq_2 <- find_cycle(A2, 1:45, 35)
cq_3 <- find_cycle(A3, 1:45, 28)
cq_4 <- find_cycle(A4, 1:45, 25)
cq_5 <- find_cycle(A5, 1:45, 23)
cq_6 <- find_cycle(A6, 1:45, 20)
Sample <- c(rep("s1", 45), rep("s2", 45), rep("s3", 45), rep("s4", 45), rep("s5", 45), rep("s6", 45))
Cqs <- c(rep(cq_1, 45), rep(cq_2, 45), rep(cq_3, 45), rep(cq_4, 45), rep(cq_5, 45), rep(cq_6, 45))
Cycle <- rep(1:45, 6)
Fluorescence <- c(A1, A2, A3, A4, A5, A6)
StdCv <- data.frame(Sample, Cqs, Cycle, Fluorescence)
shades <- c("gray0", "gray20", "gray40", "gray60", "gray80", "gray90")
plot(Fluorescence~Cycle, StdCv[StdCv$Sample=="s1",], type = "l", lwd = 3, col=shades[1], xlab="Amplification cycle", ylab="Fluorescence")
points(Fluorescence~Cycle, StdCv[StdCv$Sample=="s2",], type = "l", lwd = 3, col=shades[2])
points(Fluorescence~Cycle, StdCv[StdCv$Sample=="s3",], type = "l", lwd = 3, col=shades[3])
points(Fluorescence~Cycle, StdCv[StdCv$Sample=="s4",], type = "l", lwd = 3, col=shades[4])
points(Fluorescence~Cycle, StdCv[StdCv$Sample=="s5",], type = "l", lwd = 3, col=shades[5])
points(Fluorescence~Cycle, StdCv[StdCv$Sample=="s6",], type = "l", lwd = 3, col=shades[6])
abline(h=1000)
points(unique(StdCv$Cqs)[1], 1000, cex = 2, bg=shades[1], pch = 21)
points(unique(StdCv$Cqs)[2], 1000, cex = 2, bg=shades[2], pch = 21)
points(unique(StdCv$Cqs)[3], 1000, cex = 2, bg=shades[3], pch = 21)
points(unique(StdCv$Cqs)[4], 1000, cex = 2, bg=shades[4], pch = 21)
points(unique(StdCv$Cqs)[5], 1000, cex = 2, bg=shades[5], pch = 21)
points(unique(StdCv$Cqs)[6], 1000, cex = 2, bg=shades[6], pch = 21)
legend("topleft",legend = unique(StdCv$Input), title = "Input", pch = 19, col = shades)
```
