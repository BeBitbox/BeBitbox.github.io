---
layout: post
title:  "Architectural principles"
date:   2024-09-20 15:21:57 +0100
permalink: /architectura-principles/
---

The following principles are for me personally the key guidelines to follow when designing software solutions.

![Architect](/images/cyber-architect.png)

### Managed Service approach 
Public cloud provides like AWS and Azure offer fully managed services that will provide a lot of functionality out-of-the-box.
I use it for solutions that are not critical or part of my core-business.
Maintaining, updating, or managing such services myself is rarely worthwhile when specialized teams, backed by strong SLAs, handle them efficiently.
As an architect, my primary focus is creating useful and valuable solutions.
When possible I try to outsource non-critical components to other parties.

### Prevent vendor lock-in
For every architecture decision, take into account that it is not a binding marriage. 
Take into account what it will take to migrate from the vendor, the software and especially the data.
It's better to have an exit-plan because I have no idea where the technology will go in 5 years.
What if the software licenses suddenly become more expensive? Or the hosting? Or there is a new alternative technology available?
This also includes the managed services, I mentioned in previous point.

### DDD
Domain Driven Design is a methodology to design big maintainable software solutions.
First we need to define different domains, their models inside them and the boundaries with the outside world.
This can lead to microservice architecture, making it very easy to work in parallel on different domains, with different teams.

### Event driven
Every state change in a domain should result into meaningful business events, so applications interested in those changes can listen to the events.
I love an Event-Driven Architecture, but it has its caveats and downsides.
An event should be something that happened, has some value for the outside world and can be thrown on an eventbus.
Commands are something that should happen. It should remain peer-to-peer and instead of an eventbus, use API-calls.
All the events together will be an eventstore, an audit-trail, a gold pile of data.

### Build Once, Deploy Anywhere
Every new application should be as containerized as possible: it should spin-up locally, on-premise, in the cloud,… from one base-image.
Ideally the same image is deployed on both production as test-environments which only needs environment specific variables to run.

### You build it, you run it!
Every team should be able to run and test something from “A” to “Z”. 
For a project or initiative you should have a cross-functional team that can go through all the stages: analysis, development, testing and deploying. 
The team is responsible for the entire chain, so they need to have as few external dependencies as possible.
This will greatly reduce the amount of meetings, overhead and discussions.

### Continuous integration, Continuous delivery
Developers can merge the code when all the tests are green, ensuring that there is no regression being introduced.
After the build phase, the software can be deployed reliable and automatic.
This process will ensure that the time from a requested code change to running software in production will be as short as possible.

### Version Control
All software, documentation and IaC (infrastructure as code) is checked into a version control system, so we keep a complete history of the changes.
This makes it easy to debug, roll-back and ensure there is no data loss.

### Hexagonal Architecture (also known as ports and adapters)
Divide the code inside an application into ports and adapters, so it’s easy to change the technology or extract functionality when needed.
The main idea is to group functional logic inside the core including ports as interface, and make sure the domain does not depend on the adapters.
The adapters are specific implementations of ports that will be very specific mapping or configuration, like a REST-adapter or NoSQL code to write in Mongo.

### Clean code/architecture
Follow the best common practices of software development: clean code, SOLID, clean Architecture,... 
Example: the code should be self-explanatory with good names that matches the business lingo.

### Automated testing
To improve the CI and CD, it is necessary to have automated testing, that can automatically run on every deploy.
This will ensure that a small code change will not introduce new bugs. 
The testing can involve: unit/component/integration/smoke/stress/e2e/contract/...
