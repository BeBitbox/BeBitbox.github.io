---
layout: post
title:  Book Release it (second edition)
date:   2024-03-21 15:21:57 +0100
permalink: /release-it/
---

## The book

I read the book "Release It! Design and Deploy Production-Ready Software", Second Edition, by Michael T. Nygard.
The goal of this book is to discuss the gap between software development and actual application code running in production environments. 

![Book Cover](/images/release-it.png)

## My short feedback
This book contains a lot of knowledge about what can go wrong in the real world and the book does a great job summarizing it.
The mission of an ITer should be to create and deploy software that is balanced, up +99,999% of the time (the five nines) and when things go wrong, detect and fix it as soon as possible.
I agree 100% with that vision and the DevOps approach of the author.

The book describes some wartime stories of devastating production issues and how they were able to solve it.
This was really the most fun part to read.
The more boring part was the theoretic part, and it could be quite tedious at times.
I didn't learn much, except 'Database queries should always have a limit'.
This is so true because your data grows over time and so possibly the query results.
Define upper limits so that you don't get memory exceptions and take the limits by default into your design.

In the end I have my summary below, and see what applies on the current software I'm developing.

## Summary

### Anti-patterns
* Locks (database locks, software locks, thread locks,...), which leads to thread starvation
* Pools filling up, like connection or processing pools
* Hard coded configuration: no possibilities to tweak of configure without compiling code
* Single Point of Failure: critical component without failover
* Cascading failures: too tightly coupled components will cause that when one goes down, the other one will follow
* Snowflake servers: too much manual configuration that makes it hard to recreate a system
* Cache too big: caching is great, but keep it under control
* Synchronized calls: avoid when possible, because big cause of thread-locking
* Dog pile: Servers do transient load all at once, like rebooting all the servers at once because of a big configuration change, or like a cron that is the same for all servers

## Stability patterns
* Health checks: on the application, but also on database query (select count(*) from dual)
* Caching (redis/memcached) to increase performance and capacity
* Limits on database queries: every database query should be limited
* Timeouts are implemented to stop threads hanging forever
* Circuit breakers: detect failing parts of the system and avoids calls that will probably fail anyway
* Bulkheads (inspired by the compartments in ships, to prevent liquid flowing to fast from one side to another): so isolate when possible
* Keep data growth under control, using archiving or other tools
* Roll the logs to avoid too much disk usage
* Fail fast: validation and resource check first before continuing
* Let it crash: save the system, by letting some components crash
* Handshaking pattern: server lets us know when it is ready to accept incoming connections 
* Test Harness: emulate network errors during testing
* Decouple software components as much as possible

## Capacity
* Identify the bottlenecks of your system
* Specific load testing helps to determine the constraints of the system
* When more capacity is needed: determine between vertical and horizontal scaling
* Elastic scaling: autoscaling, Kubernetes, Cloud solutions,...
* Efficient resource utilization: determine CPU, memory, network usage and see how to improve
* Rate limiting and throttling: determine the SLA you offer to customers and block or slow some requests

## Software design
* Use the previous mentioned stability patterns
* Modular architecture: well-defined and loosely coupled modules or applications using Micro-services and event-driven architecture
* Evolutionary design: embrace future changes in system requirements or customer behavior, so make incremental changes easy. Create API's that are forward-compatible and open to change
* Anticipating failure: take redundancy, failover mechanisms and graceful degradation in account
* Cross-disciplinary teams: bundle all the necessary knowledge in one team

## Operational work
* Automate as much as possible
* Continuous Integration: automated build, test, packaging processes
* Continuous Delivery: automated releases, deployments
* Proactive monitoring and alerting
* Incident management: have a blameless playbook on what to do when certain events happen
* Infrastructure as code: a system must be easy to recreate, so avoid manual installations
* Security: define roles, group, permissions for all the users or collaborators
