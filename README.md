# basic_hypothesis


This script in R performs a series of statistical analyses and visualizations on automotive data.

### Loading Packages and Descriptive Statistics:

- `library(pastecs)`: Loads the `pastecs` package, which is used for statistical analysis.
- `round(stat.desc(vehiculos[, vehiculos2], basic = FALSE, norm = TRUE), digits = 3)`: Calculates various descriptive statistics (excluding basic ones, including normalization) for selected columns of the `vehiculos` DataFrame and rounds the results to three decimal places. A similar operation is performed on the `coches2` DataFrame for specific columns.

### Quantile-Quantile Plots with `car` Package:

- `library(car)`: Loads the `car` package, which provides functions for regression diagnostics.
- `qqPlot(coches2$peso)`: Creates a quantile-quantile plot for the `peso` variable of `coches2` to check normality.
- `qqPlot(coches2$peso, groups = coches2$origen)`: Creates a quantile-quantile plot with grouping by the `origen` variable.

### Density Plots with `ggplot2`:

- `library(ggplot2)`: Loads the `ggplot2` package for data visualization.
- `ggplot(coches2, aes(consumo)) + geom_density()`: Creates a density plot for the `consumo` variable in `coches2`.
- `ggplot(coches2, aes(consumo, color = origen)) + geom_density()`: Creates a density plot for `consumo` with different colors for different `origen` values.

### Normality Tests:

- `library(nortest)`: Loads the `nortest` package for normality tests.
- `vehiculosnumerico <- coches2[, c("cilindros", "desplazamiento", "CV", "peso", "aceleracion", "precio")]`: Extracts numerical columns from `coches2` into `vehiculosnumerico`.
- `shapiro.test(coches2$cilindros)`: Performs the Shapiro-Wilk normality test on the `cilindros` column.
- `lapply(vehiculosnumerico, shapiro.test)`: Applies the Shapiro-Wilk test to each column in `vehiculosnumerico`.
- `lapply(vehiculosnumerico, lillie.test)`: Applies the Lilliefors (Kolmogorov-Smirnov) normality test to each column.

### Multivariate Normality and Visualization:

- `library(MVN)`: Loads the `MVN` package for multivariate normality testing.
- `library(MSQC)`: Loads the `MSQC` package for multivariate statistical quality control.
- The `mvn` function is used multiple times with various arguments to test multivariate normality in different ways (Mardia's, Royston's tests, and others), including visualization options like QQ plots and perspective plots.

### Levene's Test for Equality of Variances:

- `library(car)`: Re-loads the `car` package.
- `lapply(vehiculosnumerico, leveneTest, coches2$origen)`: Applies Levene's Test to each column in `vehiculosnumerico` to check for equality of variances across groups defined by `coches2$origen`.

### Box's M Test for Equality of Covariance Matrices:

- `library(biotools)`: Loads the `biotools` package.
- `boxM(coches3[, c("cilindros", "desplazamiento", "CV", "peso", "aceleracion", "precio")], coches3$origen)`: Conducts Box's M test on selected variables in `coches3` for equality of covariance matrices across different groups in `origen`.

### Visualizing Data:

- `library("PerformanceAnalytics")`: Loads the `PerformanceAnalytics` package.
- `plot(vehiculosnumerico)`: Plots the `vehiculosnumerico` data, but this code might not work as expected since the `plot` function from `PerformanceAnalytics` is designed for time series objects.



