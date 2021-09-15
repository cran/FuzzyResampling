
<!-- README.md is generated from README.Rmd. Please edit that file -->

# FuzzyResampling

<!-- badges: start -->

[![R-CMD-check](https://github.com/mroman-ibs/FuzzyResampling/workflows/R-CMD-check/badge.svg)](https://github.com/mroman-ibs/FuzzyResampling/actions)
<!-- badges: end -->

The goal of FuzzyResampling, a library written in R, is to provide
additional resampling procedures, apart from the classical bootstrap
(i.e. Efron’s approach, see (Efron and Tibshirani 1994)), for fuzzy
data. In the classical approach, secondary samples are drawing with
replacement from the initial sample. Therefore most of these bootstrap
samples contain repeated values. Moreover, if the size of the primary
sample is small then all secondary samples consist of only a few
distinct values, which is a serious disadvantage.

To overcome this problem, special resampling algorithms for fuzzy data
were introduced (see (Grzegorzewski, Hryniewicz, and Romaniuk 2019,
2020a, 2020b; Grzegorzewski and Romaniuk 2021; Romaniuk and Hryniewicz
2019)). These methods randomly create values that are “similar” to
values from the initial sample, but not exactly the same. During the
creation process, some of the characteristics of the initial fuzzy
values are kept (e.g., the value, the width, etc.). It was shown that
these algorithms provide serious advantages in some statistical areas
(like standard error estimation or hyphothesis testing) if they are
compared with the classical approach. For detailed information
concerning the theoretical foundations and practical applications of
these resampling methods please see the above-mentioned references.

The initial sample (in the form of a vector or a matrix) should consist
of triangular or trapezoidal fuzzy numbers.

The following procedures are available in the library (R language):

-   *classicalBootstrap* - classical approach based on Efron’s method,
-   *VAmethod* - resampling method which preserves the value and
    ambiguity (see (Grzegorzewski, Hryniewicz, and Romaniuk 2020a)),
-   *EWmethod* - resampling method which preserves the expected value
    and width (see (Grzegorzewski, Hryniewicz, and Romaniuk 2020b)),
-   *VAAmethod* - resampling method which preserves the value, left-hand
    and right-hand ambiguities (see (Grzegorzewski and Romaniuk 2021)),
-   *VAFmethod* - resampling method which preserves the value, ambiguity
    and fuzziness (see (Grzegorzewski, Hryniewicz, and Romaniuk 2020a)),
-   *dmethod* - resampling method which preserves the left end of the
    cores and increments (see (Romaniuk and Hryniewicz 2019)),
-   *wmethod* - resampling method which uses the special *w density* to
    “smooth” the output fuzzy value (see (Romaniuk and
    Hryniewicz 2019)).

## Installation

You can install the latest development version of FuzzyResampling with:

``` r
library(devtools)
install_github("mroman-ibs/FuzzyResampling")
```

You can install the latest stable version from CRAN with:

``` r
install.packages("FuzzyResampling")
```

## Examples

``` r
# set seed

set.seed(12345)

# load library

library(FuzzyResampling)

# prepare some fuzzy numbers

fuzzyValues <- matrix(c(0.25,0.5,1,1.25,0.75,1,1.5,2.2,-1,0,0,2),ncol = 4,byrow = TRUE)

fuzzyValues
#>       [,1] [,2] [,3] [,4]
#> [1,]  0.25  0.5  1.0 1.25
#> [2,]  0.75  1.0  1.5 2.20
#> [3,] -1.00  0.0  0.0 2.00
# generate the secondary sample using the classical approach

classicalBootstrap(fuzzyValues)
#>       [,1] [,2] [,3] [,4]
#> [1,]  0.75    1  1.5  2.2
#> [2,] -1.00    0  0.0  2.0
#> [3,]  0.75    1  1.5  2.2
# generate the secondary sample using the VA method

VAmethod(fuzzyValues)
#>            [,1]       [,2]       [,3]     [,4]
#> [1,]  0.9141124  0.9179438  1.7262290 1.747542
#> [2,] -0.5303703  0.8901852  0.9132088 1.423582
#> [3,] -0.3356065 -0.3321967 -0.3321967 2.664393
# generate the secondary sample (6 fuzzy numbers) using the d-method

dmethod(fuzzyValues, b = 6)
#>       [,1] [,2] [,3] [,4]
#> [1,]  0.75  1.0  1.5 3.50
#> [2,]  0.00  1.0  1.5 1.75
#> [3,]  0.25  0.5  1.0 1.25
#> [4,]  0.75  1.0  1.0 3.00
#> [5,] -0.25  0.0  0.5 1.20
#> [6,] -0.50  0.5  1.0 1.25
```

``` r
# help concerning the VA method

?VAmethod
```

## References

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-Efron1994" class="csl-entry">

Efron, B., and R. J. Tibshirani. 1994. *An Introduction to the
Bootstrap*. Chapman; Hall/CRC.

</div>

<div id="ref-grzegorzewski2019" class="csl-entry">

Grzegorzewski, P., O. Hryniewicz, and M. Romaniuk. 2019. “Flexible
Bootstrap Based on the Canonical Representation of Fuzzy Numbers.” In
*Proceedings of EUSFLAT 2019*. Atlantis Press.
https://doi.org/<https://doi.org/10.2991/eusflat-19.2019.68>.

</div>

<div id="ref-grzegorzewskietal2020" class="csl-entry">

———. 2020a. “Flexible Bootstrap for Fuzzy Data Based on the Canonical
Representation.” *International Journal of Computational Intelligence
Systems* 13: 1650–62.
https://doi.org/<https://dx.doi.org/10.2991/ijcis.d.201012.003>.

</div>

<div id="ref-grzegorzewskiamcs2020" class="csl-entry">

———. 2020b. “Flexible Resampling for Fuzzy Data.” *International Journal
of Applied Mathematics and Computer Science* 30: 281–97.
https://doi.org/<https://doi.org/10.34768/amcs-2020-0022>.

</div>

<div id="ref-Grzegorzewski2021" class="csl-entry">

Grzegorzewski, P., and M. Romaniuk. 2021. “Bootstrap Methods for Fuzzy
Data.”

</div>

<div id="ref-romaniuk_hryniewicz" class="csl-entry">

Romaniuk, M., and O. Hryniewicz. 2019. “Interval-Based, Nonparametric
Approach for Resampling of Fuzzy Numbers.” *Soft Computing* 23:
5883–903. https://doi.org/<https://doi.org/10.1007/s00500-018-3251-5>.

</div>

</div>