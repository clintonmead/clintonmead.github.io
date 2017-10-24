## Welcome

This document is intended to give a brief rundown of my previous work experience and github contributions. Whilst intended to be a document for employers, it also contains a broad overview of my work on Github.

## Employment history:

### Haskell Programmer - University of New South Wales (April 2017 to September 2017)

Limited term contract funded by a research grant. Work primarily consisted of redeveloping the lexer, parser and type checker for the compiler for the language [MCK](http://cgi.cse.unsw.edu.au/~mck/pmck/).

### Staffer - Senator Leyonhjelm (Feburary 2016 - December 2016)

Tasks included creating, analysing and adjusting social media advertising campaigns, development on websites using PHP and Wordpress, and analysis of electoral results data. 

### Application Support - University of Wollongong (2006 - 2015)

Application support and integration development primarily for [Blackboard](http://www.blackboard.com/learning-management-system/blackboard-learn.aspx) but also [Equella](http://www.equella.com/). Variety languages used, including significant amounts of PL/SQL and SQL, but also Java, C++, Perl, Groovy, Python and Shell. The infrastructure which I worked on was Solaris Zones and Oracle databases. 

## Education:

Bachelor of Mathematics/Bachelor of Computer Science - University of Wollongong (2003 - 2006)

## Github projects:

Below is a non-complete list of my github projects. Currently all of my projects are in Haskell.

### [Freelude](https://hackage.haskell.org/package/freelude)

[`Freelude`](https://hackage.haskell.org/package/freelude) is intended to work as a replacement `Prelude`, generalising concepts such as categories, functors, and even applicatives and monads, so they can be applied to more datatypes, such as sets and unboxed vectors. An overview of `Freelude` can be found in the main page of it's [hackage documentation](https://hackage.haskell.org/package/freelude-0.1.0.1/docs/Freelude.html).

### [Indextype](https://hackage.haskell.org/package/indextype)

[`Indextype`](https://hackage.haskell.org/package/indextype) is a package of a number of type families that can be used to not only select elements from tuples, functions and constructors, but also form constraints such as "this type is a pair". 
[`Freelude`](https://github.com/clintonmead/freelude) uses this package directly. More information on `Indextype` is best found on it's [hackage page](https://hackage.haskell.org/package/indextype).

### [Polydata](https://hackage.haskell.org/package/polydata)

[`Polydata`](https://hackage.haskell.org/package/polydata) allows one to encapulate polymorphic data in a way that it can be passed into functions in a generic way that perserves it polymorphism. More details can be found in the [hackage documentation for `polydata-core`](https://hackage.haskell.org/package/polydata-core-0.1.0.0/docs/Data-Poly.html). `Polydata` also depends on [`Indextype`](https://github.com/clintonmead/indextype).

### [Typed-streams](https://hackage.haskell.org/package/typed-streams)

[`Typed-streams`](https://hackage.haskell.org/package/typed-streams) is an attempt to get C-like performance out of Haskell code which uses higher level concepts like folds, maps, and list like appends. By being more explicit about the way "lists" or "streams" are constructed than the usual list constructor, we can sometimes help GHC compile to C like loops. The [`typed-streams` hackage documentation](https://hackage.haskell.org/package/typed-streams-0.1.0.1/docs/Data-Stream-Typed.html) gives an example of code which using lists runs quite slowly but using `typed-streams` allows for C-like performance.

### [Fast-mult](https://hackage.haskell.org/package/fast-mult)

[`Fast-mult`](https://hackage.haskell.org/package/fast-mult) is an integer type that intelligently delays multiplications in such a way that multiplications are only performed with similar sized operands, greatly improving the performance of repeated muliplications which produce large integers. Hence it can improve the performance of existing numeric algorithms without changing the algorithms themselves. More details are in [`fast-mults` hackage documentation] https://hackage.haskell.org/package/fast-mult-0.1.0.2/docs/Data-FastMult.html).

### [Disjoint-set-stateful](https://hackage.haskell.org/package/disjoint-set-stateful)

[`Disjoint-set-stateful`](https://hackage.haskell.org/package/disjoint-set-stateful) is a Haskell implementation of a [disjoint-set data structure](https://en.wikipedia.org/wiki/Disjoint-set_data_structure) in the ST monad. It uses mutable unboxed arrays internally so should be quite fast.

### [Generic-enum](https://hackage.haskell.org/package/generic-enum) 

[`Generic-enum`](https://hackage.haskell.org/package/generic-enum) is a backwards compatable replacement of the standard Haskell `Enum` class which allows one to directly produce non-list data structures from functions such as `enumFrom`. This can be useful when one wants to use the standard enum function to generically produce infinite structures, which could loop forever if an intermediate list is created. 

## Contributions to other projects:

### Rank-2-classes

I've made a number of contributions to the [rank2classes](https://hackage.haskell.org/package/rank2classes) package, which can be seen in my [repository fork of `grampa`](https://github.com/clintonmead/grampa). These generally involve defining functors and applicatives over rank-2 types. 

### GHC

I have a [patch to GHC](https://phabricator.haskell.org/D3822) in progress that adds a number of primative operations to GHC, namely involving signed multiplication. It currently just requires me to add test cases.

## Future potential projects:

Below I've put a few ideas of things I'd like to attempt in the future:

### Smart monoid folds

I did a [blog post](https://clintonmeadprogramming.wordpress.com/2016/01/22/monoids-and-fast-folding-part-1/) a bit over a year ago about reorgansing `Foldable` so that `foldMap` would appropriately select the most efficient fold based on the Monoid type. The code is probably just needs a clean up and upload, but it might be worth integrating into `Freelude` in some way also.

### Sort out the build system for my projects.

Many of my github projects are now integrated with [TravisCI](https://travis-ci.org/clintonmead), but currently I do the upload to Hackage, not TravisCI. Instead TravisCI should be doing this after a successful build. Ideally however, after a successful build I'd like not only TravisCI to upload the package to Hackage, but also tag the commit and change the Cabal file to point to that tagged commit instead of master. 

### Get my packages onto stack

I'd like to get my packages into [Stack](https://www.stackage.org) as I use it to build myself. I probably want to sort out my build system first.

### Extend cabal to deal with orphan instances

When developing packages, I often run into this problem: I have created a class `C`, and some other package as data type `T`. It would make sense for `T` to be an instance of `C`, but most users of my package will never use `T`, and most users of `T`s package will never use my package.

I'd like to extend cabal so dependencies can have "features", and so dependencies are recompiled if their current compilation did not include that requested feature. That way additional dependencies are only compiled if required.

This probably isn't a simple patch, but I feel it would be useful as package developers would be more happy to add interaction with other packages, without fears of excessive dependencies nor having to create packages just full of orphan instances.

### Covert some of my projects into other languages

Whilst I haven't used it yet, I have an interest in Rust. I'd also like to convert some of my packages into Scala and C++.
