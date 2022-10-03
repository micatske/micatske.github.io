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

The project is designed to automatically estimate functions in symbolic form use sympy package.
### Function Spaces

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


# CNN-LSTM-STOCK

### Data
We use the US-stock from Yahoo Finance and Index data from MarketWatch. From 2017-09-01 to 2022-08-31. We predict the stock/index using the close price.

For stock:
We use GOOG,TSLA

For Index:
We use S&P 500

### Use
One need to specify "stock" or "index" and stock or index name in the command line

For example

```
python test.py stock GOOG
```

```
python test.py index SP500
```
to predict SP500
### Neutral Network Structure
We use a CNN-LSTM based model to predict stock with an attention layer. We start with three 1D Convolution layers with max pooling layers and then connect the two LSTM layers with an attention layer. To avoid overfitting, we added two drop out layers. During training, we also use early stopping. Here's the full Neutral network structure. 
![Network](/images/projects/model.png)


## Training and Testing Result

![GOOG](/images/projects/TSLAtrain.png)
![RESG](/images/projects/TSLA.png)

# ![Covid-19 Cases Analysis](https://github.com/micatske/covid-analysis)

 * Virtualized World Covid Data in confirmed, recovery, death and daily cases for different countries and regions
using Johns Hopkins University’s Data
 * Virtualized Swiss Covid confirmed cases, testing, and hospitalized number using BAG data
 * Analyzed and Modeled relation between GDP per capita, Social support, Healthy life expectancy, Freedom to
make life choices to confirmed cases
* Predict the total cases using Polynomial Regression Model