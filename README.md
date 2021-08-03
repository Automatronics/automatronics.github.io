# Automatronics Homepage

https://automatronics.github.io/

## Static Site Generation

Franklin.jl

https://franklinjl.org/

https://github.com/tlienart/Franklin.jl


Start Julia REPL.

```sh
julia
```

Alternative: using Docker.

```sh
docker pull julia:1.6.2
docker run --rm -v $PWD:/site -p 8000:8000 julia
# cd("/site")
```

Creating site.

```julia
using Pkg
Pkg.activate(".")
Pkg.add(["Franklin", "NodeJS", "Conda"])
# Pkg.update()

using NodeJS
run(`$(npm_cmd()) install highlight.js`)

using Conda
Conda.pip_interop(true)
Conda.pip("install", "css_html_js_minify")

using Franklin
newsite("."; template = "basic")

serve(; host = "0.0.0.0", port = 8000, launch = false)
```
