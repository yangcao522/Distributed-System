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

##   Map-Reduce

Input1 -&gt; Map -&gt; a,1  b,1  c,1  
Input2 -&gt; Map -&gt;        b,1  
Input3 -&gt; Map -&gt; a,1         c,1  
                               \|       \|       \|  
                               \|       \|       -&gt; Reduce -&gt; c,2  
                               \|        -----&gt; Reduce -&gt; b,2  
                               ---------&gt; Reduce -&gt; a,2

1. MR calls Map\(\) for each input file, produces set of k2, v2 "intermediate" data, each Map\(\) call is a "task"
2. MR gathers all intermediate v2's for a given k2, and passes them to a Reduce call
3. final output is set of &lt;k2, v3&gt; pairs from Reduce\(\) stored in R output files

\[diagram: MapReduce API -- map\(k1, v1\) -&gt; list\(k2, v2\) reduce\(k2, list\(v2\) -&gt; list\(k2, v3\)\]

### MapReduce scales well.

You can get more throughput by buying more computers. Rather than special-purpose efficient parallelizations of each application. Computers are cheaper than programmers!

### What will likely limit the performance?



  

  


