
# staplr <img src="man/figures/logo.png" align="right" height="150"/>

[![Project Status: Active - The project has reached a stable, usable
state and is being actively
developed.](http://www.repostatus.org/badges/latest/active.svg)](http://www.repostatus.org/#active)
[![Licence](https://img.shields.io/badge/licence-GPL--3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0.en.html)
[![Build
Status](https://travis-ci.org/pridiltal/staplr.svg?branch=master)](https://travis-ci.org/pridiltal/staplr)

-----

[![CRAN\_Status\_Badge](http://www.r-pkg.org/badges/version/staplr)](https://cran.r-project.org/web/packages/staplr/index.html)
[![](http://cranlogs.r-pkg.org/badges/staplr)](http://cran.rstudio.com/web/packages/staplr/index.html)

-----

[![Last-changedate](https://img.shields.io/badge/last%20change-2019--07--22-yellowgreen.svg)](/commits/master)

<!-- README.md is generated from README.Rmd. Please edit that file -->

# staplr

This package provides functions to manipulate PDF files:

  - fill out PDF forms: get\_fields() and set\_fields()
  - merge multiple PDF files into one: staple\_pdf()
  - remove selected pages from a file: remove\_pages()
  - rename multiple files in a directory: rename\_files()
  - rotate entire pdf document: rotate\_pdf()
  - rotate selected pages of a pdf file: rotate\_pages()
  - Select pages from a file: select\_pages()
  - splits single input PDF document into individual pages: split\_pdf()
  - splits single input PDF document into parts from given points:
    split\_from()

This package is still under development and this repository contains a
development version of the R package *staplr*.

## Installation

staplr requires a Java installation on your system. You can get the
latest version of java from [here](https://www.java.com/en/download/).
[OpenJDK](https://openjdk.java.net/) also works.

You can install the stable version from CRAN.

``` r
install.packages('staplr', dependencies = TRUE)
```

You can install staplr from github with:

``` r
# install.packages("devtools")
devtools::install_github("pridiltal/staplr")
```

## Example

``` r
library(staplr)
# Merge multiple PDF files into one
staple_pdf()

# This command prompts the user to select the file interactively. 
# Remove page 2 and 3 from the selected file.
remove_pages(rmpages = c(2,3))

# This function selects pages from a file;
select_pages(selpages = c(1,3))

# This function splits a single input PDF document into individual pages
split_pdf()

# This function writes renamed files back to directory
#if the directory contains 3 PDF files
rename_files(new_names = paste("file",1:3))

# These functions are to fill out pdf forms
get_fields() 
set_fields()
# This includes 2 external functions `get_fields` and `set_fields` 
# and files to use as examples.
# This is what the example file looks like
```

![image](https://user-images.githubusercontent.com/6352379/37745585-bc7bb8e8-2d32-11e8-918c-e52a0a549118.png)

``` r
# If you get path to this file by
pdfFile = system.file('testForm.pdf',package = 'staplr')

# And do
fields = get_fields(pdfFile)
# You'll get a list of fields that the pdf contains 
# along with some additional information about the fields.

# You make modifications in any of the fields by
fields$TextField1$value = 'this is text'
set_fields(pdfFile, 'newFile.pdf', fields)

# This will create a filled pdf file
```

![image](https://user-images.githubusercontent.com/6352379/37745838-65986038-2d34-11e8-9d16-5d6514ef24ab.png)

## Troubleshooting

  - While default java options should be enough for most use cases, if
    you need to, you can change java options that is used to run pdftk
    by doing

<!-- end list -->

``` r
options('staplr_java_options' = '-Xmx512m') 
```

This option is not affected by `rJava` settings.

  - This package uses [pdtk-java](https://gitlab.com/pdftk-java/pdftk)
    which requires a working Java and rJava installation. If any
    problems arise it’ll likely be because rJava cannot locate your
    `JAVA_HOME`. Make sure your `JAVA_HOME` is configured correctly. You
    may have to do `sudo R CMD javareconf` on linux machines.

  - If for any reason you’d prefer to run a local installation of pdftk
    rather than using the version that is shipped with the package, do

<!-- end list -->

``` r
# set staplr_custom_pdftk to the path to local installation
# just setting to pdftk will do if it's already in your path
 options('staplr_custom_pdftk' = 'pdftk') 
```

If you want to do this, you can get the original version of pdftk from
[here](https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/). Note that
MacOS users with a version higher than “High Sierra” should use
[this](https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/pdftk_server-2.02-mac_osx-10.11-setup.pkg)
version instead.

Make sure to set the option back to `NULL` if you want to use the built
in pdftk later.

## References

  - <https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/>
