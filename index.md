## Welcome/Summary

I'm a developer based in Sydney Australia. 

I prefer to work in strongly typed functional programming languages, particularly Haskell, but have also worked with Scala.

I also have an interest in working with Rust.

I have done significant work with C# in the past also. 

Throughout most of my career I've done a lot of SQL, mainly focusing on relational databases (Postgres and Oracle) but I have had some interaction with BigQuery also.

I also have some experience using C++, TypeScript, Java, Python, Perl and Groovy. 

Outside of programming languages, I have used Nix extensively to manage a build system, and have used Terraform a bit to manage Google infrastructure.

Below you will see what is roughly an ordinary CV, but I have also included my thoughts on how I approach the craft of software engineering below. Keep reading (or [skip](#My-approach-to-software-development) to the bottom) to read that.

If you think I'd be valuable to your organisation feel free to send me an email at [clintonmead@gmail.com](mailto:clintonmead@gmail.com) or drop me a message on [LinkedIn](https://www.linkedin.com/in/clintonmead/).

[Click here to save this page as PDF](https://pdfcrowd.com/url_to_pdf/).

## Employment history:

### Haskell developer - PaidRight (July 2022 - March 2025)

Primary backend developer at [PaidRight](https://www.paidright.io). Backend was written in Haskell, developed and maintained interfaces with Google BigQuery, Google PubSub, GCS, Postgres and Auth0, as part of the required application logic. Also developed a typesafe API exposed via OpenAPI that produced typesafe TypeScript code which would trigger compile errors if inconsistent changes were made to the backend and frontend. These were achieved with the help of significant contributions to [Autodocodec](github.com/NorfairKing/autodocodec/) and [AesonDiff](https://github.com/clintonmead/aeson-diff). Also maintained the build system using Nix.

### Scala/Javascript developer - Complii (July 2021 - March 2022)

Sole developer and adminstrator of [ThinkCaddie](https://thinkcaddie.com). Scala backend with Javascript frontend, served by AWS EC2 instances and a AWS RDS Postgres database. The Javascript frontend is based on [React+Redux](https://react-redux.js.org/), and the Scala backend is using the [Play Framework](https://www.playframework.com/), with a functional programming style used throughout both the backend and frontend. As sole developer and adminstrator I worked throughout the entire stack, and also did the devops work and deployments. I also developed a NixOS based virtual machine configuration designed to get new developers up and running with all build dependencies and editer plugins within minutes.

### C# developer - yReceipts/eyos (Feburary 2018 - June 2021)

C# and .NET developer. Particular focus on interfacing with Windows printing and UI development. Large part of my role was developing a generic rules based model for matching products purchased at checkout against a large number of "promotions", that would trigger on based on a rule and provide some sort of discount or free product to the user. I designed this rule engine in a way that allowed for rules to be nested within rules yet these rules could be resolved in real-time, and promotions even alerted mid-transaction. A significant part of my role here also was to bring functional programming practices where appropriate to a more imperative/object-orientated codebase.

### Haskell Programmer - University of New South Wales (April 2017 to September 2017)

Limited term contract funded by a research grant. Work primarily consisted of redeveloping the lexer, parser and type checker for the compiler for the language [MCK](http://cgi.cse.unsw.edu.au/~mck/pmck/).

### Staffer - Senator Leyonhjelm (Feburary 2016 - December 2016)

Tasks included creating, analysing and adjusting social media advertising campaigns, development on websites using PHP and Wordpress, and analysis of electoral results data. 

### Application Support - University of Wollongong (2006 - 2015)

Application support and integration development primarily for [Blackboard](http://www.blackboard.com/learning-management-system/blackboard-learn.aspx) but also [Equella](http://www.equella.com/). Role included application support, focused on maintaining and enhancing the performance of a clustered system serving 1000+ simutaneous users, both of the front-end, and the back-end and Oracle database. Also work involved maintaining and extending integrations between university systems, which were written mostly in Perl with some shell scripting. Also implemented single-signon protocols between off the shelf products and PL/SQL inhouse products, and developed custom Oracle database hosted hierachical staff permissioning models for the University content management system Equella. I also worked on various data processing tasks for the school of psychology, primarily in C++.

## Other skills

### Linux

I have ran Linux in some form at home for most of this century, firstly with Red Hat Linux and then moving on to [Debian (Potato)](https://www.debian.org/releases/potato) in 2000. I have also build NixOS virtual machines. So I am comfortable with the linux command line and have a reasonable idea of how to administer Linux systems, at least at the home system level.

### Marrying Functional and Object Orientated Programming

I have a lot of experience with both functional and object-orientated programming. In particular, in my roles with object-orientated languages, I have learnt how to combine both these paradigms to get the some of the advantages of both, without going to far and having "square peg/round hole" issues. This is a tricky balance that I've learnt from experience to a certain extent.

## Education:

Bachelor of Mathematics/Bachelor of Computer Science - University of Wollongong (2003 - 2006). A copy of my [academic transcript is here](https://clintonmead.github.io/transcript.html). 

## Github projects:

Below is a non-complete list of my [github](https://github.com/clintonmead) projects. They are written in both Haskell, Rust and C#. They 

## Haskell:

### [Autodocodec](github.com/NorfairKing/autodocodec/)

Autodocodec is not my project, but a project I have made significant contributions to, which allows one, with a single definition, define a codec, decodec, and documentation, and consistently generate, serialisers, deserialisers (for JSON or other formats), OpenAPIs and other things. My contributions primary focused around increasing the library's flexibility and adding new datatypes for the library to natively handle.

### [AesonDiff](https://github.com/clintonmead/aeson-diff)

AesonDiff also originally wasn't my project, but was handed over to me after making significant contributions as it was otherwise dormant. AesonDiff is an implementation of the [JSON Patch](https://en.wikipedia.org/wiki/JSON_Patch) standard in Haskell. I added OpenAPI spec generation to this library and extensions to the protocol to make typesafe usage easier from typescript.

### [rank2classes](https://hackage.haskell.org/package/rank2classes)

I've made a number of contributions to the [rank2classes](https://hackage.haskell.org/package/rank2classes) package, which can be seen in my [repository fork of `grampa`](https://github.com/clintonmead/grampa). These generally involve defining functors and applicatives over rank-2 types. 

### [Fast-mult](https://hackage.haskell.org/package/fast-mult)

[`Fast-mult`](https://hackage.haskell.org/package/fast-mult) is an integer type that intelligently delays multiplications in such a way that multiplications are only performed with similar sized operands, greatly improving the performance of repeated muliplications which produce large integers. Hence it can improve the performance of existing numeric algorithms without changing the algorithms themselves. More details are in [`fast-mults` hackage documentation]( https://hackage.haskell.org/package/fast-mult-0.1.0.2/docs/Data-FastMult.html).

### [Disjoint-set-stateful](https://hackage.haskell.org/package/disjoint-set-stateful)

[`Disjoint-set-stateful`](https://hackage.haskell.org/package/disjoint-set-stateful) is a Haskell implementation of a [disjoint-set data structure](https://en.wikipedia.org/wiki/Disjoint-set_data_structure) in the ST monad. It uses mutable unboxed arrays internally so should be quite fast.

### [Freelude](https://hackage.haskell.org/package/freelude)

[`Freelude`](https://hackage.haskell.org/package/freelude) is intended to work as a replacement `Prelude`, generalising concepts such as categories, functors, and even applicatives and monads, so they can be applied to more datatypes, such as sets and unboxed vectors. An overview of `Freelude` can be found in the main page of it's [hackage documentation](https://hackage.haskell.org/package/freelude-0.1.0.1/docs/Freelude.html). This was presented at the [October 2017 FP-Syd](http://fp-syd.ouroborus.net/wiki/Past/2017) meetup.

### [Indextype](https://hackage.haskell.org/package/indextype)

[`Indextype`](https://hackage.haskell.org/package/indextype) is a package of a number of type families that can be used to not only select elements from tuples, functions and constructors, but also form constraints such as "this type is a pair". 
[`Freelude`](https://github.com/clintonmead/freelude) uses this package directly. More information on `Indextype` is best found on it's [hackage page](https://hackage.haskell.org/package/indextype).

### [Polydata](https://hackage.haskell.org/package/polydata)

[`Polydata`](https://hackage.haskell.org/package/polydata) allows one to encapulate polymorphic data in a way that it can be passed into functions in a generic way that perserves it polymorphism. More details can be found in the [hackage documentation for `polydata-core`](https://hackage.haskell.org/package/polydata-core-0.1.0.0/docs/Data-Poly.html). `Polydata` also depends on [`Indextype`](https://github.com/clintonmead/indextype).

### [Typed-streams](https://hackage.haskell.org/package/typed-streams)

[`Typed-streams`](https://hackage.haskell.org/package/typed-streams) is an attempt to get C-like performance out of Haskell code which uses higher level concepts like folds, maps, and list like appends. By being more explicit about the way "lists" or "streams" are constructed than the usual list constructor, we can sometimes help GHC compile to C like loops. The [`typed-streams` hackage documentation](https://hackage.haskell.org/package/typed-streams-0.1.0.1/docs/Data-Stream-Typed.html) gives an example of code which using lists runs quite slowly but using `typed-streams` allows for C-like performance.

### [Static-closure](https://hackage.haskell.org/package/static-closure)

[Static-closure](https://hackage.haskell.org/package/static-closure) is an implementation of applicative style serialisable data and arbitary functions, made possible with the `StaticPointers` extension to GHC. Whilst [Distributed-closure](https://hackage.haskell.org/package/distributed-closure) is a similar module, [Static-closure](https://hackage.haskell.org/package/static-closure) is more flexible, has less unsafe typecasts in it's implementation, and includes a Template Haskell approach to deriving instances which eliminates significant boilerplate.

### [Generic-enum](https://hackage.haskell.org/package/generic-enum) 

[`Generic-enum`](https://hackage.haskell.org/package/generic-enum) is a backwards compatable replacement of the standard Haskell `Enum` class which allows one to directly produce non-list data structures from functions such as `enumFrom`. This can be useful when one wants to use the standard enum function to generically produce infinite structures, which could loop forever if an intermediate list is created. 

### [Map-classes](https://hackage.haskell.org/package/map-classes)

[`Map-classes`](https://hackage.haskell.org/package/map-classes) provides typeclasses for a variety of colletion types, so one can write generic algorithms which work on many implementations of collections without changing code.

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

## My approach to software development

I think the best programmers think of themselves like they're bad programmers. This is not due to a lack of confidence but because it's true. Generally I've worked on systems where the part of the codebase I build and maintain is at least tens of thousands of lines of code, and connected to that is perhaps hundreds of thousands of lines from collegues and millions of lines from underlying libraries. Any decent sized software product is a rediculously complex system where no one person knows how all the parts work. Yet our mushy brains can probably remember at most five objects at a time. 

Like most human endevours, we can enhance our limited natural abilities with tools. For software developers, our tool is programming languages, but I believe in particularly our best tool is strongly typed programming languages. Like how a spanner can increase torque one hundred fold, the compilers of strongly typed programming languages can check thousands of invariants in how codebase each time we modify it. But tools can be used in different ways, so below is a discussion about how I use type systems to help develop correct, extensible and flexible software.

Note that some, perhaps most of the ideas below may seem rather obvious and not particularly novel. Many of the below ideas are not my own, and likely the ones I've come up with myself others have came up with independently before me. But I am hoping the combination of all of these will give you some idea of the thought and approach I put into developing software.

### The three states software can be in:

There are broadly three states a piece of software can be in, regarding it's correctness.

In this, I could be referring to a function, a module, a library, a PR, or an entire application. Any piece of software that has some notion (either strictly or loosely defined) about what is it's "correct" behaviour can be categorised as being in one of these three states, namely:

1. Correct
2. Obviously incorrect OR 
3. Subtlely incorrect

Of these the best state is being correct. 

The next best state is obviously incorrect, as software that is obviously incorrect, firstly fail to compile, be caught by basic automated tests, or caught in manual testing before it gets close to an actual user.

The worst state is subtlely incorrect. These are the issues that tend to be the most costly for organisations, because they slip through automated checks and testing, and even may slip by users for some time. When they are discovered also, there is often significant investment required to find the cause of the issue, because of the length of time the issue may have been hiding.

Of note here is that "obviously incorrect" is generally better than "subtlely incorrect". That is correct is best, but if you're going to get something wrong, it's actually better to get it very wrong generally. A bug that occurs 100% of the time is often less costly than one that occurs 1% of the time. 

In summary, correct software is best, very wrong software is second best, almost correct software is worst.

I think a lot of people know this, but I haven't often seen it been explicitly stated. I'm driving the perhaps obvious point home here because it drives the rest of my philosophy on software development. That is, I try to deliberately develop software in a way that, firstly increases the chance my software will be correct, but more importantly, most ensures that if it is incorrect, it is OBVIOUSLY incorrect, and not subtlely incorrect.

### The three layers of a software system

Unlike above, when I refer to a software system in this section, I'm generally referring to larger pieces of software, perhaps a whole app, a library, or a module. This has to do with the organisation and breakdown of software.

Software systems have three broad layers:

1. The "real world" layer
2. The "abstract" layer
3. The "nitty-gritty" layer

I think it's important to give some context first about how they tie together. The "abstract layer" is what glues everything together and is the most general part.

Code generally follows the following pattern:

1. One/some of many real world types, like "people", "widgets", etc.
2. One/some of many implementation types, like a "set", a "database" etc.
3. A bit of "abstract" code in the middle, that itself doesn't require or even mention any particular real world or implementation type, but instead just requires such types follow some interface. 

Below we'll break this into some detail and look into some examples. 

#### The "real world" layer

If you were to employ me to write software, you're making money from users and/or customers, and it's most likely they are paying you because they want to use software to help them do something in the real world. As much as I find pure mathematics and software problems fascinating, that's probably not what your user/customers are paying you for, and it's probably not what you're paying me for. Software generally does real world stuff. And there are requirements, and rules, about how those real world things are suppose to interact. So this is the first part of concrete advice for developing software: model your real world types.

"Strings" and "Ints" are not real world things. They're computer things. Real world things are things like "dollars", "first name", "seconds". Dollars are not ints. $3 multiplied by $4 is nonsensical. Alice + Bob is also nonsensical. In nothing other than a childs word game do you reasonably put together "Alice" and "Bob" to get "AliceBob".

Most programming languages have rules that they enforce, for their "computer" objects, like strings and ints, including what are and what are not valid ways to combine and manipulate them. This is useful. We've long moved past the idea of using assembly language to manipulate bits and bytes. We have, in almost every modern programming language, types.

But a programming language just knows about a number of primative data structures, not your particular real world problem. However programming languages generally give one tools to describe the structure and interactions between such real world concepts and objects. 

However I've often notice programmers dont use these tools, and their software is a mess of strings and ints and arrays of strings and ints.

Instead, when I get a problem, I first:

1. Define the entities in the problem.
2. Define what interactions are valid between the entities.

Note the above involved no actual executable code. It's just data definitions and stub-functions. However, once you've done this you've done much of the hard work, and importantly, you've broken down the problem into smaller managable chunks. Yes, defining all your real world entities as separate data types does introduce a bit of extra boilerplate, but it results in more a maintenable and extensible codebase because you've got the compiler checking that you're not jamming things together in non-sensical ways.

Now, names may be represented as strings, and dollars representated as ints or floats or whatever, but names are not strings, and dollars are not ints.

This is one of the first steps towards software correctness. As much as possible, model the real world requirements in the type system. Humans have mushy brains that have trouble keeping track of more than five things at a time. A compiler will got through a codebase of tens of thousands of lines in seconds and tell you every time you've violated your own assumptions. Furthermore, and more importantly, it will tell you where you've violated your coworkers, or ex-coworkers assumptions. And it will do so reliably, more so than documentation and tests. Not that tests aren't important also, but compile time guarentees, when they are available, are generally better. I will talk more about this later.  

#### The "abstract" layer

Modelling our real world types in the type system is important, instead of just using representational types everywhere. But here's the issue. The real world is complicated. Actually determining the rules and requirements any significant software system should follow is impossible. You will always often realise you haven't thought about some edge case and whilst the software may be doing exactly what it was "designed" to do it's really doing what it's "meant" to do. This is one of those "subtlely incorrect" issues which we're really trying to avoid.

The abstract layer doesn't mention our real world types. Someone reading the abstract layer should have little to no understanding of what our application actually does. Generic interfaces often fall into this category. For example an interface that represents a key-value store. A set, or a vector, would be in the abstract layer (even though their actual implementation will be in the layer below).

Like the real world layer, entities in the abstract layer have particular laws for them which they are expected to always follow. But, the good thing about the entities in the abstract layer is they are in some sense "simpler". For example, I can reliably say:

1. Adding an element to a vector increases it's length by one. 
2. That a set doesn't contain duplicate elements. 
3. That `(a + b) + c` is the same as `a + (b + c)`. 

Abstract layer objects can have "implementations", which may seem confusing as we have an "implementation" layer below, but I would say that abstract layer objects or interfaces that are just statements of laws and facts that the objects follow, as opposed to say, an "algorithm", which is more of an implementation layer concept, particularly when such an algorithm is non-trivial or has lower level optimisations.

Compared to abstract layer objects, real world objects are more complicated. They have more complex rules that we often find hard to define precisely, often running into edge cases which we didn't initially consider. Also, our application is likely quite distinct to any other application on the planet (if not, why are we be building it?). There are no common libraries/frameworks we can use to model our "real world" types. But then the idea is to map our real world types to abstract types through defined interface. Then we have the advantage of either:

- Using preexisting code, avoiding reinventing the wheel OR
- Defining our own interface, but one that is simpler that the real world one, and also perhaps useable for multiple purposes.

As much as many people find mathematics complicated, it is actually, compared to the real world, really simple. In mathematics, we define the rules. We can explicitly enumerate them with confidence. Sometimes the consequences of those rules might be hard to understand, but at least we know what they are. In the real world, it's far harder to define exactly what we're trying to achieve, and what we're trying to achieve is often changing. 

In the abstract layer, there's less things that can go wrong, because you've purposely exposed LESS details. When dealing with a real world type or implementation type, these are often quite complex. Abstract types are relatively more simple, and there's less ways you can combine them, and the fewer ways you can combine them are more likely to be correct, and if they are wrong, they are likely to be more OBVIOUSLY wrong, not SUBTLELY wrong. 

Because of this "simplicity" of the abstract layer, one should try to extract as much application logic as possible and think about it in the abstract layer. This layer is the least likely to be incorrect, and it's also the most likely to be flexible. 

Often programming languages standard libraries provide various abstractions a host of ways to manipulate those abstractions, so if you can fit your problem into one of these existing abstractions, all the better. You've saved reinventing the wheel.

So of course some of your codebase has to deal with real world types, and some will have to actually deal with the nitty gritty of algorithms and writing to/from databases/calling APIs etc. But one should try to write as much code as possible that mentions neither of these things directly, but it instead an instead acts as an independent interface which can help glue real world objects together with various implementations. 

#### The "implementation" layer 

This is the part where we're actually "doing stuff". The "nitty-gritty" basically. There's broadly two types of code here:

1. Code that actually interacts with real world things, like external APIs, the disk, databases, etc. 
2. Algorithmic code. Like the actual implementation of a quicksort algorithm (not that you would reinvent the wheel here)

The implementation layer, like the abstract layer, should not give hints about what our application is actually doing. 

However, the implementation layer, like the real world layer is complicated. However, the reasons for it's complexity is different. In the "real world" layer the complexity is because the problem we're trying to solve is:

1. Hard to define AND
2. A moving target AND
3. Unique (no-one else is building exactly our app)

The implementation layer is complext for completely different reasons, such that:

- We may be doing with external systems that can for example, fail due to network outages or other issues.
- We are moving outside of the confines of our own code/language, and our compiler can not assist us.
- The algorithms we're writing are just a bit fiddly, and again, our type system doesn't give us strong guarentees of correctness. 

The good thing about this layer is because it's not specific to our application, we may be able to find libraries that have already been written to do these tasks. 

As discussed in the "abstract layer", one of the things we should try to avoid, except for very trivial tasks, is to mash together real world application logic with implementation without clear separation, as this results in two bad outcomes.

- We are putting together two parts of our system which both have significant complexity AND
- We've destroyed the ability to reuse code existing code for the implementation part of the code because we've mixed in application logic (which is necessarily unique to our particular problem).

### How does all this affect the way I develop software?

How actually the "real world", "abstract" and "implementation" layers should be divided up depends a number of factors, they could be separate libraries, separate files/folders, or the separation may not be as formal as that, but the important thing here is that problems are logically divided up in this fashion. 

Also whilst above I've spoken about this separation on an entire application level, much like babushka dolls, it can apply to subcomponents. For example, if one was to write an API implementation, the "real world" would be it's external interface, and the types that describe that. Eventually the API will actually do things, like update a database or something, which is the implementation layer, but between these layers there are likely some abstractions one can make, perhaps combining lower level operations into convienient packages.

These layers are not hard and fast guidelines, especially for smaller sub-components of software. The important thing is at least attempting to divide problems up into:

1. The real world interface and objects
2. Some useful abstractions (ideally, ones which already exist) which we can clearly establish rules of interaction which are independent of our real world problem and implementation details.
3. The implementation details of the actual work we'll need to end up doing. 

### On testing...

If you ask people "what's the primary tool you use to guarentee your software is correct" they will generally say tests.

I disagree.

If I was at high school, and in an exam asked to prove that two odd numbers add to give an even number, I wouldn't say "oh well 1 + 3 = 4, 5 + 11 = 16, 7 + 7 = 14" it holds in three cases therefore it's true?

You wouldn't get any marks for that. You'd instead write a proof.

Tests have the issue in that they only test the things that you've thought about testing. But what's likely to go wrong is something you haven't thought about testing. 

Of course there are techniques to mitigate this. Having others write tests. Writing randomised property tests. 

But this is why I focus on not "test driven development", but "proof driven development".

What are proofs? Well the compiler of a strongly typed language is essentially a proof checking machine. 

Put the invariants and properties you expect to hold directly in the type system. Make invalid states unrepresentable. As much as possible use abstractions to reduce complexity.

Now there are some things compilers can't prove. Particularly involving interactions with external systems. These sort of interactions need to be tested.

So I'm not saying "don't write tests", it's just acknoledging that proofs, where they can be used, can be even better than tests. If one writes software like I suggest, the proofs are essentially zero cost, and unlike manually written tests, automatically adapt with any new requirements. 

I'm not claiming that one should scrap "test driven development". But I think software reliability improves if one does not entirely focus 100% of tests, and instead puts some investment into proofs also. 

### Why develop software in these way?

The craft of developing software isn't really about small projects. To use [Big O notation](https://en.wikipedia.org/wiki/Big_O_notation), I don't think they way I develop software affects the constant factor all that much. It's about reducing the scaling factor.

The hardest problem in software development of any significant size is managing complexity. I have seen application development grind to a snails pace and require entire rewrites because managing complexity was never considered a priority. It was a death by a thousand cuts. Lots of little hacks, over months and years, with developers coming and leaving, resulted in codebases which essentially had zero value for the business who developed them, and had to be scrapped entirely.

I don't like this happening on a personal level, and I also think it's bad business, particularly as I think it can be generally avoided.

There's two facts I think of building products:

1. No-one is ever exactly sure about what we should build, i.e. what the market actually wants and will pay for.
2. If we manage to work out point one (which we won't) it's a moving target anyway.

This is why I develop software in this fashion. As a developer, it's often no good building code that does exactly what you're told it should do but is really difficult to change because, firstly, what we should be doing is probably different to what we think we should be doing, and what we need to do in six months time is different to today.

I keep this in the back of my mind. Of course there's no use over-generalising, but not-generalising at all is doomed to fail unless one makes the unrealisic assumption that one exactly knows the market and it will not change.

This is often thought as a tradeoff, i.e. generalisation vs short term development time, but I'm not convinced that all generalisation increases the time to develop. In contrast, I think a reasonable amount of generalisation and structure can make software faster to develop. You can have your cake and eat it too, as long as you know how much cake to eat. 

But I do get it, sometimes you need get things out, time is money, and one can't always take the time to design software well. One of the heuristic I use is "building shit is okay, but piling shit on top of shit is almost always bad idea". Often you don't know your market, it is silly to invest significant time into something that may be scrapped anyway. And often something is time critical, you're losing money or customers and you need to get something out. Sometimes you need to fight fires. But if you're in fire-fighting mode not 20% of the time, but 100% of the time, there's something fundamentally wrong and you're likely being very unproductive and spending money on what should be an asset but will likely have little value in the future.

Do your quick experiments, make some hacky prototypes, but if they work, before building on top of them, engineer them properly. One doesn't build a skyscrapper by starting with a one story house and just adding floors. You might be able to get away with adding second floor, but eventually you'll have to have a look at the fountains and the structural components, otherwise you'll just end up with a pile of rubble. 

Yet it seems many people in the industry think you can build a skyscrapper just by piling on floors. We're supposed to be engineers, but thank God some software engineers aren't building our apartment blocks!

So in summary, what does developing software in a structured manner, which more explicitly represents your real world types, focuses on abstract code where possible, and separates implementation achieve:

1. Your application can be changed to fit evolving needs at a lower cost.
2. It's less likely to have bugs, particularly subtle ones.
3. It is more easy to grow an extend, as existing complexity is managed.

In the end I think these aren't just theoritical ideas, they help the bottom line, as they both increase the speed of new features to market, increasing potential revenue, and reduce employee costs because less developers can manage a larger codebase. 

### Why write all this in my CV?

If you're a potential employer looking to hire me, you're going to make a significant investment into me anyway, which will dwarf the half an hour or so it takes you to read all this. You're probably going to be interviewing me also, so there's a few hours of your time there.

I understand that many software developers do not look at the craft of software development like I do. I don't think I'm unique but I don't think I'm in the majority also. As my views are in the minority there's a good chance that you may just think I'm not right for your organisation. And that's okay, it's better we both find that out sooner rather than latter.

But, knowing that I'm in the minority, I don't expect everyone to think like me. Indeed I've mostly worked with people that don't think like me. And had very productive working relationships with such people, learning from each other, both building off each others strengths, but also maintaining our distinct approaches. 

The question you should ask is, do you want a voice like mine in your organisation, into that mix of ideas? Is there a place for this sort of approach in your company culture, or even in particular areas of your application, even if it isn't the dominant view in your organisation.

I have no desire to control everyone else does, I just want to develop software at the professional standards I expect of myself, and make you a lot of money, so I can make a living out of doing what I like doing.

Whilst "inconsistency" is often seen as a horrible thing in a software team, I think draconian enforcement of consistency can actually be a negative thing, stifling invovation and continuous improvement. Often something non-standard becomes standard not by force or "coding standards", but just because someone does it and after a while people realise that it works better than what people are doing. Without a little flexibility and inconsistency it never would have got off the ground. 

So I'm happy to be part of a team that aren't all like me, and indeed that's been the case all my career. And if your team is happy to have those differences in style, then I'll be happy to be a part of it. 
