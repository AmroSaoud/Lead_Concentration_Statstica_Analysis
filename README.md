# Lead Concentration Statistical Analysis

## Project perspective

This project applies statistical analysis to a dataset of lead exposure and
health-related measurements. It was developed as a BMD407 final project to
explore whether lead measurements and participant characteristics are
associated with `MAXFWT` (maximum forced weight, as named in the source
analysis).

The analysis combines descriptive statistics, visual exploration, statistical
assumption checks, confidence intervals, resampling, and formal hypothesis
tests. Some of the descriptive-statistics and confidence-interval helpers are
implemented from scratch to demonstrate the underlying calculations.

## Repository contents

| File | Description |
| --- | --- |
| [`Project/ProjectB.R`](Project/ProjectB.R) | Main R analysis script |
| [`Project/lead.RData`](Project/lead.RData) | R data file loaded by the script |
| `Project/Final-Report-B.docx` | Final written report |
| `Project/Notes.docx` | Project notes |

## Functionality

The R script:

- Loads and inspects the `lead.RData` dataset.
- Converts coded categorical variables such as `Area`, `Sex`, `Lead_type`,
  and `Exposed` to factors.
- Calculates summaries including means, medians, minima, maxima, quartiles,
  and frequency tables.
- Detects numeric outliers using the 1.5 × IQR rule.
- Creates histograms, bar charts, scatter plots, regression lines, and
  boxplots.
- Checks normality with histograms, Q-Q plots, and Shapiro-Wilk tests.
- Checks variance assumptions with Levene's test.
- Calculates 90%, 95%, and 99% confidence intervals for `MAXFWT` by sex.
- Builds bootstrap sampling distributions and percentile confidence intervals.
- Tests differences in `MAXFWT` between males and females using a t-test and,
  when normality is not supported, a Mann-Whitney/Wilcoxon test.
- Tests whether participants with `Ld72 > 40` have lower `MAXFWT` than the
  comparison group using a one-sided Wilcoxon test.
- Compares the four sex/lead-type groups with Kruskal-Wallis analysis,
  factorial ANOVA, and Tukey post-hoc comparisons.

## Requirements

Install R and the packages used by the script:

```r
install.packages(c(
  "car",
  "infer",
  "tibble",
  "dunn.test",
  "report",
  "multcomp"
))
```

Base R functions and the `stats` package provide most of the remaining
statistical procedures.

## Running the analysis

Because the script loads `lead.RData` using a relative path, run it from the
`Project` directory:

```bash
cd Project
Rscript ProjectB.R
```

Alternatively, open `Project/ProjectB.R` in RStudio, set the working directory
to `Project`, and run the script interactively. The script produces plots in
the active R graphics device and prints statistical results to the console.

## Main conclusions reported by the analysis

- The two-sample comparison of `MAXFWT` by sex was not statistically
  significant.
- The group with `Ld72 > 40` had significantly lower `MAXFWT` than the
  comparison group in the one-sided Wilcoxon test.
- The four sex/lead-type groups showed evidence of differences in the
  Kruskal-Wallis analysis, with selected pairwise differences identified by
  Tukey post-hoc comparisons.

These conclusions are specific to the included dataset and the assumptions
and significance level used in the script; they should not be generalized
without additional data and validation.
