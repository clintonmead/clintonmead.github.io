# Clinton Mead's Resume/Portfolio

## Summary

Hi, I'm a software developer based in Sydney Australia. 

I've worked in a variety of programming lanauges, particularly Haskell, C# and Scala.

I also have some experience using C++, TypeScript, Java, Python, Perl and Groovy, and an interest in working with Rust.

Also throughout most of my career I've done a lot of SQL, mainly focusing on relational databases (Postgres and Oracle) but I have had some interaction with BigQuery also.

Outside of programming languages, I have used Nix extensively to manage a build system, and have used Terraform a bit to manage Google infrastructure.

If you think I'd be valuable to your organisation feel free to send me an email at [clintonmead@gmail.com](mailto:clintonmead@gmail.com) or drop me a message on [LinkedIn](https://www.linkedin.com/in/clintonmead/).

Note, if you're reading this in a PDF, a web based and up to date version of this resume can be found at [https://clintonmead.github.io/](https://clintonmead.github.io/). 

You can also save this page as a PDF by [clicking here](https://pdfcrowd.com/url_to_pdf/).

## Employment history:

### Haskell Engineer - PaidRight (July 2022 - Feburary 2025)

Primary backend developer at [PaidRight](https://www.paidright.io). Backend was written in Haskell, developed and maintained interfaces with Google BigQuery, Google PubSub, GCS, Postgres and Auth0, as part of the required application logic. Also developed a typesafe API exposed via OpenAPI that produced typesafe TypeScript code which would trigger compile errors if inconsistent changes were made to the backend and frontend. These were achieved with the help of significant contributions to [Autodocodec](https://github.com/NorfairKing/autodocodec/) and [AesonDiff](https://github.com/clintonmead/aeson-diff). I was also the primary maintainer of our Nix build system, and did work in updating our Terraform infrastructure when it came to deploying our backend.

### Scala/Javascript Engineer - Complii (July 2021 - March 2022)

Sole developer and adminstrator of [ThinkCaddie](https://thinkcaddie.com). Scala backend with Javascript frontend, served by AWS EC2 instances and a AWS RDS Postgres database. The Javascript frontend was based on [React+Redux](https://react-redux.js.org/), and the Scala backend was using the [Play Framework](https://www.playframework.com/), with a functional programming style used throughout both the backend and frontend. As sole developer and adminstrator I worked throughout the entire stack, and also did the devops work and deployments. I also developed a NixOS based virtual machine configuration designed to get new developers up and running with all build dependencies and editor plugins within minutes.

### C# Engineer - yReceipts/eyos (Feburary 2018 - June 2021)

C# and .NET Engineer. Particular focus on interfacing with Windows printing and UI development. Large part of my role was developing a generic rules based model for matching products purchased at checkout against a large number of “promotions”, that would trigger on based on a rule and provide some sort of discount or free product to the user. I designed this rule engine in a way that allowed for rules to be nested within rules yet these rules could be resolved in real-time. A significant part of my role here also was to bring functional programming practices where appropriate to a more imperative/object-orientated codebase.

### Haskell Engineer - University of New South Wales (April 2017 to September 2017)

Limited term contract funded by a research grant. Work primarily consisted of redeveloping the lexer, parser and type checker for the compiler for the language [MCK](http://cgi.cse.unsw.edu.au/~mck/pmck/).

### Staffer - Senator Leyonhjelm (Feburary 2016 - December 2016)

Tasks included creating, analysing and adjusting social media advertising campaigns, development on websites using PHP and Wordpress, and analysis of electoral results data.

### Application Development and Support - University of Wollongong (2006 - 2015)

Application support and integration development primarily for [Blackboard](http://www.blackboard.com/learning-management-system/blackboard-learn.aspx) but also [Equella](http://www.equella.com/). Role included application support, focused on maintaining and enhancing the performance of a clustered system serving 1000+ simultaneous users, both of the front-end, and the back-end and Oracle database. Also work involved maintaining and extending integrations between university systems, which were written mostly in Perl with some shell scripting. Also implemented single-signon protocols between off the shelf products and PL/SQL inhouse products, and developed custom Oracle database hosted hierarchical staff permissioning models for the University content management system Equella. I also worked on various data processing tasks for the school of psychology, primarily in C++.

## Education:

Bachelor of Mathematics/Bachelor of Computer Science - University of Wollongong (2003 - 2006). A copy of my [academic transcript is here](https://clintonmead.github.io/transcript.html). 

## Open source work

Below I've placed some of my more major and recent open source work. However you can see additional work [here](https://clintonmead.github.io/opensource.html).

## Contributions to existing projects

### Haskell:

#### [Autodocodec](github.com/NorfairKing/autodocodec/)

Autodocodec is not my project, but a project I have made significant contributions to, which allows one, with a single definition, define a codec, decodec, and documentation, and consistently generate, serialisers, deserialisers (for JSON or other formats), OpenAPIs and other things. My contributions primary focused around increasing the library's flexibility and adding new datatypes for the library to natively handle.

#### [AesonDiff](https://github.com/clintonmead/aeson-diff)

AesonDiff also originally wasn't my project, but was handed over to me after making significant contributions as it was otherwise dormant. AesonDiff is an implementation of the [JSON Patch](https://en.wikipedia.org/wiki/JSON_Patch) standard in Haskell. I added OpenAPI spec generation to this library and extensions to the protocol to make typesafe usage easier from typescript. Due to these contributions the maintainer handed over the project to me and I am now the maintainer.

## Original projects

### Haskell:

#### [Fast-mult](https://hackage.haskell.org/package/fast-mult)

[`Fast-mult`](https://hackage.haskell.org/package/fast-mult) is an integer type that intelligently delays multiplications in such a way that multiplications are only performed with similar sized operands, greatly improving the performance of repeated muliplications which produce large integers. Hence it can improve the performance of existing numeric algorithms without changing the algorithms themselves. More details are in [`fast-mults` hackage documentation]( https://hackage.haskell.org/package/fast-mult-0.1.0.2/docs/Data-FastMult.html). I do have plans to extend modify and extend this to handle addition also, and perhaps write a version in Rust.

### Rust:

#### [Haskell Bits](https://github.com/clintonmead/haskell_bits)

A port of Haskell concepts into Rust, including the Functor/Applicative/Monad hierarchy. I did a presentation on this at [June 2019 Rust-Syd](https://www.meetup.com/en-AU/Rust-Sydney/events/262194894/).

### C#:

#### [Typeclasses in C#](https://github.com/clintonmead/type-classes-in-csharp)
A proof of concept for a Functor/Applicative/Monad hierarchy in C#, presented at [November 2018 FP-Syd](http://fp-syd.ouroborus.net/wiki/Past/2018).

## Ideas for future projects

### Haskell:

#### CRUD stuff type generation

In web application, a CRUD style datatype is quite common, an entity that one wants create, read, update, delete, and often perform bulk queries on also. There's a number of components to this:

1. A backing database
2. Serialisation/deserialisation code
3. A webserver that serves the API
4. An OpenAPI specification to generate typesafe types in a different lanugage, documentation and an admin/testing interface.

In addition for each of these four steps will often need different implementations for the different operations, create, read, update and delete.

And for these entities, the fields of these entities may be treated differently. For example, some fields my be considered the "primary key", which is unique and used for creation and deletion operations. Additionally, some may be freely modifiable by the client, but others (say the owner of the entity) may be controlled by the server itself. Furthermore, some fields, say a "created time" or "id", may be auto-generated on creation by the database.

The idea behind this framework is to encapulate these details in a single type defintion, and then generate database calls, serialisation/deserialisation function, a webserver, and an API spec which are all consistent, without repeating all this work for every entity created (as much of the time this is quite boilerplatey anyway). However, one must leave some room for custom logic to be injected where required, as things like authentication and authorisation are needed, and permissioning logic may be complex. 

I have done some work towards this, and some of my contributions towards [Autodocodec](#autodocodec) and [AesonDiff](#aesondiff) have been in pursuit of this.

I would also like to add telemetry providers to this framework also.

The idea should be that adding new entities to a web application should be a job that should be completed within minutes in most cases, allowing for more rapid prototyping and expanding an application, and reducing the number of backend developers required to maintain an application, even when there is a significant frontend and UI team.

## More about me

### Approach of software development

[You can read some thoughts](https://clintonmead.github.io/philosophy.html) on my approach to designing software. Whilst I don't think my approach is unique I don't think it's the norm either so it's probably worthwhile reading this to get a better idea of whether or not I'd fit into your team and culture.

### Football

I'm a keen football goalkeeper, playing both indoor and outdoor, so if your company lunchtime team needs a keeper I can assist!
