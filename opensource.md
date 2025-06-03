## Minor open source work.

Below is a more exhaustive list of my open source work, but including more minor projects/things I have done quite a well ago. I'm happy to talk about any of these, but I might not be able to rattle details off the top of my head without refreshing my memory. My more significant and recent open source work is in my [CV](https://clintonmead.github.io/index.html).

### Haskell:

Many of these libraries were created in 2017 in part of a process of self learning Haskell at a deeper level. This was before I had industry experience in Haskell, though I had been using it as a hobbyist periodically since 2002. 

Unlike some of the projects listed in my [CV](https://clintonmead.github.io/index.html) these weren't developed with a particular application in mind, but I do thing they contain some interesting ideas nevertheless. 

#### [Disjoint-set-stateful](https://hackage.haskell.org/package/disjoint-set-stateful)

[`Disjoint-set-stateful`](https://hackage.haskell.org/package/disjoint-set-stateful) is a Haskell implementation of a [disjoint-set data structure](https://en.wikipedia.org/wiki/Disjoint-set_data_structure) in the ST monad. It uses mutable unboxed arrays internally so should be quite fast.

#### [Freelude](https://hackage.haskell.org/package/freelude)

[`Freelude`](https://hackage.haskell.org/package/freelude) is intended to work as a replacement `Prelude`, generalising concepts such as categories, functors, and even applicatives and monads, so they can be applied to more datatypes, such as sets and unboxed vectors. An overview of `Freelude` can be found in the main page of it's [hackage documentation](https://hackage.haskell.org/package/freelude-0.1.0.1/docs/Freelude.html). This was presented at the [October 2017 FP-Syd](http://fp-syd.ouroborus.net/wiki/Past/2017) meetup.

#### [Indextype](https://hackage.haskell.org/package/indextype)

[`Indextype`](https://hackage.haskell.org/package/indextype) is a package of a number of type families that can be used to not only select elements from tuples, functions and constructors, but also form constraints such as "this type is a pair". 
[`Freelude`](https://github.com/clintonmead/freelude) uses this package directly. More information on `Indextype` is best found on it's [hackage page](https://hackage.haskell.org/package/indextype).

#### [Polydata](https://hackage.haskell.org/package/polydata)

[`Polydata`](https://hackage.haskell.org/package/polydata) allows one to encapulate polymorphic data in a way that it can be passed into functions in a generic way that perserves it polymorphism. More details can be found in the [hackage documentation for `polydata-core`](https://hackage.haskell.org/package/polydata-core-0.1.0.0/docs/Data-Poly.html). `Polydata` also depends on [`Indextype`](https://github.com/clintonmead/indextype).

#### [Typed-streams](https://hackage.haskell.org/package/typed-streams)

[`Typed-streams`](https://hackage.haskell.org/package/typed-streams) is an attempt to get C-like performance out of Haskell code which uses higher level concepts like folds, maps, and list like appends. By being more explicit about the way "lists" or "streams" are constructed than the usual list constructor, we can sometimes help GHC compile to C like loops. The [`typed-streams` hackage documentation](https://hackage.haskell.org/package/typed-streams-0.1.0.1/docs/Data-Stream-Typed.html) gives an example of code which using lists runs quite slowly but using `typed-streams` allows for C-like performance.

#### [Static-closure](https://hackage.haskell.org/package/static-closure)

[Static-closure](https://hackage.haskell.org/package/static-closure) is an implementation of applicative style serialisable data and arbitary functions, made possible with the `StaticPointers` extension to GHC. Whilst [Distributed-closure](https://hackage.haskell.org/package/distributed-closure) is a similar module, [Static-closure](https://hackage.haskell.org/package/static-closure) is more flexible, has less unsafe typecasts in it's implementation, and includes a Template Haskell approach to deriving instances which eliminates significant boilerplate.

#### [Generic-enum](https://hackage.haskell.org/package/generic-enum) 

[`Generic-enum`](https://hackage.haskell.org/package/generic-enum) is a backwards compatable replacement of the standard Haskell `Enum` class which allows one to directly produce non-list data structures from functions such as `enumFrom`. This can be useful when one wants to use the standard enum function to generically produce infinite structures, which could loop forever if an intermediate list is created. 

#### [Map-classes](https://hackage.haskell.org/package/map-classes)

[`Map-classes`](https://hackage.haskell.org/package/map-classes) provides typeclasses for a variety of colletion types, so one can write generic algorithms which work on many implementations of collections without changing code.

#### [Atomic-File-Ops](https://hackage.haskell.org/package/atomic-file-ops)

[Atomic-File-Ops](https://hackage.haskell.org/package/atomic-file-ops) has some utility functions for atomically modifying files, such that readers only ever see the before written or after written state, not an intermediate state, as long as they do all their reads from one file handle. 

### C#:

#### [Battletech Mods](https://github.com/clintonmead/BattletechMods)
A variety of mods for the game [Battletech](http://battletechgame.com/), using [Harmony](https://github.com/pardeike/Harmony) to patch CLR methods at runtime and reflection to change ingame private data. 

