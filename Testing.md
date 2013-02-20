Roxygen2
========

This is the standard method of documentation used in PEcAn development,
it provides inline documentation similar to doxygen.\
* Website:
[https://github.com/yihui/roxygen2](https://github.com/yihui/roxygen2)\
* Documentation:
[http://cran.r-project.org/web/packages/roxygen2/roxygen2.pdf](http://cran.r-project.org/web/packages/roxygen2/roxygen2.pdf)\
* See PEcAn source code (`R/*.R` files) for examples.

Basic Roxygen2 instructions:
----------------------------

Section headers link to “Writing R extensions” which provides in-depth
documentation. This is provided as an overview and quick reference.

### [Tags](http://cran.r-project.org/doc/manuals/R-exts.html#Documenting-functions)

* tags are preceeded by `##'`
* tags required by R:
**  `@title` tag is required, along with actual title
**  `@param` one for each parameter, should be defined
**  `@return` must state what function returns (or nothing, if something occurs as a side effect
*   tags strongly suggested for most functions:
**  `@author`
**  `@examples` can be similar to test cases.
*   optional tags:
**  `@export` required if function is used by another package
**  `@import` can import a required function from another package (if package is not loaded or other function is not exported)
**  `@seealso` suggests related functions. These can be linked using `\code{link{}}`

### Text markup

#### [Formatting](http://cran.r-project.org/doc/manuals/R-exts.html#Marking-text)

* `\bold{}`
* `\emph{}` italics

#### [Links](http://cran.r-project.org/doc/manuals/R-exts.html#Marking-text)

* `\url{www.url.com}` or `\href{url}{text}` for links
* `\code{\link{thisfn}}` links to function “thisfn” in the same
    package
* `\code{\link{foo::thatfn}}` links to function “thatfn” in package
    “foo”
* `\pkg{package_name}`

#### [Math](http://cran.r-project.org/doc/manuals/R-exts.html#Mathematics)

* `\eqn{a+b=c}` uses LaTex to format an inline equation
* `\deqn{a+b=c}` uses LaTex to format displayed equation
* `\deqn{latex}{ascii}` and `\eqn{latex}{ascii}` can be used to
    provide different versions in latex and ascii.

#### [Lists](http://cran.r-project.org/doc/manuals/R-exts.html#Lists-and-tables)

```
    \enumerate{
    \item A database consists of one or more records, each with one or
    more named fields.
    \item Regular lines start with a non-whitespace character.
    \item Records are separated by one or more empty lines.
    }
```
note:    `\itemize` and `\enumerate` commands may be nested.

#### [Tables](http://cran.r-project.org/doc/manuals/R-exts.html#Lists-and-tables)

```
    \tabular{rlll}{
    [,1] \tab Ozone \tab numeric \tab Ozone (ppb)\cr
    [,2] \tab Solar.R \tab numeric \tab Solar R (lang)\cr
    [,3] \tab Wind \tab numeric \tab Wind (mph)\cr
    [,4] \tab Temp \tab numeric \tab Temperature (degrees F)\cr
    [,5] \tab Month \tab numeric \tab Month (1--12)\cr
    [,6] \tab Day \tab numeric \tab Day of month (1--31)
    }
```
Example
-------

Here is an example documented function, myfun

```{r}
    ##' My function adds three numbers
    ##'
    ##' A great function for demonstrating Roxygen documentation
    ##' @title My function
    ##' @param a numeric
    ##' @param b numeric
    ##' @param c numeric
    ##' @return d, numeric sum of a + b + c
    ##' @export
    ##' @author David LeBauer
    ##' @examples
    ##' myfun(1,2,3)
    ##' \dontrun{myfun(NULL)}
    myfun <- function(a, b, c){
      d <- a + b + c
      return(d)
    }
```

In emacs, with the cursor inside the function, the keybinding C-x O will generate an outline or update the Roxygen2 documentation.

Updating documentation
----------------------

* After adding documentation run the following command (replacing common with the name of the folder you want to update):

```{r}
require(devtools)
document("common")
```

Add new .Rd files to bzr repository
-----------------------------------

```
git add man/
git commit -m "added documentation to package foo" man/*
```