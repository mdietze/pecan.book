Coding Style
------------

Consistent coding style improves readability and reduces errors in
shared code.

R does not have an official style guide, but Hadley Wickham provides one that is well
thought out and widely adopted. [Advanced R: Coding Style](http://r-pkgs.had.co.nz/style.html).

Both the Wickham text and this page are derived from [Google's R Style Guide](https://google.github.io/styleguide/Rguide.xml).

## Use Roxygen2 documentation

This is the standard method of documentation used in PEcAn development,
it provides inline documentation similar to doxygen. Even trivial
functions should be documented.

See [Roxygen2](Roxygen2.md) Wiki page

## Write your name at the top

Any function that you create or make a meaningful contribution to should
have your name listed after the author tag in the function documentation.

## Use testthat testing package

See [Unit_Testing](Testing.md) wiki for instructions, and [Advanced R: Tests](http://r-pkgs.had.co.nz/tests.html).

* tests provide support for documentation - they define what a function is (and is not) expected to do 
* all functions need tests to ensure basic functionality is maintained during development.
* all bugs should have a test that reproduces the bug, and the test should pass before bug is closed


## Don't use shortcuts

R provides many shortcuts that are useful when coding interactively, or for writing scripts. However, these can make code more difficult to read and can cause problems when written into packages.

### Function Names (`verb.noun`)

Following convention established in PEcAn 0.1, we use the all lowercase with periods to separate words. They should generally have a `verb.noun` format, such as `query.traits`, `get.samples`, etc.

### File Names

File names should end in `.R`, `.Rdata`, `.Rscript` and should be meaningful, e.g. named after the primary functions that they contain. There should be a separate file for each major high-level function to aid in identifying the contents of files in a directory.

### Use "<-" as an assignment operator

* Because most R code uses <- (except where = is required), we will use <-
* "=" is used for function arguments

### Use Spaces

* around all binary operators (=, +, -, <-, etc.). 
* after but not before a comma

### Use curly braces

The option to omit curly braces is another shortcut that makes code easier to write but harder to read and more prone to error.

## Package Dependencies: 

### library vs require 

When another package is required by a function or script, it can be called in the following ways:

1. As a package dependency loaded with the package
   This should be the default approach when writing functions in a package. There can be some exceptions, for example when a rarely-used or non-essential function requires an esoteric package. 
2. using `library`
   if dependency is not met, will print an error and stop
3. using `require`
   will print a warning and continue (but will throw an error when a function from the required package is called) 

Reference: Stack Overflow ["What is the difference between require and library?"](http://stackoverflow.com/questions/5595512/what-is-the-difference-between-require-and-library)

### DEPENDS, SUGGESTS, IMPORTS

It is considered best practice to use DEPENDS and SUGGESTS in DESCRIPTION; SUGGESTS should be used for packages that are called infrequently, or only in examples and vignettes; suggested packages are called by require inside a function.

Consider using IMPORTS instead of depends in the DESCRIPTION files. This will make loading packages faster by allowing it to have functions available without loading the hierarchy of dependencies, dependencies of dependencies, ad infinitum ...
From p. 6 of the "R extensions manual":http://cran.r-project.org/doc/manuals/R-exts.html

> The `Suggests` field uses the same syntax as `Depends` and lists packages that are not necessarily needed. This includes packages used only in examples, tests or vignettes (see Section 1.4 [Writing package vignettes], page 26), and packages loaded in the body of functions. E.g., suppose an example from package foo uses a dataset from package bar. Then it is not necessary to have bar use foo unless one wants to execute all the examples/tests/vignettes: it is useful to have bar, but not necessary. Version requirements can be specified, and will be used by R CMD check.


