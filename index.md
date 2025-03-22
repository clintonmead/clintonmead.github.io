# WIP CV

## Who am I?
I'm Clinton Mead, a software engineer based in Sydney Australia. My strongest languages are Haskell, C#, C++, Rust and Scala. I also have experience using Java, Python, Perl and Groovy. I've also used a lot of SQL, primarily in the context of relational databases.

## What is this and why?
As part of this Resume/CV, I'm going to first talk about a bit about who I am, not just what I've done. Naturally what I've done has resulted in who I am, but people can have similar experiences and draw different conclusions. 

I'll discuss three things:

1. My approach to software development.
2. The sort of problems I like to work on.
3. My thoughts on how teams should work.

I'll then go into a more traditional CV style approach. 

I will say some things that, whilst probably not unique, are perhaps minority opinions. That being said, everyone has opinions, even if they don't voice them, and I'm not particularly set in my ways. Indeed I've currently come to these conclusions from almost 20 years experience working as a professional software developer, and I've came to these conclusions from my particular experiences previously. As I work with new people with new ideas and with new organisations I expect some of these to change.

## My approach to software development

### The three states software can be in:

There are broadly three states a piece of software can be in, regarding it's correctness.

In this, I could be referring to a function, a module, a library, a PR, or an entire application. Any piece of software that has some notion (either strictly or loosely defined) about what is it's "correct" behaviour can be categorised as being in one of these three states, namely:

1. Correct
2. Obviously incorrect OR 
3. Subtlely incorrect

Of these the best state is being correct. 

The next best state is obviously incorrect, as software that is obviously incorrect, firstly fail to compile, be caught by basic functionality testing, or caught in manual testing before it gets close to an actual user.

The worst state is subtlely incorrect. These are the issues that tend to be the most costly for organisations, because they slip through automated checks and testing, and even may slip by users for some time. When they are discovered also, there is often significant investment required to find the cause of the issue, because of the length of time the issue may have been hiding.

Of note here is that "obviously incorrect" is generally better than "subtlely incorrect". That is correct is best, but if you're going to get something wrong, it's actually better to get it very wrong generally. A bug that occurs 100% of the time is often less costly than one that occurs 1% of the time. 

In summary, correct software is best, very wrong software is second best, almost correct software is worst.

I think a lot of people know this, but I haven't often seen it been explicitly stated. I'm driving the perhaps obvious point home here because it drives the rest of my philosophy on software development. That is, I try to deliberately develop software in a way that firstly increases the chance my software will be correct, but more importantly, most ensures that if it is incorrect, it is OBVIOUSLY incorrect, and not subtlely incorrect.

(A side note here is over the last 18 months or so I've been using AI to assist writing code, it tends to be very good at creating code in the "subtlely incorrect" category. This is something one must be very careful about.) 

### The three layers of a software system

Unlike above, when I refer to a software system in this section, I'm generally referring to larger pieces of software, perhaps a whole app, a library, or a module. This has to do with the organisation and breakdown of software.

Software systems have three broad layers:

1. The "real world" layer
2. The "abstract" layer
3. The "nitty-gritty" layer

I'll detail each of them now (p.s. If you have better naming suggestions I'm always happy to take them)

#### The "real world" layer

If you were to employ me to write software, you're making money from users and/or customers, and it's most likely they are paying you because they want to use software to help them do something in the real world. As much as I find pure mathematics and software problems fascinating, that's probably not what your user/customers are paying you for, and it's probably not what you're paying me for. Software generally does real world stuff. And there are requirements, and rules, about how those real world things are suppose to interact. So this is the first part of concrete advice for developing software: model your real world types.

"Strings" and "Ints" are not real world things. They're computer things. Real world things are things like "dollars", "first name", "seconds". Dollars are not ints. $3 multiplied by $4 is nonsensical. "Alice" + "Bob" is also nonsensical. In nothing other than a childs word game do you reasonably put together "Alice" and "Bob" to get "AliceBob".

Even more nonsensical is $3 multiplied by 4 seconds. 

Now, names may be represented as strings, and dollars representated as ints or floats or whatever, but names are not strings, and dollars are not ints.

This is one of the first steps towards software correctness. As much as possible, model the real world requirements in the type system. Humans have mushy brains that have trouble keeping track of more than five things at a time. A compiler will got through a codebase of tens of thousands of lines in seconds and tell you every time you've violated your own assumptions. Furthermore, and more importantly, it will tell you where you've violated your coworkers, or ex-coworkers assumptions. And it will do so reliably, more so than documentation and tests. Not that these aren't important also, but they aren't as reliable like clockwork. I will talk more about this later.  

#### The "abstract" layer

Modelling our real world types in the type system is important, instead of just using representational types everywhere. But here's the issue. The real world is complicated. Actually determining the rules and requirements any significant software system should follow is impossible. You will always put something out and eventually realise you haven't thought about some edge case and whilst the software may be doing exactly what it was designed to do it's really not what you meant it to do. This is one of those "subtlely incorrect" issues which we're really trying to avoid.

The abstract layer doesn't mention our real world types. Someone reading the abstract layer should have little to no understanding of what our application actually does. Generic interfaces often fall into this category. For example an interface that represents a key-value store. A set, or a vector, would be in the abstract layer (even though their actual implementation will be in the layer below).

Like the real world layer, entities in the abstract layer have particular laws for them which they are expected to always follow. But, the good thing about the entities in the abstract layer is they are in some sense "simpler". I can reliably say that adding an element to a vector increases it's length by one. That a set doesn't contain duplicate elements. That `(a + b) + c` is the same as `a + (b + c)`. 

On the other hand, our real world objects are more complicated. They have more complex rules that we often find hard to define precisely, often running into edge cases which we didn't initially consider. Also, our application is likely quite distinct to any other application on the planet (if not, why are we be building it?). There are no common libraries/frameworks we can use to model our "real world" types. But then the idea is to map our real world types to abstract types through defined interface. Then we have the advantage of either:

- Using preexisting code, avoiding reinventing the wheel OR
- Defining our own interface, but one that is simpler that the real world one, and also perhaps useable for multiple purposes.

As much as many people find mathematics complicated, it is actually, compared to the real world, really simple. In mathematics, we define the rules. We can explicitly enumerate them with confidence. Sometimes the consequences of those rules might be hard to understand, but at least we know what they are. In the real world, we're not really sure what the rules are in the first place. People think mathematics is more complex that the real world, but that's because that sort of preciseness is a part of doing mathematics. But if one actually made a fair comparison and demanded that level of preciseness when thinking about the real world, one would find mathematics is relatively easier to comprehend.

So, because of this relative simplicity of the abstract layer, this is the layer where the least likely to go wrong. Even more importantly, in the abstract layer, if things go wrong, they are more likely to be OBVIOUSLY wrong, not SUBTLELY wrong.

This is why, if one can put things in the abstract layer, that is, abstract away real world details whilst staying away from messy implementation details (as discussed below) then put the logic here. Logic in the abstract layer is the least likely to be wrong, because less things can go wrong. The abstract layer should be the reliable core and glue that brings together the "real world" layer and the "nitty gritty" layer discussed below.

#### The "nitty gritty" layer 

...

# Old CV here

## Welcome/Summary

I'm a developer based in Sydney Australia. My strongest languages are Haskell, C#, C++, Scala and Rust. I also have experience using Java, Python, Perl and Groovy. In my previous role at the University of Wollongong I also did a lot of work using SQL and PL/SQL on Oracle databases, and some system administration on Sun Solaris systems. 

If you think I'd be valuable to your organisation feel free to send me an email at [clintonmead@gmail.com](mailto:clintonmead@gmail.com) or drop me a message on [LinkedIn](https://www.linkedin.com/in/clintonmead/).

[Click here to save this page as PDF](https://pdfcrowd.com/url_to_pdf/).

## Employment history:

### Accenture (April 2022 - ongoing)

### Scala/Javascript developer (July 2021 - March 2022)

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

I have ran Linux in some form at home for most of this century, firstly with Red Hat Linux and then moving on to [Debian (Potato)](https://www.debian.org/releases/potato) in 2000. I have started to experiment with configuring NixOS virtual machines. So I am comfortable with the linux command line and have a reasonable idea of how to administer Linux systems, at least at the home system level.

### Marrying Functional and Object Orientated Programming

I have a lot of experience with both functional and object-orientated programming. Most of my functional programming experience is unpaid and most of my object-orientated experience has been professional, but I have also done open source work in both fields also. In particular, I have an interest in how compilers work in both areas, so have somewhat of an understanding of the mechanics of say, a virtual-call vs a typeclass dictionary. Object-orientated and functional programming can be powerful when used together, as their strengths can used for different problems, but they can clash, so through my experience I've learnt how to meld whilst minimising friction.

## Education:

Bachelor of Mathematics/Bachelor of Computer Science - University of Wollongong (2003 - 2006). A copy of my [academic transcript is here](https://clintonmead.github.io/transcript.html). 

## Github projects:

Below is a non-complete list of my [github](https://github.com/clintonmead) projects. They are written in both Haskell, Rust and C#.

## Haskell:

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
