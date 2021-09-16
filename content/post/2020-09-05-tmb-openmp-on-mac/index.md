---
title: "OpenMP support for TMB on Mac"
authors: 
  - "kinhnguyen"
date: 2020-09-05
categories: ["programming"]
tags: ["data.table", "TMB", "OpenMP"]
output:
  blogdown::html_page:
    toc: true
    fig_width: 6
    dev: "svg"
---

## Problem

Up to Mac Catalina, by default, installing R packages with OpenMP support (e.g. `data.table`,
`TMB`) has been compiled without it.

For TMB codes, changes such as

- use `parallel_accumulator()` or  
- include OpenMP's headers and library, and 
- add `#pragma openmp parallel for` before `for` loop in the likelihood
  calculation

done after installing TMB from CRAN are not relevant – TMB was already compiled
with `_OPENMP` flag undefined. This can be checked by running `TMB::openmp()`
which outputs

> OpenMP not supported. 

or `library(data.table)` which outputs

> ...This installation of data.table has not detected OpenMP support. It should
> still work but in single-threaded mode. **This is a Mac.**...

## Solution

![it works on my machine](https://hackernoon.com/hn-images/1*ookfwogTLx_1qhHaiFJoJw.png)

The following steps are one way to make them work:

- install the lastest [R 4.0.2](https://cloud.r-project.org/bin/macosx/R-4.0.2.pkg)
- install  [clang-8.0.0.pkg (OS X 10.11+, signed, 64-bit)](https://cloud.r-project.org/bin/macosx/tools/clang-8.0.0.pkg)as r-project noted
> Important: this release uses Xcode 10.1 and GNU Fortran 8.2. If you wish
  to compile R packages from sources, you will need to download and GNU
  Fortran 8.2 - see the [tools](https://cloud.r-project.org/) directory.

  although the note's clearly missing a word after "download", should it be `Clang`? I assume it is.

Then for TMB

- change the `Makevars` 

```bash
# in terminal
touch ~/.R/Makevars
open ~/.R/Makevars
```

to

```make
MY_LOC   =  /usr/local/clang8
CML_LOC  =  /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk
CC       =  $(MY_LOC)/bin/clang -fopenmp -isysroot $(CML_LOC)
CXX      =  $(MY_LOC)/bin/clang++ -fopenmp -isysroot $(CML_LOC)
  CFLAGS = -g -O3 -Wall -pedantic -std=gnu99 -mtune=native -pipe
CXXFLAGS = -g -O3 -Wall -pedantic -std=c++11 -mtune=native -pipe
LDFLAGS  = -L$(MY_LOC)/lib -Wl,-rpath,$(MY_LOC)/lib
```
- clone [TMB's repos](https://github.com/kaskr/adcomp)

```bash
git clone https://github.com/kaskr/adcomp ~/adcomp
```

- open a new R session, remove `TMB` if it is already installed and compile `TMB` locally, e.g. with `devtools`
```r
remove.packages("TMB")
devtools::install('~/adcomp/TMB')
TMB::openmp()
[1] 8
```

The number of threads is now 8 (total cores on this Mac).

You might want to keep the `Makevars` as it is, and if a package failed to install afterwards it is most likely that that package has not included a check for `_OPENMP` flag. In this case, what a user can do is removing the `-fopenmp` flag in the `Makevars` above and notify the package's owners.

## Benchmarking

We can run the `linreg_parallel` example to see if things speed up (noting that
we are using the same `Makevars` but `TMB` does have a check for `_OPENMP`
flag in `parallel_accumulator` code.)

```r
remove.packages('TMB')
install.packages('TMB')
> TMB::openmp()
[1] 0
Warning message:
In TMB::openmp() : OpenMP not supported.
v1 = microbenchmark::microbenchmark(TMB::runExample("linreg_parallel"))
v1
> v1
Unit: milliseconds
                               expr      min       lq     mean  median       uq
 TMB::runExample("linreg_parallel") 189.8356 206.6781 460.8431 215.181 221.8238
      max neval
 24590.55   100
```

new R session

```r
remove.packages('TMB')
devtools::install('~/Github/adcomp/TMB')
> TMB::openmp()
[1] 8
> v2 = microbenchmark::microbenchmark(TMB::runExample("linreg_parallel"))
> v2
Unit: milliseconds
                               expr      min       lq     mean   median
 TMB::runExample("linreg_parallel") 183.2058 200.7899 452.8837 211.5193
       uq      max neval
 222.3681 23842.13   100
```

Hmm, no improvement?