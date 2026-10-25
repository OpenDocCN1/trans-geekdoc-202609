The details are beyond the scope of this book, but the survfit function from package survival can do the heavy lifting for us.

In the code snippet below, I call survfit to estimate and plot the survival curves for both the drug and placebo groups; see Figure 1.11. Here, you can see that the estimated survival curves between the treatment and control group are similar, indicating that D-penicillamine is rather ineffective. The log-rank test can be used to test for differences between the survival distributions of two groups. Some decision tree algorithms for the analysis of survival data use the log-rank test to help partition the data; see, for example, Segal [1988] and Leblanc and Crowley [1993].

```
palette("Okabe-Ito")
plot(survfit(Surv(time, status) ~ trt, data = pbc2), col = 2:3,
     conf.int = FALSE, las = 1, xlab = "Days until death",
     ylab = "Estimated survival probability")
legend("bottomleft", legend = c("PenicillMain", "Placebo"),
       lty = 1, col = 2:3, text.col = 2:3, inset = 0.01, bty = "n")
palette("default")
```

![](bbox=[0.18, 0.41, 0.88, 0.7])

FIGURE 1.11: Kaplan-Meier estimate of the survival function for the randomized subjects in the Mayo Clinic PBC data by treatment group (i.e., drug vs. placebo). The median survival times are 3282 days (drug) and 3428 days (placebo).

In Section 3.5.3, we'll see how a simple tree-based analysis can estimate the survival function conditional on a set of predictors, denoted \(\hat{S}(t|\boldsymbol{x})\), by partitioning the learning sample into non-overlapping groups with similar survival rates; here, we'll see further evidence that D-penicillamine was not effective