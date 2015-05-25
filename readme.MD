# List of likelihood-free examples

This is a list of example applications for use with likelihood-free (aka plug-and-play) methods of statistical inference like [ABC](http://en.wikipedia.org/wiki/Approximate_Bayesian_computation).
They are split into 3 categories:

1. Simulator code available.

   Simulator code allows these applications to be used as part of any likelihood-free method.

2. Simultor output available.

   Here a dataset is available of (input, output) or (parameter, data) pairs.
   These can be used in a subset of likelihood-free methods.

3. Other examples.

   These are examples described in the literature for which simulators could be implemented with some effort.

This list is a work in progress.
Please add or get in touch about any further examples you are familiar with.
Challenging applications are particularly welcome to help motivate new methods.
These include simulators with high dimensional inputs or outputs or which are very computationslly intensive to run.

##Simulator code available

* **g-and-k distribution**.
This is a flexible 4-parameter distribution with an intractable pdf.
It has often been used as a test in the ABC literature, starting with [Allingham et al](http://link.springer.com/article/10.1007/s11222-008-9083-x).
My unfinished R package [gk](https://github.com/dennisprangle/gk) simulates from this distribution.
Simulation requires only 1 line of code so it is very easy to reimplement in other languages.

* **Moving average models**.
[Marin et al](http://www.sciencedirect.com/science/article/pii/S0167947311004245) use inference for an MA(1) model as an example of ABC parameter inference where the exact posterior is avaiable.
[Pudlo et al](http://arxiv.org/abs/1406.6288) extend the example to ABC model choice between MA(1) and MA(2) models, which is quite challenging.
Again exact posterior values are available.
The models can be simulated from using the `arima.sim` command in R and are simple to reimplement.

* **Ricker and blowfly models**.
These are ecological models of population size data used in [Wood](http://www.nature.com/nature/journal/v466/n7310/full/nature09319.html).
Simulator code is available in the R package [synlik](http://cran.r-project.org/web/packages/synlik/index.html).

* **Spatial extremes.**
Max-stable processes can be used to model spatial extreme data.
These processes can be simulated using the R package [SpatialExtremes](http://cran.r-project.org/web/packages/SpatialExtremes/index.html).
An ABC analysis was performed by [Erhardt and Smith](http://www.sciencedirect.com/science/article/pii/S0167947311004245) and is implemented in the R package [ABCExtremes](http://cran.r-project.org/web/packages/ABCExtremes/index.html).
This includes code to calculate the summary statistics they used.

* **Stable distibutions**.
This family of distributions has similar properties to the normal distribution but heavier tails.
Most have an intractable pdf.
The R [stabledist](http://cran.r-project.org/web/packages/stabledist/index.html) package simulates from this distribution.
For more background see [wikipedia]((http://en.wikipedia.org/wiki/Stable_distribution).
It has been used in ABC analysis of financial data by [Peters et al](http://projecteuclid.org/euclid.ba/1339616543) and [Jasra et al](http://link.springer.com/article/10.1007/s11222-010-9185-0) amongst others.
Some effort might be needed to reimplement their full models.

* **Trait dynamics**.
This is a model of ecological dynamics of traits in species from [Jabot](http://www.sciencedirect.com/science/article/pii/S002251930900530X).
A simulator is included in the [EasyABC](http://cran.r-project.org/web/packages/EasyABC/index.html) R package.

##Simulator output available

* **coal dataset**.
This data is generated from a coalescent model and is available in the [abctools](http://cran.r-project.org/web/packages/abctools/index.html) R packages.
100,000 simulated datasets, 7 summary statistics, 2 parameters.
100 further simulated datasets are available to use as observations.
A larger dataset for the same example (1,000,000 simulations) is available from [Matt Nunes's webpage](http://www.maths.lancs.ac.uk/~nunes/ABC/coaloracle.rda).

* **human dataset**.
This genetic data on humans under 3 demographic models is available in the [abc.data](http://cran.r-project.org/web/packages/abc.data/index.html) R package.
150,000 simulations, 3 summary statistics, 4 parameters, 3 models, and observed data from 3 populations.

* **musigma2 dataset**.
This is made up of has population mean and variance under a normal model and is available in the [abc.data](http://cran.r-project.org/web/packages/abc.data/index.html) R package.
150,000 simulations, 2 summary statistics, 2 parameters.
The observations are taken from the classic [iris](http://en.wikipedia.org/wiki/Iris_flower_data_set) dataset.
Details from the true posterior are also provided.

##Other examples

* **M/G/1 queues**.
A queue with Markov arrival and non-Markov service times in which only departure times are observed has an intractable likelihood but is very simple to write a simulator for.
ABC analyses have been performed by [Blum and Francois](http://link.springer.com/article/10.1007/s11222-009-9116-0) and [Fearnhead and Prangle](http://onlinelibrary.wiley.com/doi/10.1111/j.1467-9868.2011.01010.x/full) amongst others.
Recently an exact MCMC approach has been proposed by [Shestopaloff and Neal](http://arxiv.org/abs/1401.5548) which could be used for comparison.