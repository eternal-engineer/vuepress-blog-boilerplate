---
title: A philosophy of software design
date: 2020-03-22 00:00:00
excerpt: Chapter notes
type: post
blog: true
tags:
    - book
    - notes
    - software design
---

## Chapter One - It's all about complexity

* The greatest limitation in writing software is our ability to understand the systems we are creating.
* Creating working software is expensive. It’s very much a cost and time optimisation game. More complex the software, the more time it takes and more expensive it becomes.
* Good designs are complexity reducers. They keep the complexity level in check.
* Two approaches to fight complexity
    * Eliminate complexity - remove special cases, consistent styling, etc.
    * Encapsulate complexity - so that we can work on a system without dealing with it's complexity  
* Software Design is not an upfront task we do. We have the ability, and we should continuously iterate and improve. 
* Incremental design also means continuous redesign
* The question to ask while making a design change is: Is the software less or more complex? Complexity is a very good measure of design. 


## Chapter Two - The nature of complexity

* Complexity is **anything** related to the **structure** of a software system that makes it hard to **understand and modify**
* Complexity is a point in time measure of the **piece** of code we are trying to understand or modify. for example, if a complex system is rarely used and doesn't need to be understood, it adds little value to the overall complexity
* Complexity is more apparent to readers :) 

**Symptoms of complexity**

* Change amplification - huge change radius for a visible small change.
* Cognitive Load - How much information do I need to know to complete a task. Too much information increases the chances of missing out on something crucial and hence bugs crop up. eg. global variables, API's with destructive side effects.
* Unknown Unknowns - not sure which piece of code to change for completing a task. This is a factor for every person who's new to the team


* One of the most import design goals is to make the system ***obvious***. Obvious systems reduce onboarding thereby reducing time, effort and money

**Causes of complexity**

Complexity is caused by two things - ***dependencies and obscurity***

**Dependencies**

* A *dependency* exist if a given piece of code cannot be understood in isolation.
* Too many dependencies lead to cascading changes which are harder to test and causes more bugs. Huge change amplification also causes high cognitive load

**Obscurity** 

* means unknowns. it happens when the important information is not obvious. for example, a variable with a very generic name that doesn't carry much useful information. example, time, date, etc.
* Hidden dependencies are also obscurities. Obscurities causes unknown unknowns



