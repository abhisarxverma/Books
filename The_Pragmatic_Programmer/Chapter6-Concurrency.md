# **🕑 Chapter 6 - Concurrency** 

**Concurrency** is when two or more pieces of code act as if they run at the same time and **parallelism** is when they do run at the same time.

## **🌎 Everything is Concurrent**

Concurrency is requirement if you want your application to be able to deal with the real world, where things are asynchronous: users are interacting, data is being fetched, external services are being called, all at the same time.

## **⛓️‍💥 Breaking Temporal Coupling**

### **Looking for Concurrency**

> ** 👉Analyze Workflow to Improve Concurrency**

An activity diagram consist set of actions drawn around rounded box - 

- The arrow leaving an action leads to either another action (Which can start once the first action is completed)
- or to a thick line called Synchronization bar.
- Once all actions leading to the synchronization bar are complete you can then proceed along any arrows leaving the bar..
- An action with no arrays leading into it can be started at any time.

### **Opportunities For Concurrency**

We're hoping to find activities that take time, but not time in our code. Querying a database, accessing an external service, waiting for user input: all these things would normally stall our program until they complete. And these all are opportunities to do something more productive than the CPU equivalent of twiddling one's thumbs.

### **Opportunities For Parallelism**

**Remember**
Concurrency is software mechanism, and parallelism is Hardware mechanism

If we have multiple processors either locally or remotely, then if can split work out among them we can reduce the overall time things take.

The Ideal things to split this way are pieces of work tha tare relatively independent - where each can proceed without waiting for anything from the others. A common pattern is to take a large pieces of work. Split it into independent chunks, process each in parallel, then combine the results.