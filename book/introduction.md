# `pyhf` Tutorial

## Welcome!

<p align="center">
<a href="https://github.com/scikit-hep/pyhf"><img src="https://raw.githubusercontent.com/scikit-hep/pyhf/master/docs/_static/img/pyhf-logo-small.png"></a>
</p>

Welcome to the `pyhf` tutorial!
We'll first point you towards our documentation website ([pyhf.readthedocs.io/](https://pyhf.readthedocs.io/)) and recommend that you visit it for much more detailed explanations and examples.
Let's dive right in.


We won't review the full pedagogy of `HistFactory`, so instead we'll point you to
the [`pyhf` talk at SciPy 2020](https://github.com/matthewfeickert/talk-SciPy-2020).

<!-- http://www.get-youtube-thumbnail.com/ -->
[![SciPy 2020 talk YouTube](https://i3.ytimg.com/vi/FrH9s3eB6fU/maxresdefault.jpg)](https://youtu.be/FrH9s3eB6fU)

Instead, let's move to looking at the `pyhf` API right away.

## Installation

### Make a Virtual Environment

````{tabbed} Locally
```
$ python3 -m venv pyhf-tutorial
$ source pyhf-tutorial/bin/activate
(pyhf-tutorial) $ python -m pip install -U pip setuptools wheel
```
````

````{tabbed} On CC7 lxplus/tier-3

First we need to set up the 'views' with the right paths to ensure we use the correct `pip`

```
$ export ATLAS_LOCAL_ROOT_BASE=/cvmfs/atlas.cern.ch/repo/ATLASLocalRootBase
$ source $ATLAS_LOCAL_ROOT_BASE/user/atlasLocalSetup.sh
$ lsetup "views LCG_98python3 x86_64-centos7-gcc8-opt"
$ export PYTHONPATH=/cvmfs/sft.cern.ch/lcg/views/LCG_98python3/x86_64-centos7-gcc8-opt/python:/cvmfs/sft.cern.ch/lcg/views/LCG_98python3/x86_64-centos7-gcc8-opt/lib
```

Then we can go ahead and create the virtual environment

```
$ python3 -m venv pyhf-tutorial
$ source pyhf-tutorial/bin/activate
(pyhf-tutorial) $ python -m pip install -U pip setuptools wheel
```
````

````{tabbed} On SLC6 lxplus/tier-3

First we need to set up the 'views' with the right paths to ensure we use the correct `pip`

```
$ export ATLAS_LOCAL_ROOT_BASE=/cvmfs/atlas.cern.ch/repo/ATLASLocalRootBase
$ source $ATLAS_LOCAL_ROOT_BASE/user/atlasLocalSetup.sh
$ lsetup "views LCG_98python3 x86_64-slc6-gcc8-opt"
$ export PYTHONPATH=/cvmfs/sft.cern.ch/lcg/views/LCG_98python3/x86_64-slc6-gcc8-opt/python:/cvmfs/sft.cern.ch/lcg/views/LCG_98python3/x86_64-slc6-gcc8-opt/lib
```

Then we can go ahead and create the virtual environment

```
$ python3 -m venv pyhf-tutorial
$ source pyhf-tutorial/bin/activate
(pyhf-tutorial) $ python -m pip install -U pip setuptools wheel
```
````

Once you have a virtual environment set up, you can use `source pyhf-tutorial/bin/activate` to get back into it again. Note the prefix `(pyhf-tutorial) $` on your command line, which indicates that you're inside a virtual environment named 'pyhf-tutorial'.

### Getting pyhf

If you haven't already, make a new Python 3 virtual environment and then install `pyhf` from either [PyPI](https://pypi.org/project/pyhf/) with `pip`

```
(pyhf-tutorial) $ python -m pip install pyhf
```

 or [Conda-forge](https://anaconda.org/conda-forge/pyhf)

```
(pyhf-tutorial) $ conda config --add channels conda-forge
(pyhf-tutorial) $ conda install pyhf
```

### Installation Extras

If you're installing from PyPI, you can also install with some of the "extras" that will be useful for doing typical HEP analysis workflows with `pyhf`.

````{tabbed} Read/Write XML+ROOT
```
(pyhf-tutorial) $ python -m pip install pyhf[xmlio]
```

The 'xmlio' extra additionally installs [`uproot`](https://github.com/scikit-hep/uproot4) to read `ROOT` files.
````

````{tabbed} Use PyTorch and Tensorflow
```
(pyhf-tutorial) $ python -m pip install pyhf[torch,tensorflow]
```

The 'torch' extra installs [`pytorch`](https://pytorch.org/) and the 'tensorflow' extra installs [`tensorflow`](https://www.tensorflow.org/).
````

````{tabbed} Using Minuit Optimization
```
(pyhf-tutorial) $ python -m pip install pyhf[minuit]
```

The 'minuit' extra installs [`iminuit`](https://iminuit.readthedocs.io/).
````


See our [installation docs](https://pyhf.readthedocs.io/en/v0.6.3/installation.html) for more information about installation options.

### Dependencies for this tutorial

To get all the dependencies needed for this tutorial you can just install from the included `requirements.txt` in the top level `binder/` directory of [the source repository](https://github.com/pyhf/tutorial-dance-codas-2022)

```
(pyhf-tutorial) $ python -m pip install -r binder/requirements.txt
```

If you want to also get the dependencies to build and explore the Jupyter Book form of the tutorial you can install them with

```
(pyhf-tutorial) $ python -m pip install -r book/requirements.txt
```

### Citation

`pyhf` `v0.6.0` and later makes it very easy to get the proper citation for the version of the library that you're using! Simply ask the CLI API to get the properly formatted BibTeX references.

```
(pyhf-tutorial) $ pyhf --citation
@software{pyhf,
  author = {Lukas Heinrich and Matthew Feickert and Giordon Stark},
  title = "{pyhf: v0.6.3}",
  version = {0.6.3},
  doi = {10.5281/zenodo.1169739},
  url = {https://doi.org/10.5281/zenodo.1169739},
  note = {https://github.com/scikit-hep/pyhf/releases/tag/v0.6.3}
}

@article{pyhf_joss,
  doi = {10.21105/joss.02823},
  url = {https://doi.org/10.21105/joss.02823},
  year = {2021},
  publisher = {The Open Journal},
  volume = {6},
  number = {58},
  pages = {2823},
  author = {Lukas Heinrich and Matthew Feickert and Giordon Stark and Kyle Cranmer},
  title = {pyhf: pure-Python implementation of HistFactory statistical models},
  journal = {Journal of Open Source Software}
}
```

Alternatively, [check the website](https://pyhf.readthedocs.io/en/v0.6.3/citations.html).

### Statistics References

For more information about some of the theoretical topics covered with `pyhf`, see Kyle Cranmer's [Statistics and Data Science](https://cranmer.github.io/stats-ds-book/intro.html) book.

### Questions and Further Information on `pyhf`

For more information on `pyhf` please check the [documentation website](https://pyhf.readthedocs.io/).
Additionally, if you have a question about the use of `pyhf` not covered in the documentation, please ask a question the `pyhf` [GitHub Discussions](https://github.com/scikit-hep/pyhf/discussions).
If you believe you have found a bug in `pyhf`, please report it in the [GitHub Issues](https://github.com/scikit-hep/pyhf/issues/new?template=Bug-Report.md&labels=bug&title=Bug+Report+:+Title+Here).
If you're interested in getting updates from the `pyhf` dev team and release announcements you can join the [`pyhf-announcements` mailing list](https://groups.google.com/group/pyhf-announcements/subscribe) (through Google Groups).
