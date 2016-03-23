# TestRunner

### A test runner library for [Julia](http://julialang.org)

[![Build Status](https://travis-ci.org/gdziadkiewicz/TestRunner.jl.svg?branch=master)](https://travis-ci.org/gdziadkiewicz/TestRunner.jl)
[![Build status](https://ci.appveyor.com/api/projects/status/l5h55yi87aag0dh3?svg=true)](https://ci.appveyor.com/project/gdziadkiewicz/testrunner-jl)

`TestRunner.jl` is a [Julia](http://julialang.org) test runner library used by standalone [Tk](https://github.com/JuliaLang/Tk.jl) based [GUITestRunner](https://github.com/meoke/GUITestRunner.jl) and [atom-julia-test-runner](https://github.com/mateuszkaleta/atom-julia-test-runner) extension for [Atom](https://github.com/atom/atom). It can parse [FactCheck](https://github.com/JuliaLang/FactCheck.jl) tests and run them returning results as an information rich, tree structure.

MIT Licensed - see [LICENSE.md](https://github.com/gdziadkiewicz/TestRunner.jl/blob/master/LICENSE.md)

**Installation**: `julia> Pkg.clone("https://github.com/gdziadkiewicz/TestRunner.jl")`

### Basics
Test file structure parsing:
```julia
using TestRunner

testFilePath = "tests.jl"
structure = get_test_structure(testFilePath)
```

Running tests from file:
```julia
using TestRunner

testFilePath = "tests.jl"
results = run_all_tests(testFilePath)
```

Both structure and results are returned as a tree of `TestStructureNode` objects.

Functions designed to retrieve informations from the nods:
* `children` - returns children of given `TestStructureNode`
* `line` - returns line at which given `TestStructureNode` starts in tests source code
* `name` - returns name of given `TestStructureNode`. For `@fact` it is the custom error messages passed as second argument, for `facts` and `context` it is the description providede as first argument.
* `result` - returns result of the assertion as `RESULT` enum. Works only for `FactNode` type. Possible results are:
  * `test_success`
  * `test_failure`
  * `test_error`
  * `test_pending`
  * `test_not_run`
* `details` - returns message which would be printed by `FactCheck` as output of given test. Works only for `FactNode` type.
* `stacktrace` - returns the stacktrace for given `FactNode`. It will not be an empty string only for nodes with result `test_error`.

### Limitations
* At the moment TestRunner does not handle any kind of branching logic in tests(there are plans to fix this issue as soon as Julia 0.5 gets released).
* TestRunner does not support macro generated tests.
