Frustration: One Year With R
================
Reece Goding

-   [1 Introduction](#1-introduction)
    -   [1.1 Length](#11-length)
    -   [1.2 Experience](#12-experience)
    -   [1.3 Ignorance](#13-ignorance)
    -   [1.4 Assumed Knowledge](#14-assumed-knowledge)
    -   [1.5 Disclaimer](#15-disclaimer)
-   [2 General Feelings](#2-general-feelings)
-   [3 What R Does Right](#3-what-r-does-right)
    -   [3.1 Mathematics and Statistics](#31-mathematics-and-statistics)
    -   [3.2 Names and Data Frames](#32-names-and-data-frames)
    -   [3.3 Outstanding Packages](#33-outstanding-packages)
    -   [3.4 Vectorization](#34-vectorization)
    -   [3.5 Functional Programming](#35-functional-programming)
        -   [3.5.1 First-class Functions](#351-first-class-functions)
        -   [3.5.2 First-class
            Environments](#352-first-class-environments)
        -   [3.5.3 Generic Functions](#353-generic-functions)
    -   [3.6 Syntax](#36-syntax)
    -   [3.7 Miscellaneous Positives](#37-miscellaneous-positives)
-   [4 What R Does Wrong](#4-what-r-does-wrong)
    -   [4.1 Lists](#41-lists)
    -   [4.2 Strings](#42-strings)
    -   [4.3 Variable Manipulation](#43-variable-manipulation)
    -   [4.4 Switch](#44-switch)
    -   [4.5 Subsetting](#45-subsetting)
        -   [4.5.1 Combining Operators](#451-combining-operators)
        -   [4.5.2 Removing Dimensions](#452-removing-dimensions)
        -   [4.5.3 Dangers of $](#453-dangers-of-)
        -   [4.5.4 Indistinguishable
            Errors](#454-indistinguishable-errors)
        -   [4.5.5 Named Atomic Vectors](#455-named-atomic-vectors)
        -   [4.5.6 Silence](#456-silence)
        -   [4.5.7 Subsetting by
            Predicates](#457-subsetting-by-predicates)
    -   [4.6 Vectorization Again](#46-vectorization-again)
    -   [4.7 R Won’t Help You](#47-r-wont-help-you)
        -   [4.7.1 The Documentation](#471-the-documentation)
        -   [4.7.2 The Functions](#472-the-functions)
        -   [4.7.3 Extended Example:
            Matrices](#473-extended-example-matrices)
        -   [4.7.4 The Error Messages](#474-the-error-messages)
        -   [4.7.5 Mapply Challenge](#475-mapply-challenge)
        -   [4.7.6 Stealing from the
            Tidyverse](#476-stealing-from-the-tidyverse)
    -   [4.8 The Community](#48-the-community)
    -   [4.9 Generic Functions Again](#49-generic-functions-again)
        -   [4.9.1 The Class System](#491-the-class-system)
        -   [4.9.2 Existing Functions](#492-existing-functions)
        -   [4.9.3 Internal Generics](#493-internal-generics)
        -   [4.9.4 S4](#494-s4)
    -   [4.10 Factor Variables](#410-factor-variables)
    -   [4.11 Syntactic Sugar](#411-syntactic-sugar)
        -   [4.11.1 Sequences](#4111-sequences)
        -   [4.11.2 Non-standard
            Evaluation](#4112-non-standard-evaluation)
    -   [4.12 Missing Features](#412-missing-features)
    -   [4.13 Miscellaneous Negatives](#413-miscellaneous-negatives)
-   [5 The Tidyverse](#5-the-tidyverse)
    -   [5.1 Dplyr](#51-dplyr)
    -   [5.2 Ggplot2](#52-ggplot2)
    -   [5.3 Lubridate](#53-lubridate)
    -   [5.4 Magrittr](#54-magrittr)
    -   [5.5 Purrr](#55-purrr)
    -   [5.6 Stringr and Tibble](#56-stringr-and-tibble)
-   [6 Conclusion](#6-conclusion)

# 1 Introduction

What follows is an account of my experiences from about one year of
roughly daily R usage. It started out as a list of things that I liked
and disliked about the language, but eventually grew to be something
huge. Once the list exceeded ten thousand words, I knew that it must be
published. By the time I was done, it had nearly tripled in length. It
took five months of weekends just to get it all in R Markdown.

This isn’t an attack on R or a pitch for anything else. It is only an
account of what I’ve found to be right and wrong with the language.
Although the length of my list of what is wrong far exceeds that of what
is right, that may be my failing rather than R’s. I suspect that my list
of what R does right will grow as I learn other languages and begin to
miss some of R’s benefits. I welcome any attempts to correct this or any
other errors that you find. Some major errors will have slipped in
somewhere or other.

## 1.1 Length

To start, I must issue a warning: This document is **huge**. I have
tried to keep everything contained in small sections, such that the
reader has plenty of points where they can pause and return to the
document later, but the word count is still far higher than I’m happy
with. I have tried to not be too petty, but every negative point in here
comes from an honest position of frustration. There are some things that
I really love about R, I’ve even devoted [an entire section to
them](#3-what-r-does-right). However, if there is one point that I
really want this document to get across, it’s that R is filled to the
brim with small madnesses. Although I can name a few major issues with
R, its ultimate problem is the sum of its little problems. This document
couldn’t be short.

Also, on the topic of the sections in this document, watch out for all
of the internal links. Nothing in R Markdown makes them look distinct
from external ones, so you might lose your place if you don’t take care
to open all of your links in a new tab/window.

## 1.2 Experience

Before I say anything nasty about R, a show of good faith is in order.
In my year with R, I have done the following:

-   Added almost 100 [R
    solutions](https://github.com/ReeceGoding/Rosetta-Code-Submissions)
    to [Rosetta Code](https://rosettacode.org/wiki/Rosetta_Code).
-   Asked over 100 Stack Overflow R questions.
-   Read both editions of [*Advanced R*](https://adv-r.hadley.nz/) from
    cover to cover. I didn’t do the exercises, but I’d recommend the
    books to any serious R user.
-   Read [*R for Data Science*](https://r4ds.had.co.nz/) from cover to
    cover. It’s a good enough non-technical introduction to the
    Tidyverse and a handful of other popular parts of R’s ecosystem.
    However, I can’t give it a strong recommendation for a variety of
    reasons:
    -   A lot of the exercises didn’t specify what they wanted from your
        answer. This made checking your solutions against anyone else’s
        quite difficult.
    -   It deliberately avoids the fundamentals of programming –
        e.g. making functions, loops, and if statements – until the
        second half. I therefore suspect that any non-novice would be
        better off finding an introduction to the relevant packages with
        their favourite search engine.
    -   Despite my efforts, I can find no “*Tidyverse for Programmers*”
        book. When one is inevitably written, it will make this book
        redundant for many potential readers.
-   Read [*The R
    Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf) and
    some other well-known PDFs and manuals, such as [*Rtips. Revival
    2014!*](https://pj.freefaculty.org/R/Rtips.html) and the official
    [*An Introduction to
    R*](https://cran.r-project.org/doc/manuals/r-release/R-intro.html),
    [*R Language
    Definition*](https://cran.r-project.org/doc/manuals/r-release/R-lang.html),
    and [*R FAQ*](https://cran.r-project.org/doc/FAQ/R-FAQ.html)
    manuals. Out of all of these, I must recommend [*The R
    Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf). The
    page count may be intimidating, but it’s a delightfully fast read
    that mirrors many of my points. In many cases I have pointed the
    reader straight to its relevant section. Its only true fault is its
    age. I wish that I could claim that this document is a sequel to it,
    but I’m writing to review rather than advise.
-   Made minor contributions to open source R projects.

At minimum, I can say with confidence that unless I happen to pick up an
R-focused statistics textbook – [the *R FAQ* has some tempting
items](https://cran.r-project.org/doc/FAQ/R-FAQ.html#What-documentation-exists-for-R_003f)
– I’ve already done all of the R-related reading that I ever plan to do.
All that is left for me is to use the language more and more. I hope
that this section shows that I’ve given it a good chance before writing
this review of it.

## 1.3 Ignorance

I am not an R expert. I freely admit that I am lacking in the following
regards:

-   You can never have done enough statistics with R. I’ve mostly used R
    as a programming language rather than a statistics tool. My
    arguments would certainly be stronger if I had some published stats
    work to back them up, even just blogs. I might correct this at some
    point.
-   The above point makes me more ignorant of formulae objects
    (e.g. expressions like `foo ~ log(bar) * bar^2`), the `plot()`
    function, and factor variables than I ought to be. I saw a lot of
    them during my degree, but have long since forgotten them and have
    never needed to pick them back up. For similar reasons, I have
    nothing to say on how hard it can sometimes be to read data in to R.
-   I haven’t used enough of the community’s favourite libraries. My
    biggest regret is my near-total ignorance of `data.table`. From
    [what little I’ve
    seen](https://atrebas.github.io/post/2019-03-03-datatable-dplyr/),
    it’s a real pleasure. More practice with `ggplot2`, the wider
    Tidyverse, and R Markdown is also in order. If I continue to use R,
    I will gradually master these. For now, it suffices to say that my
    experience with base R far exceeds my knowledge of both the
    Tidyverse and many other well-loved packages. If I’ve missed any
    gems, let me know.
-   My experience with R’s competitors is minimal. In particular, I have
    virtually no experience with Python or Julia. Most of my points on R
    are about R on its own merits, rather than comparing it to its
    competition. I plan to pick up Python soon, but Julia is in my
    distant future.
-   Although I have used SQL professionally, how it compares to R has
    rarely crossed my mind. This suggests that I’m missing something
    about both languages.
-   R’s functional aspects make me wish that I knew more Lisp. I’m
    slowly picking it up, but I’ve currently not got any further than
    chapter 4 of *Structure and Interpretation of Computer Programs*.
    R’s clear Scheme inspiration makes Lisp books a lot less fun to
    read; It’s like I’ve already been spoiled on some of the best bits.
-   I haven’t done enough OOP in R. My only real experience of it is
    with S3. S4 looks enough like CLOS that I expect that I will revisit
    it at some point after picking up Common Lisp, but that will just be
    to play around.
-   I have never made a package for R and have no experience with the
    ecosystem surrounding that (e.g. `roxygen2`). I have no plans for
    this.
-   I have no experience in developing large projects in R. This is
    likely a part of why I have never felt the need to make significant
    use of its OOP. I do not expect this to change.

The above list is unlikely to be exhaustive. I’m not against reading
another book about R as a programming language, but [*Advanced
R*](https://adv-r.hadley.nz/) seems to be the only one that anyone ever
mentions. For the foreseeable future, the main thing that I plan to do
to improve my evaluation of R is to learn Python. I’ll probably read a
book on it.

## 1.4 Assumed Knowledge

You’d be a fool to read this without some experience of R. I don’t think
that I’ve written anything that requires an expert level of
understanding, but you’re unlikely to get much out of this document
without at least a basic idea of R. I’ve also mentioned the Tidyverse a
few times without giving it much introduction, particularly its `tibble`
package. If you care enough about R to consider reading this document,
then you really ought to be familiar with the most popular parts of the
Tidyverse. It’s rare for any discussion of R to go long without some
mention of `purrr`, `dplyr` or `magrittr`.

## 1.5 Disclaimer

This document started out as personal notes that I had no intention of
publishing. There’s a good chance that I might have copy and pasted
someone’s example from somewhere and totally forgot that it wasn’t my
own. If you spot any plagiarism, let me know.

# 2 General Feelings

My overall feelings about R are tough to quantify. As I mentioned near
the start, its ultimate problem is the sum of its little problems.
However, if I must speak generally, then I think that the problem with R
is that it’s always some mix of the following:

1.  A statistics language with countless useful libraries and an
    excellent collection of mathematical tools.
2.  A Scheme-inspired language that tries to be functional while
    maintaining a C-like syntax.
3.  Decades of haphazard patches for S.
4.  A collection of [semantic
    semtex](https://wiki.c2.com/?SemanticSemtex) that is powerful in the
    hands of a master and crippling in the hands of a novice.

When it’s anything but \#3, R is great. Statisticians and mathematicians
love it for \#1 and programmers love it for \#2 and \#4. If it weren’t
for \#3, R would be an amazing – albeit, domain-specific – language, but
\#3 is such a big factor that it makes the language unpredictable,
inconsistent, and infuriating. Mixed with \#4, it makes being an R
novice hellish. It gives me little doubt that R is not the ideal tool
for many of the jobs that it wants to do, but \#1 and \#2 leave me with
equally little doubt that R can be a very good tool.

# 3 What R Does Right

As a final show of good faith, here is what I think R does right. In
summary, along with having some great functional programming toys, R has
some domain-specific tools that can work excellently when they’re in
their element. Whatever the faults of R, it’s always going to be my
first choice for some problems.

## 3.1 Mathematics and Statistics

R wants to be a mathematics and statistics tool. Many of its fundamental
design choices support this. For example, vectors are primitive types
and R isn’t at all shy about giving you a table or matrix as output.
Similarly, the base libraries are packed with maths and stats functions
that are usually a good combination of relevant, generic, and helpful.
Some examples:

-   Lots of stats is made easy. Commands like `boxplot(data)` or
    `quantile(data)` just work and there are lots of handy functions
    like `colSums()`, `table()`, `cor()`, or `summary()`.

-   R is **the** language of research-level statistics. If it’s stats, R
    either has it built-in or has a library for it. It’s impossible to
    visit a statistics Q&A website and not see R code. For this reason
    alone, R will never truly die.

-   The generic functions in the base stats library work magic. Whenever
    you try to print or summarise a model from there, you’re going to
    get all of the details that you could ever realistically ask for and
    you’re going to get them presented in a very helpful way. For
    example

    ``` r
    model <- lm(mpg ~ wt, data = mtcars)
    print(model)
    ## 
    ## Call:
    ## lm(formula = mpg ~ wt, data = mtcars)
    ## 
    ## Coefficients:
    ## (Intercept)           wt  
    ##      37.285       -5.344
    summary(model)
    ## 
    ## Call:
    ## lm(formula = mpg ~ wt, data = mtcars)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -4.5432 -2.3647 -0.1252  1.4096  6.8727 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  37.2851     1.8776  19.858  < 2e-16 ***
    ## wt           -5.3445     0.5591  -9.559 1.29e-10 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 3.046 on 30 degrees of freedom
    ## Multiple R-squared:  0.7528,   Adjusted R-squared:  0.7446 
    ## F-statistic: 91.38 on 1 and 30 DF,  p-value: 1.294e-10
    ```

    shows us plenty of useful information and works just as well even if
    we change to another type of model. Your mileage may vary with
    packages, but it usually works as expected. Other examples are easy
    to come by, e.g. `plot(model)`.

-   The rules for subsetting data, although requiring mastery, are
    extremely expressive. Coupled with sub-assignment tricks like
    `result[which(result < 0.5)] <- 0`, which often do exactly what you
    think they will, you can really save yourself a lot of work. Being
    able to demand precisely what parts of your data that you want to
    see or change is a really great feature.

-   The factor and ordered data types are definitely the sort of tools
    that I want to have in a stats language. [They’re a bit
    unpredictable](#410-factor-variables), but they’re great when they
    work.

-   It’s no surprise that an R terminal has fully replaced my OS’s
    built-in calculator. It’s my first choice for any arithmetical task.
    When checking a gaming problem, I once opened R and used
    `(0.2 * seq(1000, 1300, 50) + 999) / seq(1000, 1300, 50)`. That
    would’ve been several lines in many other languages. Furthermore, a
    general-purpose language that was capable of the same would’ve had a
    call to something long-winded like `math.vec.seq()` rather than just
    `seq()`. I find the cumulative functions, e.g. `cumsum()` and
    `cummax()`, similarly enjoyable.

-   How many other language have matrix algebra fully built-in? Solving
    systems of linear equations is just `solve()`.

-   The `rep()` function is outstandingly versatile. I’d give examples,
    but those found in its documentation are more than sufficient. Open
    up R and run `example(rep)` if you want to see them. If tricks like
    `cbind(rep(1:6, each = 6), rep(1:6, times = 6))` have yet to become
    second nature, then you’re really missing out.

-   On top of replacing your computer’s calculator, R can replace your
    graphing calculator as well. Unless you need to tinker with the axes
    or stop the asymptotes causing you problems – problems that your
    graphing calculator would give you anyway – functions like
    `curve(x / (x^3 + 9), -10, 10)` (output below) do exactly what you
    would expect and exactly how.

    ![](Frustration-One-Year-With-R_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

## 3.2 Names and Data Frames

These seem like trivial features, but the language’s deep integration of
them is extremely beneficial for manipulating and presenting your data.
They assist subsetting, variable creation, plotting, printing, and even
[metaprogramming](#352-first-class-environments).

-   The ability to name the components of vectors,
    e.g. `c(Fizz=3, Buzz=5)`, is a nice trick for toy programs. The same
    syntax is used to much greater effect with lists, data frames, and
    S4 objects. However, it’s good to show how far you can get with even
    the most basic case. Here’s my submission for a [General
    FizzBuzz](https://rosettacode.org/wiki/General_FizzBuzz) task:

    ``` r
    namedGenFizzBuzz <- function(n, namedNums)
    {
      factors <- sort(namedNums)#Required by the task: We must go from least factor to greatest.
      for(i in 1:n)
      {
        isFactor <- i %% factors == 0
        print(if(any(isFactor)) paste0(names(factors)[isFactor], collapse = "") else i)
      }
    }
    namedNums <- c(Fizz=3, Buzz=5, Baxx=7)#Notice that we can name our inputs without a function call.
    namedGenFizzBuzz(105, namedNums)
    ```

    I’ve little doubt that an R guru could improve this, but the amount
    of expressiveness in each line is already impressive. A lot of that
    is owed to R’s love for names.

-   Having a tabular data type in your base library – the data frame –
    is very handy for when you want a nice way to present your results
    without having to bother importing anything. Due to this and the
    aforementioned ability to name vectors, my output in coding
    challenges often looks nicer than most other people’s.

-   I like how data frames are constructed. Even if you don’t know any R
    at all, it’s pretty obvious what
    `data.frame(who = c("Alice", "Bob"),  height = c(1.2, 2.3))`
    produces and what adding the
    `row.names = c("1st subject", "2nd subject")` argument would do.

-   As a non-trivial example of how far these features can get you, I’ve
    had some good fun making alists out of syntactically valid
    expressions and using only those alists to build a data frame where
    both the expressions and their evaluated values are shown:

    ``` r
    expressions <- alist(-x ^ p, -(x) ^ p, (-x) ^ p, -(x ^ p))
    x <- c(-5, -5, 5, 5)
    p <- c(2, 3, 2, 3)
    output <- data.frame(x,
                         p,
                         setNames(lapply(expressions, eval), sapply(expressions, deparse)),
                         check.names = FALSE)
    print(output, row.names = FALSE)
    ##   x p -x^p -(x)^p (-x)^p -(x^p)
    ##  -5 2  -25    -25     25    -25
    ##  -5 3  125    125    125    125
    ##   5 2  -25    -25     25    -25
    ##   5 3 -125   -125   -125   -125
    ```

    (stolen from my submission
    [here](https://rosettacode.org/wiki/Exponentiation_with_infix_operators_in_(or_operating_on)_the_base)).
    Did you notice that the output knew the names of `x` and `p` without
    being told them? Did you also notice that a similar thing happened
    in after our call to `curve()` earlier on? Finally, did you notice
    how easy it was to get such neat output?

## 3.3 Outstanding Packages

[I’ve already admitted a great deal of ignorance of this
topic](#13-ignorance), but there are some parts of R’s ecosystem that
I’m happy to call outstanding. The below are all things that I’m sure to
miss in other languages.

-   `corrplot`: It has less than ten functions, but it only needed one
    to blow my mind. Once you’ve even as much as read [the
    introduction](https://cran.r-project.org/web/packages/corrplot/vignettes/corrplot-intro.html),
    you will never try to read a correlation matrix again.
-   `ggplot2`: I’m not experienced enough to know what faults it has,
    but it’s fun to use. That single fact makes it blow any other
    graphing software that I’ve used out of the water: **It’s fun**.
-   `magrittr`: It sold me on pipes. I’d say that any package that makes
    you consider changing your programming style is automatically
    outstanding. However, the real reason why I love it is because
    whenever I’ve run `bigLongExpression()` in my console and decided
    that I really wanted `foo()` of it, it’s so much easier to press the
    up arrow and type CTRL+SHIFT+M+“foo” than it is to do anything that
    results in `foo(bigLongExpression())` appearing. Maybe there’s a
    keyboard shortcut that I never learned, but this isn’t the only
    reason why I love `magrittr`. [I’ll say more about it much
    later](#54-magrittr).
-   `R Markdown` has served me well in writing this document. It’s
    buggier than I’d like, rarely has helpful error messages, and does
    things that I can’t explain or fix even after setting a bounty on
    Stack Overflow, but it’s still a great way to make a document
    from R. It’s the closest thing that I know of to an R user’s LaTeX.
    I had to wait on [this bug
    fix](https://github.com/rstudio/rmarkdown/pull/2093) before I could
    start numbering my sections. Hopefully it didn’t break anything.

## 3.4 Vectorization

[When it’s not causing you problems](#46-vectorization-again), the
vectorization can be the best thing about the language:

-   The vector recycling rules are powerful when mastered. Expressions
    like `c("x", "y")[rep(c(1, 2), times = 4)]` let you do a lot with
    only a little work. My favourite ever FizzBuzz could well be

    ``` r
    x <- paste0(rep("", 100), c("", "", "Fizz"), c("", "", "", "", "Buzz"))
    cat(ifelse(x == "", 1:100, x), sep = "\n")
    ```

    I wish that I could claim credit for that, but I stole it from an
    old version of [this page](https://rosettacode.org/wiki/FizzBuzz#R)
    and improved it a little.

-   Basically everything is a vector, so R comes with some really cool
    vector-manipulation tools like `ifelse()` (as seen above) and makes
    it very easy to use a function on an entire collection. Can you
    believe that `mtcars / 20` actually works?

-   Tricks like `array / seq_along(array)` save a lot of loop writing.

-   Even simple things like being able to subtract a vector from a
    constant (e.g. `10 - 1:5`) and get a sensible result are a gift when
    doing mathematics.

-   Vectorization of functions is sometimes very useful, particularly
    when it lets you do what should’ve been two loops worth of work in
    one line. You’d be amazed by how often you can get away with calling
    `foo(1:100)` without needing to vectorize `foo()` yourself.

## 3.5 Functional Programming

R’s done a good job of harnessing the power of functional languages
while maintaining a C-like syntax. It makes no secret of being inspired
by Scheme and has reaped many of its benefits.

### 3.5.1 First-class Functions

It’s impossible to not notice that functions are first-class in R.
You’re almost forced to learn functional programming idioms like mapping
functions, higher-order functions, and anonymous functions. This is a
good thing. Where else do you find a language with enough useful
higher-order functions for the community to be able to discourage new
users from writing loops? Some examples:

-   All of the functional programming toys that you could want are
    easily found in R, e.g. closures, anonymous functions, and
    higher-order functions like `Map()`, `Filter()`, and `Reduce()`.
    Once you’re used to them, you can write some very expressive code.
-   The apply family of functions is basically a set of DSL mapping
    functions for stats. Both `apply()` and `tapply()` can produce some
    very concise code, as can related functions like `by()`.
-   Where else can you write functions that are both anonymous and
    recursive? Not that you should, of course.
-   First-class functions sometimes interact with R’s vectorization
    obsession in a very entertaining way. In how many other languages do
    you see somebody take a list of functions and, in a single line,
    call them all with a vector as a single argument to each function?
    Code like `lapply(listOfFuns, function(f) f(1:10))` is entirely
    valid. It calls each function in `listOfFuns` with the entire vector
    `1:10` as their first argument.
-   Code like `Vectorize(foo)(1:100)` is not particularly hard to
    understand, but I’d struggle to name another language that lets me
    do the same thing with so much ease.

### 3.5.2 First-class Environments

Not only are functions first-class in R, environments are too. You
therefore have lots of control over what environment an expression is
evaluated in. This is an amazing source of power that tends to scare off
beginners, but I cannot overstate how much of an asset it can be. If
you’re not familiar with the below, look it up. You will not regret it.

-   Because R’s environments are first-class, functions like `with()`
    and `within()` can generate them on the fly. I’ve seen this called
    “*data masking*”. [*Advanced R* has a whole chapter on
    it](https://adv-r.hadley.nz/translation.html). It lets you do things
    like “*treat this list of functions as if it were a namespace, so I
    can write code that uses function names that I wouldn’t dare use
    elsewhere*”. This can also be used with data. For example,
    `tapply(mtcars$mpg, list(mtcars$cyl, mtcars$gear), mean)` uses
    `mtcars` far too many times, but
    `with(mtcars, tapply(mpg, list(cyl, gear), mean))` gives us an easy
    fix. Ad-hoc namespaces are an amazing thing to have, particularly
    when using functions that don’t have a `data` argument
    (e.g. `plot()`).
-   Modelling functions like `lm()` use the data-masking facilities that
    I’ve just described, as do handy functions like `subset()`. This
    saves incredible amounts of typing and massively increases the
    readability of your stats code. For example,
    `aggregate(mpg ~ cyl + gear, mtcars, mean)` returns very similar
    output to my above calls to `tapply()` without needing the
    complexity of using `with()`. It also allows for ridiculously
    concise code like `aggregate(. ~ cyl + gear, mtcars, mean)`.
-   You can write your own data-masking functions. Doing so relies on
    controlling the non-standard evaluation of some of your arguments.
    It’s the closest thing that R has to metaprogramming. The names
    mechanisms do a lot to remove any ambiguity from your attempts at
    this. Stealing an example from the documentation, do I even need to
    explain what
    `transform(airquality, new = -Ozone, Temp = (Temp-32)/1.8)` does?
    Being able to do all of that in one line is outstanding. Without R
    allowing developers to add new functions like this, the Tidyverse
    would’ve been impossible.

You might have spotted a pattern by now. R often lets you do very much
with very little.

### 3.5.3 Generic Functions

Generic function OO is pretty nice to have, even if I wouldn’t use
anything more complicated than S3. Being able to call `foo(whatever)`
and be confident that it’s going to do what I mean is always nice. Some
positives of R’s approach are:

-   As mentioned [earlier on](#31-mathematics-and-statistics), S3 is
    used excellently in the base R stats library. Functions like
    `print()`, `plot()`, and `summary()` almost always tell me
    everything that I wanted to know and tell me them with great
    clarity.

-   When you’re not trapped by [the
    technicalities](#49-generic-functions-again), S3 is an outstandingly
    simple tool that does exactly what R needs it to do. Have a look at
    all of the methods that the pre-loaded libraries define for `plot()`

    ``` r
    methods(plot)
    ##  [1] plot.acf*           plot.data.frame*    plot.decomposed.ts*
    ##  [4] plot.default        plot.dendrogram*    plot.density*      
    ##  [7] plot.ecdf           plot.factor*        plot.formula*      
    ## [10] plot.function       plot.hclust*        plot.histogram*    
    ## [13] plot.HoltWinters*   plot.isoreg*        plot.lm*           
    ## [16] plot.medpolish*     plot.mlm*           plot.ppr*          
    ## [19] plot.prcomp*        plot.princomp*      plot.profile.nls*  
    ## [22] plot.raster*        plot.spec*          plot.stepfun       
    ## [25] plot.stl*           plot.table*         plot.ts            
    ## [28] plot.tskernel*      plot.TukeyHSD*     
    ## see '?methods' for accessing help and source code
    ```

    because a statistician often only need to dispatch on the type of
    model being used, S3 is the perfect tool to make functions like
    `plot()` easy to extend, meaning that it’s easy to make it give your
    users exactly what they want. This isn’t just theoretical either.
    The output for `methods(plot)` gets a lot longer if I go through my
    list of packages and start loading some random number of them. Go
    try it yourself!

-   S3 generics and objects are very easy to write. The trade-off is
    that they don’t do anything to protect you from yourself. However,
    being able to tell R to shut up and do what I want it to a nice part
    of S3.

-   I like the idea of S3’s group generics, but I don’t like not being
    able to make my own. However, I think that you can do it for S4.

-   I have it on good authority that biology people often need to
    dispatch on more than one type of model at a time. This means that
    they shower the S4 object system with greater praise than what I’ve
    just given S3. Apparently, the `bioconductor` package is the
    outstanding example of their love of it.

-   S4 has multiple inheritance and multiple dispatch. I’m not going to
    say that multiple inheritance is a good thing, but it’s not always
    found in other OOP systems.

-   RC and the `R6` package are about as close as you’re ever going to
    get to having Java-like OOP in a mostly function language.

## 3.6 Syntax

Some of the syntax is nice:

-   [It can cause you problems](#4111-sequences), but the `:` operator
    is handy for things like `for(i in 1:20){...}`.
-   The `for` loop syntax is always the same:
    `for(element in vector){...}`. This means that there is no
    difference between the typical “*do n times*” case like
    `for(i in 1:n)` and the “*for every member of this collection*” case
    like `for(v in sample(20))`. I appreciate the consistency.
-   The `...` notation has a very nice “*do what I mean*” feel,
    particularly when you’re playing around with anonymous functions.
-   Because of `repeat` loops, you never need to write `while(TRUE)`.
-   [Although I have major issues with them](#45-subsetting), the rules
    for accessing elements sometimes give nice results. For example
    `array[c(i, j)] <- array[c(j, i)]` swaps elements `i` and `j` in a
    very clean way.
-   It’s nice to be able to do many variable assignments in one line
    e.g. `Alice <- Bob <- "Married"`. The best examples are when you do
    something like
    `lastElement <- output[lastIndex <- lastIndex + 1] <- foo`, letting
    you avoid having to do anything twice.
-   The syntax for manipulating environments makes sense. You have to
    learn the difference between `<-` and `<<-` , but having
    environments use a subset of the list syntax was a very good idea.
    It was a similarly good idea to have a lot of R’s internals
    (e.g. quoted function calls) be pairlists. This lets them be
    manipulated in exactly the same way as lists. The similarities
    between lists, pairlists, environments, and data frames go deeper
    than you may expect. For example, the `eval()` function lets you
    evaluate an expression in the specified environment, but it’s happy
    to take any of the data types that I’ve just listed in place of an
    environment. At times, R almost lets you forget that lists and
    environments aren’t the same thing.
-   The function names for making and manipulating S4 objects and
    functions are generally what you would expect them to be. For
    example, once you know `setClass()` and `setGeneric()`, you can
    probably guess what the corresponding function for methods is
    called.

## 3.7 Miscellaneous Positives

-   The built-in vectors `letters` and `LETTERS` come in handy
    surprisingly often. You’ll see me use them a lot.
-   The base library surprises me from time to time. It’s always worth
    putting what you want in to a search engine; Sometimes, you’ll find
    it. My most recent surprises were `findInterval()` and `cut()`.
-   The `na.print` argument to `print()`, trivial as it is, can be a
    thing of beauty.
-   R’s condition handling and recovery system is build atop S3, making
    it extremely customisable by letting you add and handle custom
    metadata pretty much however you want. It also has some nice
    built-in types of conditions like errors, warnings, and messages, as
    well as having `finally` blocks in `tryCatch()`. The only real
    oddity of the system is that its conditionals are treated as
    functions of the error, meaning that you will have to write strange
    code like
    `tryCatch(code, error = function(unused) "error", warning = function(unused) "warning")`.
    However, this is the price that you pay for being able to use code
    like
    `tryCatch(code, myError = function(e) paste0(e$message, " was triggered by ",e$call,". Try ",e$suggestion)`.
    As a final point of interest, I’ve heard that R’s condition handling
    system is one of the best copies of Common Lisp’s, which I’ve heard
    awesome things about.
-   Speaking of Lisp, [statistical Lisps used to be a
    thing](https://en.wikipedia.org/wiki/XLispStat). I’ve heard rumours
    of them still being used in Japan, but I can’t find anything to back
    that up. Everything that I’ve found says that [R killed them
    off](https://www.jstatsoft.org/article/view/v013i07/v13i07.pdf). As
    far as I know, nobody’s tried to make another such Lisp since the
    90’s. The fact that R can claim to have eradicated an entire
    category of language design is a great point in its favour. It’s
    also possible evidence that I’m correct to say that R resembling C
    is to its benefit. However, I’d be overjoyed to hear of such Lisps
    making a comeback. Imagine if we’re just one good Clojure library
    away from R surrendering to its Scheme roots and birthing a modern
    statistical Lisp.
-   Base R is quite stable. Breaking changes are almost unheard of. I
    don’t agree that they should be trying so hard to maintain
    compatibility with S, but this is an undeniable benefit of that
    decision.
-   The fact that the Tidyverse is just an R library, rather than an
    entirely separate language, is a testament to R’s metaprograming. I
    like being able to define new infix operators and replacement
    functions, but the Tidyverse went above and beyond. Where else do
    you see an entire library of pipes? Until very recently, base R
    didn’t even have pipes!
-   The Tidyverse is proof that people are trying to fix R. Although
    that comes with the implication that R is broken, the fact that
    people are both willing and able to fix it definitely says something
    nice about R.
-   I generally like the RStudio IDE. When Emacs is the only alternative
    that anyone takes seriously, you know that you’ve done a good job.
-   There is only one implementation of R that anyone’s ever heard of,
    so you never need to worry about undefined behaviour.

# 4 What R Does Wrong

This is where this documents starts to get long. Brace yourself. I
really don’t want to give off the impression that I hate R, but there
are just too many things wrong with it. Again, R’s ultimate problem is
the sum of its small madnesses. No language is perfectly consistent or
without compromises, but R’s choices of compromises and inconsistencies
are utterly unpredictable. I could deal with a handful of problems like
the many that will follow, but this is far more than a handful.

## 4.1 Lists

We’ll start gentle. R’s list type is an unavoidable part of the
language, but it’s very strange. As the following examples show, it’s
frequently a special case that you can rarely avoid.

-   <https://stackoverflow.com/questions/2050790/> does a good job of
    demonstrating that the list type is not like anything that another
    language would prepare you for. It and its many answers are very
    much worth a read.

-   Lists are the parent class of data frames, which are mandatory for
    anyone who wants to do stats in R, and most of the problems with
    lists are inherited by data frames. This makes the oddities of lists
    unavoidable.

-   Particularly when extracting single elements of lists, you need to
    be vigilant for whether R is going to give what you wanted or the
    list containing what you wanted. Most of this comes down to learning
    the distinction between `[` and `[[` and `sapply()` and `lapply()`.
    It’s not too bad, but it’s a complication.

-   Because they won’t attempt to coerce your inputs to a common type
    and because, unless you count matrices, you cannot nest vectors
    (e.g. `c(c(1, 2), c(3, 4))` is `1:4`), lists are what you’re most
    likely to use when you want to put two or more vectors in one place.
    A lot of your lists will therefore be nested structures. This is not
    inherently a problem, but extracting elements from nested structures
    is hard, both in a general sense and specifically for R’s lists. R
    does little to help you with this. Give
    <https://stackoverflow.com/q/9624169/> and some of its answers a
    read. Why does this simple question get seven different answers? Do
    we really need libraries, anonymous functions, or knowing that `[`
    is a function, just for what ought to be a commonplace operation?

-   Some common R functions do not work properly with lists. Some
    functions like `sort()` and `order()` will not work at all, even if
    you list only contains numbers, and other will work but misbehave.
    For example, what do you expect to get from
    `c(someList, someVectorWithManyElements)`? You might expect a list
    that is now one item longer. Instead, you get your original list
    with every element of the vector appended to it in new slots, i.e. a
    list that is `length(someVectorWithManyElements)` longer.

    ``` r
    c(list(1, 2, 3), LETTERS[1:5])
    ## [[1]]
    ## [1] 1
    ## 
    ## [[2]]
    ## [1] 2
    ## 
    ## [[3]]
    ## [1] 3
    ## 
    ## [[4]]
    ## [1] "A"
    ## 
    ## [[5]]
    ## [1] "B"
    ## 
    ## [[6]]
    ## [1] "C"
    ## 
    ## [[7]]
    ## [1] "D"
    ## 
    ## [[8]]
    ## [1] "E"
    ```

    The same output is given by `append()`. To get
    `list(1, 2, 3, LETTERS[1:5])`, you must do something like
    `x <- list(1, 2, 3); x[[4]] <- LETTERS[1:5]`.

-   Note the use of `[[4]]` and not `[4]` above. Using `[4]` gets you a
    warning and the output `list(1, 2, 3, "A")`. The `[` version is
    intended for cases like `x[4:8] <- LETTERS[1:5]`, which gives the
    same output as `c()` did above. The `[`/`[[` distinction is a
    beginner’s nightmare, as is R’s tendency to give you many ways to do
    the same thing.

-   Primarily due to the commonality of data frames, R has a handful of
    functions that are essentially “*foo, but the list version*”.
    `lapply()` is the most obvious example.

-   A few functions, such as `strsplit()`, can catch you off guard by
    returning a list when there’s no obvious reason why a vector or
    matrix wouldn’t have done. For `strsplit()` in particular, I think
    that the idea is that it’s designed to be used on character vectors
    of lengths greater than one. However, in my experience, I almost
    always want a length-one version. I’d far rather have that function
    and `lapply()`/`sapply()`/whatever it as need be than have to
    constantly use `strsplit("foo")[[1]]`. Similarly, some functions,
    e.g. `merge()`, insist on returning data frames even when the inputs
    were matrices. Coercing these unwanted outputs in to what you
    actually wanted is often harder than it has any right to be.

I think that the ultimate problem with lists is that the right way to
use them is not easy to guess from your knowledge of the language’s
other constructs. If everything in R worked like lists do, or if lists
weren’t so common, then you wouldn’t really mind. As it is, you’ll often
make mistakes with lists and have to guess your way through correcting
them. This isn’t terrible. It’s just annoying.

## 4.2 Strings

R’s strings suck. The overarching problem is that because there is no
language-level distinction between characters vectors and their
individual elements, R’s vectorization means that almost everything that
you want to do with a string needs to be done by knowing the right
function to use (rather than by using R’s ordinary syntax). I find that
the correct functions can be hard to find and use. Although it doesn’t
fix many of these issues, the common sentiment of “*just use
`stringr`/`stringi`*” is difficult to dismiss.

-   Technically, R doesn’t even have a type for strings. You would want
    a string to be a vector of characters, but R’s characters are
    already vectors, so R can’t have a normal string type. Despite this,
    the documentation often uses the word “*string*”. [The language
    definition will tell you how to make sense of
    that](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Vector-objects),
    but I don’t think that information is found anywhere in the sorts of
    documentation that you’ll find in your IDE.

-   It’s a pain to have to account for how R has two types of empty
    string: `character(0)` and `""`.

-   Character vectors aren’t trivially split in to the characters that
    make each element. For example, `"dog"[1]` is `"dog"` because
    `"dog"` is a vector of length one. The idiomatic way to split up a
    string in to its characters – `strsplit("dog", "")` – returns a
    list, so rather than just getting the `"d"` from `"dog"` by doing
    `"dog"[1]`, you have to do something like
    `unlist(strsplit("dog", ""))[1]` or `strsplit("dog", "")[[1]][1]`.
    The `substr()` function can serve you better for trivial jobs, but
    you often need `strsplit()`.

-   Here’s a challenge: Find the function that checks if `"es"` is in
    `"test"`. You’ll be on for a while.

-   Many of R’s best functions for handling strings expect you to know
    regex and are all documented in the same place (grep {base}, titled
    “*Pattern Matching and Replacement*”). If you don’t know regex –
    exactly what I’d expect of R’s target audience – then you’re thrice
    damned:

    -   Firstly, you’re going to have a very hard time figuring out that
        the functions in `?grep` are probably what you need. A glance at
        their documentation suggests that they’re difficult materials
        and therefore presumably not required for your task.
    -   Secondly, you’re going to struggle to find the correct function
        in that documentation because the information that you need is
        surrounded by concepts that are not familiar to you. This
        reinforces your initial impression that you’re in the wrong
        place, letting you stumble over the first point again.
    -   Thirdly and finally, the function names will be meaningless to
        you – “*what the heck does `regexpr()` mean and how does it
        relate to `regexec()`?*” – leaving you with no straws to clutch
        at.

-   Even once you have found the right function for the job, it can be
    tough to use. Compare the `stringr` answer to [this
    question](https://stackoverflow.com/questions/12427385/) to the base
    R answers. Or better yet, use `gregexpr()` or `gregexec()` for any
    task and then tell me with a straight face that you both understand
    their outputs and find them easy to work with.

    ``` r
    gregexpr("a", c("greatgreat", "magic", "not"))
    ## [[1]]
    ## [1] 4 9
    ## attr(,"match.length")
    ## [1] 1 1
    ## attr(,"index.type")
    ## [1] "chars"
    ## attr(,"useBytes")
    ## [1] TRUE
    ## 
    ## [[2]]
    ## [1] 2
    ## attr(,"match.length")
    ## [1] 1
    ## attr(,"index.type")
    ## [1] "chars"
    ## attr(,"useBytes")
    ## [1] TRUE
    ## 
    ## [[3]]
    ## [1] -1
    ## attr(,"match.length")
    ## [1] -1
    ## attr(,"index.type")
    ## [1] "chars"
    ## attr(,"useBytes")
    ## [1] TRUE
    ```

-   The most useful function for printing strings seem to
    counter-intuitively be `cat()` rather than `print()` or `format()`.
    For example, `print()` ignores your `\n` characters. The only time
    where `print()` comes in really handy for string-related stuff is
    when your inputs are either quoted or lists. In both cases,
    `print()` accepts these but `cat()` does not. Without significant
    coercion (mostly `deparse()`), I’ve yet to find a way to mix `\n`
    with quoted input. Most of my attempts to do anything clever that
    mixes printing and lists end with me giving up and using a data
    frame.

-   [Without defining a new
    operator](https://stackoverflow.com/q/4730551/), you can’t add
    strings in the way that other languages have taught you to,
    i.e. `"a"+"b"`. [John Chambers is against fixing
    this](https://www.stat.math.ethz.ch/pipermail/r-devel/2006-August/039004.html).
    I’m not convinced that he’s wrong, but it is annoying.

-   If you’re converting numbers to characters, or using a function like
    `nchar()` that’s meant for characters but accepts numbers, a
    shocking number of things will break when your numbers get big
    enough for R to automatically start using scientific notation.

    ``` r
    nchar(10000)
    ## [1] 5
    nchar(100000)
    ## [1] 5
    a <- 10000
    nchar(a) == nchar(a * 100)
    ## [1] TRUE
    ```

    You’re supposed to use `format()` to coerce these sorts of numbers
    in to characters, but you won’t know about that until something
    breaks and `nchar()`’s documentation doesn’t seem to mention it (try
    `?as.character`). The `format()` function also has a habit of
    requiring you to set the right flags to get what you want.
    `trim = TRUE` comes up a lot. If you’re using a package or
    unfamiliar function, you’re forced to check to see if the author
    dealt with these issues before you use their work. I’d rather just
    have a generic `nchar()`-like function that does what I mean. Would
    you believe that `nchar()`’s documentation says it’s a generic? It’s
    not lying and it later tells you that `nchar()` coerces
    non-characters to characters, but R sure does know how to mess with
    your expectations.

## 4.3 Variable Manipulation

R has some problems with its general facilities for manipulating
variables. Some of the following will be seen **every** time that you
use R.

-   It lacks both `i++` and `x += i`. It also lacks anything that would
    make these unnecessary, such as Python’s `enumerate`.

-   One day, you’ll be tripped up by R’s hierarchy of how it likes to
    simplify mixed types outside of lists. For example, `c(2, "2")`
    returns `c("2", "2")`. [An exercise from *Advanced
    R*](https://adv-r.hadley.nz/vectors-chap.html#exercises-4) presents
    a few troubling cases:

    -   “*Why is `1 == "1"` true?*”
    -   “*Why is `-1 < FALSE` true?*”
    -   “*Why is `"one" < 2` false?*”.

-   To get complete information about the typing and structure of
    something, you will almost certainly need to call several functions.
    For example, do any of the following tell you everything about `x`?

    ``` r
    x <- diag(3)
    x
    ##      [,1] [,2] [,3]
    ## [1,]    1    0    0
    ## [2,]    0    1    0
    ## [3,]    0    0    1
    typeof(x)
    ## [1] "double"
    class(x)
    ## [1] "matrix" "array"
    attributes(x)
    ## $dim
    ## [1] 3 3
    str(x)
    ##  num [1:3, 1:3] 1 0 0 0 1 0 0 0 1
    ```

-   R likes to use “*double*” and “*numeric*” almost interchangeably.
    You’ve just seen one such example (`str(x)` vs `typeof(x)`).

-   Integers are almost second class. `?integer` suggests that they’re
    mostly for talking to other languages, but the problem seems to go
    deeper than that. It’s as if R tries to avoid integers unless you
    tell it not to. For example, `4` is a double, not an integer. Why?
    Unless you’re very careful, any integer that you give to R will
    eventually be coerced in to a double.

-   I don’t like how there’s no trivial way to express a condition like
    1 &lt; x &lt; 5. In a maths language, I’d expect that exact syntax
    to work. There’s probably a good reason why it doesn’t, and it’s not
    at all hard to build an equivalent condition, but it still annoys me
    from time to time. I suspect that the `<-` syntax for variable
    assignment is to blame.

-   The distinction between `<-` and `=` is something that you’d have to
    look up. I’d try to explain the difference, but from what I’ve
    gathered, the difference only matters when using `=` rather than
    `<-` causes bugs. Like most R users, I’ve picked up the habit of
    “*use `=` only for the arguments of functions and use `<-`
    everywhere else*”.

-   `<-` was designed for keyboards that don’t exist any more. It’s a
    pain to type on a modern system.

-   The day that you accidentally have `<` rather than `<-` without it
    throwing an error will be an awful one. The reverse can also happen.
    For example, there are two things that you could have meant by
    `if(x<-2)`.

-   `Y<--2` is a terrible way to have to say “*set `Y` to be equal to
    negative two*”. `Y<<--2` is even worse.

-   `<<-` is probably the only good thing about the convention of using
    `<-`, but it’s only useful if you either know what a closure is and
    have reason to use one or if you’re some sort of guru with R’s
    first-class environments. You can sometimes use `<<-` to great
    effect without deliberately writing a closure, but it always feels
    like a hack because you’re implicitly using one. For example,
    `replicate(5, x <- x+1)` and `replicate(5, x <<- x+1)` are very
    different, with the `<<-` case being a very cool trick,

    ``` r
    x <- 1
    replicate(5, x <- x+1)
    ## [1] 2 2 2 2 2
    x
    ## [1] 1
    replicate(5, x <<- x+1)
    ## [1] 2 3 4 5 6
    x
    ## [1] 6
    ```

    but it only works because `replicate()` quietly wraps its second
    argument in an anonymous function.

-   The idiomatic way to add an item to the end of a collection is
    `a[length(a) + 1] <- "foo"`. This is rather verbose. It’s also [a
    bit unpredictable when adding a collection to a list](#41-lists).

-   A quote from [the language
    definition](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Argument-evaluation):
    “*supplied arguments and default arguments are treated
    differently*”. This usually doesn’t trip you up, but you’re certain
    to discover it on the first day that you use `eval()`. It has
    `parent.frame()` as one of its default arguments, but calling
    `eval()` with that argument supplied manually will produce different
    results than what you get from letting it be supplied by default.

    ``` r
    x <- 1
    (function(x) eval(quote(x + 1)))(100)
    ## [1] 101
    (function(x) eval(quote(x + 1), envir = parent.frame()))(100)
    ## [1] 2
    ```

    An easier-to-discover example can be found in section 8.3.19 of
    [*The R
    Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf).

-   Variable names can be partially matched. See
    <a href="https://rosettacode.org/wiki/Named_parameters\#R" class="uri">https://rosettacode.org/wiki/Named_parameters\#R</a>
    for some examples. I can’t tell if it’s disgusting or awesome, but
    it’s definitely dangerous. If I called `f(n = 1)`, I probably didn’t
    mean `f(nukeEarth = 1)`! At least it throws an error if it fails to
    partially match (e.g. if there were multiple valid partial matches).
    More on that [when I cover the `$` operator](#dangers-of-), which
    usually has the same issue.

-   The `...` argument doesn’t make its users throw errors when they’ve
    been called with arguments that they don’t have or, even worse,
    those that they do have, but you misspelled. *Advanced R* has a
    great example in [its Functions
    chapter](https://adv-r.hadley.nz/functions.html#exercises-17). Would
    you have guessed that `sum(1, 2, 3, na.omit = TRUE)` returns `7`,
    not `6`? Similarly, [the Functionals
    chapter](https://adv-r.hadley.nz/functionals.html#argument-names)
    shows how this can lead to some baffling errors and what strange
    things you have to do help your users avoid them.

-   For many other examples, see section 8 of [*The R
    Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf).

## 4.4 Switch

R has some strange ideas about switch statements:

-   It’s not a special form of any kind; Its syntax is that of a normal
    function call. If I’m being consistent in my formatting, then I
    should be calling it “*R’s `switch()` function*”.

-   It’s only [about 70 lines of C
    code](https://github.com/wch/r-source/blob/trunk/src/main/builtin.c#L1009),
    suggesting that it can’t be all that optimised.

-   R doesn’t have one switch statement, it has two. One where it
    switches on a numeric input and another for characters. The numeric
    version makes the strange assumption that the first argument
    (i.e. the argument being switched on) can be safely translated to a
    set of cases that must follow an ordering like “*if input is 1, do
    the first option, if 2, do the second…*”. There is no flexibility
    like letting you start at 2, having jumps higher than 1, or letting
    you supply a default case. Reread that last one: R has a switch
    without defaults! It’s frankly the worst switch that I’ve ever seen.
    The other version, the one that switches on characters, is more
    sensible. I’d give examples, but I don’t know how to demonstrate a
    non-feature.

-   As is a trend in R, both versions of switch are capable of silently
    doing nothing. For example, these do nothing:

    ``` r
    switch(3, "foo", "bar")
    switch("c", a = "foo", b = "bar")
    print(switch("c", a = "foo", b = "bar")) #Showing off the return value.
    ## NULL
    ```

    and they do it silently, returning `NULL`. I’d expect a warning
    message informing me of this, but there is no such thing. If you
    want that behaviour, then you have to write it yourself by ending
    each statement with a final unnamed branch that throws an error,
    e.g. `switch("c", a = "foo", b = "bar", stop("Invalid input"))` or
    `switch("c", a = "foo", b = "bar", warning("Invalid input"))`. Of
    course, you can’t do that with the numeric version, because R has a
    switch without defaults.

## 4.5 Subsetting

Now for the nasty stuff. R’s rules for selecting elements, deleting
elements, and any other sort of subsetting require mastery. They’re
extremely powerful once mastered, but until that point, they make using
R a nightmare. For a stats language, this is unforgivable. Before
mentioning any points that are best put in their own subsections, I’ll
cover some more general points:

-   You never quite know whether you want to use `x`, the name of `x`,
    or a function like `subset()`, `which()`, `Find()`, `Position()`, or
    `match()`. R’s operators make this even more of mess. You either
    want `$`, `[`, `@` or even `[[`. Making the wrong choice of `[x]`,
    `[x,]`, `[,x]` or `[[x]]` is another frequent source of error. You
    will get used to it eventually, but your hair will not survive the
    journey. [Similar
    stories](https://www.talyarkoni.org/blog/2012/06/08/r-the-master-troll-of-statistical-languages/)
    can be found about the apply family.

-   The `[[` operator has been accused of inconsistent behaviour.
    [*Advanced R* covers this better than I
    could](https://adv-r.hadley.nz/subsetting.html#subsetting-oob). The
    short version is that it sometimes returns `NULL` and other times
    throws an error. Personally, I’ve never noticed these because I’ve
    rarely tried to subset `NULL` and I don’t see any reason why you
    would use `[[` on an atomic vector. As far as I know, `[` does the
    same job. The only exception that I can think of is if your atomic
    vector was named. For example:

    ``` r
    a <- c(Alice = 1, Bob = 2)
    a["Alice"]
    ## Alice 
    ##     1
    a[["Alice"]]
    ## [1] 1
    ```

-   When doing variable assignment on anything more than
    one-dimensional, `object` and `object[]` behave differently when you
    try to assign variables to them. Compare:

    ``` r
    (c <- b <- diag(3))
    ##      [,1] [,2] [,3]
    ## [1,]    1    0    0
    ## [2,]    0    1    0
    ## [3,]    0    0    1
    b[] <- 5
    c <- 5
    b
    ##      [,1] [,2] [,3]
    ## [1,]    5    5    5
    ## [2,]    5    5    5
    ## [3,]    5    5    5
    c
    ## [1] 5
    ```

    This kind of makes sense, but it will trip you up.

-   The syntax for deleting elements of collections by index can be
    rather verbose. You can’t just pop out an element, you have to write
    `vect <- vect[-index]` or `vect <- vect[-c(index, nextIndex, ...)]`.

-   R is 1-indexed, but accessing element 0 of a vector gives an empty
    vector rather than an error. This probably makes sense considering
    that index -1 deletes element 1, but it’s a clear source of major
    errors.

-   With the sole exception of environments, every named object in R is
    allowed to have duplicate names. I guarantee that will one day break
    your subsetting (e.g. see section 8.1.19 of [*The R
    Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf)).
    Fortunately, the constructor for data frames has a `check.names`
    argument that corrects duplicates by default. Unfortunately, it does
    this silently, so you may not notice that some of your column names
    have been changed. Another oddity is that many functions that work
    on data frames, most notably `[`, will silently correct duplicated
    names even if you told the original data frame to not do so. Why
    even let me have duplicated names if you’re going to make it so hard
    to keep them?

    ``` r
    data.frame(x = 1:3, x = 11:13)
    ##   x x.1
    ## 1 1  11
    ## 2 2  12
    ## 3 3  13
    #Notice the x.1? You didn't ask for that. To get x twice, you need this:
    correctNames <- data.frame(x = 1:3, x = 11:13, check.names = FALSE)
    correctNames
    ##   x  x
    ## 1 1 11
    ## 2 2 12
    ## 3 3 13
    correctNames[1:3, ]#As expected.
    ##   x  x
    ## 1 1 11
    ## 2 2 12
    ## 3 3 13
    correctNames[1:2]#What?
    ##   x x.1
    ## 1 1  11
    ## 2 2  12
    ## 3 3  13
    ```

    Not only is this behaviour inconsistent, it is **silent**; No
    warnings or errors are thrown by the above code. Tibbles are much
    better about this:

    ``` r
    library(tibble)
    #We can't repeat our original first line, because tibble(x = 1:5, x = 11:15) throws an error:
    ## > tibble(x = 1:5, x = 11:15)
    ## Error: Column name `x` must not be duplicated.
    ## Use .name_repair to specify repair.
    #We follow the error's advice.
    #The .name_repair argument provides a few useful options, so we must pick one.
    correctNames <- tibble(x = 1:5, x = 11:15, .name_repair = "minimal")
    correctNames
    ## # A tibble: 5 × 2
    ##       x     x
    ##   <int> <int>
    ## 1     1    11
    ## 2     2    12
    ## 3     3    13
    ## 4     4    14
    ## 5     5    15
    correctNames[1:3,]#Good
    ## # A tibble: 3 × 2
    ##       x     x
    ##   <int> <int>
    ## 1     1    11
    ## 2     2    12
    ## 3     3    13
    correctNames[1:2]#Still good!
    ## # A tibble: 5 × 2
    ##       x     x
    ##   <int> <int>
    ## 1     1    11
    ## 2     2    12
    ## 3     3    13
    ## 4     4    14
    ## 5     5    15
    ```

    This may seem like an isolated example, but there’s more to this
    than I’m really letting on. A related example is that the
    `check.names` argument in `data.frame()` is very insistent on
    silently doing things, even to the point of overruling arguments
    that you explicitly set. For example, I’m pretty sure that these
    column names aren’t what I asked for.

    ``` r
     as.data.frame(list(1, 2, 3, 4, 5), col.names = paste("foo=bar", 6:10))
    ##   foo.bar.6 foo.bar.7 foo.bar.8 foo.bar.9 foo.bar.10
    ## 1         1         2         3         4          5
     as.data.frame(list(1, 2, 3, 4, 5), col.names = paste("foo=bar", 6:10), check.names = FALSE)
    ##   foo=bar 6 foo=bar 7 foo=bar 8 foo=bar 9 foo=bar 10
    ## 1         1         2         3         4          5
    ```

    As far as I can tell, it’s doing this in order to make the names
    suitable for subsetting – subsetting with non-unique or
    non-syntactic column names could be a pain – but the decision to not
    inform the user of this correction is baffling. Even if you’re
    fortunate enough to have noticed the silent change to your data, the
    lack of a warning message will leave you with no idea how to correct
    it. You could perhaps argue that duplicated names are the user’s
    fault and they deserve what they get, but that argument falls apart
    for non-syntactic names. Who hasn’t put a space or an equals sign in
    their column names before? Mind, tibbles aren’t much better when it
    comes to non-syntactic names. Neither `tibble("Example col" = 4)`
    nor `data.frame("Example col" = 4)` warn you of the name change.

-   For what I believe to be memory reasons, objects of greater than one
    dimension are stored in column order rather than row order. Quick,
    what output do you expect from `matrix(1:9, 3, 3)`?

    ``` r
    matrix(1:9, 3, 3)
    ##      [,1] [,2] [,3]
    ## [1,]    1    4    7
    ## [2,]    2    5    8
    ## [3,]    3    6    9
    ```

    This gives us a matrix with first row `c(1, 4, 7)`. This goes
    against the usual English convention of reading from left to right.
    It is also inconsistent with functions like `apply()`, where
    `MARGIN = 1` corresponds to their by-row version and `MARGIN = 2` is
    for by-column (if R privileges columns, shouldn’t they be the `= 1`
    case?). This means that you can never really be sure if R is working
    in column order or row order. This is bad enough on its own, but it
    can also be a source of subtle bugs when working with matrices. Many
    mathematical functions don’t see any difference between a matrix and
    its transpose.

-   There is no nice way to access the last element of a vector. Of all
    things, the idiomatic way is `x[length(x)]`. The only good part of
    this is that `x[length(x) - 0:n]` is a very nice way to get the last
    `n + 1` elements. You could use `tail()`, but Stack Overflow tells
    me it’s very slow.

-   The `sort()` and `order()` functions are the main ways to sort stuff
    in R. If you’re trying to sort some data by a particular variable,
    then R counter-intuitively wants you to use `order()` rather than
    `sort()`. The syntax for `order()` doesn’t help matters. It returns
    a permutation, so rather than `order(x, params)`, you will want
    `x[order(params),]`. My only explanation for this is that it makes
    `order()` much easier to use with the `with()` function. For
    example, `data[with(data, order(col1, col2, col3)),]` is perhaps
    more pleasant to write than the hypothetical
    `order(data, data$col1, data$col2, data$col3)`. The Tidyverse’s
    `dplyr` solves these problems:
    `dplyr::arrange(data, col1, col2, col3)` does what you think. I’d
    much rather use `arrange(mtcars, cyl, disp)` than
    `mtcars[with(mtcars, order(cyl, disp)),]`.

-   The `order()` case above illustrates another frequent annoyance with
    subsetting. Rather than asking for what you want, you often need to
    generate a vector that matches up to it. A collection of booleans (R
    calls these “*logical vectors*”) is one of the most common ways to
    do this, with `duplicated()` being a typical example.

    ``` r
    head(Nile)
    ## [1] 1120 1160  963 1210 1160 1160
    duplicated(head(Nile))
    ## [1] FALSE FALSE FALSE FALSE  TRUE  TRUE
    head(Nile)[duplicated(head(Nile))]
    ## [1] 1160 1160
    ```

    This means that you will usually be asking for `items[bools]` (and
    maybe `[,bools]` or `[bools,]`…) in order to get the items that you
    want. There is great power in being able to do this, but having to
    do it is annoying and can catch you off guard. For example, what do
    you expect `lower.tri()` to return when called on a matrix? What you
    wanted from `lower.tri(mat)` is probably what you get from
    `mat[lower.tri(mat)]`. Also, don’t expect a helpful error message if
    your construction of `bools` is wrong. As I’ll discuss later on,
    [the vector recycling](#46-vectorization-again) rules will often
    make an incorrect construction give sensible-looking output.

-   For reasons that I cannot explain, `aperm(x, params)` is the correct
    syntax, not `x[aperm(params)]` or anything like it. I think that
    it’s trying to be consistent with R’s ideas of how to manipulate
    matrices, but it’s yet another source of confusion: I don’t want to
    have to think about if I’m treating my data like a matrix or like a
    data frame.

-   Good luck trying to figure out how to find a particular sequence of
    elements within a vector. For example, try finding if/where the
    unbroken vector `1:3` has occurred in
    `sample(6, 100, replace = TRUE)`. You’re best off just writing the
    `for` loop.

### 4.5.1 Combining Operators

This one isn’t too bad, but it’s worth a mention. Combining operations
can lead to some counter-intuitive results:

-   If `a <- 1:5`, what do you expect to get from `a[-1] <- 12:15`? Do
    you expect `a[1]` to be removed or not? This is great once you know
    how it works, but it’s confusing to a beginner.

    ``` r
    a <- 1:5
    a[-1] <- 12:15
    a
    ## [1]  1 12 13 14 15
    ```

-   Because `data[-index]` can be used to remove elements and
    `data["colName"]` can be used to select elements, you might expect
    `data[-"colName"]` or `data[-c("colName1", "colName2")]` to work.
    You would be wrong. Both throw errors.

    ``` r
    ## > mtcars[-"wt"]
    ## Error in -"wt" : invalid argument to unary operator
    ```

-   Attempting to remove both by index and by name at the same time will
    never work. For example, `mtcars[-c(1, "cyl")]` is an error and
    `mtcars[c(1, "cyl")] <- NULL` will only remove the `cyl` variable.
    Weirdly enough, I can’t actually show this
    `mtcars[c(1, "cyl")] <- NULL` example. R is perfectly happy to show
    it, but R Markdown isn’t. What happens is that `c(1, "cyl")` is
    coerced to `c("1", "cyl")`. After this, R does not inform you that
    there is no `1` column to remove.

-   Selecting and deleting at the same time doesn’t work either. For
    example, `data[c(-1, 5)]` is an error.

    ``` r
    ## > Nile[c(-1, 5)]
    ## Error in `[.default`(Nile, c(-1, 5)) : 
    ##   only 0's may be mixed with negative subscripts
    ```

Now for the serious stuff…

### 4.5.2 Removing Dimensions

This issue is notorious: R likes to remove unnecessary dimensions from
your data in ways that are not easily predicted, forcing you to waste
time preventing them. Rumour has it that this can be blamed on S being
designed as a calculator rather than as a programming language. I can’t
cite that, but it’s easy to believe. No programmer would include any of
the below in a programming language.

-   Unless you add `, drop=FALSE` to all of your data selection/deletion
    lines, you run the risk of having all of your code that expects your
    data to have a particular structure unexpectedly break. This gives
    no errors or warnings. Compare:

    ``` r
    (mat <- cbind(1:4, 4:1))
    ##      [,1] [,2]
    ## [1,]    1    4
    ## [2,]    2    3
    ## [3,]    3    2
    ## [4,]    4    1
    mat[, -1]
    ## [1] 4 3 2 1
    mat[, -1, drop=FALSE]
    ##      [,1]
    ## [1,]    4
    ## [2,]    3
    ## [3,]    2
    ## [4,]    1
    ```

    and you will see that one of these is not a matrix. Data frames have
    the same issue unless you do all of your subsetting in a 1D form.

    ``` r
    mat <- cbind(1:4, 4:1)
    (frame <- as.data.frame(mat))
    ##   V1 V2
    ## 1  1  4
    ## 2  2  3
    ## 3  3  2
    ## 4  4  1
    frame[, -1]
    ## [1] 4 3 2 1
    frame[, -1, drop=FALSE]
    ##   V2
    ## 1  4
    ## 2  3
    ## 3  2
    ## 4  1
    frame[-1]#1D subsetting
    ##   V2
    ## 1  4
    ## 2  3
    ## 3  2
    ## 4  1
    ```

    The Tidyverse, specifically `tibble`, does its best to remove this.

    ``` r
    library(tibble)
    mat <- cbind(1:4, 4:1)
    (tib <- as_tibble(mat))
    ## Warning: The `x` argument of `as_tibble.matrix()` must have unique column names if `.name_repair` is omitted as of tibble 2.0.0.
    ## Using compatibility `.name_repair`.
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was generated.
    ## # A tibble: 4 × 2
    ##      V1    V2
    ##   <int> <int>
    ## 1     1     4
    ## 2     2     3
    ## 3     3     2
    ## 4     4     1
    tib[, -1]
    ## # A tibble: 4 × 1
    ##      V2
    ##   <int>
    ## 1     4
    ## 2     3
    ## 3     2
    ## 4     1
    tib[, -1, drop=FALSE]
    ## # A tibble: 4 × 1
    ##      V2
    ##   <int>
    ## 1     4
    ## 2     3
    ## 3     2
    ## 4     1
    tib[-1]
    ## # A tibble: 4 × 1
    ##      V2
    ##   <int>
    ## 1     4
    ## 2     3
    ## 3     2
    ## 4     1
    tib[, -1, drop=TRUE]
    ## [1] 4 3 2 1
    ```

    You can think of tibbles as having `drop=FALSE` as their default. I
    can’t explain why base R doesn’t do the same. It’s got to either be
    some sort of compromise for matrix algebra or for making working in
    your console nicer.

-   The `drop` argument is even stranger than I’m letting on. Its
    defaults differ depending on whether there may only be one column
    remaining or if there may only be one row. To quote the
    documentation (`?"[.data.frame"`): “*The default is to drop if only
    one column is left, but **not** to drop if only one row is left*”.
    Unlike the previous point, I can sort of make sense of this. For
    example, a single column can only ever be one type (even if that may
    be a container for mixed types, such as a list) but a single row
    could easily be a mix of types. Dropping on a row of mixed types
    will just give you a really ugly list, so you’d much rather have a
    data frame. With a column, it’s only with years of experience that
    the community has realised that they probably still want the data
    frame; It’s nowhere near as obvious that the vector is not
    preferable.

-   As you can tell by taking a close look at the documentation for `[`
    and that of `[.data.frame`, the `drop` argument does not do the same
    thing for arrays and matrices as it does for data frames. This means
    that my earlier example could be dishonest. However, the confusion
    that you would need to overcome in order to check for if I’ve been
    dishonest is so great that it proves that there’s definitely
    something wrong with the `drop` argument.

-   You may think that `object` and `object[,]` are the same thing. They
    are not. You would expect and get an error if `object` is
    one-dimensional. However, if it’s a data frame or matrix with one of
    its dimensions having size 1, then you do not get an error and both
    `object` and `object[,]` are very different.

    ``` r
    library(tibble)
    colMatrix <- matrix(1:3)
    colMatrix
    ##      [,1]
    ## [1,]    1
    ## [2,]    2
    ## [3,]    3
    colMatrix[,]
    ## [1] 1 2 3
    rowMatrix <- matrix(1:3, ncol = 3)
    rowMatrix
    ##      [,1] [,2] [,3]
    ## [1,]    1    2    3
    rowMatrix[,]
    ## [1] 1 2 3
    colFrame <- as.data.frame(colMatrix)
    colFrame
    ##   V1
    ## 1  1
    ## 2  2
    ## 3  3
    colFrame[,]
    ## [1] 1 2 3
    rowFrame <- as.data.frame(rowMatrix)
    rowFrame
    ##   V1 V2 V3
    ## 1  1  2  3
    rowFrame[,]
    ##   V1 V2 V3
    ## 1  1  2  3
    colTib <- as_tibble(colMatrix)
    colTib
    ## # A tibble: 3 × 1
    ##      V1
    ##   <int>
    ## 1     1
    ## 2     2
    ## 3     3
    colTib[,]
    ## # A tibble: 3 × 1
    ##      V1
    ##   <int>
    ## 1     1
    ## 2     2
    ## 3     3
    rowTib <- as_tibble(rowMatrix)
    rowTib
    ## # A tibble: 1 × 3
    ##      V1    V2    V3
    ##   <int> <int> <int>
    ## 1     1     2     3
    rowTib[,]
    ## # A tibble: 1 × 3
    ##      V1    V2    V3
    ##   <int> <int> <int>
    ## 1     1     2     3
    ```

    Can you guess why? It’s because the use of `[` makes R check if it
    should be dropping dimensions. This makes `object` and
    `object[,,drop=FALSE]` equivalent, whereas `object[,]` is a vector
    rather than whatever it was originally. Tibbles, of course, don’t
    have this issue.

-   If you’ve struggled to read this section, then you’re probably now
    aware of another point: It’s really easy to get the commas for
    `drop=FALSE` mixed up. What do you think that you get if you try to
    select `data[4, drop=FALSE]`? If `data` is a data frame, you get
    column 4 and a warning that the `drop` argument was ignored. Did you
    expect row 4? Whether you did or not, you should be able to see why
    somebody may come to the opposite answer. Although I see no sensible
    alternative, the `drop` argument needing its own comma is terrible
    syntax for a language where a stray comma is the difference between
    your data’s life and death. This is made even worse by the syntax
    for `[` occasionally needing stray commas. Expressions like
    `data[4,]` are commonplace in R, so it’s far too easy to forget that
    you needed the extra comma for the `drop` argument.

### 4.5.3 Dangers of $

The `$` operator is both silently hazardous and redundant:

-   As an S3 generic, you can never be certain that `$` does what you
    want it to when you use it on a class from a package. For example,
    it’s common knowledge that base R’s `$` and the Tidyverse’s `$` are
    not the same thing. In fact, `$` does not even behave consistently
    in base R. Compare the following partial matching behaviour:

    ``` r
    library(tibble)
    list(Bob = 5, Dobby = 7)$B
    ## [1] 5
    env <- list2env(list(Bob = 5, Dobby = 7))
    env$B
    ## NULL
    data.frame(Bob = 5, Dobby = 7)$B
    ## [1] 5
    tibble(Bob = 5, Dobby = 7)$B
    ## Warning: Unknown or uninitialised column: `B`.
    ## NULL
    ```

    For what it’s worth, replacing `Dobby` with `Bobby` gives more
    consistent results.

    ``` r
    library(tibble)
    list(Bob = 5, Bobby = 7)$B
    ## NULL
    env <- list2env(list(Bob = 5, Bobby = 7))
    env$B
    ## NULL
    data.frame(Bob = 5, Bobby = 7)$B
    ## NULL
    tibble(Bob = 5, Bobby = 7)$B
    ## Warning: Unknown or uninitialised column: `B`.
    ## NULL
    ```

    In theory, I should note that `[` and `[[` are also S3 generics and
    therefore should share this issue. In practice, I rarely notice such
    misbehaviour.

-   Consistency aside, partial matching is inherently dangerous.
    `data$Pen` might give the `Penetration` column if you forgot that
    you removed the `Pen` column. By default, R does not give you any
    warnings when partial matches happen, so you won’t have any idea
    that you got the wrong column.

-   The documentation for `$` points out its redundancy in base R:
    “*`x$name` is equivalent to `x[["name", exact = FALSE]]`*”. In other
    words, even if I want the behaviour of `$`, I can get it with `[[`.
    Another benefit of `[[` is that it will only partially match if you
    tell it to (use `exact = FALSE`). That matters because…

-   The partial matching of `$` can be even worse than I’ve just
    described. If there are multiple valid partial matches, rather than
    get any of them, you get `NULL`. This is what happened with the
    Bob/Bobby example above. To give another example, `mtcars$di` and
    `mtcars$dr` both give sensible output because there is only one
    valid partial match, but `mtcars$d` is just `NULL`. I’m largely okay
    with this behaviour, but you don’t even get a warning!

    ``` r
    mtcars$di
    ##  [1] 160.0 160.0 108.0 258.0 360.0 225.0 360.0 146.7 140.8 167.6 167.6 275.8
    ## [13] 275.8 275.8 472.0 460.0 440.0  78.7  75.7  71.1 120.1 318.0 304.0 350.0
    ## [25] 400.0  79.0 120.3  95.1 351.0 145.0 301.0 121.0
    mtcars$dr
    ##  [1] 3.90 3.90 3.85 3.08 3.15 2.76 3.21 3.69 3.92 3.92 3.92 3.07 3.07 3.07 2.93
    ## [16] 3.00 3.23 4.08 4.93 4.22 3.70 2.76 3.15 3.73 3.08 4.08 4.43 3.77 4.22 3.62
    ## [31] 3.54 4.11
    mtcars$d
    ## NULL
    ```

-   Tibbles try to fix the partial-matching issues of `$` by completely
    disallowing partial matching. They will not partially match even if
    you tell them to with `[[, exact=FALSE]]`. If you try to partially
    match anyway, it will give you a warning and return `NULL`. I
    sometimes wonder if it should be an error.

    ``` r
    library(tibble)
    mtTib <- as_tibble(mtcars)
    mtTib$di
    ## Warning: Unknown or uninitialised column: `di`.
    ## NULL
    mtTib$dr
    ## Warning: Unknown or uninitialised column: `dr`.
    ## NULL
    mtTib$d
    ## Warning: Unknown or uninitialised column: `d`.
    ## NULL
    mtcars[["d", exact = FALSE]]
    ## NULL
    mtTib[["d", exact = FALSE]]
    ## Warning: `exact` ignored.
    ## NULL
    ```

-   On the base R side, there is a global option that you can set to
    make `$` give you warnings whenever partial matching happens. It’s
    disabled by default. Common sense suggests that it should be
    otherwise.

-   The `$` operator is another case of R quietly changing your data
    structures. For example, I would call `mtcars$mpg` unreadable.

    ``` r
    mtcars$mpg
    ##  [1] 21.0 21.0 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 17.8 16.4 17.3 15.2 10.4
    ## [16] 10.4 14.7 32.4 30.4 33.9 21.5 15.5 15.2 13.3 19.2 27.3 26.0 30.4 15.8 19.7
    ## [31] 15.0 21.4
    typeof(mtcars$mpg)
    ## [1] "double"
    ```

    You probably wanted `mtcars["mpg"]`

    ``` r
    mtcars["mpg"]
    ##                      mpg
    ## Mazda RX4           21.0
    ## Mazda RX4 Wag       21.0
    ## Datsun 710          22.8
    ## Hornet 4 Drive      21.4
    ## Hornet Sportabout   18.7
    ## Valiant             18.1
    ## Duster 360          14.3
    ## Merc 240D           24.4
    ## Merc 230            22.8
    ## Merc 280            19.2
    ## Merc 280C           17.8
    ## Merc 450SE          16.4
    ## Merc 450SL          17.3
    ## Merc 450SLC         15.2
    ## Cadillac Fleetwood  10.4
    ## Lincoln Continental 10.4
    ## Chrysler Imperial   14.7
    ## Fiat 128            32.4
    ## Honda Civic         30.4
    ## Toyota Corolla      33.9
    ## Toyota Corona       21.5
    ## Dodge Challenger    15.5
    ## AMC Javelin         15.2
    ## Camaro Z28          13.3
    ## Pontiac Firebird    19.2
    ## Fiat X1-9           27.3
    ## Porsche 914-2       26.0
    ## Lotus Europa        30.4
    ## Ford Pantera L      15.8
    ## Ferrari Dino        19.7
    ## Maserati Bora       15.0
    ## Volvo 142E          21.4
    typeof(mtcars["mpg"])
    ## [1] "list"
    ```

    and you definitely did not want `mtcars[, "mpg"]` or
    `mtcars[["mpg"]]`, which both give the same output as using `$`.

    ``` r
    mtcars[, "mpg"]
    ##  [1] 21.0 21.0 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 17.8 16.4 17.3 15.2 10.4
    ## [16] 10.4 14.7 32.4 30.4 33.9 21.5 15.5 15.2 13.3 19.2 27.3 26.0 30.4 15.8 19.7
    ## [31] 15.0 21.4
    mtcars[["mpg"]]
    ##  [1] 21.0 21.0 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 17.8 16.4 17.3 15.2 10.4
    ## [16] 10.4 14.7 32.4 30.4 33.9 21.5 15.5 15.2 13.3 19.2 27.3 26.0 30.4 15.8 19.7
    ## [31] 15.0 21.4
    ```

    Would you have guessed that? Tibbles share the above behaviour with
    `$` and `[[`, but keep `["name"]` and `[, "name"]` identical due to
    their promise to not drop dimensions with `[`.

-   The `$` operator does not have any uses beyond selection. For
    example, there is no way to combine `$` with operators like `-` and
    there’s no way to pass arguments like `drop=FALSE` to it.

-   `$` is not allowed for atomic vectors like `c(fizz=3, buzz=5)`,
    unlike `[` and `[[`. This is particularly annoying when dealing with
    named matrices because you end up having to use `mat[, "x"]` where
    `mat$x` should have done.

-   Section 8.1.21 of [*The R
    Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf):
    There exists a `$<-` operator. You hardly ever see it used. [*The R
    Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf)
    points out that it does not do partial matching, even for lists,
    unlike `$`. This is actually documented behaviour – in fact,
    `?Extract` mentions it twice – but I challenge you to find it. I can
    see why it would be difficult to make a `$<-` with partial matching,
    but making `$<-` inconsistent with `$` is just laughable.

In conclusion, once you know the difference between `["colname"]` and
`[, "colname"]`, `$` is only useful if it’s making your code cleaner,
saving you typing, or if you actually want the partial matching.
Personally, I’m uncomfortable with the inherent risks of partial
matching, so `$` is only really useful for interactive use and my IDE’s
auto-completion. That might even be its intended job. But if that is the
case, nobody warns you of it.

### 4.5.4 Indistinguishable Errors

When dealing with any sort of collection, any of the following mistakes
can give indistinguishable results. This can make your debugging so
messy that by the time that you’re done, you don’t know what was broken.

-   Trying to select an incorrect sequence of elements. This can be
    caused by `:` or `seq()` misbehaving or by simple user error. [A
    tiny bit more on that later](#4111-sequences)

-   The vector recycling rules silently causing the vector that you used
    to select elements to be recycled in an undesired way. [More on that
    later](#46-vectorization-again).

-   Selecting an out-of-bounds value. You almost always don’t get any
    error or warning when you do this. For example, both out-of-bounds
    positive numbers and logical vectors that are longer than the vector
    that you’re subsetting silently return `NA` for the inappropriate
    values.

    ``` r
    length(LETTERS)
    ## [1] 26
    LETTERS[c(1, 5, 20, 100)]
    ## [1] "A" "E" "T" NA
    LETTERS[rep(TRUE, 100)]
    ##   [1] "A" "B" "C" "D" "E" "F" "G" "H" "I" "J" "K" "L" "M" "N" "O" "P" "Q" "R"
    ##  [19] "S" "T" "U" "V" "W" "X" "Y" "Z" NA  NA  NA  NA  NA  NA  NA  NA  NA  NA 
    ##  [37] NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA 
    ##  [55] NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA 
    ##  [73] NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA  NA 
    ##  [91] NA  NA  NA  NA  NA  NA  NA  NA  NA  NA
    ```

    Again, as with many of the issues that we’ve mentioned recently,
    **this happens silently**.

-   Accessing/subsetting a collection in the wrong way. For example,
    wrongly using any of `[c(x, y)]`, `[x, y]`, or `[cbind(x, y)]`,
    selecting `[x]` rather than `[x, ]`, `[[x]]`, or `[, x]`, using the
    wrong `rbind()/cbind()`, or an error in your call to anything like
    `subset()` or `within()`.

-   Selecting element 0.

-   Any sort of off-by-one errors, e.g. a modulo mistake of any sort,
    genuine off-by-one errors, or R’s 1-indexing causing you to trip up.

-   Misuse of searching functions like `which()`, `duplicated()`, or
    `match()`.

This list also reveals another issue with subsetting: There’s too many
ways to do it…

### 4.5.5 Named Atomic Vectors

…and they don’t all work everywhere. For example, there’s a wide range
of tools for using names to work with lists and data frames, but very
few of them work for named atomic vectors (which includes named
matrices).

-   The `$` operator simply does not work.

-   Although `namedVector["name"]` can be used for subsetting and
    subassignment, `namedVector["name"] <- NULL` throws an error. For a
    list or data frame, this would have deleted the selected data
    points.

    ``` r
    typeof(letters)
    ## [1] "character"
    named <- setNames(letters, LETTERS)
    tail(named)
    ##   U   V   W   X   Y   Z 
    ## "u" "v" "w" "x" "y" "z"
    named["Z"]
    ##   Z 
    ## "z"
    named["Z"] <- "Super!"
    tail(named)
    ##        U        V        W        X        Y        Z 
    ##      "u"      "v"      "w"      "x"      "y" "Super!"
    #So subsetting and subassignment work just fine. However, for NULL...
    ## > named["Z"] <- NULL
    ## Error in named["Z"] <- NULL : replacement has length zero
    #But for a data frame, this is just fine.
    (data <- data.frame(A = 1, B = 2, Z = 3))
    ##   A B Z
    ## 1 1 2 3
    data["Z"] <- NULL
    data
    ##   A B
    ## 1 1 2
    ```

    Incidentally, `anyAtomicVector[index] <- NULL` is also an error.
    e.g. `LETTERS[22] <- NULL`.

-   Sorry, did I say that `namedVector["name"]` works for subsetting?

    ``` r
    a <- diag(3)
    colnames(a) <- LETTERS[1:3]
    a
    ##      A B C
    ## [1,] 1 0 0
    ## [2,] 0 1 0
    ## [3,] 0 0 1
    a["A"]
    ## [1] NA
    a["Z"]
    ## [1] NA
    ```

    Long story short, named atomic vectors make a distinction between
    names and colnames that data frames do not.

    ``` r
    a <- diag(3)
    colnames(a) <- LETTERS[1:3]
    colnames(a)
    ## [1] "A" "B" "C"
    names(a)
    ## NULL
    names(mtcars)
    ##  [1] "mpg"  "cyl"  "disp" "hp"   "drat" "wt"   "qsec" "vs"   "am"   "gear"
    ## [11] "carb"
    colnames(mtcars)
    ##  [1] "mpg"  "cyl"  "disp" "hp"   "drat" "wt"   "qsec" "vs"   "am"   "gear"
    ## [11] "carb"
    identical(names(mtcars), colnames(mtcars))
    ## [1] TRUE
    ```

    So what happens when you give an atomic vector plain old names
    rather than colnames? For a non-matrix, it works fine (see the
    `named <- setNames(letters, LETTERS)` example above). For a matrix -
    and presumably for any array, but let’s not get in to that
    distinction - it’s a little bit more complicated. Look closely at
    this output before reading further.

    ``` r
    a <- diag(3)
    (a <- setNames(a, LETTERS[1:3]))
    ##      [,1] [,2] [,3]
    ## [1,]    1    0    0
    ## [2,]    0    1    0
    ## [3,]    0    0    1
    ## attr(,"names")
    ## [1] "A" "B" "C" NA  NA  NA  NA  NA  NA
    a["A"]
    ## A 
    ## 1
    a["Z"]#For a data frame, this would be an error...
    ## <NA> 
    ##   NA
    ```

    When you try to give an atomic vector ordinary names, R will only
    try to name it element-by-element (even if said vector has
    dimensions). Data frames, on the other hand, treat names as
    colnames. R ultimately sees named matrices as named atomic vectors
    that happen to have a second dimension. This means that you can
    subset them with both `["name"]` and `[, "name"]` and get different
    results.

    ``` r
    a <- setNames(diag(3), LETTERS[1:3])
    colnames(a) <- LETTERS[1:3]
    a
    ##      A B C
    ## [1,] 1 0 0
    ## [2,] 0 1 0
    ## [3,] 0 0 1
    ## attr(,"names")
    ## [1] "A" "B" "C" NA  NA  NA  NA  NA  NA
    a["A"]
    ## A 
    ## 1
    a["Z"]
    ## <NA> 
    ##   NA
    a[, "A"]
    ## [1] 1 0 0
    #I'd love to show a[, "Z"], but it throws the error "Error in a[, "Z"] : subscript out of bounds".
    #This is clearly consistent with a["Z"] and my earlier bits on out-of-bounds stuff not throwing errors. 
    ```

    Of course, `["name"]` and `[, "name"]` aren’t identical for data
    frames either, but let’s not get back in to talking about the `drop`
    argument. Starting to see what I mean about R being inconsistent?

-   You cannot use named atomic vectors to generate environments. This
    means that awesome tricks like
    `within(data, remove(columnIDoNotWant, anotherColumn))` work for
    lists and data frames but not for named atomic vectors.

    ``` r
    #Data frames are fine.
    head(within(mtcars, remove("mpg")))
    ##                   cyl disp  hp drat    wt  qsec vs am gear carb
    ## Mazda RX4           6  160 110 3.90 2.620 16.46  0  1    4    4
    ## Mazda RX4 Wag       6  160 110 3.90 2.875 17.02  0  1    4    4
    ## Datsun 710          4  108  93 3.85 2.320 18.61  1  1    4    1
    ## Hornet 4 Drive      6  258 110 3.08 3.215 19.44  1  0    3    1
    ## Hornet Sportabout   8  360 175 3.15 3.440 17.02  0  0    3    2
    ## Valiant             6  225 105 2.76 3.460 20.22  1  0    3    1
    #Named atmomic vectord are not.
    ## > within(setNames(letters, LETTERS), remove("Z"))
    ## Error in UseMethod("within") : 
    ##   no applicable method for 'within' applied to an object of class "character"
    ```

-   When you want to work with the names of named atomic vectors, you
    probably want to access their names directly and use expressions
    like `namedVect[!names(namedVect) %in% c("remove", "us")]`.

    ``` r
    namedVect <- setNames(letters, LETTERS)
    namedVect[!names(namedVect) %in% c("A", "Z")]
    ##   B   C   D   E   F   G   H   I   J   K   L   M   N   O   P   Q   R   S   T   U 
    ## "b" "c" "d" "e" "f" "g" "h" "i" "j" "k" "l" "m" "n" "o" "p" "q" "r" "s" "t" "u" 
    ##   V   W   X   Y 
    ## "v" "w" "x" "y"
    ```

    However, this is a bad habit for non-atomic vectors because, unless
    you take the precautions [mentioned
    earlier](#452-removing-dimensions), `[` likes to remove duplicated
    names and unnecessary dimensions from your data.

-   Don’t think that functional programming will save you from my
    previous point. The base library’s higher-order functions don’t play
    nice with the `names()` function. I think it’s got something to do
    with `lapply()` using `X[[i]]` under the hood (see its
    documentation).

    ``` r
    namedVect <- setNames(letters, LETTERS)
    Filter(function(x) names(x) == "A", namedVect)
    ## named character(0)
    head(lapply(namedVect, function(x) names(x) == "A"))
    ## $A
    ## logical(0)
    ## 
    ## $B
    ## logical(0)
    ## 
    ## $C
    ## logical(0)
    ## 
    ## $D
    ## logical(0)
    ## 
    ## $E
    ## logical(0)
    ## 
    ## $F
    ## logical(0)
    head(sapply(namedVect, function(x) names(x) == "A"))
    ## $A
    ## logical(0)
    ## 
    ## $B
    ## logical(0)
    ## 
    ## $C
    ## logical(0)
    ## 
    ## $D
    ## logical(0)
    ## 
    ## $E
    ## logical(0)
    ## 
    ## $F
    ## logical(0)
    ```

    Did you notice that `Filter` and `lapply`’s arguments are in
    inconsistent orders? A little bit more on that [much
    later](#472-the-functions).

From the above few points, you can see that it’s hard to find a way to
manipulate named atomic vectors by their names that is both safe for
them and for other named objects. The only one that comes to mind is to
use `[` with the aforementioned precautions. That’s bad enough on its
own – it makes R feel unsafe and inconsistent – but it also makes named
atomic vectors feel like an afterthought. I find that most of my code
that makes extended use of named atomic vectors comes out looking
disturbingly unidiomatic. A little bit more on that [when I talk about
matrices](#473-extended-example-matrices).

### 4.5.6 Silence

I’ve already given a few examples of R either silently doing nothing or
silently doing what you don’t want. Let’s have a few more:

-   Again, much of what I’ve listed in the [Indistinguishable
    Errors](#454-indistinguishable-errors) and [Removing
    Dimensions](#452-removing-dimensions) sections occur silently.

-   As documented
    [here](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Indexing-by-vectors),
    negative out-of-bounds values are silently disregarded when deleting
    elements. For example, if you have `x <- 1:10`, then `x[-20]`
    returns an unmodified version of `x` without warning or error.

    ``` r
    x <- 1:10
    x[20]
    ## [1] NA
    x
    ##  [1]  1  2  3  4  5  6  7  8  9 10
    x[-20]
    ##  [1]  1  2  3  4  5  6  7  8  9 10
    identical(x, x[-20])
    ## [1] TRUE
    ```

    Given that `x[20]` is `NA` – a questionable decision in of itself –
    is this the behaviour that you expected?

-   Subassigning `NULL` to a column that your data does not have does
    not give a warning or error. For example, trying to access
    `mtcars["weight"]` is an error, but `mtcars["weight"] <- NULL`
    silently does nothing. `$` and `$<-` have the same issue.

-   Using `within()` to remove unwanted columns from your data,
    e.g. `within(data, rm(colName1, colName2))`, does nothing to any
    columns with duplicated names. Again, no warning or error…

    ``` r
    dupe <- cbind(mtcars, foo = 3, foo = 4)
    head(dupe)
    ##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb foo foo
    ## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4   3   4
    ## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4   3   4
    ## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1   3   4
    ## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1   3   4
    ## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2   3   4
    ## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1   3   4
    head(within(dupe, rm(carb, foo)))
    ##                    mpg cyl disp  hp drat    wt  qsec vs am gear foo foo
    ## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4   4   4
    ## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4   4   4
    ## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4   4   4
    ## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3   4   4
    ## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3   4   4
    ## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3   4   4
    ```

    By the way, `cbind()` doesn’t silently correct duplicated column
    names. By now, you probably expected otherwise. This is documented
    behaviour, but I don’t think that anyone ever bothered to read the
    docs for `cbind()`.

-   Using `subset()` rather than `within()` is sometimes suggested for
    operations like what I was trying to do in the previous point. For
    example, you can remove columns with
    `subset(data, select = -c(colName1, colName2))`. However, for
    duplicated names, I’d argue that `subset()` is even weirder than
    `within()`. With `subset()`, attempting to remove a duplicated
    column by name will only remove the first such column and removing
    any non-duplicated column will change the names of your duplicated
    columns.

    ``` r
    #First, I'll show subset() working as normal and save us some space.
    mtcars2 <- subset(mtcars, mpg > 25, select = -c(cyl, disp, hp, wt))
    mtcars2
    ##                 mpg drat  qsec vs am gear carb
    ## Fiat 128       32.4 4.08 19.47  1  1    4    1
    ## Honda Civic    30.4 4.93 18.52  1  1    4    2
    ## Toyota Corolla 33.9 4.22 19.90  1  1    4    1
    ## Fiat X1-9      27.3 4.08 18.90  1  1    4    1
    ## Porsche 914-2  26.0 4.43 16.70  0  1    5    2
    ## Lotus Europa   30.4 3.77 16.90  1  1    5    2
    dupe <- cbind(mtcars2, foo = 3, foo = 4, foo = 5)
    dupe
    ##                 mpg drat  qsec vs am gear carb foo foo foo
    ## Fiat 128       32.4 4.08 19.47  1  1    4    1   3   4   5
    ## Honda Civic    30.4 4.93 18.52  1  1    4    2   3   4   5
    ## Toyota Corolla 33.9 4.22 19.90  1  1    4    1   3   4   5
    ## Fiat X1-9      27.3 4.08 18.90  1  1    4    1   3   4   5
    ## Porsche 914-2  26.0 4.43 16.70  0  1    5    2   3   4   5
    ## Lotus Europa   30.4 3.77 16.90  1  1    5    2   3   4   5
    subset(dupe, select = -foo)#Names have silently changed and only one foo was dropped.
    ##                 mpg drat  qsec vs am gear carb foo foo.1
    ## Fiat 128       32.4 4.08 19.47  1  1    4    1   4     5
    ## Honda Civic    30.4 4.93 18.52  1  1    4    2   4     5
    ## Toyota Corolla 33.9 4.22 19.90  1  1    4    1   4     5
    ## Fiat X1-9      27.3 4.08 18.90  1  1    4    1   4     5
    ## Porsche 914-2  26.0 4.43 16.70  0  1    5    2   4     5
    ## Lotus Europa   30.4 3.77 16.90  1  1    5    2   4     5
    subset(dupe, select = -c(foo, foo))#Identical to previous.
    ##                 mpg drat  qsec vs am gear carb foo foo.1
    ## Fiat 128       32.4 4.08 19.47  1  1    4    1   4     5
    ## Honda Civic    30.4 4.93 18.52  1  1    4    2   4     5
    ## Toyota Corolla 33.9 4.22 19.90  1  1    4    1   4     5
    ## Fiat X1-9      27.3 4.08 18.90  1  1    4    1   4     5
    ## Porsche 914-2  26.0 4.43 16.70  0  1    5    2   4     5
    ## Lotus Europa   30.4 3.77 16.90  1  1    5    2   4     5
    subset(dupe, select = -carb)#Foo's names have silently changed, despite us not touching foo!
    ##                 mpg drat  qsec vs am gear foo foo.1 foo.2
    ## Fiat 128       32.4 4.08 19.47  1  1    4   3     4     5
    ## Honda Civic    30.4 4.93 18.52  1  1    4   3     4     5
    ## Toyota Corolla 33.9 4.22 19.90  1  1    4   3     4     5
    ## Fiat X1-9      27.3 4.08 18.90  1  1    4   3     4     5
    ## Porsche 914-2  26.0 4.43 16.70  0  1    5   3     4     5
    ## Lotus Europa   30.4 3.77 16.90  1  1    5   3     4     5
    subset(dupe, select = -c(carb, foo))#Names have silently changed and only one foo was dropped.
    ##                 mpg drat  qsec vs am gear foo foo.1
    ## Fiat 128       32.4 4.08 19.47  1  1    4   4     5
    ## Honda Civic    30.4 4.93 18.52  1  1    4   4     5
    ## Toyota Corolla 33.9 4.22 19.90  1  1    4   4     5
    ## Fiat X1-9      27.3 4.08 18.90  1  1    4   4     5
    ## Porsche 914-2  26.0 4.43 16.70  0  1    5   4     5
    ## Lotus Europa   30.4 3.77 16.90  1  1    5   4     5
    ```

    I think that the worst example here is
    `subset(dupe, select = -carb)`. I didn’t touch `foo`, so why change
    it? I’d rather have `within()`’s silent inaction than `subset()`’s
    silent sabotage.

Needless to say, there will be more examples of R silently misbehaving
later on in this document. This was just a good place to throw in a few
that are specific to subsetting.

### 4.5.7 Subsetting by Predicates

This should be easy, shouldn’t it? Go through the data and only give me
the bits that have the property that I’m asking for. What could possibly
go wrong? Turns out, it’s quite a lot. Even predicates as simple as
“*does the element equal `x`?*” are a minefield. I understand why these
examples are the way that they are – really, I do – but how to delete
unwanted elements is one of the first things that you’re going to want
to learn in a stats language. For something that you’re going to want to
be able to do on day one of using R, there are far too many pitfalls.

-   You might think that `setdiff()` is sufficient for removing data –
    it’s certainly the first thing tool that a mathematician would reach
    for – but it has the side-effect of removing duplicate entries from
    the original vector and destroying your data structures by applying
    `as.vector()` to them.

    ``` r
    Nile
    ## Time Series:
    ## Start = 1871 
    ## End = 1970 
    ## Frequency = 1 
    ##   [1] 1120 1160  963 1210 1160 1160  813 1230 1370 1140  995  935 1110  994 1020
    ##  [16]  960 1180  799  958 1140 1100 1210 1150 1250 1260 1220 1030 1100  774  840
    ##  [31]  874  694  940  833  701  916  692 1020 1050  969  831  726  456  824  702
    ##  [46] 1120 1100  832  764  821  768  845  864  862  698  845  744  796 1040  759
    ##  [61]  781  865  845  944  984  897  822 1010  771  676  649  846  812  742  801
    ##  [76] 1040  860  874  848  890  744  749  838 1050  918  986  797  923  975  815
    ##  [91] 1020  906  901 1170  912  746  919  718  714  740
    setdiff(Nile, 1160)#Not a time series any more.
    ##  [1] 1120  963 1210  813 1230 1370 1140  995  935 1110  994 1020  960 1180  799
    ## [16]  958 1100 1150 1250 1260 1220 1030  774  840  874  694  940  833  701  916
    ## [31]  692 1050  969  831  726  456  824  702  832  764  821  768  845  864  862
    ## [46]  698  744  796 1040  759  781  865  944  984  897  822 1010  771  676  649
    ## [61]  846  812  742  801  860  848  890  749  838  918  986  797  923  975  815
    ## [76]  906  901 1170  912  746  919  718  714  740
    setdiff(Nile, 0)#Hey, where did the other 1160s go?
    ##  [1] 1120 1160  963 1210  813 1230 1370 1140  995  935 1110  994 1020  960 1180
    ## [16]  799  958 1100 1150 1250 1260 1220 1030  774  840  874  694  940  833  701
    ## [31]  916  692 1050  969  831  726  456  824  702  832  764  821  768  845  864
    ## [46]  862  698  744  796 1040  759  781  865  944  984  897  822 1010  771  676
    ## [61]  649  846  812  742  801  860  848  890  749  838  918  986  797  923  975
    ## [76]  815  906  901 1170  912  746  919  718  714  740
    ```

    It’s more safe if you’re dealing with names,
    e.g. `data[setdiff(names(data), "nameOfThingToDelete")]`

    ``` r
    head(mtcars)
    ##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb
    ## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
    ## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
    ## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
    ## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
    ## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
    ## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
    head(mtcars[setdiff(names(mtcars), "wt")])
    ##                    mpg cyl disp  hp drat  qsec vs am gear carb
    ## Mazda RX4         21.0   6  160 110 3.90 16.46  0  1    4    4
    ## Mazda RX4 Wag     21.0   6  160 110 3.90 17.02  0  1    4    4
    ## Datsun 710        22.8   4  108  93 3.85 18.61  1  1    4    1
    ## Hornet 4 Drive    21.4   6  258 110 3.08 19.44  1  0    3    1
    ## Hornet Sportabout 18.7   8  360 175 3.15 17.02  0  0    3    2
    ## Valiant           18.1   6  225 105 2.76 20.22  1  0    3    1
    ```

    but anything that’s only sometimes safe doesn’t fill me with
    confidence.

-   Because `which()` is an extremely intuitive function for
    extracting/changing subsets of your data and for dealing with
    missing values (see [*The R
    Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf),
    section 8.1.12), it is one of the first things that a beginner will
    learn about. However, although your intuition is screaming for you
    to do it, you almost never want to use
    `data <- data[-which(data==thingToDelete)]`. The problem with this
    is that when `which()` finds no matches, it evaluates to something
    of length 0, so `data[-which(data==thingToDelete)]` also returns
    something of length 0, deleting your data.

    ``` r
    Nile
    ## Time Series:
    ## Start = 1871 
    ## End = 1970 
    ## Frequency = 1 
    ##   [1] 1120 1160  963 1210 1160 1160  813 1230 1370 1140  995  935 1110  994 1020
    ##  [16]  960 1180  799  958 1140 1100 1210 1150 1250 1260 1220 1030 1100  774  840
    ##  [31]  874  694  940  833  701  916  692 1020 1050  969  831  726  456  824  702
    ##  [46] 1120 1100  832  764  821  768  845  864  862  698  845  744  796 1040  759
    ##  [61]  781  865  845  944  984  897  822 1010  771  676  649  846  812  742  801
    ##  [76] 1040  860  874  848  890  744  749  838 1050  918  986  797  923  975  815
    ##  [91] 1020  906  901 1170  912  746  919  718  714  740
    Nile[-which(Nile==1160)]#This is fine.
    ##  [1] 1120  963 1210  813 1230 1370 1140  995  935 1110  994 1020  960 1180  799
    ## [16]  958 1140 1100 1210 1150 1250 1260 1220 1030 1100  774  840  874  694  940
    ## [31]  833  701  916  692 1020 1050  969  831  726  456  824  702 1120 1100  832
    ## [46]  764  821  768  845  864  862  698  845  744  796 1040  759  781  865  845
    ## [61]  944  984  897  822 1010  771  676  649  846  812  742  801 1040  860  874
    ## [76]  848  890  744  749  838 1050  918  986  797  923  975  815 1020  906  901
    ## [91] 1170  912  746  919  718  714  740
    which(Nile==11600)
    ## integer(0)
    Nile[-which(Nile==11600)]#This is not.
    ## numeric(0)
    ```

    What you probably expected was `which()` leaving your data unchanged
    when it has not found a match. You might also have expected a
    warning or error, but surely you’ve learned your lesson by now?
    Anyway, section 8.1.13 of [*The R
    Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf)
    offers some ways to get this behaviour, but the only
    practical-looking suggestion is `data[!(data %in% thingToDelete)]`.
    I think that you can get away with removing the curly brackets
    there.

    ``` r
    Nile[!Nile %in% 1160]
    ##  [1] 1120  963 1210  813 1230 1370 1140  995  935 1110  994 1020  960 1180  799
    ## [16]  958 1140 1100 1210 1150 1250 1260 1220 1030 1100  774  840  874  694  940
    ## [31]  833  701  916  692 1020 1050  969  831  726  456  824  702 1120 1100  832
    ## [46]  764  821  768  845  864  862  698  845  744  796 1040  759  781  865  845
    ## [61]  944  984  897  822 1010  771  676  649  846  812  742  801 1040  860  874
    ## [76]  848  890  744  749  838 1050  918  986  797  923  975  815 1020  906  901
    ## [91] 1170  912  746  919  718  714  740
    Nile[!Nile %in% 11600]
    ##   [1] 1120 1160  963 1210 1160 1160  813 1230 1370 1140  995  935 1110  994 1020
    ##  [16]  960 1180  799  958 1140 1100 1210 1150 1250 1260 1220 1030 1100  774  840
    ##  [31]  874  694  940  833  701  916  692 1020 1050  969  831  726  456  824  702
    ##  [46] 1120 1100  832  764  821  768  845  864  862  698  845  744  796 1040  759
    ##  [61]  781  865  845  944  984  897  822 1010  771  676  649  846  812  742  801
    ##  [76] 1040  860  874  848  890  744  749  838 1050  918  986  797  923  975  815
    ##  [91] 1020  906  901 1170  912  746  919  718  714  740
    ```

    That’s mostly okay. However,
    `identical(Nile, Nile[!Nile %in% 11600])` is `FALSE`. Can you guess
    why? It’s like R has no always safe ways to subset.

-   At least removing elements that are equal to a particular number is
    simple for vectors. Even for lists, it’s just `data[data!=x]`. It’s
    maybe not what a beginner would guess (“*I have to write `data`
    twice?*”), but it’s simple enough.

-   For removing a vector from a list of vectors, you’re going to want
    to learn some functional programming idioms. Not hard if you’re a
    programmer, but shouldn’t this be easier in a stats and maths tool?
    Anyway, you probably want
    `Filter(function(x) all(x!=vectorToDelete), data)`. You can also do
    it with the apply family, but I don’t see why you would.

-   Removing what you don’t want from a data frame largely comes down to
    mastering the subsetting rules, a nightmare that I’ve spent the
    previous few thousand words covering. I often end up with very ugly
    lines like
    `outcomes[outcomes$playerChoice == playerChoice & outcomes$computerChoice == computerChoice, "outcome"]`

-   Before you ask, `subset()`, `with()`, and `within()` aren’t good
    enough either. I’ve already mentioned some of their issues, but
    [more on them later](#4112-non-standard-evaluation).

Overall, it’s like R has no safe ways to subset. What is safe for one
job is often either unsafe, invalid, or inconsistent for another. R’s
huge set of subsetting tools is useful – maybe even good – once
mastered, but until then you’re forced to adopt a guess-and-check style
of programming and pray that you get a useful error/warning message when
you get something wrong. Worse still, these prayers are rarely answered
and, in the cases where R silently does something that you didn’t want,
they’re outright mocked. Do you understand how damning that is for a
stats language? I can’t stress this point enough. Subsetting in R should
be easy and intuitive. Instead, it’s something that I’ve managed to
produce thousands of words of complaints about and it still trips me up
with alarming regularity, despite my clear knowledge of the correct way
to do things. If I want a vector of consonants, you can bet that I’m
going to write `letters[-c("a", "e", "i", "o", "u")]`,
`letters[-which(letters == c("a", "e", "i", "o", "u"))]`, and
`letters[c("a", "e", "i", "o", "u") %in% letters]` before remembering
the right way to do it. If I’m still making those mistakes for something
simple, then I can only imagine what it’s like for a true beginner doing
something complicated.

## 4.6 Vectorization Again

[You’ve heard the good](#34-vectorization), now for the bad. R’s
vectorization is probably the best thing about the language and it will
work miracles when you’re wanting to do mathematics. However, it will
trip you up in other areas. A lot of these points are minor, but when
they cause you problems their source can be tough to track down. This is
because R is working as intended and therefore not giving you any
warnings or errors (spotting a pattern?). Furthermore, if you have
correctly identified that you have a vectorization problem, then pretty
much any function in R could be to blame, because most of R’s functions
are vectorized.

-   The commonality of vectors leads to some new syntax that must be
    memorised. For example, `if(x|y)` and `if(x||y)` are very different
    and using `&&` rather than `&` can be fatal. Compare the following:

    ``` r
    mtcars[mtcars$mpg < 20 && mtcars$hp > 150,]
    ##  [1] mpg  cyl  disp hp   drat wt   qsec vs   am   gear carb
    ## <0 rows> (or 0-length row.names)
    mtcars[mtcars$mpg < 20 & mtcars$hp > 150,]
    ##                      mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## Hornet Sportabout   18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
    ## Duster 360          14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
    ## Merc 450SE          16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
    ## Merc 450SL          17.3   8 275.8 180 3.07 3.730 17.60  0  0    3    3
    ## Merc 450SLC         15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
    ## Cadillac Fleetwood  10.4   8 472.0 205 2.93 5.250 17.98  0  0    3    4
    ## Lincoln Continental 10.4   8 460.0 215 3.00 5.424 17.82  0  0    3    4
    ## Chrysler Imperial   14.7   8 440.0 230 3.23 5.345 17.42  0  0    3    4
    ## Camaro Z28          13.3   8 350.0 245 3.73 3.840 15.41  0  0    3    4
    ## Pontiac Firebird    19.2   8 400.0 175 3.08 3.845 17.05  0  0    3    2
    ## Ford Pantera L      15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
    ## Ferrari Dino        19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
    ## Maserati Bora       15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8
    ```

    Personally, I find that it’s easy to remember to use `&` for `if`
    but I often forget to use `&` for subsetting.

-   The `if` statements accept vectors of length greater than 1 as their
    predicate, but will only pay attention to the very first element.
    This throws a warning and there is a global option to make it an
    error instead, but I can’t see why R accepts such predicates at all.
    Why would I ever use `if(c(TRUE, FALSE))` to mean “*if the first
    element of my vector is true, then…*”? This is also what the `&&`
    and `||` syntax is for (e.g. `c(TRUE, FALSE) && c(TRUE, FALSE)` is
    `TRUE`), but I still don’t see why anyone would use several logical
    vectors and only be interested in their first elements.

-   When dealing with anything 2D, you need to be very careful to not
    mix up any of `length()`, `lengths()`, `nrow()`, or `ncol()`. In
    particular, `length()` is so inconsistent that I’m unsure why they
    let it work for 2D structures ([probably something to do with it
    being an internal generic](#493-internal-generics)). For example,
    the length of a data frame is its number of columns and the length
    of a matrix is its number of elements.

    ``` r
    (a <- diag(4))
    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    0    0    0
    ## [2,]    0    1    0    0
    ## [3,]    0    0    1    0
    ## [4,]    0    0    0    1
    (b <- as.data.frame(a))
    ##   V1 V2 V3 V4
    ## 1  1  0  0  0
    ## 2  0  1  0  0
    ## 3  0  0  1  0
    ## 4  0  0  0  1
    length(a)
    ## [1] 16
    length(b)
    ## [1] 4
    ```

-   Vectors are collections and therefore inherit the previous section’s
    issues about selecting elements.

-   Because virtually everything is already a vector, you never know
    what to use when you want a collection or anything nested. Lists?
    Arrays? `c()`? Data frames? One of `cbind()`/`rbind()`? Matrices?
    You get used to it eventually, but it takes a while to understand
    the differences.

-   Some functions are vectorized in such a way that you’re forced to
    remember the difference between how they behave for n length-one
    vectors and and how they behave for the corresponding single vector
    of length n. For example, `paste("Alice", "Bob", "Charlie")` is not
    the same as `paste(c("Alice", "Bob", "Charlie"))`.

    ``` r
    paste("Alice", "Bob", "Charlie")
    ## [1] "Alice Bob Charlie"
    paste(c("Alice", "Bob", "Charlie"))
    ## [1] "Alice"   "Bob"     "Charlie"
    paste("Alice", "Bob", "Charlie", collapse = "")
    ## [1] "Alice Bob Charlie"
    paste(c("Alice", "Bob", "Charlie"), collapse = "")
    ## [1] "AliceBobCharlie"
    ```

    I’m not saying that this doesn’t make sense, but it is a source of
    unpredictability.

-   Another unpredictable example: What does
    `max(100:200, 250:350, 276)` return? You might be surprised to
    discover that the output is the single number `350`, rather than a
    vector of many outputs.

    ``` r
    max(100:200, 250:350, 276)
    ## [1] 350
    ```

    The fix for this isn’t some `collapse`-like argument like it is for
    `paste()`, it’s an entirely different function: `pmax()`. Why?

    ``` r
    pmax(100:200, 250:350, 276)
    ##   [1] 276 276 276 276 276 276 276 276 276 276 276 276 276 276 276 276 276 276
    ##  [19] 276 276 276 276 276 276 276 276 276 277 278 279 280 281 282 283 284 285
    ##  [37] 286 287 288 289 290 291 292 293 294 295 296 297 298 299 300 301 302 303
    ##  [55] 304 305 306 307 308 309 310 311 312 313 314 315 316 317 318 319 320 321
    ##  [73] 322 323 324 325 326 327 328 329 330 331 332 333 334 335 336 337 338 339
    ##  [91] 340 341 342 343 344 345 346 347 348 349 350
    ```

-   A further annoyance comes from how many things behave differently on
    vectors of length one. For example, `sample(1:5)` is exactly the
    same as `sample(5)`, which is bound to give you bugs when you use
    `sample(5:n)` for changing `n`.

-   R has rules for recycling vector elements when you try to get it to
    do something with several vectors that don’t all have the same
    length. You saw this abused when I gave the
    `x <- paste0(rep("", 100), c("", "", "Fizz"), c("", "", "", "", "Buzz"))`
    FizzBuzz example. When recycling occurs, R only throws a warning if
    the longest vector’s length is not a multiple of the others. For
    example, neither `Map(sum, 1:6, 1:3)` nor that FizzBuzz line warn
    you that recycling has occurred, but `Map(sum, 1:6, 1:4)` will.

    ``` r
    Map(sum, 1:6, 1:3)
    ## [[1]]
    ## [1] 2
    ## 
    ## [[2]]
    ## [1] 4
    ## 
    ## [[3]]
    ## [1] 6
    ## 
    ## [[4]]
    ## [1] 5
    ## 
    ## [[5]]
    ## [1] 7
    ## 
    ## [[6]]
    ## [1] 9
    Map(sum, 1:6, 1:4)
    ## Warning in mapply(FUN = f, ..., SIMPLIFY = FALSE): longer argument not a
    ## multiple of length of shorter
    ## [[1]]
    ## [1] 2
    ## 
    ## [[2]]
    ## [1] 4
    ## 
    ## [[3]]
    ## [1] 6
    ## 
    ## [[4]]
    ## [1] 8
    ## 
    ## [[5]]
    ## [1] 6
    ## 
    ## [[6]]
    ## [1] 8
    ```

    The first case – where no warnings are given – can be an unexpected
    source of major error. [The authors of the Tidyverse seem to agree
    with
    me](https://r4ds.had.co.nz/vectors.html#scalars-and-recycling-rules).
    For example, you’re only allowed to recycle vectors of length 1 when
    constructing a tibble, so `tibble(1:4, 1:2)` will throw a clear
    error message whereas `data.frame(1:4, 1:2)` silently recycles the
    second argument. Similarly, `map2(1:6, 1:3, sum)` is an error, but
    `map2(1:6, 1, sum)` is not.

    ``` r
    library(tibble)
    ## > tibble(1:4, 1:2)
    ## Error: Tibble columns must have compatible sizes.
    ## * Size 4: Existing data.
    ## * Size 2: Column at position 2.
    ## ℹ Only values of size one are recycled.
    ## Run `rlang::last_error()` to see where the error occurred.
    data.frame(1:4, 1:2)
    ##   X1.4 X1.2
    ## 1    1    1
    ## 2    2    2
    ## 3    3    1
    ## 4    4    2
    library(purrr)
    ## > map2(1:6, 1:3, sum)
    ## Error: Mapped vectors must have consistent lengths:
    ## * `.x` has length 6
    ## * `.y` has length 3
    map2(1:6, 1, sum)
    ## [[1]]
    ## [1] 2
    ## 
    ## [[2]]
    ## [1] 3
    ## 
    ## [[3]]
    ## [1] 4
    ## 
    ## [[4]]
    ## [1] 5
    ## 
    ## [[5]]
    ## [1] 6
    ## 
    ## [[6]]
    ## [1] 7
    ```

-   Section 8.1.6 of [*The R
    Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf): The
    recycling of vectors lets you attempt to do things that look correct
    to a novice and make sense to a master, but are almost certainly not
    what was wanted. For example, `c(4, 6) == 1:10` is `TRUE` only in
    its sixth element. The recycling rules turn it in to
    `c(4, 6, 4, 6, 4, 6, 4, 6, 4, 6) == 1:10`. Again, there is no
    warning given to the user unless the longest vector’s length is not
    a multiple of the other’s. In this case, what you wanted was
    probably `c(4, 6) %in% 1:10`, maybe with a call to `all()`.

    ``` r
    c(4, 6) == 1:10
    ##  [1] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE
    c(4, 6, 4, 6, 4, 6, 4, 6, 4, 6) == 1:10
    ##  [1] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE
    c(4, 6) %in% 1:10
    ## [1] TRUE TRUE
    all(c(4, 6) %in% 1:10)
    ## [1] TRUE
    ```

-   Some functions don’t recycle in the way that you would expect. For
    example, read the documentation for `strsplit()` and ask yourself if
    you expect `strsplit("Alice", c("l", "c"))` and
    `strsplit("Alice", "l")` to give the same output. If you think that
    they don’t, you’re wrong. If you expected the first option to warn
    you about the `"c"` part not being used, you’re sane, but wrong. If
    you want to see how the second argument is supposed to work, re-run
    the earlier code with `c("Alice", "Boblice")` as your first
    argument.

    ``` r
    strsplit("Alice", c("l", "c"))
    ## [[1]]
    ## [1] "A"   "ice"
    strsplit("Alice", "l")
    ## [[1]]
    ## [1] "A"   "ice"
    strsplit(c("Alice", "Boblice"), c("l", "c"))
    ## [[1]]
    ## [1] "A"   "ice"
    ## 
    ## [[2]]
    ## [1] "Bobli" "e"
    ```

-   Remember what I said about needing to generate the correct logical
    vector when you want to subset a collection? Logical vectors are
    also recycled when subsetting collections. Because this vector
    recycling does not always throw warnings or errors, it’s a new Hell.
    I’m honestly not sure if the exact rules for when this does/doesn’t
    throw warnings/errors are documented anywhere. [The language
    definition](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Indexing-by-vectors)
    claims that using a logical vector to subset a longer vector follows
    the same rules as when you’re using two such vectors for arithmetic
    (i.e. you get a warning if the larger of the two’s length isn’t a
    multiple of the smaller’s). However, I know this to be false.

    ``` r
    a <- 1:10
    a + rep(1, 9) #Arithmetic; Gives a warning.
    ## Warning in a + rep(1, 9): longer object length is not a multiple of shorter
    ## object length
    ##  [1]  2  3  4  5  6  7  8  9 10 11
    a[rep(TRUE, 9)] #Logical subsetting; 10 results without warning.
    ##  [1]  1  2  3  4  5  6  7  8  9 10
    a[c(TRUE, FALSE, TRUE)] #Again, 10 results. Shouldn't it be either 10 with a warning or just 3?
    ## [1]  1  3  4  6  7  9 10
    ```

    I’ll take this chance to repeat my claim that this is extremely
    powerful if used correctly, but the potential for errors slipping
    through unnoticed is huge. This toy example isn’t so bad, but wait
    until these errors creep in to your dataset with 50 rows and
    columns, leaving you with no damn idea where it all went wrong. The
    first time where this really caught me out was when I used the same
    logical vector for two similar datasets of slightly different sizes.
    I had hoped that if anything went wrong, I’d get an error. Because I
    didn’t, I continued on without knowing that half of my data was now
    ruined.

-   Logical vectors also recycle `NA` without warning. I can’t point to
    any documentation that contradicts this, but it will always catch
    you off guard. On the bright side, this is consistent with the
    addition and subsetting rules for numeric vectors with `NA`s.

    ``` r
    arithmetic <- c(2, NA)
    arithmetic + c(11, 12, 13, 14) #Keeps NA and recycles.
    ## [1] 13 NA 15 NA
    logic <- c(TRUE, FALSE, TRUE, NA)
    LETTERS[logic]
    ##  [1] "A" "C" NA  "E" "G" NA  "I" "K" NA  "M" "O" NA  "Q" "S" NA  "U" "W" NA  "Y"
    LETTERS[arithmetic] #Keeps NA and recycling is not expected.
    ## [1] "B" NA
    ```

-   You sometimes have to tell R that you wanted to work on the entire
    vector rather than its elements. For example,
    `rep(matrix(1:4, nrow = 2, ncol = 2), 5)` will not repeat the matrix
    5 times, it will repeat its elements 5 times. The fix is to use
    `rep(list(matrix(1:4, nrow = 2, ncol = 2)), 5)` instead.

    ``` r
    m <- matrix(1:4, nrow = 2, ncol = 2)
    rep(m, 5)
    ##  [1] 1 2 3 4 1 2 3 4 1 2 3 4 1 2 3 4 1 2 3 4
    rep(list(m), 5)
    ## [[1]]
    ##      [,1] [,2]
    ## [1,]    1    3
    ## [2,]    2    4
    ## 
    ## [[2]]
    ##      [,1] [,2]
    ## [1,]    1    3
    ## [2,]    2    4
    ## 
    ## [[3]]
    ##      [,1] [,2]
    ## [1,]    1    3
    ## [2,]    2    4
    ## 
    ## [[4]]
    ##      [,1] [,2]
    ## [1,]    1    3
    ## [2,]    2    4
    ## 
    ## [[5]]
    ##      [,1] [,2]
    ## [1,]    1    3
    ## [2,]    2    4
    ```

    Similarly, you might think that `vect %in% listOfVectors` will work,
    but it will instead check if the elements of `vect` are elements of
    `listOfVectors`. Again, the solution is to wrap the vector in a
    list. For example, you want `list(1:4) %in% list(5:10, 10:15, 1:4)`
    not `1:4 %in% list(5:10, 10:15, 1:4)`.

    ``` r
    list(1:4) %in% list(5:10, 10:15, 1:4)
    ## [1] TRUE
    1:4 %in% list(5:10, 10:15, 1:4)
    ## [1] FALSE FALSE FALSE FALSE
    ```

    You might be surprised that the last result was entirely `FALSE`.
    After all, some of `1:4` is in the last element of the list. I’ll
    leave that one to you.

Again, for the most part, these aren’t major issues. I don’t
particularly like the inconsistency between functions like `paste()` and
`max()`, but the only true minefield is the vector recycling rules. When
they silently do things that you don’t want, you’re screwed.

## 4.7 R Won’t Help You

R makes no secret of being essentially half a century of patches for S.
Many things disagree, lack any clear conventions, or are just plain bad,
but show no signs of changing. Because so many packages depend on these
inconsistencies, I don’t think that they will ever be removed from base
R. R could be salvaged if its means of helping you manage the
inconsistency were up to scratch – e.g. the documentation, the
function/argument names, or the warning/error messages – but they’re
not. It’s therefore hard to guess about anything or to help yourself
when you’ve guessed wrong. These sounds like minor complaints, but R can
be so poor in these regards that it becomes a deal-breaker for the
entire language. If there’s one thing that will make you quit R forever,
it’s this. It may sound like I’m being harsh, but I’m not alone in
saying it. Both *Advanced R* and [*The R
Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf) can
barely go a section without pointing out an inconsistency in R.

Really, this is R’s biggest issue. You can get used to the arcane laws
powering R’s subsetting and vectorization, the abnormalities of its
variable manipulations, and it’s tendency to do dangerous things without
warning you. However, this is the one thing that you can never learn to
live with. R is openly, dangerously, and eternally inconsistent and also
does a poor job of helping you live with that. In the very worst cases,
you can’t find the relevant documentation, the thing that’s conceptually
close to what you’re after doesn’t link to it, the examples are as poor
as they are few, the documentation is simultaneously incomplete and
filled with irrelevant information while assuming familiarity with
something alien, the error messages don’t tell you what line threw the
errors that your inevitable misunderstandings caused, the dissimilarity
between what you’re working with and the rest of the language makes it
impossible to guess where you’ve slipped up, there’s undocumented
behaviour that you need to look at the C code to discover, and you know
that none of this will ever be fixed!

These issues tend to overlap, but I’ve done my best to split this up in
to sections that cover each aspect of this problem. All in all, this
section came out to be shorter than I expected. However, I hope that I
have made the magnitude of some of these points clear.

### 4.7.1 The Documentation

If R had outstanding documentation, then I could live with its
inconsistencies. Sadly, it doesn’t. The documentation does almost
nothing to help you in this regard and has more than its fair share of
issues:

-   Some of the docs are ancient and therefore have examples that are
    either terrible, few in number, or non-existent. The references in
    these docs suggests that this is a disease inherited from S, but
    sometimes it’s really unforgivable:
    -   The Examples section in the documentation for control flow shows
        no examples of how to use `if`, `while`, `repeat`, `break`, or
        `next`. They’re explained in the actual text, but I expect the
        Examples section to give examples!
    -   The documentation for the list data type has five examples, many
        of which are for the other seven functions that it shares it
        documentation with, despite it being an absolutely fundamental
        data type. For some reason, that documentation also includes a
        library call. And yes, that does mean that some of the functions
        don’t have examples.
    -   For stats functions, we typically see documentation for a set of
        algorithms. However, said documentation will often have far
        fewer examples than there are members in said set. The
        `quantile()` function’s docs are an extreme examples of this. A
        similar sin can be found in the docs for `lm()` and `glm()`.
        However, their See Also sections link to a lot of functions that
        use them in their own examples, so I can just barely forgive
        this.

    The Tidyverse seems to be far better in this regard, with the
    examples often taking up almost as much room as the actual
    documentation. However, I don’t like how its docs often don’t have a
    Value section, like a lot of base R’s docs do.
-   Some of the docs have no examples at all e.g. `UseMethod()`,
    `vcov()`, and `xtfrm()`.
-   Some of the docs will document many seemingly identical things and
    not tell you how they differ. For example, can you tell from the
    documentation if there’s a difference between `rm()` and `remove()`?
    An even worse case is trying to figure out the difference between
    `resid()` and `residuals()`. The documentation correctly tells you
    that one is an alias for another, but then it tells you that
    `resid()` is intended to encourage you to not do a certain thing.
    This implies that `residuals()` does not have that same intention,
    incorrectly hinting that they might have different behaviour.
-   In some of the standard libraries, you can find functions without
    any documentation. For example, `MASS::as.fraction()` is totally
    undocumented.
-   The [*R Language
    Definition*](https://cran.r-project.org/doc/manuals/r-release/R-lang.html)
    is incomplete. I imagine that this will really bother some people on
    principle alone. Personally, I would be satisfied if it were
    incomplete in the sense of “*each section is complete and correct,
    but the document is missing many key sections*”. However, it’s
    really more like a rough draft. It has [sentences that stop
    mid-word](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Inheritance),
    [prompts for where to write something
    latter](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Propagation-of-names),
    and lots of information that is either clearly incomplete or very
    out of date.
-   A lot of R’s base functions are not written in R, so if you really
    want to understand how an R function works, you need to learn an
    extra language. I find that a lot of the power users have gotten
    used to reading the C source code for a lot of R. That wouldn’t be
    so bad, but…
-   For a long time, I didn’t know why many of my technical questions on
    Stack Overflow were answered by direct reference to R’s code,
    without any mention of its documentation. I eventually learned that
    R’s functions occasionally have undocumented behaviour, meaning that
    you can’t trust anything other than the code. For example:
    -   Where do the docs tell you that the `expr` argument in
        `replicate()` gets wrapped in an anonymous function, meaning
        that you can’t use it to do `<-` variable assignment to its
        calling environment (e.g. code like
        `n <- 0; replicate(5, n <- n + 1)` does not change `n`)? You
        might just spot this if you check the R code, but even then it’s
        not clear.

        ``` r
          replicate
        ## function (n, expr, simplify = "array") 
        ## sapply(integer(n), eval.parent(substitute(function(...) expr)), 
        ##     simplify = simplify)
        ## <bytecode: 0x559970311690>
        ## <environment: namespace:base>
        ```

    -   Where do `rep()`’s docs tell you that it’s a special kind of
        generic where your extensions to it won’t dispatch properly?
        Even the R code – `function (x, ...)  .Primitive("rep")` – won’t
        help you here.

    -   Where do `lapply()` and `Filter()`’s docs tell you that they
        don’t play nice with the `names()` function? Again, even the R
        code won’t help here.

        ``` r
          lapply
        ## function (X, FUN, ...) 
        ## {
        ##     FUN <- match.fun(FUN)
        ##     if (!is.vector(X) || is.object(X)) 
        ##         X <- as.list(X)
        ##     .Internal(lapply(X, FUN))
        ## }
        ## <bytecode: 0x55996db63f10>
        ## <environment: namespace:base>
        ```

    You can sometimes find parts of the documentation that very vaguely
    hint to this misbehaviour, but such things are rarely specific or
    said at a non-expert level: Their meaning is only obvious in
    retrospect. On the rare occasion that the documentation is specific
    about the misbehaviour, it can be incomplete. For example, the
    documentation for `choose()` tells you that it behaves differently
    for small `k`, but what is “*small `k`*”? I think that it’s 29 or
    less, but that assumes that I’ve found the correct C code (I think
    it’s
    [this](https://github.com/wch/r-source/blob/trunk/src/nmath/choose.c)?)
    and read it correctly.
-   In the same vein to the `choose()` example, functions in the base
    stats library do not always tell you which calculation method they
    used. This can make you falsely assume that a figure was calculated
    exactly. For example, `prop.test()` computes an approximation, but
    the only mention of this in its documentation is the See Also
    section saying “*`binom.test()` for an exact test of a binomial
    hypothesis*”. Not only is this in a terrible place, it only suggests
    that an approximation has been used in `prop.test()`. The details of
    the approximation are left for the reader to guess.
-   Some functions act very strangely because they’re designed with S
    compatibility in mind. This issue goes on to damage the
    documentation for said functions. For example, have a look at the
    docs for the `seq()` function. It won’t tell you what `seq_along()`
    does, but it will tell you what to use `seq_along()` instead of!
    I’ll let [Stack
    Overflow](https://stackoverflow.com/questions/59378862/) explain
    `seq.int()`’s documentation issues. Said documentation is so poor
    that I’ve been scared out of using the function. I really don’t know
    why R pays this price: Who is still using S? Another example is the
    `**` function. I’ll let the Arithmetic Operators documentation (try
    `?'**'`) speak for itself on that one. Its three sentences on the
    topic are `**`’s only documentation. Given that you shouldn’t ever
    really use it, it would be harsh of me to say more or point out its
    oddities. For further reading, I will only give
    [this](https://rosettacode.org/wiki/Exponentiation_order#R).
-   As the previous example shows, backwards compatibility is a priority
    for R. This means that its inconsistencies will almost certainly
    never be fixed. Things would be better if the docs did a better job
    of helping you, but this section demonstrates ad nauseam that they
    do not. One wonders if there’s ever been any real interest in fixing
    it.
-   Some docs assume stats knowledge even when there should be no need
    to. If you don’t know what “*sweeping out*” is, you will never
    understand the docs for `sweep()`. I find `rmultinom()`’s docs to be
    similarly lacking. It talks about “*the typical multinomial
    experiment*” as if you’ll know what that is. Its Details section
    tells you the mathematical technicalities, but if I wanted that then
    I would’ve went to Wikipedia. All that they had to do was give an
    example about biased die and that would’ve told the reader all that
    they will need to know. A similar case can be made about `rbinom()`,
    but I can forgive that on the grounds of “*who uses R without
    knowing at least that much stats?*”.
-   The docs often do a bad job of linking to other relevant functions.
    For example, `match()`’s doesn’t tell you about `Position()`,
    `subset()`, `which()`, or the various grep things, `mapply()`’s
    doesn’t tell you about `Map()`, and `rbinom()`’s doesn’t tell you
    about `rmultinom()`.
-   I sometimes can’t understand how to search for functions in the
    documentation. For example, `Filter()`’s docs are in the “*funprog
    {base}*” category, but putting `?funprog` in to R won’t return those
    docs. Another oddity is that it’s sometimes case sensitive. For
    example, `?Extract` works but `?extract` doesn’t. In case you missed
    it, there is no `Extract()` or `extract()` function.
-   I find that the documentation tries to cover too many functions at
    once. For example, in order to understand any particular function in
    the funprog or grep documentation, you’re probably going to have to
    go as far as understanding all of them. The worst case is the
    Condition Handling and Recovery documentation (`?tryCatch`), which
    lists about 30 functions, forever dooming me to never really
    understand any more of R’s exception system than `stop()` and
    `stopifnot()`. A much smaller example is that both `abs()` and
    `sqrt()` are documented in the same place, despite barely having
    anything in common and not sharing this documentation with anything
    else. This issue also compromises the quality of the examples that
    are given. For example, the funprog documentation gives no examples
    of how to use `Map()`, `Find()`, or `Position()`, something that
    never would have happened if they were alone in their own
    documentation pages. Then again, `which()` and `arrayInd()` are the
    only functions in their documentation, and `arrayInd()`has no
    examples, so maybe I’m giving R too much credit. After all, like I
    hinted at earlier, even totally fundamental stuff like lists have
    more functions in their documentation than examples.
-   The docs sometimes spend a distracting amount of time comparing
    their subjects to other languages that you might not know. The best
    example is the funprog docs, which are needlessly cluttered with
    mentions of Common Lisp. A close second to this is the documentation
    for pairlists, which even in [the language
    definition](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Pairlist-objects)
    have little more description than “*Pairlist objects are similar to
    Lisp’s dotted-pair lists*”. My favourite example is probably
    “*regexpr and gregexpr with perl = TRUE allow Python-style named
    captures*”, if only because it manages to mention two languages in a
    totally unexpected way. I should also mention that I’ve already
    complained about how some functions are so obsessed with S
    compatibility that both their documentation and functionality are
    compromised. As a final but forgiveable case, `sprintf()` is
    deliberately about C-style stuff and therefore never shuts up about
    C, making the R documentation pretty difficult for anyone who
    doesn’t know C.
-   If pairlists are not really intended for use by normal users, why
    are they documented in the exact same place as normal lists, which
    are critical to normal R usage?
-   Guidelines for unusual operators, such as using `[` as a function,
    are rather hard to find in the documentation. One example that I
    found particularly annoying is in the `names()` documentation. It
    can’t make its mind up about whether it wants to talk about the
    `names(x) <- value` version or the `"names<-"(x, value)` version.
    The only place where it’s apparent that there’s a meaningful
    difference between the two is in the second part of the Values
    section, which says:
    -   “*For `names<-`, the updated object. (Note that the value of
        `names(x) <- value` is that of the assignment, `value`, not the
        return value from the left-hand side.)*”

    …Wasn’t that helpful? You’ll only really be able to understand it if
    you understand the abstract notion of R’s replacement functions, but
    nowhere in the `names()` documentation will point you to that. In
    fact, unless you find the correct section of the language
    definition, you’re never going to find it at all (I’m not linking to
    that, go prove my point and find it yourself!).

Don’t get me wrong, R’s documentation isn’t terrible. Its primary issue
is that it does a poor job of helping you navigate R’s inconsistencies.
If the examples were plentiful and the docs for each function linked to
plenty of other related functions without themselves being cluttered
with mentions of other functions and languages, then it would go a long
way towards stopping R from tripping people up.

### 4.7.2 The Functions

There are several inconsistencies in R’s functions and how you use them.
This means that you either have to adopt a guess-and-check style of
coding or constantly double-check the documentation before using a lot
of R’s functions. Neither are satisfactory.

-   There are a few too many functions that have names synonymous with
    “*do more than once*”. There’s `replicate()`, `repeat` loops, and
    `rep()`. Good luck remembering which does what.
-   Why do we have both `structure()` and `str()` or `seq()` and
    `sequence()`, all of which are different, while having
    `rm()`/`remove()` and `residuals()`/`resid()`, which are not? The
    potential for confusion is obvious: If I were to write a new
    function, `Pos()`, should you or should you not assume that it’s an
    alias for `Position()`?
-   There is no consistent convention for function names in the base
    libraries, even for related functions. I struggle to think of a
    function-naming scheme that isn’t found somewhere in R. For example,
    the documentation for `mean()` links to both `colMeans()` and
    `weighted.mean()`. Similarly, the `seq()` documentation contains
    both `seq.int()` and `seq_len()`. I also don’t like how there’s both
    `readline()` and `readLines()` or `nrow()` and `NROW()`. Or how
    about `all.equal()` and `anyDuplicated()`? There’s even all of those
    functions with leading capitals like `Vectorize()` or the funprog
    stuff. I could go on…
-   The above issue gets even worse if we discuss functions that you’d
    expect to exist but don’t. For example, we have `write()` but not
    `read()` (the equivalent is probably `scan()`).
-   Argument names are also inconsistent. Most of the apply family calls
    its function argument `FUN`, but `rapply()` and the funprog stuff
    use `f`.
-   Related functions sometimes expect their arguments to be given in a
    different order. For example, except for `mapply()`, the entire
    apply family wants the data to come before the function, whereas all
    of the funprog functions (e.g. `Map()`, `Filter()`, etc), want the
    reverse. When you realise that you picked the wrong function for a
    job, this makes rewriting your code infuriating.
-   Functions that should be related in theory are not always related in
    practice. For example, `subset()` is not documented with the Set
    Operations (`union()`, `setdiff()`, etc) and works on completely
    different principles. The Set Operations are the extremely dangerous
    functions that remove duplicates from their inputs and apply
    `as.vector()` to them. The `subset()` function is a non-standard
    evaluation tool like `within()`, making it completely different and
    [dangerous in a different way](#4112-non-standard-evaluation).
    Finally, despite it being documented with the Set Operations, none
    of these warnings apply for `is.element()`. I regret every time that
    I wrote off someone’s advice to use `subset()` because of my
    (entirely reasonable!) assumption that it would be a (dangerous) Set
    Operation.
-   Functions with related names sometimes have different effects. For
    example, here is a damning quote from [section 3.2.4 of *Advanced
    R*](https://adv-r.hadley.nz/vectors-chap.html#testing-and-coercion):
    -   “*Generally, you can test if a vector is of a given type with an
        `is.*()` function, but these functions need to be used with
        care. `is.logical()`, `is.integer()`, `is.double()`, and
        `is.character()` do what you might expect: they test if a vector
        is a character, double, integer, or logical. Avoid
        `is.vector()`, `is.atomic()`, and `is.numeric()`: they don’t
        test if you have a vector, atomic vector, or numeric vector;
        you’ll need to carefully read the documentation to figure out
        what they actually do.*”

    Another example is that `any()`, `all()`, and `identical()` are all
    predicate functions, but `all.equal()` and `anyDuplicated()` are
    definitely not.
-   Similar to the above, from [the solutions to *Advanced
    R*](https://advanced-r-solutions.rbind.io/vectors.html#lists):
    -   “*Note that `as.vector()` and `is.vector()` use different
        definitions of "vector!"*”.

    The above quote is then followed by showing that
    `is.vector(as.vector(mtcars))` returns `FALSE`. I’ve found similar
    issues with `as.matrix()` and `is.matrix()`.
-   The language can’t really decide if it wants you to be using lambdas
    or not. For example, the apply family has arguments like `...` and
    `MoreArgs` to make it so you don’t always have to make an anonymous
    function, but the funprog stuff gives you no such choice. The sad
    thing is, I almost always find that I want the lambdas anyway, so
    the apply family’s tools to help you avoid them only serve to
    complicate the documentation.
-   As an enjoyable example of how these inconsistencies can ruin your
    time with R, read the documentation for `Vectorize()`. It’s packed
    with tips for avoiding these pitfalls.

### 4.7.3 Extended Example: Matrices

Let’s talk about matrices. I’ve already discussed some oddities like how
functions like `[`, `$` and `length()` treat them in ways that seem
inconsistent with either the rest of the language or your expectations,
but let’s go deeper:

-   [As covered earlier](#455-named-atomic-vectors), matrices want to
    have rownames and colnames rather than names. This gives us a few
    more inconsistencies to deal with that I didn’t mention at the time.
    The rest of the language has trained you to use
    `setNames(data, names)`. When you do this, `data` is returned with
    its column names changed without any changes to `data`. However,
    matrices want `colnames(data) <- names` and the obvious equivalent
    for `rownames()`. This modifies `data` and does not return it.

    ``` r
    a <- b <- diag(3)
    (colnames(a) <- c("I", "Return", "Me"))
    ## [1] "I"      "Return" "Me"
    a#Changed
    ##      I Return Me
    ## [1,] 1      0  0
    ## [2,] 0      1  0
    ## [3,] 0      0  1
    setNames(b, c("I", "Return", "b"))
    ##      [,1] [,2] [,3]
    ## [1,]    1    0    0
    ## [2,]    0    1    0
    ## [3,]    0    0    1
    ## attr(,"names")
    ## [1] "I"      "Return" "b"      NA       NA       NA       NA       NA      
    ## [9] NA
    b#Not changed
    ##      [,1] [,2] [,3]
    ## [1,]    1    0    0
    ## [2,]    0    1    0
    ## [3,]    0    0    1
    ```

    Not only are the function names inconsistent (why not
    `colNames()`?), the syntax is wildly so. Furthermore, take a look at
    the incomprehensible error message that `colnames()` gives if you
    use `diag(3)` directly rather than assigning it to a variable before
    calling `colnames()`.

    ``` r
    a <- diag(3)
    colnames(a) <- c("Not", "A", "Problem")
     ## > colnames(diag(3)) <- c("Big", "Bad", "Bug")
     ## Error in colnames(diag(3)) <- c("Big", "Bad", "Bug") : 
     ##  target of assignment expands to non-language object
     ## > colnames(a <- diag(3)) <- c("Has", "Similar", "Problem")
     ## Error in colnames(a <- diag(3)) <- c("Has", "Similar", "Problem") : 
     ##  object 'a' not found
    ```

    `setNames()` has no such issue.

    ``` r
    setNames(diag(3), c("Works", "Just", "Fine"))
    ##      [,1] [,2] [,3]
    ## [1,]    1    0    0
    ## [2,]    0    1    0
    ## [3,]    0    0    1
    ## attr(,"names")
    ## [1] "Works" "Just"  "Fine"  NA      NA      NA      NA      NA      NA
    setNames(a <- diag(3), c("Works", "Just", "Fine"))
    ##      [,1] [,2] [,3]
    ## [1,]    1    0    0
    ## [2,]    0    1    0
    ## [3,]    0    0    1
    ## attr(,"names")
    ## [1] "Works" "Just"  "Fine"  NA      NA      NA      NA      NA      NA
    ```

    In truth, I don’t mind either `colnames()` or `setNames()`. I just
    wish that R would pick one way of handling names and stick to it.

-   Unlike anything else in R that I can think of, matrices are happy to
    let you work by row and even have dedicated functions for it, with
    `rowSums()` and `apply(..., MARGIN = 1)` being the obvious examples.
    There is a good reasons for this difference – matrices are always
    one type, unlike things like data frames – but it’s still an
    inconsistency. Said inconsistently leads to code that is tough to
    justify. For instance, I frequently find that I want to treat the
    output of `expand.grid()` as a matrix.
    `unique(t(apply(expand.grid(1:4, 1:4, 1:4, 1:4), 1, sort)))` is one
    of my recent examples. This isn’t too bad, but I honestly have no
    idea why I needed the `t()`. Experience has taught me not to
    question it, which is pretty bad in of itself. R’s inconsistencies
    eventually makes you either fall in to the habit of not questioning
    sudden transformations of your data or forces you to become
    completely paralysed when trying to understand what ought to be
    trivial operations in your code. Doubts like “*is there really no
    better way? R is supposed to be good with this sort of stuff*”
    become frequent when wanting to work by row.

-   So what happens if, when manipulating a matrix, you try to write the
    `sapply()` that the rest of the language has taught you to expect?
    It typically gets treated like a vector in column-order.

    ``` r
    (mat <- matrix(1:9, nrow = 3, byrow = TRUE))
    ##      [,1] [,2] [,3]
    ## [1,]    1    2    3
    ## [2,]    4    5    6
    ## [3,]    7    8    9
    sapply(mat, sum)
    ## [1] 1 4 7 2 5 8 3 6 9
    sapply(mat, max)
    ## [1] 1 4 7 2 5 8 3 6 9
    ```

    The trick for avoiding this is to use numbers as your data argument
    and let subsetting be the function.

    ``` r
    mat <- matrix(1:9, nrow = 3, byrow = TRUE)
    sapply(1:3, function(x) sum(mat[x, ]))
    ## [1]  6 15 24
    sapply(1:3, function(x) max(mat[x, ]))
    ## [1] 3 6 9
    ```

    Better yet, just use `apply()`.

    ``` r
    mat <- matrix(1:9, nrow = 3, byrow = TRUE)
    apply(mat, MARGIN = 1, sum)
    ## [1]  6 15 24
     apply(mat, MARGIN = 1, max)
    ## [1] 3 6 9
    ```

    But why did we have the learn any of this in the first place?

-   Your turn: What does `seq_along(diag(3))` return? `1:3` or `1:9`?
    What if you added a row? What if you added a column? Or is the name
    of that function `seq.along()`? Are you sure? Tempted to check the
    docs? Which docs? Feeling helpless? You should!

-   Many functions that are designed for matrices should be forgotten
    about everywhere else. Several guides warn against using `apply()`
    on non-matrices and I wouldn’t dare use `t()` on a non-matrix (try
    `t(iris)`).

-   On a similar note, I always expect `c()` of a matrix to work in
    row-order. It doesn’t. However, that’s probably more the fault of
    `c()` and I than it is of matrices. There are times when I can’t
    explain `c(mtcars)` to myself.

-   Named matrices are named atomic vectors, so they break in the ways
    [discussed earlier](#455-named-atomic-vectors). This puts you in a
    dilemma when you’re using data that’s essentially only one type: Do
    you keep it as a matrix and lose the awesome subsetting powers of a
    data frame? Or do you make it in to a data frame and lose the power
    to work by row that matrices give you? At times, I’m tempted to
    forget that I named the matrix in the first place and just
    manipulate it like a mathematician. None of these solutions are
    good.

Overall, matrices are so inconsistent with the rest of the language that
your matrix-manipulation code never looks right. It leaves you with an
awful sense of unease.

### 4.7.4 The Error Messages

Something to mention while we’ve still got some bad error messages fresh
in our minds: People often say that R’s error messages aren’t very good
and I’m starting to agree. Errors like “*`dim(X)` must have a positive
length*” are useless when you’re not told which function in the line
that threw the error had that error, what `X` is, or in the very worst
cases, what line the error was even in. This means that almost any error
that R throws is going to require you looking through both the result of
`traceback()` (to find where the error happened) and the documentation
(to identify the problematic argument). It seems that this issue gets
even worse when you try to do statistics. Warnings like “*Warning
message: In `ks.test(foo, bar)` : ties should not be present for the
Kolmogorov-Smirnov test*” don’t even tell you where the tie was. Was it
in one of my arguments? Is it some technical detail of the test? It is
somewhere safe to ignore? You don’t know and R won’t tell you unless you
study the documentation. Worst come to worst, you have to read the code
or learn the secret for getting `traceback()` to work on warning
messages. And yes, that last bit is something that you have to learn. It
makes warnings messages a lot harder to debug than errors.

Of course, the more worrying issue is when R gives you no
warnings/errors at all. I’d much rather have a bad error message than
none at all, but a bad error message is still annoying.

### 4.7.5 Mapply Challenge

Maybe you think I’m clutching at straws? I admit, I do sometimes wonder
if my outrage is unjustified. Let’s settle this with a challenge. If you
win, then by all means close this document and write me off as a madman.
If you lose, then maybe I’ve got a point. Okay, here’s your challenge:

|                                                                                                                                                                                                                                                                                                                                                                                  |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **CHALLENGE**                                                                                                                                                                                                                                                                                                                                                                    |
| Taking in to account R’s vector recycling rules, figure out how `mapply()`’s `MoreArgs` and `...` arguments differ and when you would want to pass something as a `MoreArgs` argument rather than in the `...` argument. No cheating by going online (trust me, it won’t help much anyway). Solve this without leaving your R IDE. You’re encouraged to check the documentation. |

If my criticisms are true, you will find that `mapply()`’s documentation
is of little help and that your confidence in your R knowledge is too
small to make an educated guess.

|                                                                                                                 |
|:----------------------------------------------------------------------------------------------------------------|
| **HINT 1**                                                                                                      |
| Don’t try to cheat by looking at `mapply()`’s code; Most of it is in C and therefore will be of no help to you. |

|                                                                                                                                                                                                                             |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **HINT 2**                                                                                                                                                                                                                  |
| You might think that the documentation for `sapply()` will help you, but it’ll actually mislead you because `mapply()`’s `...` is essentially `sapply()`’s `X` and `sapply()`’s `...` is most like `mapply()`’s `MoreArgs`. |

Solution below. Time to stop scrolling.

|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **SOLUTION**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| .                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| .                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| .                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| .                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| .                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| .                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| .                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **How do `MoreArgs` and `...` differ?**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| It’s tough to explain. `mapply()` uses the default vector recycling rules for the `...` arguments but reuses every element of `MoreArgs` for each call. Because the `MoreArgs` argument must be a list and R recycles the elements of lists (e.g. using a length 1 list as a `...` argument will have the element of that list reused for each call), the difference is subtle to the point of near invisibility. Ultimately, `MoreArgs = list(a, b, c)` is equivalent to using `list(a)`, `list(b)`, and `list(c)` as three separate `...` arguments. The answer is therefore that `MoreArgs` only exists as syntactic sugar for this `...` case.                                               |
| **When use `MoreArgs` rather than `...`?**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Beyond what I’ve already said, I barely have any idea. If you want to keep some function arguments fixed for each call, then just use an anonymous function. I struggle to invent a useful example of where I’d even consider using `MoreArgs`, never mind one that doesn’t look tailor-made to make the anonymous function option look better. The one and only example that the documentation gives for using `MoreArgs` does not help here. Their example of `mapply(rep, times = 1:4, MoreArgs = list(x = 42))` is identical to `mapply(rep, times = 1:4, list(x = 42))`. Read that again: **You can get identical functionality by deleting the thing that they’re trying to demonstrate!** |
| **Bonus**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Did you notice that the documentation for `mapply()` has a notable omission? It doesn’t mention this, but you can call `mapply()` without the `...` argument, e.g. `mapply(rep, MoreArgs = list(1:4))`. You won’t get sensible output, but you also don’t get any warnings or errors.                                                                                                                                                                                                                                                                                                                                                                                                            |

If I’ve won this challenge, then allow me to take a victory lap by
making the following point: By giving you the options of using `...`,
`MoreArgs`, or an anonymous function to do the same task, R gives you
plenty of room to confuse yourself without providing any help in its
documentation. Either provide fewer options, document them better, or
make them so commonplace and consistent within the language that I only
need to understand it once in order to understand it everywhere!

### 4.7.6 Stealing from the Tidyverse

On top of many of the things that I’ve already said about the apply
family, fans of the Tidyverse, particularly `purrr`, often point out of
the following inconsistencies. They’ve never bothered me, but they’re
undeniably correct. It makes me wonder why we can’t just give all of the
apply family a `simplify` argument that takes either `TRUE`, `FALSE`, or
whatever `vapply()` would consider a valid `FUN.VALUE` argument.

-   Probably due to its use of `as.vector()`, `apply()` has no
    `simplify` argument. Version 4.0.6 did something about this, but
    I’ve yet to get my head around it.
-   There is no equivalent to `vapply()` for any member of the apply
    family other than `sapply()`. Among others, neither `tapply()` nor
    `mapply()` have one.
-   You can argue that some functions are missing in base R. For
    example, if we think of `lapply()` as “*list in, data frame out*”
    and `by()` as “*data frame in, list out*”, and so on for `sapply()`
    and others, then where is the “*array in, list out*” function?
-   This might be a repeat of my complaints about the documentation, but
    there are several apply family functions that hardly anyone uses or
    understands. Few understand `eapply()` and even fewer use it. Just
    about everyone who uses R for stats has had to invest a few hours
    getting their head around `tapply()`, but at least that’s worth it.
    As for the other obscure ones – e.g. `simplify2array()`, `rapply()`
    – I honestly cannot recall ever using them or seeing them used.

## 4.8 The Community

There are some community issues that make R harder to learn and work
with. Put together with the earlier issues, it means that help can often
neither be found inside nor outside of R.

-   The community can’t agree on if we should be using base R’s data
    frames, the Tidyverse’s tibbles, or the `data.table` package. Even
    if you find one that you like, you can bet that you will someday
    want to use a package that requires another. For example, if your
    friendly neighbourhood package author made use of the default
    `drop = TRUE` argument when manipulating data frames, you’re not
    going to be allowed to use tibbles. Protecting the user from this
    isn’t easy, because both data.tables and tibbles will return `TRUE`
    for `is.data.frame()`.
-   Much like the data frame point, the community is also split on which
    OOP system it should use. For example, `R6` gets about as much
    mention as RC, even though they both do the same job. Depending on
    when they were made, you also see some popular libraries that are
    fully committed to some particular OOP system. For example, you will
    see a lot of S3 in base R, but the `Bioconductor` package sticks to
    S4. Fortunately, all of this only becomes a problem when you want to
    contribute to these packages. If all goes well, you will never
    really notice which OOP system has been used; You will just have
    polymorphic code and not need to question it.
-   A lot of people seem to treat R as secondary to the Tidyverse
    packages. Many books essentially ignore base R or go out of their
    way to tell you why the Tidyverse is better – *Advanced R* is a good
    example of the latter, particularly the second edition, so much so
    that I needed to read both editions – and many R Q&A sites will give
    you a Tidyverse solution to pretty much any problem, even if it can
    be solved almost as well in base R. You sometimes see the same with
    `data.table`, but it’s much less common.
-   The popularity of the Tidyverse is a major blow to your motivation
    to learn R. Why would anyone want to learn a language that is
    treated as secondary to some packages? Worse still, if that turns
    out to be the best way to use R, then you’re forced to admit that R
    is a polished turd with a fragmented community. Why would you ever
    knowingly use a polished turd? The popularity of the Tidyverse is
    possibly the strongest piece of evidence that not only does R suck,
    the community knows it.
-   If base R is best ignored in favour of packages, or at least if the
    community thinks so, then how are you expected to actually learn R?
    When do you stop learning the base library and move on?
-   Data science people have a strong preference for Python, so a lot of
    good tutorials that should be in R are only available in Python.
    I’ve also noticed at least one case where the R package
    documentation is clearly inferior to the Python equivalent, despite
    the gap in functionality not being as wide.
-   R’s functional programming aspects are so strong that loops,
    particularly `for` loops, are considered a code smell. This goes
    double in the Tidyverse, with the *R for Data Science* book not even
    introducing them until chapter 21 (of 30). There are practical
    reasons for this, mostly in relation to the apply family’s code
    being written in C and therefore being faster than most R loops.
    However, it encourages you to do some silly things. For example, you
    have to make a judgement call between writing a `for` loop that is
    inherently fast but slowed down by being written in R or writing an
    `sapply()` that ought to be slow but is speeded up due to `sapply()`
    calling C code. This issue also affects how you present your code.
    Calls to the apply family are inherently one-liners, so it’s
    difficult to find the right way to present/comment them when they
    become complex. You either end up introducing unnecessary variables
    in to your code or indenting it in unconventional ways. The
    Tidyverse’s solution – piping – often does the trick, but it openly
    admits to not being a universal solution. The new `|>` base R pipe
    doesn’t do the trick either. As any advocate of the Tidyverse will
    tell you, base R just isn’t designed for piping.

## 4.9 Generic Functions Again

R’s generic function OOP systems are yet another source unpredictability
and internal inconsistency. [They’re very cool](#353-generic-functions)
and I must admit that I’ve not used them much, but what I’ve seen when
trying to use them has discouraged me. Most of what I’m about to say is
about S3, but you’ll rarely find much said about R’s OOP systems at all.
It’s not really any surprise. S3, S4, RC, and any of the OOP systems
that come from packages are all openly admitted to being bolted-on to R
rather than something that was part of its design from the early days.
Points like the below make discovering this fact unavoidable.
Presumably, this is what the Julia fans are talking about when they say
that they’re the only ones who have a generic function OOP system that
is baked-in to their language. I’ve never used Julia or enough S4 or RC
to be able to really comment, but I bet they’re right.

### 4.9.1 The Class System

The class system is a mess and the docs do a poor job of explaining it.
Good luck understanding it without a book like *Advanced R* and a
package like `sloop`. I believe that this problem is mostly isolated to
S3, but I’ve not used enough S4 to be able to say that with any
certainty. Here are some problems that you’re likely to encounter early
on:

-   Functions like `mode()` and `storage.mode()` exist only for
    compatibility with S. As an R user, they exist only to increase your
    confusion. This is particularly common when reading the language
    definition; It never shuts up about the modes of things.

-   *Advanced R* makes [a strong
    case](https://adv-r.hadley.nz/base-types.html#numeric-type) for
    `is.numeric()` being inconsistent, particularly regarding its
    interaction with S3.

-   The documentation for `class()` uses vague statements like “*method
    dispatch may use more classes than are returned by `class(x)`*”.
    May? **MAY???** What am I supposed to do with that? Where do I look
    for more info? It mentions `.class2()`, but warns you against using
    it. Why? It doesn’t say! Did you think that `.class2()` would have
    its own documentation somewhere else? It doesn’t! All of the
    documentation for `.class2()` is in the docs for `class()` and most
    of that is a warning to not use it!

-   Call `class()` on a matrix and you will see that they have a few
    classes. However, `is.object()`, which has docs that correctly state
    that it will return `TRUE` for anything with a class attribute,
    returns `FALSE`.

    ``` r
    a <- diag(3)
    class(a)
    ## [1] "matrix" "array"
    is.object(a)
    ## [1] FALSE
    ```

    Why? Because `class()` also returns implicit classes – as detailed
    in its docs – which `is.object()` ignores because implicit classes
    aren’t part of the class attribute. The documentation for
    `is.object()` does not mention this fact and the `class()`
    function’s output does not tell you which classes are implicit. Can
    you see the potential for confusion? The docs never lied or even
    mislead, but they make naivety fatal. Maybe that’s starting to
    become a theme.

-   So what base R function actually returns the non-implicit classes? I
    think that you have to use `attr(foo, "class")`. I say “*I think*”
    because the documentation for `class()` does not offer any help.

-   Don’t ask what determines the implicit classes of an object or how
    S3 dispatch occurs with them. It’s far too complicated and not
    clearly documented in any place that I know of. It’s also what’s
    used for dispatching on anything without a class attribute, such as
    matrices. Good luck with that!

-   Don’t ask what an object is either. The community will tell you that
    `is.object()` is poorly named and the language definition will tell
    you that pretty much everything in R is an object. However, there
    are functions like `names(x)<-` that will not work on several types
    of objects (e.g. anything anonymous) despite their documentation
    saying that `x` can be “*an R object*”. I’d give examples, but you
    really don’t want to think too hard about this.

-   The `[` and `[[` functions like to drop the attributes from your S3
    objects, meaning that you almost always have to write a `[` and `[[`
    method for them. On the bright side, this is documented behaviour.

### 4.9.2 Existing Functions

The generic functions that you’ll find in the base and other common
libraries have a few surprises:

-   Some functions appear to be generic, but aren’t. For example, both
    `abline()` and `sample()` can behave differently depending on what
    sort of input you gave them, but that’s because they’re hard-coded
    to do so. If you expect to find some `abline.lm()` function or be
    able to write your own `abline.myClass()` method, you’ll be
    disappointed.
-   In stats libraries, I’ve seen the ability to overload function names
    abused. For example, why is the function to return a one-hot encoded
    dataset in the caret library `predict()`? I’m pretty sure that my
    Bayesian Statistics lecturer also showed me a few cases where
    `anova()` definitely does not do an ANOVA. I’m out of practice, but
    I think that the R FAQ gives [one such
    example](https://cran.r-project.org/doc/FAQ/R-FAQ.html#Why-does-the-output-from-anova_0028_0029-depend-on-the-order-of-factors-in-the-model_003f).
-   Although you can usually write your own functions to fix this, it’s
    annoying when you expect a generic function to behave in a sensible
    way on your input, only to discover that it has no special case for
    your type of input and treats it like any other vector. To repeat an
    earlier example, why does `rep(matrix(1:4, nrow = 2, ncol = 2), 5)`
    treat the input matrix like it’s a normal vector? I can’t imagine
    anyone calling `rep()` on a matrix and wanting to work
    element-by-element rather than repeating the matrix.
-   Because of S3, it’s now considered bad practice to write function
    names in the form `foo.bar()` because they look like extensions to
    `foo()`. Open up any standard R library and you will see countless
    functions written in this form that are not extensions to anything.
    `t()` and `t.test()` are the most cited example.

### 4.9.3 Internal Generics

This is tough to explain, but I’ll try. If you consult
`?"internal generic"`, you will find a big list of functions that you
cannot extend properly with S3. Specifically, anything on that list
cannot be extended to dispatch on any type of object for which
`is.object()` returns `FALSE`. For example, writing a `rep.matrix()`
function that does what my earlier example wanted is easy, but because
`rep()` is on that list and matrices are not objects in this sense,
`rep()` will not dispatch to `rep.matrix()` when given a matrix. The
documentation for `rep()` and other functions that share this
misbehaviour do not do much to help the reader discover this fact.
*Advanced R* has the only good explanation that I’ve found for this, but
it’s the sort of thing where you either have to read
[two](https://adv-r.hadley.nz/base-types.html)
[chapters](https://adv-r.hadley.nz/s3.html) or the first edition’s [OO
Field Guide](http://adv-r.had.co.nz/OO-essentials.html). The short
explanation is “*internal generics are written in C and therefore only
understand non-implicit classes and whatever internal R type the C code
ultimately gets fed*”.

-   Did you notice that `length()` is on the list mentioned above? This
    explains the inconsistency in how it behaves on data frames and
    matrices. You cannot properly extend internal generics with S3, so
    you cannot change how `length()` behaves on implicitly classed
    input. Data frames are non-implicitly lists and matrices are
    non-implicitly atomic vectors, so that’s how `length()` treats them.
    This issue isn’t unique to just data frames and matrices. *Advanced
    R* has [a comical example in its S3
    chapter](https://adv-r.hadley.nz/s3.html#object-styles): Linear
    models, which are non-implicitly lists, have a length of about 12!
    My personal favourite is giving it quoted input:

    ``` r
    length(quote(5^30))
    ## [1] 3
    length(quote(5^30 + 1))
    ## [1] 3
    length(quote(5^30 + 12))
    ## [1] 3
    length(quote(1))
    ## [1] 1
    length(quote(length(1)))
    ## [1] 2
    ```

    You will find issues like this – i.e. unexpected and tough to
    explain output – whenever using or extending most internal generics;
    `length()` is just the easiest example to show.

-   Did you notice that I lied about data frames? The careful reader
    will notice that, because they have the real `data.frame` class,
    data frames don’t have any implicit classes. That’s a thing, by the
    way, having a real class means not having implicit classes.

    ``` r
    attr(mtcars, "class")
    ## [1] "data.frame"
    class(mtcars)
    ## [1] "data.frame"
    is.object(mtcars)
    ## [1] TRUE
    ```

    This means that `length(someDataFrame)` cannot possibly dispatch to
    some `length.list()` internal method. Further inspection reveals
    that there is no S3 (i.e. non-internal) `length.data.frame()`
    method. What actually happens is that R tries to find
    `length.data.frame()`, fails, and then tries to find
    `length.default()`, only to fail again and get pointed to the
    internal C code that presumably treats data frames just like lists.
    This happens even though data frames do not have implicit classes.
    Enjoying the complexity?

-   So what happens if you try to write a `length.data.frame()` method –
    something that is totally allowed because data frames return `TRUE`
    for `is.object()` and `length()` is an internal generic function –
    and have `length()` dispatch to it? You’ll probably break R. I once
    redefined the length of a data frame to be its number of rows and I
    got a stack usage error. Please, take a few seconds to appreciate
    all of the complexity that we’ve just had to work with just for R’s
    most basic object system.

Much of the above examples makes the class system – and therefore S3
dispatch – impossible to clearly explain. Any real explanation would be
so full of exceptions that it would become incomprehensible. The only
way to explain it is to ignore the contradictions for as long as
possible, meaning that you must be given incorrect information until
you’re ready to read about the exceptions. This ultimately means that
you cannot even find a good reference manual for the class system,
because you never know if you’re reading the whole truth or not.
Furthermore, if this is at all representative of the complexity of S3,
how can anyone be expected to have the patience to even begin learning
S4? I know that it’s dishonest to blame S4 for the sins of S3, but I
wouldn’t blame any newcomer to R’s OOP for doing so.

### 4.9.4 S4

Okay then, let’s talk about S4. I promise that this will be an easier
read than the earlier sections. I’m quite ignorant of S4, as I’ve
already admitted to, so I’ve got very little to say. Regardless, the
following seems clear:

-   Everything that I’ve read about S4 gives me the impression that it
    has far fewer stupid technicalities than S3. If I’m right, then I
    find that laughable. How have we managed to make S3 more complicated
    than S4? S3 should be extremely simple, but the technicalities of
    the previous few sections are too easy to stumble upon.

-   If [*Advanced R’s* chapter on S4](https://adv-r.hadley.nz/s4.html)
    is to be trusted, then the official documentation for S4 contains a
    lot of bad advice. I’ve not looked closely, but I have noticed that
    it shares R’s tendency to put many functions in one page of
    documentation and then not give examples for many of them. For
    example, `?getMethod` documents five functions, but only gives
    examples for two. Similarly, `@` has no examples in its
    documentation.

-   S4 has some strange semantics. Why call something that is sometimes
    not a predicate function `is()`? Why does it use an `@` operator to
    do what the rest of R would use `$` for?

    ``` r
    is(mtcars)
    ## [1] "data.frame" "list"       "oldClass"   "vector"
    ```

-   As far as I can tell, S4 doesn’t inform you if there was some
    ambiguity in your dispatch, such as if it had to pick one option
    from two equally appropriate potential dispatches. I think that
    unless there is no appropriate method to dispatch to, it has some
    internal rules that silently handle these cases, meaning that there
    is no ambiguity even when there probably should be. In other words,
    it may misbehave by silently resolving the developer’s ambiguities.
    Without being too spiteful, by now I find it quite easy to believe
    that R has an OOP system that silently misbehaves.

## 4.10 Factor Variables

Section 8.2 of [*The R
Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf) calls
the factor and ordered variables “*chimeras*”. This is exactly the right
criticism. Under the hood, they’re S3 objects with integers as their
base type and a character vector – the levels – as an attribute. When
using these variables, it is difficult to predict if R will treat them
as their integer base type, as their character vector levels attribute,
or as a factor object. And that’s not even mentioning how the labels
come in to it. [*The R
Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf) has said
more than I will and gives some examples of their unpredictable
behaviour, but here are some points from my own experience:

-   There is no base R function for extracting the original object from
    its corresponding factor. To extract your original set of numbers
    (assuming that they were numbers, if not, you get nonsense) from a
    factor variable called `f`, the documentation tells you to use
    either `as.numeric(levels(f))[f]` or the slower
    `as.numeric(as.character(f))`. Let’s use a bit more code than usual
    and show off what each of these functions do before and after
    composition:

    ``` r
      (withoutLabels <- factor(rep(seq(from = 2, by = 2, to = 10), 3)))
    ##  [1] 2  4  6  8  10 2  4  6  8  10 2  4  6  8  10
    ## Levels: 2 4 6 8 10
      (withLabels <- factor(rep(seq(from = 2, by = 2, to = 10), 3), labels = LETTERS[1:5]))
    ##  [1] A B C D E A B C D E A B C D E
    ## Levels: A B C D E
      fList <- list(withoutLabels, withLabels)
      #Just to make sure that we're on the same page, here's the output of str().
      #The internal integers are in plain site.
      lapply(fList, str)
    ##  Factor w/ 5 levels "2","4","6","8",..: 1 2 3 4 5 1 2 3 4 5 ...
    ##  Factor w/ 5 levels "A","B","C","D",..: 1 2 3 4 5 1 2 3 4 5 ...
    ## [[1]]
    ## NULL
    ## 
    ## [[2]]
    ## NULL
      #Nothing surprising to start:
      lapply(fList, levels)
    ## [[1]]
    ## [1] "2"  "4"  "6"  "8"  "10"
    ## 
    ## [[2]]
    ## [1] "A" "B" "C" "D" "E"
      #as.character() returns the non-attribute part of what you get when you print the factor
      #i.e. the result of mapping its internal integers to its character vector of levels.
      #Notice that these are characters. It's not obvious from printing your factors that
      #the non-attribute part becomes a character.
      lapply(fList, as.character)
    ## [[1]]
    ##  [1] "2"  "4"  "6"  "8"  "10" "2"  "4"  "6"  "8"  "10" "2"  "4"  "6"  "8"  "10"
    ## 
    ## [[2]]
    ##  [1] "A" "B" "C" "D" "E" "A" "B" "C" "D" "E" "A" "B" "C" "D" "E"
      #Calling `as.numeric()` on a factor does not return the original numbers.
      #It returns the underlying integers.
      #Why would you ever want or expect these?
      lapply(fList, as.numeric)
    ## [[1]]
    ##  [1] 1 2 3 4 5 1 2 3 4 5 1 2 3 4 5
    ## 
    ## [[2]]
    ##  [1] 1 2 3 4 5 1 2 3 4 5 1 2 3 4 5
      #Subsetting with factors always treats them as their integer base type.
      #If the factor fundamentally has nothing to do with integers
      #(e.g. if you made the factor from something that was originally a set of characters),
      #then you can expect nonsense.
      #If the factor did originally have something to do with integers,
      #then you're probably going to be very confused because it hasn't subsetted with
      #the numbers that you get from printing the factor.
      #In short, it's almost never a good idea, but R lets you do it anyway.
      #Now ask yourself: What is the point of having a categorical data type if
      #it's not practical to subset with?
      lapply(fList, function(f) levels(f)[f])
    ## [[1]]
    ##  [1] "2"  "4"  "6"  "8"  "10" "2"  "4"  "6"  "8"  "10" "2"  "4"  "6"  "8"  "10"
    ## 
    ## [[2]]
    ##  [1] "A" "B" "C" "D" "E" "A" "B" "C" "D" "E" "A" "B" "C" "D" "E"
      lapply(fList, function(f) as.numeric(levels(f))[f])
    ## Warning in FUN(X[[i]], ...): NAs introduced by coercion
    ## [[1]]
    ##  [1]  2  4  6  8 10  2  4  6  8 10  2  4  6  8 10
    ## 
    ## [[2]]
    ##  [1] NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA
      lapply(fList, function(f) as.numeric(as.character(f)))
    ## Warning in FUN(X[[i]], ...): NAs introduced by coercion
    ## [[1]]
    ##  [1]  2  4  6  8 10  2  4  6  8 10  2  4  6  8 10
    ## 
    ## [[2]]
    ##  [1] NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA
    ```

-   As you’ve probably noticed by now, factor variables are inherently
    complex enough that they need you to either carefully read their
    documentation or be an R master before you can use them with
    confidence. You cannot tell me that `as.numeric(levels(f))[f]` made
    perfect sense when you read it or that you would have come up with
    it yourself. It’s arcane. Half of the reason why I let the code
    speak for itself above, rather than adopting my usual bullet point
    style, is because I hardly even trust myself to describe them. In
    fact, even whoever wrote the R FAQ seems to have not mastered the
    art. In [section
    7.10](https://cran.r-project.org/doc/FAQ/R-FAQ.html#How-do-I-convert-factors-to-numeric_003f),
    they suggest `as.numeric(levels(f))[as.integer(f)]` for the same
    task as what we’ve covered above. Can you see the redundant function
    call?

-   When writing example code, factors want to be called `f`, just like
    functions do. This offends me.

-   On the bright side, it looks like R version 4 is steadily trying to
    fix factors. Every few updates, we see a minor change. For example,
    before version 4, you had to pass `stringsAsFactors = FALSE` to a
    lot of functions. This was to stop R creating factor when you hadn’t
    asked for them. It was widely considered extremely annoying because
    there is nothing in the way that data frames print that signals to
    the reader that they’re looking at a factor variable. For all you
    knew, you were looking at a character vector. You often would not
    discover your mistake until you had a serious error.

Personally, I’m afraid to use factor variables. Their unpredictability
makes any code that uses them dramatically more complex, even if you’re
confident that you know their rules.

## 4.11 Syntactic Sugar

The syntactic sugar is a source of problems, often to such a great
degree that your best solution is to completely avoid the sugar. I’ll
start with some small cases before splitting some of the bigger ones in
to sections.

-   You usually only see this when dealing with `names()`, but having a
    function that is both a setter and getter is a guaranteed source of
    confusion and found more than once in R. For example,
    `names(output)` will give you the names of `output`, but
    `names(output) <- c("Alice", "Bob")` will change `output`’s names
    (it’s sugar for some complicated `"names<-"` nonsense).

    ``` r
    names(mtcars)
    ##  [1] "mpg"  "cyl"  "disp" "hp"   "drat" "wt"   "qsec" "vs"   "am"   "gear"
    ## [11] "carb"
    names(mtcars) <- LETTERS[1:11]
    head(mtcars, 2)
    ##                A B   C   D   E     F     G H I J K
    ## Mazda RX4     21 6 160 110 3.9 2.620 16.46 0 1 4 4
    ## Mazda RX4 Wag 21 6 160 110 3.9 2.875 17.02 0 1 4 4
    ```

    Now what do you think `names(foo) <- names(bar)` does? Seriously,
    can you guess? I can think of roughly four realistic guesses. Is it
    even valid syntax? Here’s the truth:

    ``` r
    names(mtcars) <- LETTERS[1:11]
    a <- rep(c("example", "text"), length.out = 11)
    names(a) <- LETTERS[12:22]
    a
    ##         L         M         N         O         P         Q         R         S 
    ## "example"    "text" "example"    "text" "example"    "text" "example"    "text" 
    ##         T         U         V 
    ## "example"    "text" "example"
    names(a) <- names(mtcars)
    a
    ##         A         B         C         D         E         F         G         H 
    ## "example"    "text" "example"    "text" "example"    "text" "example"    "text" 
    ##         I         J         K 
    ## "example"    "text" "example"
    ```

    This is probably the result that you guessed, but syntax shouldn’t
    leave you guessing. Where possible, I try to stick to `setNames()`.

-   The syntactic sugar sometimes leads to surprising syntax. For
    example `names(output[2]) <- "foo"` doesn’t work, but
    `names(output)[2] <- "foo"` does.

-   As is extremely well documented, `T` and `F` can be used in place of
    `TRUE` and `FALSE`, but you should never do this because `T` and `F`
    are just variables that can be overwritten in your code. Why let us
    do something that we never should? To my surprise, there’s actually
    a sensible answer. [Section 3.3.3 of the R
    FAQ](https://cran.r-project.org/doc/FAQ/R-FAQ.html#Others) says that
    S had `T` and `F` as reserved words, but R changed that to allow
    variables called `"T"` and `"F"` to appear in your datasets. I can
    see the reasoning behind both S’s approach and R’s change to it, but
    I still think that R’s approach of “*you can do this, but never do*”
    is obviously wrong. My suspicion is that the third option of “*just
    make `T` and `F` not mean anything until they’re assigned to*” will
    never be taken, because the current (and dangerous) approach helps
    with backwards compatibility. I don’t think that it’s a good trade.

-   Although I like R’s many functional programming tools, the
    temptation to try to use them to solve every problem is very strong.
    I’ve wasted countless hours trying to pick the right one of
    `sapply()`/`lapply()`/`mapply()`/`Filter()`/`Map()`… (not to mention
    their various arguments) when I really should’ve just written the
    `for` loop. This is more my fault than it is R’s, but it’s a curse
    that every intermediate R user will suffer from. It’s a price that
    any R expert will tell you was worth it in the end. However, it’s
    still a price that I don’t enjoy paying. It wouldn’t be so bad if R
    had less such functions, better error messages, or more consistency
    between these functions, but we’ve already discussed that can of
    worms. Don’t think that I’m advocating for `purrr` here. It has so
    many functional programming tools that it arguably makes the
    situation worse. I’ll cover its costs and benefits
    [later](#55-purrr).

### 4.11.1 Sequences

The `:` operator is absolutely lovely… until it screws you. The solution
is to prefer the `seq()` functions to using `:`. Some quick examples:

-   Stuff like `i in 1:n` is great, but if you accidentally have
    `n <= 0`, it silently gives behaviours that you probably don’t want.

    ``` r
    1:2
    ## [1] 1 2
    1:1
    ## [1] 1
    1:0
    ## [1] 1 0
    1:-1
    ## [1]  1  0 -1
    ```

    `seq_len()` is better behaved, so I try to stick to it.

    ``` r
    seq_len(2)
    ## [1] 1 2
    seq_len(1)
    ## [1] 1
    seq_len(0)
    ## integer(0)
    #seq_len(-1) is an error.
    ```

-   `:` has operator precedence issues. You might expect stuff like
    `-6/2:3` to generate `(-(6/2)):3` i.e. `-3:3`. It doesn’t.

    ``` r
    -6/2:3 #Treated as -6/(2:3)
    ## [1] -3 -2
    ```

    I’ll leave `-6/2:6/2` as an exercise for the reader. I’d like to
    keep things simple and say that the trick is that `:` is always
    evaluated first, but that’s actually not true. Even if we’re only
    talking about arithmetical operations, exponentiation is done before
    `:` is applied.

    ``` r
    3^1:5 #Treated as (3^1):5
    ## [1] 3 4 5
    ```

-   Can you guess what `data[-1:5]` returns? I can’t either, so don’t
    ever try it. If you must know, it’s actually an error.

As I’ve said, `seq()` and its related functions usually fix this issue.
The only real disappointment with `seq()` itself is that its
documentation warns against not naming its arguments, so you’re forced
to write the long-winded `seq(from = 0, to = 100, by = 6)` rather than
just `seq(0, 100, 6)`.

### 4.11.2 Non-standard Evaluation

The documentation for several functions with non-standard evaluation,
e.g. `with()` and `subset()`, explicitly warns the user to not use them
when programming. This is a source of a number of problems, both
practically and in a meta sense:

-   First of all, the existence of functions that are not for
    programming use is abhorrent.
-   They’re excellent syntactic sugar, so I hate not being able to use
    them! For example, I’d argue that
    `within(data, rm(colName1, colName2))` is the best way to remove
    unwanted columns from my data: It does not require me to quote or
    escape my column names, does not require me to put `data$` before
    everything, does not require me to pass that annoying `drop = FALSE`
    argument, warns me if I am trying to remove a column that is not in
    my data, and reads almost like English. All in all, that’s some
    major advantages over using `[`. They both have some misbehaviour if
    your column names are duplicated, but that’s not very relevant here.
-   The documentation for a lot of the functions that use non-standard
    evaluation warn you to take care with them, but they do very little
    to tell you how or why. I’ve searched high and low, but I sincerely
    believe that there is almost nothing in R’s documentation that tells
    you what can go wrong with these functions. Seriously, if you can
    find it, let me know. I’ve even read the [Thomas Lumley
    article](https://developer.r-project.org/nonstandard-eval.pdf) that
    some of the docs tell you to check and I still can’t find much of
    relevance. As with `.class2()`, I find R’s habit of putting
    unexplained warnings in its documentation deeply maddening.
-   Because you don’t know when it’s safe to use these functions and
    when it isn’t, you feel incredible anger when the perfect solution
    to your problem is to use one of them. You get in situations like
    “*I could either easily do this with `with()` or write out an
    `mapply()` with a long-winded anonymous function…*” and always have
    to choose to do things the hard way. It makes you want to never use
    R outside of the REPL. This is one part where the Tidyverse
    completely destroys base R.
-   So what can actually go wrong with them? To be honest, I don’t
    really know. A lot of these functions internally rely on a function
    called `substitute()`, which has special behaviour when it tries to
    interact with anything defined in the global environment, so it’s
    slightly difficult to invent easy-to-type examples of these
    functions misbehaving. All that I’ve managed to find is:
    -   I’ve been told that if something exists in the calling
        environment of your function with non-standard evaluation, but
        not in the data that you’re trying to work on, then you’re in
        trouble. I’ve yet to be able to invent an example that shows
        unexpected behaviour.
    -   Code like `subset(data, exampleCol > x)` will misbehave if `x`
        is a column in `data` but you intended it to come from the
        calling environment.

    ``` r
    head(airquality)
    ##   Ozone Solar.R Wind Temp Month Day
    ## 1    41     190  7.4   67     5   1
    ## 2    36     118  8.0   72     5   2
    ## 3    12     149 12.6   74     5   3
    ## 4    18     313 11.5   62     5   4
    ## 5    NA      NA 14.3   56     5   5
    ## 6    28      NA 14.9   66     5   6
    head(subset(airquality, Wind * 5 > Temp))
    ##    Ozone Solar.R Wind Temp Month Day
    ## 5     NA      NA 14.3   56     5   5
    ## 6     28      NA 14.9   66     5   6
    ## 8     19      99 13.8   59     5   8
    ## 9      8      19 20.1   61     5   9
    ## 15    18      65 13.2   58     5  15
    ## 18     6      78 18.4   57     5  18
    Temp <- 90000000
    head(subset(airquality, Wind * 5 > Temp))#Identical to the previous call.
    ##    Ozone Solar.R Wind Temp Month Day
    ## 5     NA      NA 14.3   56     5   5
    ## 6     28      NA 14.9   66     5   6
    ## 8     19      99 13.8   59     5   8
    ## 9      8      19 20.1   61     5   9
    ## 15    18      65 13.2   58     5  15
    ## 18     6      78 18.4   57     5  18
    ```

    I think that this is the case that `with()`’s documentation is
    trying to warn you about. `subset()`’s documentation does not appear
    to contain any such warning, unless you’re generous enough to count
    “*the non-standard evaluation of argument subset can have
    unanticipated consequences*”. How hard would it have been to give an
    example like the one that I’ve just given?
    -   [*Advanced R* tries to explain some other
        issues](https://adv-r.hadley.nz/evaluation.html#base-evaluation),
        but the extent of them has never been completely clear to me.

Of all the problems that I’ve written about, this section’s probably
bother me the most. So many of R’s problems could be sidestepped if we
could fearlessly use `with()` and `subset()` at all times, but R’s nasty
habit of not explaining the dangers that it warms you of leaves me in
constant paranoia.

## 4.12 Missing Features

Some things seems obviously missing from R:

-   For a Scheme-inspired language, the lack of any tail call
    optimisation or any macro system is strange. Then again, being a
    heavily functional language that looks like C is one of the best
    things about R. If it had tail call optimisation or Lisp-like
    macros, it’d probably start to look more like a weird statistical
    version of Lisp.

-   You can only break out of the innermost loop. Unless you refactor,
    there’s no way to be many loops deep and break out of them all with
    one command.

-   R has no `do-while` loop. It’s never bothered me, but I think that’s
    because I’ve never used one in any language. I can see it bothering
    others, but if I need one, then I’m pretty sure that they’re trivial
    to make from a `repeat` loop.

-   Without crude `if(FALSE){}` workarounds, there’s no way to comment
    out blocks.

-   Outside of packages, R lacks any real dictionary, associative array,
    or linked list type. The closest that we can get is matching
    elements to their names [like
    this](https://adv-r.hadley.nz/subsetting.html#lookup-tables). I’ve
    always thought that it seems like a hacky way to get what other
    languages have built in. You can also do it with environments, which
    apparently has O(1) lookup, but I’ve never seen anyone do it. That
    may have something to do with how the base R syntax for creating
    environments from scratch isn’t as nice as its syntax for creating
    lists. You have to name and assign each element individually,
    e.g. `e <- new.env(); e$a <- 1;  e$b <- 2;  e$c <- 3`, rather than
    just `l <- list(a = 1, b = 2, c = 3)`. And if you’re going to use a
    package to fix this syntax issue, then you might as well just use
    one that gives you actual hash tables.

-   Given that R is a maths/stats language, I find the follow omissions
    surprising:

    -   There’s no base function for counting the number of possible
        permutations of a collection of objects.
    -   Despite there being a function for finding the combinations that
        you can make from the elements of a vector, there’s no function
        that does that with repetitions. For example, `combn(1:3, 2)`
        can’t be convinced to include `c(1, 1)`, `c(2, 2)`, and
        `c(3, 3)`.
    -   There’s no built-in big integer class.
    -   Despite supporting equations, R offers no obvious way to
        simplify them.
    -   Although R has some matrix functionality built in, there’s no
        `is.square()` function.
    -   There is no base R function to check if a number is a whole
        number. `is.integer()` checks for integer typing rather than if
        the input is in of itself an integer. The docs even show that
        `is.integer(1)` is `FALSE`. Worse still, these docs actually
        show you the code for a good `is.wholenumber()` function! Why
        couldn’t that be in the base library?

-   Once you’re aware of it, the previous issue starts coming up in
    weird places. This suggests that R’s missing something in its error
    checks. Take a look:

    ``` r
    seq_len(4.8) #Not an error
    ## [1] 1 2 3 4
    1:4.8
    ## [1] 1 2 3 4
    a <- 1:10
    a[4.8]
    ## [1] 4
    a[-4.8]
    ## [1]  1  2  3  5  6  7  8  9 10
    sample(4.8)
    ## [1] 4 1 3 2
    ```

    The pattern is that [R silently truncates the numeric index of
    choice towards
    0](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Indexing-by-vectors).

Admittedly, few if any of these are major, but they’re a bit annoying.

## 4.13 Miscellaneous Negatives

And now for everything that I’ve got left in the bag.

-   The two language problem: Sooner or later, you’ll run in to a memory
    issue, go to Stack Overflow, and be told that the solution is to use
    a package that lets R talk to C++. Julia claims to have solved this.
    I don’t know if I believe it.

-   The index in a `for` loop uses the same environment as its caller,
    so loops like `for(i in 1:10)` will overwrite any variable called
    `i` in the parent environment and set it to `10` when the loop
    finishes.

    ``` r
    i <- 2000
    for(i in 1:10){}
    i
    ## [1] 10
    ```

    This sounds awful, but I’ve never encountered it in practice. After
    all, it sounds like bad practice to use the same variable name for
    two different things. Apparently the `for` loops also like to strip
    attributes, breaking S3 objects, but again, I’ve never encountered
    this. After all, idiomatic R it to prefer functions like `sapply()`
    to `for` loops.

-   *Advanced R* claims that R is a great language to metaprogram. I
    cannot deny that the Tidyverse is very strong evidence for that, but
    who would dare metaprogram a language as poorly documented and as
    inconsistent as I’ve claimed R is? Certainly not me. I can’t even
    predict R’s behaviour when I’m programming it, never mind
    metaprogramming! I’ve regretted most of my attempts at doing so. I
    usually get tripped up by some quirk of R’s string-manipulation
    facilities and how the strings get parsed as expressions.

-   For a language that was inspired by Scheme, R’s metaprogramming
    feels very limited. As far as I can tell, aside from the typical
    operation of building code from text that I’d expect any language to
    be capable of, it is only used to facilitate the creation of
    functions that evaluate their arguments in a non-standard way.
    Usually, this doesn’t go any further than creating an ad-hoc
    environment where the function’s arguments make sense, despite said
    arguments having no meaning in the calling environment. Typical
    examples are `with()` and modelling functions like `lm()`, which let
    you write code like `lm(mpg ~ wt, mtcars)`. Being able to say “*let
    me tell you what data I want you to treat like an environment, so I
    can refer to its variables as if they were objects in the calling
    environment*” is great, but it’s nowhere near what a Lisp user would
    expect.

-   The `plot()` function has some strange defaults. For example, you
    need to have a plot before you can plot points, and it often doesn’t
    know what to do in terms of how long/wide its axes should be. I also
    don’t like how “*predict `mpg` from `wt`*” is `foo(mpg~wt)`, but
    “*plot `mpg` on the y-axis and `wt` on the x-axis*” is
    `plot(wt, mpg)`. I understand why both options are the way that they
    are, but it creates unpredictability.

-   I seem to have terrible luck with the documentation for R’s
    libraries. Even when using popular packages that have been around
    for years, I often find documentation errors that are so basic that
    I can’t explain how they’ve gone unnoticed. I’ve seen documentation
    that reports the wrong return types, imports unnecessary libraries
    in its example code, and completely fails to mention significant
    parameters! I try to fix these when I find them, so I can no longer
    name names, but it’s a source of significant annoyance.

-   *Advanced R* points out that [good R code is
    rare](https://adv-r.hadley.nz/introduction.html#why-r), but I have a
    different take on it that I think explains my poor luck with R
    libraries: Statisticians don’t want to write code or learn GitHub
    and programmers don’t want to use any more R than they strictly need
    to. This means that nobody is really doing any bug fixing or even
    reporting. On the bright side, this makes it very easy to improve
    other people’s R code and get accepted pull requests.

# 5 The Tidyverse

As I’ve already admitted, my knowledge of the Tidyverse is much less
than my knowledge of base R. However, no critique of R is complete
without at least giving this a mention. Its popularity, along with R
version 4.0.6. adopting some its ideas (pipes and a shorter anonymous
function syntax), are clear evidence that it’s on to something. Before
going in to the specific libraries, I’ll give some general thoughts:

-   I can’t back down from the “*polished turd*” point that I [made
    earlier](#48-the-community). No matter how good the Tidyverse is,
    any attempt to fix R’s inconsistencies by making new libraries is
    doomed to fail. Base R is inconsistent, so the only way to be
    consistent with it is to be inconsistent. For example, `as.foo()` is
    inconsistent with R’s S3 system, but it’s what I’d expect to find
    with a new class called `foo` in a library. The only solution to
    this problem is to somehow write code that completely ignores base
    R, but that becomes impossible as soon as you try to load anyone
    else’s packages.
-   I’m sure that I’ve seen the main author of the Tidyverse quoted as
    saying that he didn’t want it to be a monolith. However, it
    undeniably is one. Tidyverse packages will throw errors with
    `rlang`, be made specifically to work with other Tidyverse packages
    (see the [first paragraph of the
    manifesto](https://cran.r-project.org/web/packages/tidyverse/vignettes/manifesto.html)),
    and depreciate their own functions in favour of functions from
    different Tidyverse packages.
-   For [the reasons explained earlier](#43-variable-manipulation), the
    authors are very scared of the `...` argument’s ability to pass
    arguments to where they should not have gone. To counter this, most
    of the Tidyverse functions use names that you would never type. This
    means that without an IDE prompting you, you’re going to get a lot
    of the argument names wrong. I’ve slipped up with `tibble`’s
    `.name_repair` argument a few times. Get it wrong and R probably
    won’t let you know!
-   I really understand the “*consistent interface*” selling point of
    the Tidyverse. Because of the `[x]`/`[x,]`/`[,x]` business, I often
    guess wrong with functions like `base::order()`, but I almost never
    guess wrong with `dplyr::arrange()`.
-   The API of the Tidyverse is rarely stable; It constantly depreciates
    functions and [owns up to its willingness to do
    so](https://cran.r-project.org/web/packages/tidyverse/vignettes/paper.html).
    I understand the value of not being tied to your past mistakes – see
    my many complaints about base R’s interest in supporting S – but
    it’s rare that I look through the documentation for a Tidyverse
    package and not see a note saying that something either is
    depreciated or soon will be. It’s even worse when I see a Stack
    Overflow answer with just the function that I need, only to find
    that my newer version of the package doesn’t even have the old
    function. However, the worst example by far is when the *R for Data
    Science* book can’t keep up with the depreciation. For example, when
    I read chapter 25, the code in the book was spitting out warnings
    about the `.drop` argument to `unnest()` being deprecated. Importing
    a package when making your own package is already a risky
    proposition, but **issues like this would have me do all of my work
    in base R even if there was a perfect Tidyverse function for the
    job**.
-   The Tidyverse is undeniably designed around piping (see the [second
    point of the
    manifesto](https://cran.r-project.org/web/packages/tidyverse/vignettes/manifesto.html)).
    It’s not obvious that piping is a good framework to build around. To
    keep pipes simple, you must build functions that are easy to
    compose. This means that you will design your functions to have the
    minimum number of arguments that you can get away with. If you need
    more arguments, then you will instead make more functions wherever
    possible. This is a significant increase in complexity. Surely
    arguments are less complicated than functions? I dread to think what
    it takes to replicate a function like `aggregate()` in the
    Tidyverse. Even something as simple as `dplyr::select()` has about
    10 helper functions in its documentation. I’m willing to be proven
    wrong here, but everything that I’ve just said strikes me as
    obviously true to anyone who has used `dplyr` or `purrr`.

Overall, I’m more than happy to use Tidyverse functions when I’m writing
some run-once code or messing around in the REPL, but the unstable API
point is a real killer for anything else. In terms of how it compares to
base R, I’d rather use quite a few of its packages than their base R
equivalents. However, that doesn’t mean that it can actually replace
base R. I see it as nothing more than a handy set of libraries.

Now for the specific libraries. Assume that I’m ignorant of any that
I’ve skipped.

## 5.1 Dplyr

-   I don’t like how it has name conflicts with the base R stats
    library. It just seems rude.
-   Remember all of my complaints about [base R’s
    subsetting](#45-subsetting) and how I’d rather use the [non-standard
    evaluation](#4112-non-standard-evaluation) functions if it weren’t
    for all of their vague warnings? `dplyr` completely nullifies most
    of these complains, for data frames at least. This is a huge win for
    the Tidyverse.
-   R’s [factor variables are scary](#410-factor-variables).
    `dplyr::group_by()` takes a more SQL-like approach to the problem
    and feels a lot safer to work with.
-   Compared to base R, the knowledge that `dplyr` will only output a
    tibble is a relief. There’s no need to consider if I need
    `tapply()`, `by()`, or `aggregate()` for a job or if I need to
    coerce my input in order to go in/out of functions like `table()`. I
    therefore need to do a lot less guessing. [This
    link](https://gist.github.com/hadley/c430501804349d382ce90754936ab8ec)
    demonstrates it better than I can, although the formula solution
    with `aggregate()` is in base R’s favour.
-   `dplyr::mutate()` is just plain better than base R’s `transform()`.
    In particular, it allow you to refer to columns that you’ve just
    created.
-   [This
    link](https://cran.r-project.org/web/packages/dplyr/vignettes/base.html)
    shows a comparison between base R and `dplyr`. It’s rather
    persuasive. In particular, it gives you the sense that you can make
    safe guesses about the `dplyr` functions.
-   I don’t like how the `dplyr` functions only accept data frame or
    objects derived from them. If I’m doing some work with something
    like `stringr`, I instinctively want to use a Tidyverse solution to
    problems like subsetting my inputs. However, if I reach for
    `dplyr::filter()`, I get errors due to character vector not being
    data frames.

## 5.2 Ggplot2

-   To repeat my earlier praise for this library, it’s fun. That’s a
    huge win.
-   It has amazingly sane defaults. Whenever I make the same graph in
    both this and base R’s `plot()`, `ggplot2`’s is much better. You can
    tell R to do stuff like include a useful legend or grid, but
    `ggplot2` does it by default.
-   I like how graphs are made by what amounts to composing functions.
    It makes it very easy to focus on one specific element of your plots
    at a time. I’d even go as far as say that it’s fun to see what
    happens when you replace a component with another valid but strange
    one. You can discover entirely new categories of graphs by accident.
-   I miss the genericness of base R’s `plot()`. When I can’t be
    bothered to think about what sort of plot I need, `plot()` can save
    me the trouble by making a correct guess. There is no such facility
    in `ggplot2`.

## 5.3 Lubridate

I don’t use dates much, so I don’t have much to say. In fact, I don’t
think that I’ve mentioned them before now. `lubridate` appears to be
much easier to use than base R dates and times, but I know neither very
well. I don’t like how base R seems to force you to do any time
arithmetic in seconds and date arithmetic in days. I also don’t like how
it’s hard to do arithmetic with times in base R without a date being
attached. However, I could be wrong about all of that. I really don’t
know any of them too well and I’ve never found much reason to learn. I’d
really like to see
<https://rosettacode.org/wiki/Convert_seconds_to_compound_duration>
solved in both base R and `lubridate`. I’m not saying that it would be
hard, but I’d love to see the comparison. Overall, all that I can really
say for certain is that experience has shown that when the day comes,
I’ll have a much easier time learning this package than what base R
offers for the same jobs.

## 5.4 Magrittr

Pipes come in very handy, but I’ve never been completely sold on them,
even when viewing teaching examples that are supposed to demonstrate
their superiority. I’ll admit that there is a time and a place for them
– e.g. printing and graphing code – but I think that they only really
shine when you’ve abandoned base R in favour of `purrr`. After all, base
R wasn’t built for pipes. I’d even go as far as to say that the people
who swear by `magrittr` and `purrr` have adopted a completely different
paradigm to those who don’t, so they end up using totally different
tools. For example, a master of the Tidyverse finds [*Advanced R*
chapter nine’s](https://adv-r.hadley.nz/functionals.html)

``` r
by_cyl %>% 
  map(~ lm(mpg ~ wt, data = .x)) %>% 
  map(coef) %>% 
  map_dbl(2)
```

just as informative as my
`lapply(by_cyl, function(x) lm(mpg ~ wt, data = x)$coef[[2]])` (or its
equivalent `sapply()` or `vapply()`, if you really insist). Overall, I
think that I can’t evaluate `magrittr` without also evaluating `purrr`.

As a side-note, the claim that `foo %>% bar()` is equivalent to
`bar(foo)` appears to be a white lie. Try it with a plotting function
that cares about the variable name of its argument. Spot the difference:

``` r
plot(Nile)
```

![](Frustration-One-Year-With-R_files/figure-gfm/unnamed-chunk-88-1.png)<!-- -->

``` r
library(magrittr)
## 
## Attaching package: 'magrittr'
## The following object is masked from 'package:purrr':
## 
##     set_names
Nile %>% plot()
```

![](Frustration-One-Year-With-R_files/figure-gfm/unnamed-chunk-88-2.png)<!-- -->

``` r
Nile |> plot() #The same as plot(Nile)
```

![](Frustration-One-Year-With-R_files/figure-gfm/unnamed-chunk-88-3.png)<!-- -->

Don’t get me wrong, I like pipes a lot. When you’re dealing with data,
there’s sometimes no way to avoid “*do `foo()` to my data and then do
`bar()`*” code. However, you’d be mad to use them all of the time. For
people that do use them, all that I can say is that you should take the
time to learn all of them and that said time really isn’t much. None of
them are much more complicated than `%>%` and `%$%` is a handy
replacement for `with()`.

As a final point, I don’t like how much trouble base R’s new `|>` pipe
causes me. You can’t do `x |> foo`. You instead need `x |> foo()`. Also,
to use a function where the target argument isn’t first, you need to use
some nonsense like `x |> (function(x) foo(bar, x))()`. For example,
`mtcars |> (function(x) Map(max, x))()`. I don’t like all of those extra
brackets. `magrittr` can do it with just
`mtcars %>% (function(x) Map(max, x))` or even `mtcars %>% Map(max, .)`.

## 5.5 Purrr

Unlike base R, where I can point to a specific example and explain to
you why it’s silly, my objections to `purrr` are mostly philosophical.
It certainly does some things much better than base R. For example, I
really like the consistency in the map functions. They’re a breath of
fresh air compared to base R’s apply family vs funprog mess. My code
would probably be a lot easier to read and modify if I replaced all of
my apply family and funprog calls with their `purrr` equivalents.
However, when writing the code in the first place, I’d much rather have
the flexibility that the base R functions offer. I also like `pluck()`
and it being built in to the map functions, but I’ve yet to get used to
it. Overall, I wouldn’t mind using `purrr`, but I have some major
objections:

-   It takes the idea of “*a function should only do one thing*” to a
    pathological level. I see no reason why `map_lgl()`, `map_int()`,
    `map_dbl()`, and `map_chr()` are separate functions. They do exactly
    the same thing, but will throw an error if they don’t get the return
    type in their name. Why isn’t this the job of some general mapping
    function that takes the desired output type as an argument
    (e.g. like base R’s `vapply()`)? This same issue is found in the
    entire library. There is no need for the `map2()` and `pmap()`
    functions or their countless \_type variants. Just make a general
    `map()` function! To steal a point from the [TidyverseSkeptic
    essay](https://github.com/matloff/TidyverseSkeptic/blob/master/READMEFull.md),
    `purrr` has 178 functions, and 52 are maps. What would you rather
    learn: a handful of complex map functions (like base R) or 52 simple
    ones? The only defences that I’ve seen for the `purrr` approach is
    that base R can be a bit verbose, e.g. `vapply()`’s arguments like
    `FUN.VALUE = logical(1)`, and that using the most restrictive
    possible tool for any given job increases the readability of your
    code.
-   It makes base R’s `~` operator able to form anonymous functions, at
    least within `purrr` (it’s some funky parsing). I could get used to
    it, but I don’t like how it robs the user of the ability to give the
    arguments to their anonymous function any meaningful names. This is
    because the `purrr` authors thought that the normal anonymous
    function syntax was too verbose, but I’d argue that they’ve gone too
    far and made their syntax too terse.
    `Map(function(x) runif(1), 1:3)` is not long or particularly
    obscure, but `map(1:3, ~ runif(1))` crosses the line for me, as does
    `map(data, ~ .x * 2)`. My example in the previous section, which
    included `map(~ lm(mpg ~ wt, data = .x))`, demonstrates another
    problem: It overloads the `~` operator in a dangerous way. The `~`
    inside the `map()` is very different from the `~` in the call to
    `lm()`.
-   I suspect that my above two points interact. Could it be that
    `purrr` users don’t use a generalised map function because they’ve
    written off base R’s anonymous function syntax and replaced it with
    a variant that is so terse that their code becomes unreadable
    without the names of their functions telling the reader what they’re
    doing?

Overall, I could probably be convinced that `purrr`’s way is better than
base R’s, but I doubt that `purrr`’s way is the best way.

## 5.6 Stringr and Tibble

For me, these both fall in to the same box. They’re not particularly
outstanding, but they’re clearly much better than their base R
equivalents. I’ve praised `tibble` enough already and have said plenty
about [the state of R’s strings](#42-strings). The only thing that I’ve
got left to say is that once you’ve noticed that tibbles let you use the
columns that you’ve just defined to define other columns, you really
start to hate how many extra lines of code you have to write when using
data frames for the same task.

# 6 Conclusion

If I were being generous, I would say that R teaches you some great
lessons about functional programming while being a useful DSL and that
its biggest fault is that it tries to do too much, ultimately becoming
brutally inconsistent. I’d also say that the Tidyverse is a useful set
of packages that, while unable to fix R and certainly not a panacea, do
a lot to improve it within their specific domains. However, I’m not that
generous.

The most damning thing about R is that much of [*The R
Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf) still
holds true. The fact that a nearly decade-old document that credibly
compared R to a journey in to Hell is still a useful reference manual
speaks volumes about the language’s attitude to change. To put it
plainly, **R won’t change**. If something about R frustrates you today,
**it always will**. That’s what kills the language for me. The
popularity of the Tidyverse proves that R is broken and the continuing
validity of the [*The R
Inferno*](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf) proves
that it will stay that way. You may be able to put a blanket of sanity
on top of it, as the best packages try to, but you won’t fix it. Unless
you find said packages so useful that they make R worth it, I find it
impossible to argue against jumping ship. My ultimate conclusion on R is
that it’s good, but doomed by the unshifting weight of the countless
little problems that I’ve documented here. Personally, I’m going to give
Python a shot and I wouldn’t blame you for doing the same. Let’s hope
that I don’t end up writing a document of this size complaining about
that.

All that being said, I have no intention of uninstalling R or going out
of my way to avoid it. I’d gladly use it professionally and I’ve learned
enough of its semantic semtex to get really damn good at using R to do
in few lines what other languages would do in many. I wasn’t joking when
I said that it’s the best desktop calculator that I’ve ever used. But
would I recommend learning it to anyone else? Absolutely not. We can do
so much better.
