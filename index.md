## Welcome/Summary

I'm a developer based in Sydney Australia. My strongest languages are Haskell, C#, C++ and Rust. I also have experience using Java, Python, Perl and Groovy. In my previous role at the University of Wollongong I also did a lot of work using SQL and PL/SQL on Oracle databases, and Solaris Zones. 

If you think I'd be valuable to your organisation feel free to send me an email at [clintonmead@gmail.com](mailto:clintonmead@gmail.com) or drop me a message on [LinkedIn](https://www.linkedin.com/in/clintonmead/).

[Click here to save this page as PDF](https://pdfcrowd.com/url_to_pdf/).

## Employment history:

### Scala/Javascript developer (July 2021 - ongoing)

Sole developer and adminstrator of [ThinkCaddie](https://thinkcaddie.com). Scala backend with Javascript frontend, served by AWS EC2 instances and a AWS RDS Postgres database. The Javascript frontend is based on [React+Redux](https://react-redux.js.org/), and the Scala backend is using the [Play Framework](https://www.playframework.com/), with a functional programming style used throughout both the backend and frontend. As sole developer and adminstrator I work throughout the entire stack, and also do the devops work and deployments.

### C# developer - yReceipts (Feburary 2018 - June 2021)

C# and .NET developer. Particular focus on interfacing with Windows printing and UI development. 

### Haskell Programmer - University of New South Wales (April 2017 to September 2017)

Limited term contract funded by a research grant. Work primarily consisted of redeveloping the lexer, parser and type checker for the compiler for the language [MCK](http://cgi.cse.unsw.edu.au/~mck/pmck/).

### Staffer - Senator Leyonhjelm (Feburary 2016 - December 2016)

Tasks included creating, analysing and adjusting social media advertising campaigns, development on websites using PHP and Wordpress, and analysis of electoral results data. 

### Application Support - University of Wollongong (2006 - 2015)

Application support and integration development primarily for [Blackboard](http://www.blackboard.com/learning-management-system/blackboard-learn.aspx) but also [Equella](http://www.equella.com/). Variety languages used, including significant amounts of PL/SQL and SQL, but also Java, C++, Perl, Groovy, Python and Shell. The infrastructure which I worked on was Solaris Zones and Oracle databases. 

## Education:

Bachelor of Mathematics/Bachelor of Computer Science - University of Wollongong (2003 - 2006). A copy of my [academic transcript is here](https://clintonmead.github.io/transcript.html). 

## Github projects:

Below is a non-complete list of my [github](https://github.com/clintonmead) projects. They are written in both Haskell, Rust and C#.

## Haskell:

### [Freelude](https://hackage.haskell.org/package/freelude)

[`Freelude`](https://hackage.haskell.org/package/freelude) is intended to work as a replacement `Prelude`, generalising concepts such as categories, functors, and even applicatives and monads, so they can be applied to more datatypes, such as sets and unboxed vectors. An overview of `Freelude` can be found in the main page of it's [hackage documentation](https://hackage.haskell.org/package/freelude-0.1.0.1/docs/Freelude.html). This was presented at the [October 2017 FP-Syd](http://fp-syd.ouroborus.net/wiki/Past/2017) meetup.

### [Indextype](https://hackage.haskell.org/package/indextype)

[`Indextype`](https://hackage.haskell.org/package/indextype) is a package of a number of type families that can be used to not only select elements from tuples, functions and constructors, but also form constraints such as "this type is a pair". 
[`Freelude`](https://github.com/clintonmead/freelude) uses this package directly. More information on `Indextype` is best found on it's [hackage page](https://hackage.haskell.org/package/indextype).

### [Polydata](https://hackage.haskell.org/package/polydata)

[`Polydata`](https://hackage.haskell.org/package/polydata) allows one to encapulate polymorphic data in a way that it can be passed into functions in a generic way that perserves it polymorphism. More details can be found in the [hackage documentation for `polydata-core`](https://hackage.haskell.org/package/polydata-core-0.1.0.0/docs/Data-Poly.html). `Polydata` also depends on [`Indextype`](https://github.com/clintonmead/indextype).

### [Typed-streams](https://hackage.haskell.org/package/typed-streams)

[`Typed-streams`](https://hackage.haskell.org/package/typed-streams) is an attempt to get C-like performance out of Haskell code which uses higher level concepts like folds, maps, and list like appends. By being more explicit about the way "lists" or "streams" are constructed than the usual list constructor, we can sometimes help GHC compile to C like loops. The [`typed-streams` hackage documentation](https://hackage.haskell.org/package/typed-streams-0.1.0.1/docs/Data-Stream-Typed.html) gives an example of code which using lists runs quite slowly but using `typed-streams` allows for C-like performance.

### [Fast-mult](https://hackage.haskell.org/package/fast-mult)

[`Fast-mult`](https://hackage.haskell.org/package/fast-mult) is an integer type that intelligently delays multiplications in such a way that multiplications are only performed with similar sized operands, greatly improving the performance of repeated muliplications which produce large integers. Hence it can improve the performance of existing numeric algorithms without changing the algorithms themselves. More details are in [`fast-mults` hackage documentation]( https://hackage.haskell.org/package/fast-mult-0.1.0.2/docs/Data-FastMult.html).

### [Disjoint-set-stateful](https://hackage.haskell.org/package/disjoint-set-stateful)

[`Disjoint-set-stateful`](https://hackage.haskell.org/package/disjoint-set-stateful) is a Haskell implementation of a [disjoint-set data structure](https://en.wikipedia.org/wiki/Disjoint-set_data_structure) in the ST monad. It uses mutable unboxed arrays internally so should be quite fast.

### [Static-closure](https://hackage.haskell.org/package/static-closure)

[Static-closure](https://hackage.haskell.org/package/static-closure) is an implementation of applicative style serialisable data and arbitary functions, made possible with the `StaticPointers` extension to GHC. Whilst [Distributed-closure](https://hackage.haskell.org/package/distributed-closure) is a similar module, [Static-closure](https://hackage.haskell.org/package/static-closure) is more flexible, has less unsafe typecasts in it's implementation, and includes a Template Haskell approach to deriving instances which eliminates significant boilerplate.

### [Generic-enum](https://hackage.haskell.org/package/generic-enum) 

[`Generic-enum`](https://hackage.haskell.org/package/generic-enum) is a backwards compatable replacement of the standard Haskell `Enum` class which allows one to directly produce non-list data structures from functions such as `enumFrom`. This can be useful when one wants to use the standard enum function to generically produce infinite structures, which could loop forever if an intermediate list is created. 

### [Map-classes](https://hackage.haskell.org/package/map-classes)

[`Map-classes`](https://hackage.haskell.org/package/map-classes) provides typeclasses for a variety of colletion types, so one can write generic algorithms which work on many implementations of collections without changing code.

### [Stack-lib](https://hackage.haskell.org/package/stack-lib)

[Stack-lib](https://hackage.haskell.org/package/stack-lib) is a wrapper around [stack](https://hackage.haskell.org/package/stack), designed to allow it to be easy to use [stack](https://hackage.haskell.org/package/stack) as a library. The longer term goal of this to develop an extension to stack (which I am currently naming "heap") which allows, for example, building against multiple LTS releases with one command. Also "heap" should be able to create new projects and do much of the tasks which are currently done manually, including creating and adding initial files to a git repository, connecting that repository to github, and adding continuous integration configurations against for example, Travis GI. Finally, releases should be a one command process, with the commit tested against CI, and if successful, uploaded to Hackage and tagged in git, the version number bumped, with the cabal file pointing to the newly tagged release.

### [Atomic-File-Ops](https://hackage.haskell.org/package/atomic-file-ops-0.3.0.0)

[Atomic-File-Ops](https://hackage.haskell.org/package/atomic-file-ops-0.3.0.0) has some utility functions for atomically modifying files, such that readers only ever see the before written or after written state, not an intermediate state, as long as they do all their reads from one file handle. 

## Rust:

### [Haskell Bits](https://github.com/clintonmead/haskell_bits)

An ongoing port of Haskell concepts into Rust, including the Functor/Applicative/Monad hierarchy. I did a presentation on this at [June 2019 Rust-Syd](https://www.meetup.com/en-AU/Rust-Sydney/events/262194894/), but have developed this significantly since then.

## C#:

### [Typeclasses in C#](https://github.com/clintonmead/type-classes-in-csharp)

A proof of concept for a Functor/Applicative/Monad hierarchy in C#, presented at [November 2018 FP-Syd](http://fp-syd.ouroborus.net/wiki/Past/2018).

### [Battletech Mods](https://github.com/clintonmead/BattletechMods)
A variety of mods for the game [Battletech](http://battletechgame.com/), using [Harmony](https://github.com/pardeike/Harmony) to patch CLR methods at runtime and reflection to change ingame private data. 

## Contributions to other projects:

### Rank-2-classes

I've made a number of contributions to the [rank2classes](https://hackage.haskell.org/package/rank2classes) package, which can be seen in my [repository fork of `grampa`](https://github.com/clintonmead/grampa). These generally involve defining functors and applicatives over rank-2 types. 
