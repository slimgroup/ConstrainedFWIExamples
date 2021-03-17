[![DOI](https://zenodo.org/badge/307709753.svg)](https://zenodo.org/badge/latestdoi/307709753)

# ConstrainedFWIExamples

This code base is using the Julia Language and [DrWatson](https://juliadynamics.github.io/DrWatson.jl/stable/)
to make a reproducible scientific project named
> ConstrainedFWIExamples

It is authored by Mathias Louboutin.

To (locally) reproduce this project, do the following:

0. Download this code base. Notice that raw data are typically not included in the
   git-history and may need to be downloaded independently.
1. Open a Julia console and do:
   ```
   julia> using Pkg
   julia> Pkg.activate("path/to/this/project")
   julia> Pkg.instantiate()
   ```

This will install all necessary packages for you to be able to run the scripts and
everything should work out of the box.

# Content

This repository currently contains two  notebooks 

## 01_const_fwi_judi.ipynb

This notebook implements FWI with TV constraints and box constraints with the projectd quasi-Newton method. In this example, we highlight the use of constraints for a very simple transmission example with a squared perturation on the middle. This example is using [JUDI](https://github.com/slimgroup/JUDI.jl) as the framework for wave propagation and inversion where the wave-propagators are implemented using [Devito](https://github.com/devitocodes/devito). This tutorial demonstrates that our constraints framework  [SetIntersectionProjection](https://github.com/slimgroup/SetIntersectionProjection.jl) provides better result than standard FWI while never requiring any additional PDE solves (function and/or gradient evaluation).


## 02_constr_fwi_jetpack.ipynb
This notebook implements FWI with TV constraints and box constraints with the projectd quasi-Newton method. This notebook is an adaptation of an FWI [example](https://github.com/ChevronETC/Examples/blob/main/50_fwi/01_fwi_L2.ipynb) using an open-source framework for wave propagation and inversion. The original example does not implement constraints and use a standard L-BFGS solver. In the example here, we show how to use out constraints framework, [SetIntersectionProjection](https://github.com/slimgroup/SetIntersectionProjection.jl), to setup constraints for FWI.

The major advantages of our constraints frameowrk is that, unlike standard optimization packages, are:

- The constraints projection do not involve any function or gradient evaluation, making it computationally efficient.
- The projection algorithm is implemented to be computationally scalable up to 3D, and support distriubted computing of the projection for efficiency.
- A broad range of constraints are available, not only box constraints, such as TV, nuclear norm, rank, ....

We refer to the [Documentation](https://petersbas.github.io/SetIntersectionProjectionDocs/) of the software for a more detailed overview of the capabilities and performance.

# Links

- The origianl notebook can be found at [Notebook](https://github.com/ChevronETC/Examples/blob/main/50_fwi/01_fwi_L2.ipynb) for reference. This repository is in progress so their result may have changed.

- The constraints framework can be found at [SetIntersectionProjection](https://github.com/slimgroup/SetIntersectionProjection.jl) and is described in [Projections].


[Projections]: https://slim.gatech.edu/content/algorithms-and-software-projections-intersections-convex-and-non-convex-sets-applications
