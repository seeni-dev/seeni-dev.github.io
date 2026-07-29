---
layout: post
title: "Query Engine: An old DAG mustn't have equal rights as that of latest"
---

I worked on a system which introduced a unique problem but probably common in query execution/pipeline systems.


# Problem

There was a process (A) which took the latest DAG, compiled it into code and returned a list of key-value pairs (tags) for each object you ran the code upon.

Each key is treated as a column in a DB table and is created/deleted dynamically.

Now, if you introduce a process (B) that takes the latest-1 DAG (i.e. the second-most-recent DAG, or any of previous DAGs) (Why? Maybe you wanted the previously completed DAG to run on new objects that were never run through your system. This scenario comes up when a user is expecting some version of data to show up for all objects rather than no data) and you allow process B to have the same column creation/deletion rights as that of process A, you have a problem. 

Process B is gonna delete an entire column that Process A just wrote to.


# Solution
Ideal solution must write to versioned tables (or rows) and downstream systems should be version-aware.

In most cases, restricting Process B from making schema changes will be a good-enough solution.
