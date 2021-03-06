[![](https://img.shields.io/badge/docs-stable-blue.svg)](https://caseykneale.github.io/ChemometricsTools.jl/dev/) [![Build Status](https://travis-ci.org/caseykneale/ChemometricsTools.jl.svg?branch=master)](https://travis-ci.org/caseykneale/ChemometricsTools.jl)

# ChemometricsTools.jl
This package contains a collection of tools to perform fundamental and advanced Chemometric analysis' in Julia. It is currently richer than any other free chemometrics package available in any other language. If you are uninformed as to what Chemometrics is; it could nonelegantly be described as the marriage between data science and chemistry. Traditionally it is the symbiosis of applied linear algebra/statistics which is disciplined by the physics and meaning of chemical measurements. This is somewhat orthogonal to most specializations of machine learning where "add more layers" is the modus operandi. Sometimes chemometricians also weigh the pros and cons of black box modelling and break out pure machine learning methods - so some of those techniques are in this package.

## Tutorials/Demonstrations:
  - [Transforms](https://caseykneale.github.io/ChemometricsTools.jl/dev/Demos/Transforms/)
  - [Pipelines + LoopyMSC Example](https://caseykneale.github.io/ChemometricsTools.jl/dev/Demos/Pipelines/)
  - [Classification](https://caseykneale.github.io/ChemometricsTools.jl/dev/Demos/ClassificationExample/)
  - [Regression](https://caseykneale.github.io/ChemometricsTools.jl/dev/Demos/RegressionExample/)
  - [Calibration Transfer: Direct Standardization](https://caseykneale.github.io/ChemometricsTools.jl/dev/Demos/CalibXfer/)
  - [Stacked Interval Partial Least Squares Regression](https://caseykneale.github.io/ChemometricsTools.jl/dev/Demos/SIPLS/)
  - [Curve Resolution](https://caseykneale.github.io/ChemometricsTools.jl/dev/Demos/CurveResolution/)

## Shootouts/Modeling Examples:
  - [Readme](https://github.com/caseykneale/ChemometricsTools.jl/tree/master/shootouts)
  - [Classification](https://github.com/caseykneale/ChemometricsTools.jl/blob/master/shootouts/ClassificationShootout.jl)
  - [Regression](https://github.com/caseykneale/ChemometricsTools.jl/blob/master/shootouts/RegressionShootout.jl)
  - [Fault Detection](https://github.com/caseykneale/ChemometricsTools.jl/blob/master/shootouts/AnomalyShootout.jl)

### Package Status => Closer to Acceptability (v 0.5.8)
ChemometricsTools has been accepted as an official Julia package! Yep, so you can  ```Pkg.add("ChemometricsTools")``` to install it. A lot of features have been added since the first public release (v 0.2.3 ). In 0.5.8 almost all of the functionality available can be used/abused. If you find a bug or want a new feature don't be shy - file an issue. In v0.5.1 Plots was removed as a dependency, new plot recipes were added, and now the package compiles much faster! Multilinear modeling, univariate modeling, and DOE functions are now available. Making headway into the release plan for v0.6.0. Convenience functions, documentation, bug fixes, refactoring and clean up are in progress bare with me. The git repo's master branch typically has the most advanced version, but the features on it may be less reliable because I like to do development on it.

### Seeking Collaborators
So my time and efforts for building this package are constrained. I really would like to find some collaborators to help flesh this package out, use it, find bugs. Even if your interests are more leaning towards machine learning/statistics I'd love to hear from you. Please file an issue if you are interested - or send me a message on Julia Discourse (ckneale)!

### Version Release Strategy
  - < 0.3.0 : Mapping functionality, prototyping
  - < 0.5.0 : Testing via actual usage on real data, look for missing essentials
  - *< 0.6.0 : Bake in convenience functions for ease of use. Flesh out Documentation.*
  - < 0.7.5 : Public input (find those bugs!). Adequate Unit Tests.
  - < 1.0.0 : Focus on performance, stability, generalizability, lock down the package syntax.

# Package Highlights
### Transforms/Pipelines
Two design choices introduced in this package are "Transformations" and "Pipelines". We can use transformations to treat data from multiple sources the same way. This helps mitigate user error for cases where test data is scaled based on training data, calibration transfer, etc.

Multiple transformations can easily be chained together and stored using "Pipelines". Pipelines aren't "pipes" like are present in Bash, R and base Julia. They are flexible, yet immutable, convenience objects that allow for sequential preprocessing and data transformations to be reused, chained, or automated for reliable analytic throughput.

### Model training
ChemometricsTools offers easy to use iterators for K-folds validation's, and moving window sampling/training. More advanced sampling methods, like Kennard Stone, are just a function call away. Convenience functions for interval selections, weighting regression ensembles, etc are also available. These allow for ensemble models like SIPLS, P-DS, P-OSC, etc to be built quickly. With the tools included both in this package and Base Julia, nothing should stand in your way.

### Regression Modeling
This package features dozens of regression performance metrics, and a few built in plots (Bland Altman, QQ, Interval Overlays etc) are included. The list of regression methods currently includes: CLS, Ridge, Kernel Ridge, LS-SVM, PCR, PLS(1/2), ELM's, Regression Trees, Random Forest, Monotone Regression... More to come. Chemometricians love regressions! I've also added some convenience functions for univariate calibrations, standard addition experiments and some automated plot functions for them.

### Classification Modeling
In-house classification encodings (one cold/one hot), and easy to retrieve global or multiclass performance statistics. ChemometricsTools currently includes: LDA/PCA with Gaussian discriminants, Hierchical LDA, SIMCA, multinomial softmax/logistic regression, PLS-DA, K-NN, Gaussian Naive Bayes, Classification Trees, Random Forest, Probabilistic Neural Networks, LinearPerceptrons, and more to come. You can also conveniently dump classification statistics to LaTeX/CSV reports!

### Multiway/Multilinear Modeling
I've been working to fulfill an obvious gap in the available tooling. Standard
methods for Tucker decomposition (HOSVD, and HOOI) have been included. Some preprocessing methods, and even an early view at multilinear PLS. There's a lot that could be done here, please feel free to contribute!

## Specialized tools?
This package has tools for specialized fields of analysis'. For instance, fractional derivatives for the electrochemists (and the adventurous), a handful of smoothing methods for spectroscopists, curve resolution (unimodal and nonnegativity constraints available) for forensics, process fault detection methods, etc. There are certainly plans for other tools for analyzing chemical data that packages in other languages have seemingly left out. Stay tuned.

## Where's the Data?
Please check out [ChemometricsData.jl](https://github.com/caseykneale/ChemometricsData.jl) for access to more publicly available datasets. 

Right now the 2002 International Diffuse Reflectance Conference Pharmaceutical NIR, iris, Tecator aka 'meat', and ball gear fault detection (NASA) dataset are [included](https://github.com/caseykneale/ChemometricsTools.jl/tree/master/data) in this package. But, this will be factored out eventually into ChemometricsData.jl. 

I'd love for a collaborator to contribute some: spectra, chromatograms, etc. Please reach out to me if you wish to collaborate/contribute. In the mean time you can load in your own datasets using the full extent of Julia ecosystem (XLSX.jl, CSV.jl, JSON.jl, MATLAB.jl, LibPQ.jl, Feather.jl, Arrow.jl, etc).

## What about Time Series? Cluster modeling?
Well, I'd love to hammer in some time series methods. That was originally part of the plan. Then I realized [OnlineStats.jl](https://github.com/joshday/OnlineStats.jl) already has the essentials for online learning covered, and a there are many efforts for actual time series((TimeSeries.jl)[https://github.com/JuliaStats/TimeSeries.jl]) modelling in the works. 

Similarly, if clustering methods are important to you, check out [Clustering.jl](https://github.com/JuliaStats/Clustering.jl). I may add a few supportive odds and ends in here (or contribute to the packages directly) but really, most of the Julia 1.0+ ecosystem is really reliable, well made, and community supported.

## ToDo:
  - Clean up.
  - Performance improvements.
  - Syntax improvements.
  - Documentation improvements.
  - Unit tests.

## Maybes:
  - Design of Experiment tools (Partial Factorial design, D/I-optimal, etc...)?
  - Convenience fns propagation of error, multiequilibria, kinetics?
  - Electrochemical simulations and optical simulations (maybe separate packages...)?
