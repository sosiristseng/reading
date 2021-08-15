# Plots.jl Tips


Some tips about [Plots.jl](http://juliaplots.org), the de-facto standard visulization library in Julia.

<!--more-->

## You don't have to generate data points

`Plots.jl` suppots plotting functions.

- `plot(f, tmin, tmax)` or `plot(f, tArray)`
- `plot(fx, fy, tmin, tmax)` or `plot(fx, fy, tArray)`

For example, you can easily draw a [parametric plot](http://docs.juliaplots.org/latest/generated/gr/#gr-ref3)

```julia
# plotting (x(t), y(t))
plot(sin, (x-> sin(2x)), 0, 2π, line = 4, leg = false)
```

Or make a contour plot without precalculating the function values

```julia
x = 1:0.5:20
y = 1:0.5:10

g(x, y) = (3x + y ^ 2) * abs(sin(x) + cos(y))

# Precalculate the value
X = repeat(reshape(x, 1, :), length(y), 1)
Y = repeat(y, 1, length(x))
Z = map(g, X, Y)
p2 = contour(x, y, Z)

# Generate z value on-the-fly
p1 = contour(x, y, g, fill=true)
plot(p1, p2)
```

## Subplots

You can combine multiple plots into one single plot.

```julia
l = @layout [a ; b c]
p1 = plot(...)
p2 = plot(...)
p3 = plot(...)
plot(p1, p2, p3, layout = l)
```

See also [layouts](http://docs.juliaplots.org/latest/layouts/#layouts) for more options.

## Supported styles

From [this tutorial](https://www.math.purdue.edu/~allen450/Plotting-Tutorial.html).

```julia
# tip: use Plots.supported_styles() or Plots.supported_markers() to see which linestyles or markershapes you can use
@show Plots.supported_styles();
@show Plots.supported_markers();
```

## Plotting Images

```julia
# usingPkg; Pkg.add("Images")
using Images
img1 = load("dog.jpg")
plot(img1)
```

