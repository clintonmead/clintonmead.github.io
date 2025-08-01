## Welcome/Summary

Hi, I'm a software developer based in Sydney Australia. 

I've worked in a variety of programming lanauges, particularly Haskell, C# and Scala.

I also have some experience using C++, TypeScript, Java, Python, Perl and Groovy. 

Throughout most of my career I've done a lot of SQL, mainly focusing on relational databases (Postgres and Oracle) but I have had some interaction with BigQuery also.

Outside of programming languages, I have used Nix extensively to manage a build system, and have used Terraform a bit to manage Google infrastructure.

## Employment history:

### Haskell Engineer - PaidRight (July 2022 - Feburary 2025)

Primary backend developer at [PaidRight](https://www.paidright.io). Backend was written in Haskell, developed and maintained interfaces with Google BigQuery, Google PubSub, GCS, Postgres and Auth0, as part of the required application logic. Also developed a typesafe API exposed via OpenAPI that produced typesafe TypeScript code which would trigger compile errors if inconsistent changes were made to the backend and frontend. These were achieved with the help of significant contributions to [Autodocodec](https://github.com/NorfairKing/autodocodec/) and [AesonDiff](https://github.com/clintonmead/aeson-diff). I was also the primary maintainer of our Nix build system, and did work in updating our Terraform infrastructure when it came to deploying our backend.

### Scala/Javascript Engineer - Complii (July 2021 - March 2022)

Sole developer and adminstrator of [ThinkCaddie](https://thinkcaddie.com). Scala backend with Javascript frontend, served by AWS EC2 instances and a AWS RDS Postgres database. The Javascript frontend was based on [React+Redux](https://react-redux.js.org/), and the Scala backend was using the [Play Framework](https://www.playframework.com/), with a functional programming style used throughout both the backend and frontend. As sole developer and adminstrator I worked throughout the entire stack, and also did the devops work and deployments. As part of the role, I also worked on Complii's primary product, which was a .NET Core product written in C#, which was also full-stack work from adding new database tables to creating new frontend pages.

### C# Engineer - yReceipts/eyos (Feburary 2018 - June 2021)

C# and .NET Engineer. Particular focus on interfacing with Windows printing and UI development. Large part of my role was developing a generic rules based model for matching products purchased at checkout against a large number of “promotions”, that would trigger on based on a rule and provide some sort of discount or free product to the user. I designed this rule engine in a way that allowed for rules to be nested within rules yet these rules could be resolved in real-time. A significant part of my role here also was to bring functional programming practices where appropriate to a more imperative/object-orientated codebase.

### Haskell Engineer - University of New South Wales (April 2017 to September 2017)

### Staffer - Senator Leyonhjelm (Feburary 2016 - December 2016)

### Application Development and Support - University of Wollongong (2006 - 2015)

## Education:

Bachelor of Mathematics/Bachelor of Computer Science - University of Wollongong (2003 - 2006). A copy of my [academic transcript is here](https://clintonmead.github.io/transcript.html). 

## C# Open source work

### [Battletech Mods](https://github.com/clintonmead/BattletechMods)
A variety of mods for the game [Battletech](http://battletechgame.com/), using [Harmony](https://github.com/pardeike/Harmony) to patch CLR methods at runtime and reflection to change ingame private data. 
