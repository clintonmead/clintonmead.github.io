# What is complexity?

You've probably heard statements much like the following:

> A good engineer writes less code.

> Avoid "over-engineering", keep things *simple* (italics on 'simple' added by me)

I believe that the primary task of a software engineer is to manage complexity.

Managing complexity is what really separates the good engineers from poor ones, particularly over a long term project.

So you may think I enthusiastically agree with the above statements.

Well, not really.

## What people say is "complex"

When many people use the word complex in terms of software development, they're using it in a sense such as:

- There's too much code, it's hard for me to follow.
- There's too many layers of abstraction, so it's hard to understand how the code relates to the problem being solved.
- You're using advanced language features that I don't understand so I don't like it.

Now consider the following two definitions of a "Person". I've used C# below, but you can think of a similar example in your preferred language:

    public record Person(string Name, int Age, string Email);

vs:

    public readonly record struct Name(string Value);
    public readonly record struct Age(int Value);
    public readonly record struct Email(string Value);

    public record Person(FirstName FirstName, LastName LastName, Email Email);

Under the above definition of complexity, the latter code is certainly more complex than the former. It has four times as many lines, uses an additional language feature (a `record struct`), and while my C# is a bit rusty, I presume `Name`, `Age` and `Email` may need things like serializers and deserializers defined on them to ensure they behave as expected which are already defined directly on `string`, so that's additional code. Also, one can't see the underlying types of `Name`, `Age` and `Email` at first glance in the main struct, you have to go to their record definitions, which in a more complex case may be in a separate file.

Despite all this, the latter code being four times more code (and probably more), and more indirect, I would argue that the latter code is "simpler" than the former.

## What complexity really matters in software engineering?

The particular sense of the word complexity, which I'm going to use for the remainder of this article, is taken straight from [Wikipedia](https://en.wikipedia.org/wiki/Complexity), and I quote:

> Complexity characterizes the behavior of a system or model whose components interact in multiple ways and follow local rules, leading to non-linearity, randomness, collective dynamics, hierarchy, and emergence.
>
> The term is generally used to characterize something with many parts where **those parts interact with each other in multiple ways, culminating in a higher order of emergence greater than the sum of its parts.** The study of these complex linkages at various scales is the main goal of complex systems theory. 

[Dwarf Fortress](https://en.wikipedia.org/wiki/Dwarf_Fortress) is a computer game that has been praised for its, and I quote from the Wikipedia article: *"complex and emergent gameplay"*.

Here's an [example](https://www.theguardian.com/games/2022/nov/16/unexpected-nudity-and-vomit-covered-cats-how-dwarf-fortress-tells-some-of-gamings-most-bizarre-stories):

> In 2015, players of the video game Dwarf Fortress – a wildly influential cult hit that has appeared at New York’s Museum of Modern Art, and been cited as the inspiration for Minecraft – started finding vomit-covered dead cats in taverns. When the game’s creator, 44-year-old Tarn Adams, attempted to determine the cause, he discovered that cats were walking through puddles of spilled alcohol, licking themselves clean, and promptly dying of heart failure due to a minor error in the game’s code, which overestimated the amount of alcohol ingested.

Although cats were not intended to drink alcohol, this complexity, i.e. multiple systems interacting, namely liquid spillage, the fact that animals can get dirty based on what they walk over and grooming behaviour, and a minor bug, resulted in a completely unintended result.

This is fun in a computer game, but horrible for reliable software.

## Swiss cheese

I frequently watch [Mentour Pilot](https://www.youtube.com/@MentourPilot), who is a fantastic YouTuber who produces long form content about commercial aircraft incidents and accidents. He routinely talks about the [Swiss cheese model](https://en.wikipedia.org/wiki/Swiss_cheese_model) of accident causation. In brief, when something horrible happens, it's not usually because one thing has gone wrong, it's because multiple things have gone wrong, and they've all gone wrong in a way that lines up to produce an unexpected and usually not previously considered outcome.

Does this remind you of Dwarf Fortress? Or more specifically, software bugs, whether they be minor ones or world news?

## The main game is managing complexity

The main game in software engineering is not, about "reducing lines of code" or not "over-engineering" (whatever that means). It's managing complexity. As a software system grows, it will inevitably become more complex. Your role as an engineer is to reduce as much as practical how fast that complexity grows in relation to the feature set of your system. 

So why is:

    public record Person(string Name, int Age, string Email);

more complex and:

    public readonly record struct Name(string Value);
    public readonly record struct Age(int Value);
    public readonly record struct Email(string Value);

    public record Person(FirstName FirstName, LastName LastName, Email Email);

simpler?

Because complexity is a *higher order of emergence greater than the sum of its parts*. In the first case:

1. We have this concept of a "name".
2. We have this concept of an "email"

But in the first case, we now have:

<ol start="3">
  <li>Something that happens when we assign a "name" to an "email".</li>
</ol>

What happens here is probably just a bug and people don't get their emails. Regardless of the details here, we had a system with two parts, but now we have this additional emergent behaviour that we have to consider, if people aren't careful.

Now in the latter case, the case with MORE code, we have a "name", we have an "email", but if mix them up, we get a compile error. Sure, this is an emergent behaviour as well, but it's not an emergent behaviour that's going to survive to production.

The version with MORE code, MORE abstraction, is actually LESS complex.

## Yes, I "over engineer". And I'm proud of it.

Pretty much any engineer will tell you that one benefit of "abstraction" is reducing code duplication and size.

For example, if we need to sort ints, and we need to sort strings, just write a sort function that sorts "anything" with a comparison function passed to it, either implicitly or explicitly (this is a silly example as you won't write your own sort functions generally, but you get the idea). 

This sort function is more abstract but you've reduced the amount of code by reducing repetition and this is often considered good from a maintainability perspective (i.e. reducing code == good). 

I largely agree with this. The difference is that I don't think the only benefit of abstraction is to reduce duplication. Indeed abstraction is sometimes worth it even if it DOES NOT reduce duplication. This is because abstraction is ALSO a tool for reducing COMPLEXITY and as a result, increasing correctness.

Writing a generic sort function may actually be a better way of doing things, even if you only need to sort one thing.

You can see more of this discussed in my [approach](https://clintonmead.github.io/approach.html) blog post, but in short, the real world is complex. In that, there's a bunch of moving parts with vague rules whose interactions can have unpredictable consequences.

Mathematics, even though many people would call it "complex" in the colloquial sense, is actually comparatively simple. In that the objects in the system follow well defined rules.

The more code of your code you can move into this abstract mathematical sense, the less things there are to go wrong, and importantly, when they do go wrong, they are more likely to be **obviously** wrong, not **subtlely** wrong.

## What you'll see in the way I write code.

There is some sense that "more code" = "bad", and indeed overly complex and long functions is often (but not always) an example. 

But ironically, breaking them up is likely to **increase** the number of lines of code. This is not in itself bad.

What this allows one to do is to be explicit about what the components of the function actually do. What are their inputs? What are their outputs?

It isn't that every line of code increases complexity. It's more that:

1. Lines of code that **increase** the number of possible things your program does increases complexity.
2. Lines of code that **reduce** the number of possible things your program does reduces complexity.

As a guideline, code that does stuff increases complexity, generally executable code. Code that just defines stuff, for example, data definitions, functions signatures, using existing generic library code over custom more specific code, generally reduces complexity.

So when you'll look at my code, you'll see more lines of code than average. But most of that code won't be doing anything. It will instead be there to put **restrictions** on what my code does, and in particular, how it interacts with other code.

That latter part, restricting how the code interacts, is crucial to preventing "emergence greater than the sum of its parts".

## So what should you do?

### 1. Use types

Your mushy brain is bound to mess something up in a spectacular fashion. There are no "ints" or "strings" in the real world, these are software representations. Define all your real world business types explicitly. This might seem excessive initially but it's usually just a bit of extra boilerplate, and as a percentage of the total software development process those extra (likely minutes, not hours) are trivial.

And when you find out later that an "Email" isn't just a string but actually a restricted set of strings that have rules that should be checked on parsing, that behaviour will be easier to add in later. Yes, in many cases this will never been needed, and you could have got away with just using a string, but the effort of defining your real world business types with business names separate from implementation types is such an easy thing to do I find it's just worth it in all cases. It's such a small amount of pain for a large potential amount of gain it's hardly worth thinking about.

Just be careful that you're not increasing complexity by unnecessarily repeating code when doing this. Many languages have features that help you do this, simply factoring the common code into a function is one simple approach, and for example `deriving newtype`/`deriving via` are good approaches in Haskell.

Strong types are more important than code readability. You know what's better than your colleagues being able to easily read your function implementation to work out what inputs it needs and what it produces as output? Having them read a type signature that gives them that information. Or better still, having the compiler shout that at them without ever having to need to even look at the code.

So don't do this:

    my_binary_search(T x, List<T> l /* this list should be sorted */)

Do this:

    my_binary_search(T x, SortedList<T> l)

And yes, if your language doesn't have one, take the time to create a `SortedList` class, that has the invariant that when it's constructed it sorts the list. 

Like I said, this additional boilerplate of a `SortedList` is quite trivial in the grand scheme of things, and will save significant problems in the long term. Just do it. 

### 2. Use abstractions

Yes, using abstractions means it's going to be less obvious how your code relates to the actual thing you're trying to achieve. And often, this is a GOOD thing!

I think people overestimate how important it is for engineers to be able to understand the entire codebase. Comprehensible code is not in itself a bad thing, but for any non-trivial codebase it's largely impractical for an engineer to get their head around the code even related to just one change. 

I would argue if an engineer needs to read every possible code path all the way down the call stack to be confident in making a change/bugfix correctly, then fundamentally something has gone wrong. 

This is what good layered abstractions achieve. It allows engineers to not have to read down the entire callstack to dig out where the bug is. Good abstractions are more likely to be correct, and if they are wrong, they're more likely to break in ways that don't subtly break just one use-case. Of course the world is not perfect, and it's not impossible for abstract code to be broken in some way that produces an obscure bug that comes up only in certain circumstances, but it is far less likely. If all your code, with a whole lot of different types, is all using the same broken sort function, it's probably going to throw up problems all over the place, not just with one particular type in one particular circumstance.

So yes, more abstraction means it's LESS clear how code relates to the problems you're actually trying to solve. But more abstraction means you're less likely to need to read that code again anyway. You know what's better than readable code? Code you don't have to read in the first place.

### 3. Be a library author

This follows on from the abstraction discussion, but the funny thing is that often people who criticise code as "over engineered" and "unreadable", as if having every line comprehensible and relatable at a glance is incredibly important, will then still happily go and use a library from GitHub, which in many cases is just written by a random dude much like one of your engineers (and even if it isn't, it probably relies on some code written by some [random dude](https://xkcd.com/2347/)).

Even when you call `write()`, you're calling through dozen of layers of OS code, device drivers, down to embedded code on whatever harddisk/SSD/TCP socket, all of which is abstracted away from you.

You just have to be happy to use code you don't understand. That's just a reality of software engineering, and has been since we moved off punch cards. 

One may argue that library code/OS code is well used/tested and less likely to break. That's somewhat true (although not absolutely true) and in any case, that's in one way an argument for abstraction/writing code like it's a library, not an application, because in that case you're more likely to repeatedly use the code internally in various ways, all the time improving its quality and fixing its bugs.

Of course it's good to be able to read code easily. But it's not as important as some make it out to be, and sacrificing readability for abstraction and reusability is often worth the tradeoff. 

What's more important is to design clean, reusable, abstract interfaces. When one does that, you make it clear what the code does, and not only that, get the compiler to enforce that behaviour. 

## Aren't you over-engineering/optimising too early?

You can take anything to the extreme, and abstraction is no exception. There is an argument to be made that initially it's often not clear what the best abstractions are, until the code is actually put through real world usage/more requirements and then the best abstractions can be understood. And there's some truth to this. But that doesn't mean you should baby-bathwater it and just make your first iteration of code a mess of ints and strings. 

Representing your business types as separate to implementation types is just a no-brainer that is in fact, going to help you make those abstractions when they become more clear, as you've now got a place where those abstractions can be made. And at least define the invariants you do know, like in the `SortedList` example above. 

So yes, if you're being paid to write software for someone else, they're paying you to produce particular features for the real world, so yes, spending oodles of time trying to work out the ideal abstractions for new code that's very much on the edge of your system that you don't even know will be used by anything else is excessive. But don't just ignore cheap wins, and it's worth getting in the habit of just doing simple abstractions as a matter of course. The less obvious and more complex stuff should probably wait until a piece of code has been more battle tested so there's a better idea of what it's trying to achieve, and what are the complexities that arise, but once code is starting to get reused, it's then quite important to start thinking about abstractions and interfaces seriously. 

Because while badly designed code on the edge just can be fixed at a later date with no penalty, once you're piling bad interfaces on bad interfaces, you're not only going to have to repay that debt at some point, and until you pay that debt, you're paying interest every time you build something on top. And the more you build on top the bigger that debt gets, and that interest will slow development.

In short, to put it in a crude way, if you need to build shit quickly that's okay (although do take some basic effort to make cheap wins), but avoid piling shit on top of shit.

As a side note to managers, this is why it's important to keep your engineers in the loop about what features you're planning in the future. This doesn't need to be detailed, but they need to know, as your engineers themselves are likely to be the ones driving technical debt fixes. There's always more to fix than there's time to fix it, so they need to know how to prioritise it.

It's better for an engineer to have time to work on a piece of technical debt early than have the organisation being forced to make the decision to either delay a feature or compound a technical debt unnecessarily.

So in short, yes, there's a balance to everything. But "over-engineering" is often overused, and there are some cheap wins, like defining your business types separate to implementation types, that you should pretty much always apply with few exceptions (like perhaps throwaway scripts).

## The AI post-script

All of the above were my thoughts pre-agentic AI and how I've been writing software for as long as I can remember. Probably longer than my career, I think I had some of these ideas when I started self teaching OCaml and Haskell in High School (2002), even if I couldn't articulate the ideas then.

But, I do think the advent of agentic AI in software engineering makes all of the above even more true.

### Your agent can be trained to do the boilerplate.

If you look at my [`sample-weather-api`](https://github.com/clintonmead/sample-weather-api) developed with Cursor, you'll see a lot of the code is generated by AI. 

But it initially did so in the traditional manner. The sequence went something like this:

1. I gave the API a sample URL, and asked it to generate datatypes representing it.
2. It made a datatype with a bunch of strings/ints/floats and no explicitly defined types for the sub-components.
3. I then manually made an explicit type for one of the sub-components, put this in a separate file.
4. I then I told the AI to look at the last change I made, and do that change for all the other sub-components. 

So instead of writing that extra boilerplate for dozens of subtypes, I did it once, and the AI did the rest. If you look closely at the [`sample-weather-api`](https://github.com/clintonmead/sample-weather-api) commit history admittedly there was some fine tuning later on, but after a while creating these explicit types, which in the pre-AI era would have involved a copy/paste/replace for each one, now is just one quick agentic-AI request. For subsequent APIs I just said "build this API like the previous one" and it made all the subtypes immediately. 

### Get-there-itis

In my brief experience with agentic AI (you can see [`sample-weather-api`](https://github.com/clintonmead/sample-weather-api) for some more extensive commentary), I found that the agentic AI seems to have a serious case of [get-there-itis](https://en.wiktionary.org/wiki/get-there-itis), which is an aviation term which means:

> The determination of a pilot to reach a destination even when conditions for flying are very dangerous.

What I've found is that agentic AI has a bias towards producing code which manages to compile and pass the test cases, with less concern about the broader correctness, and a particular lack of concern about how the code may be reused in unforseen ways in the future. It just wants to "get there", finish that prompt. 

Well defined types and abstractions put guardrails on the AI and reduce its ability to do things that seem correct but are subtly wrong, precisely because these guardrails reduce complexity, namely they reduce the possibility of unintended emergent behaviour the AI might run into. 

This is a bit of a sidenote, but in my limited experience, strong types and abstractions go a long way but they're not enough. Many languages have functions which are "unsafe" but necessary, but they require the programmer to ensure invariants hold that aren't checked by the compiler, otherwise unexpected behaviour will occur. The AI will use these to get around abstractions it finds inconvenient, and just say "all done" when the tests pass even though it's left a ticking time bomb. It's probably worth having compile/linter rules that restrict various "unsafe" functions from agentic AI or at least require usages of these functions to be explicitly checked by a human being and marked as checked. 

### Compiling gives quicker feedback than tests

This is what it says on the tin. Usually a compile loop is quicker than tests, particularly when the compile fails, because as long as the compiler caches build results, a file that's just been changed is likely to fail immediately. A full compile is likely to take longer, but generally you can't run tests without compiling anyway, so this is still going to be quicker.

### Compile errors give narrower context than test failures

This is an advantage I haven't particularly experienced but I predict will be more important for non-trivial codebases. I've heard one of the biggest enemies of AI is large contexts. But when a compile fails, you've got a file and a line number. A codebase which tightly defines its types and invariants such that most mistakes result in compile errors means that an agentic AI can make significant changes and refactors to one part of the code and can just follow the compile errors to fix the other parts of the code directly, maintaining a small context. 

Whereas if a change causes a test failure, potentially it's not particularly obvious to the AI for a large codebase where the problem actually lies, because it could be that the change has resulted in some other part of the code failing that just happens to use part of the changed code. It basically needs to find that needle in the haystack, and with a large codebase inevitably that means a large context is required. 

## Further reading

Some of this discussion of complexity overlaps with my [approach to software development](https://clintonmead.github.io/approach.html) I've written previously, but that is broader and discusses the process of breaking down problems as a whole.