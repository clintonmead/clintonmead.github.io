# My approach to software engineering

Below are a few notes I've put down on the thought process I use when developing software. I thought it would be good to put them on paper instead of just keeping them in my head. These are just my thoughts from my experiences, but this is somewhat of a living document; I may update these from time to time, as I get new insights from new experiences. 

## Dealing with our mushy, forgetful brains.

I think the best programmers think of themselves like they're bad programmers. This is not due to a lack of confidence but because it's true. Generally I've worked on systems where the part of the codebase I build and maintain is at least tens of thousands of lines of code, and connected to that is perhaps hundreds of thousands of lines from colleagues and millions of lines from underlying libraries. Any decent-sized software product is a ridiculously complex system where no one person knows how all the parts work. Yet our mushy brains can probably remember at most five objects at a time. 

Like most human endeavors, we can enhance our limited natural abilities with tools. For software developers, our tool is programming languages, but I believe particularly that our best tool is strongly typed programming languages. Like how a spanner can increase torque one hundredfold, the compilers of strongly typed programming languages can check thousands of invariants in the codebase each time we modify it. But tools can be used in different ways, so below is a discussion about how I use type systems to help develop correct, extensible and flexible software.

Note that some, perhaps most of the ideas below may seem rather obvious and not particularly novel. Many of the below ideas are not my own, and likely the ones I've come up with myself others have come up with independently before me. But I am hoping the combination of all of these will give you some idea of the thought and approach I put into developing software.

### The three states software can be in:

There are broadly three states a piece of software can be in, regarding its correctness.

In this, I could be referring to a function, a module, a library, a PR, or an entire application. Any piece of software that has some notion (either strictly or loosely defined) about what its "correct" behavior can be categorized as being in one of these three states, namely:

1. Correct
2. Obviously incorrect OR 
3. Subtly incorrect

Of these the best state is being correct. 

The next best state is obviously incorrect, as software that is obviously incorrect will first fail to compile, be caught by basic automated tests, or be caught in manual testing before it gets close to an actual user.

The worst state is subtly incorrect. These are the issues that tend to be the most costly for organizations, because they slip through automated checks and testing, and may even slip by users for some time. When they are discovered, there is often significant investment required to find the cause of the issue, because of the length of time the issue may have been hiding.

Of note here is that "obviously incorrect" is generally better than "subtly incorrect." That is, correct is best, but if you're going to get something wrong, it's actually better to get it very wrong generally. A bug that occurs 100% of the time is often less costly than one that occurs 1% of the time. 

In summary, correct software is best, very wrong software is second best, and almost correct software is worst.

I think a lot of people know this, but I haven't often seen it been explicitly stated. I'm driving the perhaps obvious point home here because it drives the rest of my philosophy on software development. That is, I try to deliberately develop software in a way that, first, increases the chance my software will be correct, but more importantly, ensures that if it is incorrect, it is OBVIOUSLY incorrect, and not subtly incorrect.

### The three layers of a software system

Unlike above, when I refer to a software system in this section, I'm generally referring to larger pieces of software, perhaps a whole app, a library, or a module. This has to do with the organization and breakdown of software.

Software systems have three broad layers:

1. The "real world" layer
2. The "abstract" layer
3. The "nitty-gritty" layer

I think it's important to give some context first about how they tie together. The "abstract layer" is what glues everything together and is the most general part.

Code generally follows the following pattern:

1. One/some of many real world types, like "people", "widgets", etc.
2. One/some of many implementation types, like a "set", a "database" etc.
3. A bit of "abstract" code in the middle, that itself doesn't require or even mention any particular real world or implementation type, but instead just requires such types to follow some interface. 

Below we'll break this down in some detail and look into some examples. 

#### The "real world" layer

If you were to employ me to write software, you're making money from users and/or customers, and it's most likely they are paying you because they want to use software to help them do something in the real world. As much as I find pure mathematics and software problems fascinating, that's probably not what your users/customers are paying you for, and it's probably not what you're paying me for. Software generally does real world stuff. And there are requirements and rules about how those real world things are supposed to interact. So this is the first part of concrete advice for developing software: model your real world types.

"Strings" and "Ints" are not real world things. They're computer things. Real world things are things like "dollars", "first name", "seconds". Dollars are not ints. $3 multiplied by $4 is nonsensical. Alice + Bob is also nonsensical. In nothing other than a child's word game do you reasonably put together "Alice" and "Bob" to get "AliceBob".

Most programming languages have rules that they enforce, for their "computer" objects, like strings and ints, including what are and what are not valid ways to combine and manipulate them. This is useful. We've long moved past the idea of using assembly language to manipulate bits and bytes. We have, in almost every modern programming language, types.

But a programming language just knows about a number of primitive data structures, not your particular real world problem. However, programming languages generally give one tools to describe the structure and interactions between such real world concepts and objects. 

However, I've often noticed programmers don't use these tools, and their software is a mess of strings and ints and arrays of strings and ints.

Instead, when I get a problem, I first:

1. Define the entities in the problem.
2. Define what interactions are valid between the entities.

Note the above involved no actual executable code. It's just data definitions and stub functions. However, once you've done this you've done much of the hard work, and importantly, you've broken down the problem into smaller manageable chunks. Yes, defining all your real world entities as separate data types does introduce a bit of extra boilerplate, but it results in a more maintainable and extensible codebase because you've got the compiler checking that you're not jamming things together in nonsensical ways.

Now, names may be represented as strings, and dollars represented as ints or floats or whatever, but names are not strings, and dollars are not ints.

This is one of the first steps towards software correctness. As much as possible, model the real world requirements in the type system. Humans have mushy brains that have trouble keeping track of more than five things at a time. A compiler will go through a codebase of tens of thousands of lines in seconds and tell you every time you've violated your own assumptions. Furthermore, and more importantly, it will tell you where you've violated your coworkers' or ex-coworkers' assumptions. And it will do so reliably, more so than documentation and tests. Not that tests aren't important also, but compile-time guarantees, when they are available, are generally better. I will talk more about this later.  

#### The "abstract" layer

Modelling our real world types in the type system is important, instead of just using representational types everywhere. But here's the issue. The real world is complicated. Actually determining the rules and requirements any significant software system should follow is impossible. You will often realize you haven't thought about some edge case and while the software may be doing exactly what it was "designed" to do, it's really doing what it's "meant" to do. This is one of those "subtly incorrect" issues which we're really trying to avoid.

The abstract layer doesn't mention our real world types. Someone reading the abstract layer should have little to no understanding of what our application actually does. Generic interfaces often fall into this category. For example an interface that represents a key-value store. A set, or a vector, would be in the abstract layer (even though their actual implementation will be in the layer below).

Like the real world layer, entities in the abstract layer have particular laws for them which they are expected to always follow. But the good thing about the entities in the abstract layer is they are in some sense "simpler". For example, I can reliably say:

1. Adding an element to a vector increases its length by one. 
2. That a set doesn't contain duplicate elements. 
3. That `(a + b) + c` is the same as `a + (b + c)`. 

Abstract layer objects can have "implementations", which may seem confusing as we have an "implementation" layer below, but I would say that abstract layer objects or interfaces are just statements of laws and facts that the objects follow, as opposed to, say, an "algorithm", which is more of an implementation layer concept, particularly when such an algorithm is non-trivial or has lower level optimizations.

Compared to abstract layer objects, real world objects are more complicated. They have more complex rules that we often find hard to define precisely, often running into edge cases which we didn't initially consider. Also, our application is likely quite distinct from any other application on the planet (if not, why are we building it?). There are no common libraries/frameworks we can use to model our "real world" types. But then the idea is to map our real world types to abstract types through defined interfaces. Then we have the advantage of either:

- Using pre-existing code, avoiding reinventing the wheel OR
- Defining our own interface, but one that is simpler than the real world one, and also perhaps usable for multiple purposes.

As much as many people find mathematics complicated, it is actually, compared to the real world, really simple. In mathematics, we define the rules. We can explicitly enumerate them with confidence. Sometimes the consequences of those rules might be hard to understand, but at least we know what they are. In the real world, it's far harder to define exactly what we're trying to achieve, and what we're trying to achieve is often changing. 

In the abstract layer, there are fewer things that can go wrong, because you've purposely exposed FEWER details. When dealing with a real world type or implementation type, these are often quite complex. Abstract types are relatively simpler, and there are fewer ways you can combine them, and the fewer ways you can combine them are more likely to be correct, and if they are wrong, they are likely to be more OBVIOUSLY wrong, not SUBTLY wrong. 

Because of this "simplicity" of the abstract layer, one should try to extract as much application logic as possible and think about it in the abstract layer. This layer is the least likely to be incorrect, and it's also the most likely to be flexible. 

Often programming languages' standard libraries provide various abstractions and a host of ways to manipulate those abstractions, so if you can fit your problem into one of these existing abstractions, all the better. You've saved reinventing the wheel.

So of course some of your codebase has to deal with real world types, and some will have to actually deal with the nitty-gritty of algorithms and writing to/from databases/calling APIs etc. But one should try to write as much code as possible that mentions neither of these things directly, but instead acts as an independent interface which can help glue real world objects together with various implementations. 

#### The "implementation" layer 

This is the part where we're actually "doing stuff". The "nitty-gritty" basically. There are broadly two types of code here:

1. Code that actually interacts with real world things, like external APIs, the disk, databases, etc. 
2. Algorithmic code. Like the actual implementation of a quicksort algorithm (not that you would reinvent the wheel here)

The implementation layer, like the abstract layer, should not give hints about what our application is actually doing. 

However, the implementation layer, like the real world layer, is complicated. However, the reasons for its complexity are different. In the "real world" layer the complexity is because the problem we're trying to solve is:

1. Hard to define AND
2. A moving target AND
3. Unique (no-one else is building exactly our app)

The implementation layer is complex for completely different reasons, such that:

- We may be dealing with external systems that can, for example, fail due to network outages or other issues.
- We are moving outside of the confines of our own code/language, and our compiler cannot assist us.
- The algorithms we're writing are just a bit fiddly, and again, our type system doesn't give us strong guarantees of correctness. 

The good thing about this layer is that because it's not specific to our application, we may be able to find libraries that have already been written to do these tasks. 

As discussed in the "abstract layer", one of the things we should try to avoid, except for very trivial tasks, is to mash together real world application logic with implementation without clear separation, as this results in two bad outcomes.

- We are putting together two parts of our system which both have significant complexity AND
- We've destroyed the ability to reuse existing code for the implementation part of the code because we've mixed in application logic (which is necessarily unique to our particular problem).

### How does all this affect the way I develop software?

How the "real world", "abstract" and "implementation" layers should actually be divided up depends on a number of factors; they could be separate libraries, separate files/folders, or the separation may not be as formal as that, but the important thing here is that problems are logically divided up in this fashion. 

Also while above I've spoken about this separation on an entire application level, much like babushka dolls, it can apply to subcomponents. For example, if one was to write an API implementation, the "real world" would be its external interface, and the types that describe that. Eventually the API will actually do things, like update a database or something, which is the implementation layer, but between these layers there are likely some abstractions one can make, perhaps combining lower level operations into convenient packages.

These layers are not hard and fast guidelines, especially for smaller sub-components of software. The important thing is at least attempting to divide problems up into:

1. The real world interface and objects
2. Some useful abstractions (ideally, ones which already exist) for which we can clearly establish rules of interaction that are independent of our real world problem and implementation details.
3. The implementation details of the actual work we'll need to end up doing. 

### On testing...

If you ask people "what's the primary tool you use to guarantee your software is correct" they will generally say tests.

I disagree.

If I was at high school, and in an exam asked to prove that two odd numbers add to give an even number, I wouldn't say "oh well 1 + 3 = 4, 5 + 11 = 16, 7 + 7 = 14" it holds in three cases therefore it's true?

You wouldn't get any marks for that. You'd instead write a proof.

Tests have the issue that they only test the things that you've thought about testing. But what's likely to go wrong is something you haven't thought about testing. 

Of course there are techniques to mitigate this. Having others write tests. Writing randomized property tests. 

But this is why I focus on not "test driven development", but "proof driven development".

What are proofs? Well, the compiler of a strongly typed language is essentially a proof checking machine. 

Put the invariants and properties you expect to hold directly in the type system. Make invalid states unrepresentable. As much as possible, use abstractions to reduce complexity.

Now there are some things compilers can't prove. Particularly involving interactions with external systems. These sorts of interactions need to be tested.

So I'm not saying "don't write tests", it's just acknowledging that proofs, where they can be used, can be even better than tests. If one writes software like I suggest, the proofs are essentially zero cost, and unlike manually written tests, automatically adapt with any new requirements. 

I'm not claiming that one should scrap "test driven development". But I think software reliability improves if one does not entirely focus 100% on tests, and instead puts some investment into proofs also. 

### Why develop software in this way?

The craft of developing software isn't really about small projects. To use [Big O notation](https://en.wikipedia.org/wiki/Big_O_notation), I don't think the way I develop software affects the constant factor all that much. It's about reducing the scaling factor.

The hardest problem in software development of any significant size is managing complexity. I have seen application development grind to a snail's pace and require entire rewrites because managing complexity was never considered a priority. It was a death by a thousand cuts. Lots of little hacks, over months and years, with developers coming and leaving, resulted in codebases which essentially had zero value for the business that developed them, and had to be scrapped entirely.

I don't like this happening on a personal level, and I also think it's bad business, particularly as I think it can be generally avoided.

There are two facts I think of when building products:

1. No one is ever exactly sure about what we should build, i.e. what the market actually wants and will pay for.
2. If we manage to work out point one (which we won't), it's a moving target anyway.

This is why I develop software in this fashion. As a developer, it's often no good building code that does exactly what you're told it should do but is really difficult to change because, first, what we should be doing is probably different from what we think we should be doing, and what we need to do in six months' time is different from today.

I keep this in the back of my mind. Of course there's no use over-generalizing, but not generalizing at all is doomed to fail unless one makes the unrealistic assumption that one exactly knows the market and it will not change.

This is often thought of as a tradeoff, i.e. generalization vs short term development time, but I'm not convinced that all generalization increases the time to develop. In contrast, I think a reasonable amount of generalization and structure can make software faster to develop. You can have your cake and eat it too, as long as you know how much cake to eat. 

But I do get it, sometimes you need to get things out, time is money, and one can't always take the time to design software well. One of the heuristics I use is "building shit is okay, but piling shit on top of shit is almost always a bad idea". Often you don't know your market, it is silly to invest significant time into something that may be scrapped anyway. And often something is time critical, you're losing money or customers and you need to get something out. Sometimes you need to fight fires. But if you're in fire-fighting mode not 20% of the time, but 100% of the time, there's something fundamentally wrong and you're likely being very unproductive and spending money on what should be an asset but will likely have little value in the future.

Do your quick experiments, make some hacky prototypes, but if they work, before building on top of them, engineer them properly. One doesn't build a skyscraper by starting with a one-story house and just adding floors. You might be able to get away with adding a second floor, but eventually you'll have to have a look at the foundations and the structural components, otherwise you'll just end up with a pile of rubble. 

Yet it seems many people in the industry think you can build a skyscraper just by piling on floors. We're supposed to be engineers, but thank God some software engineers aren't building our apartment blocks!

So in summary, what does developing software in a structured manner, which more explicitly represents your real world types, focuses on abstract code where possible, and separates implementation achieve:

1. Your application can be changed to fit evolving needs at a lower cost.
2. It's less likely to have bugs, particularly subtle ones.
3. It is easier to grow and extend, as existing complexity is managed.

In the end I think these aren't just theoretical ideas, they help the bottom line, as they both increase the speed of new features to market, increasing potential revenue, and reduce employee costs because fewer developers can manage a larger codebase. 
