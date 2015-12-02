# TestRunner

### A test runner library for [Julia](http://julialang.org)

[![Build Status](https://travis-ci.org/gdziadkiewicz/TestRunner.jl.svg?branch=master)](https://travis-ci.org/gdziadkiewicz/TestRunner.jl)
[![Build status](https://ci.appveyor.com/api/projects/status/l5h55yi87aag0dh3?svg=true)](https://ci.appveyor.com/project/gdziadkiewicz/testrunner-jl)

`TestRunner.jl` is a [Julia](http://julialang.org) test runner library used by standalone [Tk](https://github.com/JuliaLang/Tk.jl) based [GUITestRunner](https://github.com/meoke/GUITestRunner.jl) and [atom-julia-test-runner](https://github.com/mateuszkaleta/atom-julia-test-runner) extension for [Atom](https://github.com/atom/atom). It can parse [FactCheck](https://github.com/JuliaLang/FactCheck.jl) tests to information rich, tree structure. In the nearest future it will be able to run provided test file and parse it's output.

MIT Licensed - see LICENSE.md

**Installation**: `julia> Pkg.clone("https://github.com/gdziadkiewicz/TestRunner.jl")`

### Basics
Test file structure parsing:
```julia
using TestRunner

testFilePath = "tests.jl"
result =  get_test_structure(testFilePath)
```
