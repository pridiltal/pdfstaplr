
[![Project Status: Active  The project has reached a stable, usable state and is being actively developed.](http://www.repostatus.org/badges/latest/active.svg)](http://www.repostatus.org/#active) [![Licence](https://img.shields.io/badge/licence-GPL--3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0.en.html) [![Build Status](https://travis-ci.org/pridiltal/staplr.svg?branch=master)](https://travis-ci.org/pridiltal/staplr) [![codecov](https://codecov.io/gh/pridiltal/staplr/branch/master/graph/badge.svg)](https://codecov.io/gh/pridiltal/staplr)

------------------------------------------------------------------------

[![minimal R version](https://img.shields.io/badge/R%3E%3D-3.4.1-6666ff.svg)](https://cran.r-project.org/) [![CRAN\_Status\_Badge](http://www.r-pkg.org/badges/version/staplr)](https://cran.r-project.org/package=staplr) [![packageversion](https://img.shields.io/badge/Package%20version-0.1.0-orange.svg?style=flat-square)](commits/master)

------------------------------------------------------------------------

[![Last-changedate](https://img.shields.io/badge/last%20change-2018--02--03-yellowgreen.svg)](/commits/master) \#staplr <img src="logo.png" align="right" height="150" />

<!-- README.md is generated from README.Rmd. Please edit that file -->
staplr
======

This package provides function to manipulate PDF files: merging multiple PDF files into one.

This package is still under development and this repository contains a development version of the R package *staplr*.

Installation
------------

#### Install pdftk

download and install [pdftk](https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/) NB: this is not an R package!

#### Install staplr

You can install staplr from github with:

``` r
# install.packages("devtools")
devtools::install_github("pridiltal/staplr")
```

Example
-------

``` r
library(staplr)
staple_pdf()
```

References
----------

-   <https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/>