# Julia Modules and packages


When the code grows to a certain size, you might want to organize it.

<!--more-->

Assuming we have the file structure for the submodules

```tree
. present working directory (pwd)
| - main.jl
| - Manifest.toml
| - Project.toml
|
+---Mod1.jl
|   | - Manifest.toml
|   | - Project.toml
|   |
|   \---src
|         - Mod1.jl
|
\---Mod2.jl
    | - Manifest.toml
    | - Project.toml
    |
    \---src
          - Mod2.jl
```

## Include Submodules

You could include the little packages as submodules like this

```julia
include("./Mod1.jl/src/Mod1.jl")
using .Mod1

include("./Mod2.jl/src/Mod2.jl")
using .Mod2
```

> - Best when the submodules are used exclusively for this project.
> - Usually you want to `include()` all dependent files in the top-most file, [just like a table of contents](https://discourse.julialang.org/t/ann-patmodules-jl-a-better-module-system-for-julia/52226/40).
> - `include` and `using` lines are needed to be executed again when the code in Modx changes.
> - Use [relative module path](https://stackoverflow.com/questions/54410557/submodule-intra-dependencies-in-julia) when `Mod2` also requires `Mod1`.
> - There might be recursive `include()` calls and `replace module` warnings.
> - You can use [FromFile.jl](https://github.com/Roger-luo/FromFile.jl) to deal with these warnings.

## dev a temporary package

 `dev --local pkg...`

[Julia docs | Pkg | dev](https://docs.julialang.org/en/v1/stdlib/Pkg/)

Add local packages and track the file changes in the Julia REPL

```julia
julia> ]
pkg> activate .
pkg> dev --local Mod1 Mod2
```

Or by the Julia script counterpart

```julia
import Pkg

# To generate Project.toml if not present
Pkg.activate(".")

Pkg.develop(PackageSpec(path="Mod1.jl"))
Pkg.develop(PackageSpec(path="Mod2.jl"))
```

> - Best when `Mod1` and `Mod2` are modified frequently and shared.
> - Loaded code is determined by local files instead of package versions.
> - The updates are loaded when `using` is invoked, along with precompilation. [Revise.jl](https://timholy.github.io/Revise.jl/stable/) tracks and updates modified files and you don't have to restart the Julia process should you make changes.

## Make a hosted packages

Make a Git repo for your custom package and publish it to Git service providers, e.g. GitHub / Gitlab. And then you can `]add https://github.com/username/Mod1.jl.git`

[PkgTemplates.jl](https://github.com/invenia/PkgTemplates.jl) or [PkgSkeleton.jl](https://github.com/tpapp/PkgSkeleton.jl) is recommended to generate package with unit tests and CI/CD settings.

Nonetheless, it's just one step away from proper [registeration](https://github.com/JuliaRegistries/Registrator.jl) to the general Julia registry to be used by more people.

### Unit testing

Tip: you can have [local dependencies](https://julialang.github.io/Pkg.jl/v1/creating-packages/#Test-specific-dependencies-in-Julia-1.2-and-above) for running tests in `test/Project.toml` without the need of `extra` and `targets` sections in the main project's `Project.toml`.

Though the build-in [unit-test framework](https://docs.julialang.org/en/v1/stdlib/Test/) is good, but [Jive.jl](https://github.com/wookay/Jive.jl) provides more flexibilities.
- Discover unit testing `jl` files automatically.
- Skip or select which test(s) to run.
- Multiprocessing for faster runs.

See [TestJive](https://github.com/wookay/TestJive.jl) for code examples.

### Documentation

Use [Documenter.jl](https://juliadocs.github.io/Documenter.jl/stable/) to generate the documentation for Julia packages.

?> You may need [an SSH key](https://juliadocs.github.io/Documenter.jl/stable/lib/public/#DocumenterTools.genkeys) to deploy docs to GitHub pages.

```julia
using DocumenterTools
DocumenterTools.genkeys(user="you", repo="YourPackage.jl")
```

### Continuous integration / delivery (CI/CD)

`PkgTemplates.jl` should set up the appropriate code structure for you. I would recommend to use GitHub to host Julia packages because
- Running GH actions is unlimited for public repositories, with multiple operating systems running concurrently (matrix build).
- Julia github actions are convenient to use.
- Automation bots integrate better with GitHub. e.g. TagBot, Registerbot, and Compat Helper.

## Appending `LOAD_PATH` (⚠️ outdated)

```julia
push!(LOAD_PATH, ".")

using Mod1
using Mod2
```

> - The old way before Pkg3 and Julia 1.0, which is not recommended by now.
> - *No* need for `Project.toml` nor `Manifest.toml` in the `pwd`.
> - Local files are tracked instead of package versions.
> - VS Code language server could not identify symbols from the custom modules.

## Reference

- [Julia workflow tips](https://docs.julialang.org/en/v1/manual/workflow-tips/)
- [Pkg.jl docs](https://julialang.github.io/Pkg.jl/v1/)
- [Comparison between v0.6 and v0.7 (SO)](https://stackoverflow.com/questions/36398629/change-package-directory-in-julia/36400065#36400065)
- [Developing your Julia package (Medium post)](https://medium.com/coffee-in-a-klein-bottle/developing-your-julia-package-682c1d309507)
- [YouTube: Developing Julia packages by Chris](https://youtu.be/QVmU29rCjaA)

