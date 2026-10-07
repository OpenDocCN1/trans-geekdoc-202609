Type I sums of squares involve a hierarchical analysis. For example, suppose we are interested in the effects of educational level upon income. We might wish to consider for other factors such as the industry sector where the participant is employed (e.g., finance, hospitality, etc.). In that case, we would first remove the sum of squares due to industry sector, and then calculate in terms of Figure 9.6b, if we represent education by A and by B, the sum of squares for sector would correspond to the full circle of $SS_B$, and the education sum of squares, adjusted for sector, without respect to the a and u. Type I sums of squares rest on the assumption that cell sizes represent population sizes, an assumption that is likely to be met when the independent variable is observed rather than manipulated (e.g., income level, occasion, or clinical diagnosis) or when some treatments are more active than others (e.g., participants may find some more difficult to maintain in a study of cholesterol level).

Although the Type III sum of squares is often the default, all three types of analyses are available in most software packages. In the next section, we dropped crosses randomly from the eight cells of the Wiley–Voss data set and used software to analyze the data to note the similarities and differences among the three types of sums of squares. Appendix 9.1 details how to obtain $SS$ in both R and SPSS.

# 9.8.3 A Numerical Example

The data set is linked to the Wiley–Voss book on the website and has the file name Wiley_Unequal_N.xlsx. The means and cell frequencies are in Table 9.14. Table 9.15 presents the results of each analysis, after choosing a different model.

Table 9.14 Cell means (frequencies) for an experiment with unequal $n$

Table 9.15 Sums of squares (SS) for data with unequal cell frequencies

Note: The Type la SS is obtained when A is the first factor in the software package; the Type Ib SS is the result of entering B first. The letters in parentheses refer to the corresponding areas in Figure 9.6b. The text and Appendix 9.1 for further explanation.