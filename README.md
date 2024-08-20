## Numerical Methods in Quantum Information Science: Quantum optimal control

Optimal control lectures at the Numerical Methods in Quantum Information Science Summer School at the Mount Ida campus of University of Massachusetts Amherst
August 12th (Mon) - 18th (Sun) 2024.

### Thanks
These notebooks owe a great deal of credit to Zac Manchester's CMU 745: Optimal Control & Reinforcement Learning---the code is open source and the lectures are available on YouTube.

Shout out to the organizers of Qnumerics for making this event possible!

## Quickstart guide

__Install Julia__ [Juliaup](https://github.com/JuliaLang/juliaup) is an installer and version manager. This is one useful way to manage Julia versions and keep up with the latest changes. After installing, run `julia` to obtain the Julia _REPL_.

__Julia environments__
[(Documentation)](https://pkgdocs.julialang.org/v1/environments/#Using-someone-else's-project) Your project's environment is stored in _Project.toml_. You can interactively add packages to an environment by using the Julia command line _REPL_ and _package manager_.  

To start Julia in the project folder, type `julia --project=.`. Alternatively, start `julia`, then type `]` to enter the package manager. Type `activate .` to activate or create an environment specified by _Project.toml_ located in the current folder. 

Separately, you generate a manifest (solving the versions to create a valid environment) by running `instantiate`; instantiate will check that the environment is correct after you add all the packages you want.

__Our environment__
These notebooks are configured with a `Project.toml` containing everything you need, so you should be able to run them with this environemnt. 

```Julia
# Standard packages
using LinearAlgebra
using CairoMakie

# Our package
using Piccolo
```

__Developing__
If you are interested in developing with the source code, and want to use these notebooks as a starting point, that's great! We will show you how to do that now. First, uninstall Piccolo from the project.

We want to go straight to the source from now on--the git repositories are at [the Kestrel Quantum Github page](https://github.com/kestrelquantum). There are three packages inside [Piccolo] (_QuantumCollocation_, _NamedTrajetories_, _TrajectoryIndexingUtils_). Most likely, you want to work on _QuantumCollocation_. Clone, then add the local packages to the Project file with e.g. `dev ../relative/path/to/repo/QuantumCollocation`. This command installs a version pointing to the local code instead of the package repository. Do the same for any others you would like to work with, or just stop at QuantumCollocation. Now, you can call:

```Julia
using QuantumCollocation
```

[Revise.jl](https://timholy.github.io/Revise.jl/stable/) will let you edit source code and reload the changes in a notebook---automatically and without resetting the kernel! This is a great tool for development. `add Revise` from the REPL (within the current environment) and then include it before any packages you intend to edit:
```Julia
using Revise
using QuantumCollocation
```

### Tips for Visual Studio Code
__Julia extension__ You can run Julia notebooks and much more with [the Julia extension](https://code.visualstudio.com/docs/languages/julia). Upon opening your project folder in VS code and attempting to run an `.ipynb`, you will see that VS Code finds the interpreters managed by juliaup and defaults to using the environment based on the _Project.toml_ in the project directory.

__Fonts__ VS Code will not display all characters allowed by Julia. You can change the editor font family in the settings to `'JuliaMono'` to get full support. If you don't want to mix and mash, you can create a new VS Code settings profile for working in Julia at _File>Preferences>Profile_.

__Tests__ [(TestItemRunner.jl)](https://github.com/julia-vscode/TestItemRunner.jl) Tests should automatically populate in VS Code when working with a Piccolo package. For example, just by adding the `QuantumCollocation.jl` folder to your workspace, you should see tests appear if you click on the _Testing_ sidebar icon. If you run one of these tests, a new Julia kernel is spawned for the test. You can find the kernel if you click on the _Julia_ sidebar icon (after installing the Julia extensions). Sometimes, for the tests to recognize new changes that Revise doesn't fix, you may need to manually kill this kernel to see your changes reflected.