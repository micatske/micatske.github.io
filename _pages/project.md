---
permalink: /projects/
title: "Projects"
gallery:
  - url: software/table.png
    image_path: software/table.png
    alt: "AIAnalysis"
    title: "AIAnalysis"
  - url: software/coefplot.png
    image_path: software/coefplot.png
    alt: "covid-analysis"
    title: "covid-analysis"
  - url: software/margeff.png
    image_path: software/margeff.png
    alt: "LSTM-CNN Stock Prediction"
    title: "LSTM-CNN Stock Prediction"
header:
  og_image: "software/spatial_weighting.png"
---

Here are the lists of project I did from machine learning and data science. 

# AIAnalysis

The project is designed to automatically estimate functions in symbolic form use sympy package.## Function Spaces

We define function spaces $L^p$, $W^{k,p}$, $\dot H^s$, $H^s$, $C^{r,\alpha}$ by using the sympy, each of then taking a function symbol and parameter as input and output their corresponding norms.

For instance, we call 

```
Lp(p,f)
```

to define the standard $L^p$ space for function $f$.

### Sobolev Embedding

We build the [Sobolev inequality] (https://en.wikipedia.org/wiki/Sobolev_inequality) for the. Here we need to input our function, which will output all possible embedding spaces as a common rule. We know that they are in a linear relation. So we pick 10 possible pairs where each pair are rational numbers.

For $f$ in space $W^{k,p}(\mathbb{R}^n)$, we call 

```
Sobolev_Embed_auto(k,p,n,f)
```
to get a list of embedded spaces.

Example: For $f \in W^{2,2}(\mathbb{R})$, we call

```
Sobolev_Embed_auto(2,2,1,f**2)
```

And we have 


For $f \in W^{2,2}(\mathbb(R)^4)$

```
Sobolev_Embed_auto(2,2,4,f)
```

We have

### Para Product 

We build the Bony's Paraproduct decomposition (https://www.math.ucla.edu/~tao/247b.1.07w/notes6.pdf). We include the high-high, low-high, and low-high paraproduct. Moreover, we also have the helpful operator $\nabla$ and $\triangle$ build-in. The paraproduct can be used with the Sobolev Embedding and Holder inequality to estimate functions.

For instance, if we want to calculate the paraproduct of 

$$
\nabla f * \triangle g= \pi_{hh}(\nabla f * \triangle g)+ \pi_{hl}(\nabla f * \triangle g)+\pi_{lh}(\nabla f * \triangle g),
$$

we can simply call:
```
Paraproduct(nabla*f,lap*g)
```

The output will be in latex as the following:



{% include gallery %}



The latest [development version](https://github.com/micatske/aianalysis) on GitHub


# RWmisc

[![R build status](https://github.com/jayrobwilliams/RWmisc/workflows/R-CMD-check/badge.svg)](https://github.com/jayrobwilliams/RWmisc/actions)
[![CRAN_Status_Badge](https://www.r-pkg.org/badges/version/RWmisc)](https://CRAN.R-project.org/package=RWmisc)
[![codecov](https://codecov.io/gh/jayrobwilliams/RWmisc/branch/master/graph/badge.svg)](https://codecov.io/gh/jayrobwilliams/RWmisc)

I've collected convenience functions that I've written to address issues I frequently confront in my work into a personal R package called [RWmisc](https://CRAN.R-project.org/package=RWmisc). It includes functions for:

- Managing multiple different projections for cross-national spatial data
- Converting latitude-longitude data in archaic forms (degrees, minutes, seconds)
- Correcting for overlapping polygons when aggregating raster data to polygons
- My custom minimal ggplot2 theme

![](/images/software/spatial_weighting.png)

To install the latest release on CRAN:

```r
install.packages("RWmisc")
```

The latest [development version](https://github.com/jayrobwilliams/RWmisc) on GitHub can be installed with:

```r
library(remotes)
install_github("jayrobwilliams/RWmisc")
```
