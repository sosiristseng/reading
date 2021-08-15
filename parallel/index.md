# Julia in Parallel


When you don't want other core sitting idle.

<!--more-->

## High level packages

Recommended for regular users.

- [Folds.jl](https://github.com/JuliaFolds/Folds.jl) with a unified interfae for a variety of executers (multithreading, multiprocessing, CUDA)
- [FLoops.jl](https://github.com/JuliaFolds/FLoops.jl) with `@floop` and `@reduce` macros.
- [ThreadsX.jl](https://github.com/tkf/ThreadsX.jl) for parallelized Base functions.

## Low level constructs

### Task-based asynchronous programming

- [async @ Julia Manual](https://docs.julialang.org/en/v1/manual/asynchronous-programming/#man-asynchronous)
- [Channels: producer-consumer model](https://docs.julialang.org/en/v1/manual/asynchronous-programming/#Communicating-with-Channels)

Multithreading within in a CPU core, a.k.a "Green threading".

### Multi-threading

- [Caveats in multithreading](https://docs.julialang.org/en/v1/manual/multi-threading/#Caveats)
- Threads share memory causing data racing if data access is not properly handled.
- Suitable for SMP (Symmetric multiprocessing)

To increase the threads avaiable to Julia, start Julia with `-t / --threads` argument. e.g.

```bash
julia -t auto
```

Or through an environment variable, `JULIA_NUM_THREADS=n`. For example in `~/.profile`:

```bash
export JULIA_NUM_THREADS=4  # or $(nproc), the # of cpu threads available
```

You could check how many thread are available in the Julia session

```julia
Threads.nthreads()
```

Enable multithreading by

- `Threads.@threads for loop`
- `Threads.@spawn expr`

### Multiprocessing

[Multiprocessing @ Julia manual](https://docs.julialang.org/en/v1/manual/distributed-computing/#Multi-processing-and-Distributed-Computing)

- Suited for clusters
- Independent memory pool by default, except for shared memories.
  - Unlike Python, where multiprocessing is done by forking and worker processes inherit data from the main process.
  - As a result, `@everywhere` is needed for code running in parallel to copy the data to the worker processes.

A simple example to start julia with multiple processes:

```bash
# start julia with 1 main process + 5 worker processes with -p
julia -p 5
```

To load files for all processes without `@everywhere`, use `-L file`

```bash
# Julia with 1 main process + 7 worker processes with -p
# Load mod1.jl and mod2.jl for all processes with -L
# And execute run.jl
julia -p 7 -L mod1.jl -L mod2.jl run.jl
```

## Source

- [A quick introduction to data parallelism in Julia](https://juliafolds.github.io/data-parallelism/tutorials/quick-introduction/)
- [Aurelio's tutorial](https://techytok.com/multiprocessing-in-julia-module/).

> A [Youtube video](https://youtu.be/dczkYlOM2sg) by Porf. Allen about parallelism
> Before going multi-core, improve your serial code first!

