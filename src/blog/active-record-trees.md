---
title: Tree data structure using ActiveRecord
date: 2018-12-23 20:47:18
excerpt: Approaches to introducde hierarchy into your models
type: post
blog: true
tags:
    - rails
    - postgres
    - sql
    - data structures
    - active record
---

# Modelling tree data structure in ActiveRecord

## Problem Statement
let's start with a basic scheme; group modelling. A group has a name and a group can belong to another group.
<insert image here>

Questions that I need to answer on this data structure

* parent of a node
* root of a node
* getting children of a node
* getting all descendants of a node

This is just a classic tree. The question is how to model it in our relational database.

Let's start with something very basic.

## Approach 1: adjacency list - tell every node who their parent is

Store parent_id as a foreign key reference to the parent node. With this approach
* `parent` of a node and `children` of a node can be found in one query. 
* `root` and `descendants` will take as many queries as the height of the tree.

Pros:
* very easy to implement and understand. Can be hand rolled - no need of an external library
* storage complexity is O(n). That is the best we can get.

Cons:
* multiple queries and hence multiple network hops make it unscalable after a certain depth of tree

Things get tricky from here

## Approach 2:  recursive queries

if you are using PostgreSQL as I was, writing recursive query can get some significant performance gains. Here's a [good article](https://hashrocket.com/blog/posts/recursive-sql-in-activerecord) explaining what I mean. 

**Pros**
* just one query! You save time on network but spend more time on a single query. I am yet to run benchmarks

**Cons**
* one hard query!
* rails ORM is a wrapper for relational databases. And not every relational database supports recursive queries. Postgres does but for example MySQL doesn't. You might want to reconsider using a raw query in your code base because that limits the choice of database backends you can use
* storage complexity is O(n) but with an extra temporary table. 

**Bonus**
* if your data is not updated really fast, you can you use [materialised views](https://hashrocket.com/blog/posts/materialized-view-strategies-using-postgresql) as well. 

## Approach 3: path enumeration / materialised path

store path to node (chain of ancestors) as a varchar in each node. 

```

```

## Approach 4: Closure tree / Closure table

store relationship of every possible combination of nodes. 


## Approach 5: Nested sets

