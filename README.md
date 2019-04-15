# 1. Introduction

## Implementation

* RPC
* Threads
* Concurrency Control

## Performance

The problem of Scaling

* Load im-balance, stragglers.
* Non-parallelizable code: initialization, interaction
* Bottlenecks from shared resources, e.g. network.

## Fault Tolerance

1000s of servers, complex net -&gt; always something broken. We'd like to hide these failures from the application.

* Availability: app can make progress despite failures
* Durability: app will come back to life when failures are repaired

Big Idea: Replicated Servers

## Consistency

E.g. "Get\(k\) yields the value from the most recent Put\(k,v\)."

Problems:

* "Replica" servers are hard to keep identical.
* Clients may crash midway through multi-step update.
* Servers crash at awkward moments, e.g. after executing but before replying.
* Network may make live servers look dead; risk of "split brain".

Consistency vs. Performance

* Consistency requires communication, e.g. to get latest Put\(\).
* "Strong consistency" often leads to slow systems.
* High performance often imposes "weak consistency" on applications.

    

  

  


