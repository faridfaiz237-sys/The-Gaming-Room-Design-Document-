# The-Gaming-Room-Design-Document-

## Portfolio Reflection

**Briefly summarize The Gaming Room client and their software requirements. Who was the client? What type of software did they want you to design?**

The client was The Gaming Room, a company that owned a game called *Draw It or Lose It*, which at the time only existed as an Android app. They wanted to expand it into a web based application that could reach multiple platforms, including desktop browsers on Windows, Mac, and Linux, as well as iOS and Android, instead of being locked to a single operating system. Their core software requirements were that a game had to support one or more teams, each team had to support multiple players, game and team names had to be unique, and only one instance of the game engine could exist in memory at any given time, with unique identifiers generated for every game, team, and player.

**What did you do particularly well in developing this documentation?**

I think the strongest part of my documentation was tying every design decision directly back to a specific client requirement instead of just describing the code in isolation. When I explained the Singleton pattern in GameService, I connected it explicitly to the requirement that only one instance of the game can exist in memory, and when I explained the Iterator pattern, I connected it to the uniqueness requirement for game and team names. That made the documentation read less like a generic description of design patterns and more like an actual justification for why each pattern was the right choice for this specific client.

**What about the process of working through a design document did you find helpful when developing the code?**

Working through the UML diagram and the Domain Model section before touching the code forced me to think through the relationships between Entity, Game, Team, and Player ahead of time, rather than discovering the structure as I went. Because I had already reasoned through why Game, Team, and Player should all inherit from a shared Entity base class, the actual refactor was mostly mechanical. I already knew what belonged in the base class versus each subclass, so I wasn't second guessing the structure mid implementation. The design document essentially became a checklist I could code against.

**If you could choose one part of your work on these documents to revise, what would you pick? How would you improve it?**

I would go back and expand the System Architecture View section. I mostly left it as a placeholder since the course notes said it wasn't required for these particular projects, but in hindsight, sketching out even a simple diagram of the client server topology (browser and mobile clients, load balancer, application servers, database, and object storage for the image library) earlier in the process would have made the later Recommendations section, especially the Distributed Systems and Security answers, easier to write, since I would have already had the physical picture in front of me instead of describing it from scratch at the end.

**How did you interpret the user's needs and implement them into your software design? Why is it so important to consider the user's needs when designing?**

The client's needs showed up in the design in very direct ways. The requirement that only one instance of the game can exist in memory became the Singleton pattern. The requirement that game and team names must be unique became the Iterator pattern searching existing collections before creating a new entry. The requirement to support multiple platforms became the decision to build a responsive HTML client instead of separate native apps, and to recommend Linux for hosting, since it was the only platform that could scale that client base without heavy licensing costs. Considering the user's needs mattered because a technically elegant design that ignores what the client actually asked for isn't useful. The whole point of the design phase is translating a business requirement into a structure that satisfies it efficiently, rather than building something impressive that solves the wrong problem.

**How did you approach designing software? What techniques or strategies would you use in the future to analyze and design a similar software application?**

My approach was to start from the client's stated requirements, identify which ones implied a need for a specific design pattern or architectural decision, and only then move to the UML diagram and code. I found it useful to keep asking why the client needed this, specifically, for every class and method, rather than just describing what the code does. In the future, I'd continue using that requirements first approach, and I'd also try to sketch the system architecture earlier in the process rather than leaving it until the Recommendations phase, since having that mental picture up front makes it easier to reason about scalability, security, and distributed systems concerns from the start instead of retrofitting them at the end.
