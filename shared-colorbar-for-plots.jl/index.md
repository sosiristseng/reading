# Shared Colorbar for Plots.jl


Source: <https://discourse.julialang.org/t/plots-jl-shared-colorbar-with-subplots/47269/4>

<!--more-->

The trick is to

- make an blank scatter plot for the colorbar.
- use a dedicated space in the layout for the colorbar.

```julia
using Plots

x1 = range(0.0, 1.0, length=51)
y1 = range(-1.0, 0.0, length=51)
z1 = sin.(4*pi.*x1)*cos.(6*pi.*reshape(y1, 1, :))

x2 = range(0.25, 1.25, length=51)
y2 = range(-1.0, 0.0, length=51)
z2 = 2.0.*sin.(4*pi.*x2)*cos.(6*pi.*reshape(y2, 1, :))

x3 = range(0.0, 1.0, length=51)
y3 = range(-1.25, -0.25, length=51)
z3 = 3.0*sin.(4*pi.*x3)*cos.(6*pi.*reshape(y3, 1, :))

x4 = range(0.25, 1.25, length=51)
y4 = range(-1.25, -0.25, length=51)
z4 = 4.0.*sin.(4*pi.*x4)*cos.(6*pi.*reshape(y4, 1, :))

clims = extrema([z1; z2; z3; z4])
p1 = contourf(x1, y1, z1, clims=clims, c=:viridis, colorbar=false)
p2 = contourf(x2, y2, z2, clims=clims, c=:viridis, colorbar=false)
p3 = contourf(x3, y3, z3, clims=clims, c=:viridis, colorbar=false)
p4 = contourf(x4, y4, z4, clims=clims, c=:viridis, colorbar=false)

h2 = scatter([0,0], [0,1], zcolor=[0,3], clims=clims,
                xlims=(1,1.1), label="", c=:viridis,
                colorbar_title="cbar", framestyle=:none)

l = @layout [grid(2, 2) a{0.035w}]
p_all = plot(p1, p2, p3, p4, h2, layout=l, link=:all)
```

