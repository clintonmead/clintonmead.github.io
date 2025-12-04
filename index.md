---
title: Clinton Mead’s Resume/Portfolio
---

## Summary

Hi, I'm a software developer based in Sydney, Australia.

In my career, I've worked with a variety of programming languages, primarily Haskell, C#, Scala, Java, and C++, but also TypeScript, Python, Perl, and Unix Shell.

I've also done some open-source work in Rust.

I have extensive experience using SQL in relational databases (PostgreSQL and Oracle) and some experience with BigQuery.

Regarding DevOps, I have used Nix extensively to manage a build system and have used Terraform to manage Google infrastructure.

I've worked in various roles, including integrations, application support, and Windows UI development, but my most recent experience has been backend-focused, with some frontend and cloud infrastructure work on the side.

I've written some articles about my approach to software engineering, which you can read [here](https://clintonmead.github.io/articles.html).

If you think I'd be valuable to your organization, feel free to send me an email at [clintonmead@gmail.com](mailto:clintonmead@gmail.com) or message me on [LinkedIn](https://www.linkedin.com/in/clintonmead/).

Note: If you're reading this in a PDF, an up-to-date, web-based version of this resume can be found at [https://clintonmead.github.io/](https://clintonmead.github.io/).

You can also save this page as a PDF by [clicking here](https://pdfcrowd.com/url_to_pdf/).

## Employment History

### Haskell Engineer - PaidRight (July 2022 - February 2025)

Primary backend developer at [PaidRight](https://www.paidright.io). The backend was written in Haskell, and I developed and maintained interfaces with Google BigQuery, Google PubSub, GCS, PostgreSQL, and Auth0 as part of the required application logic. I also developed a type-safe API exposed via OpenAPI that produced type-safe TypeScript code, triggering compile errors if inconsistent changes were made to the backend and frontend. These were achieved with significant contributions to [Autodocodec](https://github.com/NorfairKing/autodocodec/) and [AesonDiff](https://github.com/clintonmead/aeson-diff). I was the primary maintainer of our Nix build system and worked on updating our Terraform infrastructure for deploying our backend.

### Scala/JavaScript Engineer - Complii (July 2021 - March 2022)

Sole developer and administrator of [ThinkCaddie](https://thinkcaddie.com). The Scala backend and JavaScript frontend were served by AWS EC2 instances and an AWS RDS PostgreSQL database. The JavaScript frontend was based on [React+Redux](https://react-redux.js.org/), and the Scala backend used the [Play Framework](https://www.playframework.com/), with a functional programming style throughout both the backend and frontend. As the sole developer and administrator, I worked across the entire stack and handled DevOps and deployments. I also developed a NixOS-based virtual machine configuration to get new developers up and running with all build dependencies and editor plugins within minutes.

### C# Engineer - yReceipts/eyos (February 2018 - June 2021)

C# and .NET Engineer with a focus on interfacing with Windows printing and UI development. A large part of my role involved developing a generic, rules-based model for matching products purchased at checkout against numerous “promotions,” triggering discounts or free products based on rules. I designed this rule engine to allow nested rules resolved in real-time. A significant part of my role was introducing functional programming practices where appropriate to a more imperative/object-oriented codebase.

### Haskell Engineer - University of New South Wales (April 2017 - September 2017)

Limited-term contract funded by a research grant. Work primarily consisted of redeveloping the lexer, parser, and type checker for the compiler for the language [MCK](http://cgi.cse.unsw.edu.au/~mck/pmck/).

### Staffer - Senator Leyonhjelm (February 2016 - December 2016)

Tasks included creating, analyzing, and adjusting social media advertising campaigns, developing websites using PHP and WordPress, and analyzing electoral results data.

### Application Development and Support - University of Wollongong (2006 - 2015)

Application support and integration development primarily for [Blackboard](http://www.blackboard.com/learning-management-system/blackboard-learn.aspx) and [Equella](http://www.equella.com/). The role focused on maintaining and enhancing the performance of a clustered system serving over 1,000 simultaneous users, covering both the frontend and backend, including an Oracle database. I maintained and extended integrations between university systems, mostly written in Perl with some shell scripting. I also implemented single-sign-on protocols between off-the-shelf and in-house PL/SQL products and developed custom Oracle database-hosted hierarchical staff permissioning models for the university’s content management system, Equella. Additionally, I worked on various data processing tasks for the School of Psychology, primarily in C++.

## Education

Bachelor of Mathematics/Bachelor of Computer Science - University of Wollongong (2003 - 2006). A copy of my [academic transcript is here](https://clintonmead.github.io/transcript.html).

## Open Source Work

Below, I've listed some of my more significant and recent open-source work. Additional work can be found [here](https://clintonmead.github.io/opensource.html).

## Contributions to Existing Projects

### Haskell

#### [Autodocodec](https://github.com/NorfairKing/autodocodec/)

Autodocodec is not my project, but I have made significant contributions to it. It allows one to define a codec, decoder, and documentation with a single definition, consistently generating serializers, deserializers (for JSON or other formats), OpenAPIs, and more. My contributions focused on increasing the library's flexibility and adding support for new datatypes.

#### [AesonDiff](https://github.com/clintonmead/aeson-diff)

AesonDiff was not originally my project but was handed over to me after I made significant contributions, as it was otherwise dormant. AesonDiff is an implementation of the [JSON Patch](https://en.wikipedia.org/wiki/JSON_Patch) standard in Haskell. I added OpenAPI spec generation and extensions to the protocol to simplify type-safe usage from TypeScript. Due to these contributions, the maintainer handed over the project, and I am now the maintainer.

## Original Projects

### Haskell

#### [Fast-mult](https://hackage.haskell.org/package/fast-mult)

[`Fast-mult`](https://hackage.haskell.org/package/fast-mult) is an integer type that intelligently delays multiplications to perform them only with similar-sized operands, greatly improving the performance of repeated multiplications producing large integers. This can enhance the performance of existing numeric algorithms without changing the algorithms themselves. More details are in [`fast-mult’s` Hackage documentation](https://hackage.haskell.org/package/fast-mult-0.1.0.2/docs/Data-FastMult.html). I plan to extend this to handle addition and possibly write a version in Rust.

### Rust

#### [Haskell Bits](https://github.com/clintonmead/haskell_bits)

A port of Haskell concepts into Rust, including the Functor/Applicative/Monad hierarchy. I presented this at [June 2019 Rust-Syd](https://www.meetup.com/en-AU/Rust-Sydney/events/262194894/).

### C#

#### [Typeclasses in C#](https://github.com/clintonmead/type-classes-in-csharp)

A proof of concept for a Functor/Applicative/Monad hierarchy in C#, presented at [November 2018 FP-Syd](http://fp-syd.ouroborus.net/wiki/Past/2018).

## Ideas for Future Projects

### Haskell

#### CRUD-Style Type Generation

In web applications, CRUD-style datatypes are common, involving entities one wants to create, read, update, delete, and often perform bulk queries on. This involves several components:

1. A backing database
2. Serialization/deserialization code
3. A web server that serves the API
4. An OpenAPI specification to generate type-safe types in another language, documentation, and an admin/testing interface

Each of these operations (create, read, update, delete) often requires different implementations. Additionally, entity fields may be treated differently: some may be considered the "primary key" (unique and used for creation/deletion), some freely modifiable by the client, and others (e.g., owner) controlled by the server. Fields like "created time" or "id" may be auto-generated by the database.

The idea behind this framework is to encapsulate these details in a single type definition, generating consistent database calls, serialization/deserialization functions, a web server, and an API spec without repetitive boilerplate. However, it must allow for custom logic injection for complex cases like authentication and authorization.

I have made progress toward this, with some contributions to [Autodocodec](#autodocodec) and [AesonDiff](#aesondiff) in pursuit of this goal.

I also plan to add telemetry providers to this framework.

The goal is to enable adding new entities to a web application within minutes, facilitating rapid prototyping, application expansion, and reducing the number of backend developers needed, even with a significant frontend and UI team.

## More About Me

### Football

I'm a keen football goalkeeper, playing both indoor and outdoor. If your company’s lunchtime team needs a keeper, I can assist!
