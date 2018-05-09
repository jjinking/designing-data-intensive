# Part 1 Foundations of Data Systems

## Chapter 1 Reliable Scalable and Maintainable Applications

Boundaries between categories of software becoming blurred

  - Redis is a datastore but also used as a message queue
  - Kafka is a message queue with db-like durability guarantees
  
Single tool is not enuf, and we end up using multiple tools; Application code has to make sure they're all in sync

### Reliability

Software works correctly despite hardware/software faults or human error

**fault**: a single component of a system deviating from its spec

**failure**: the system as a whole stops providing service

Almost impossible for system to not have faults, so we design systems to prevent faults from becoming failures

We can build **resiliant**, **fault-tolerant** systems that can automatically recover from certian kinds of faults, not all.

Netflix's *Chaos Monkey* is a tool to test fault-tolerance.

#### Hardware faults

Disk corruption, etc

Used to have smaller number of servers with hot-swappable components, but nowdays, applications use much more servers, so the pattern has changed. No longer trying to prevent loss of entire machine.

  - Use multiple servers that are less reliable (cloud), so that entire machines can fail, but it's okay
  - Use software fault-tolerance techniques to recover from machines going down

Scalability - reasonable ways to deal with growth in volume and complexity

Maintainability - engineers should be able to productively maintain current functionality and adapt to new use cases

#### Software errors

While hardware faults are independent across nodes, software bugs are not since all nodes run same or inter-dependent software. No overarching solution, but smaller helpful solutions exist:

1. Careful software design with thorough testing
2. System monitoring in production
3. Continously check guaranteed assumptions

#### Human errors

Bad interaction or configuration of system

- Make it easy to do the "right" thing
- Provide sandboxing env for people to try different things, so they don't mess up production system
- Test thoroughly: unit, integration & manual
- Set up quick and easy recovery from failures - easy rolling back of config, rollout new code gradually, tools for recomputing data
- Metrics - performance, error

### Scalability

A system's ability to cope with increased load

Multi-dimensional, only makes sense to talk about scalability w.r.t a specific type of load, i.e. data transfer load, cpu load, etc

Use **load parameters** to describe current load, i.e. requests per second to a web server
