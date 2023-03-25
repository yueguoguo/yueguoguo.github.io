---
layout:     post
title:      "Build a collaborative filtering recommender in 20 minutes with ChatGPT"
date:       2023-03-26 23:14:29
summary:    Single responsibility principle keeps codes regular and clean
categories: data science, software engineering, machine learning, design pattern, principles
---

<blockquote>
  <p>Gather together those things that change for the same reason, and separate those things that change for different reasons.</p>
  <footer><cite title="Uncle Bob (Robert Martin)">"Uncle Bob (Robert Martin)"</cite></footer>
</blockquote>

# Background

## ChatGPT

* ChatGPT is a tool that allows dialogue-like interactions. 
* ChatGPT can generate Python codes accrording to the directions in the prompts.
* ChatGPT can interactively generate code outputs when the user gives it
  addition prompts in a sequence.

## Recommender

* Build an end-to-end collaborative filtering based recommender system.
* The recommender system users the Microsoft SAR algorithm.
* The data is the Movielens 100k data set.
* The recommender model is evaluated by using precision@k and recall@k.

# Build a recommender

## Steps

* Obtain the dataset.
* Do the split of the dataset into train and test sets.
* Build the model with the SAR algorithm.
* Evaluate the model with recall@k and precision@k metrics.
* Integrate the individual functions into a pipeline script.
* Develop the unit tests.
* Reorganize the repository.
* Develop the documentation.

## Time spent

| Task                          | Time effort |
| ----------------------------- | ----------- |
| Function development          | 2 minutes   |
| Unit test development         | 1 minute    |
| Pipeline integration          | 1 minutes   |
| Debug the codes               | 10 minutes  |
| Perform necessary refactoring | 2 minutes   |
| Organize project structure    | 3 minutes   |
| Documentation                 | 1 minutes   |

# NOTEs

* recommender utils. It gives me 0.7.0 but it should be >= 1.0.0.
* recommender python importable module should be `recommenders` instead of
  `reco_utils`.
* test coverage is 85%.
* code structure and organization needs human involvement. 
* interaction with ChatGPT is sequential and it is not trivial to conduct the
  conversation in a non-linear way.
* the prompts should be kept and reused for iterative improved, but sometimes
  the subtle changes are not well processed by ChatGPT. 

# Code repository

The code repository can be found
[here](https://github.com/yueguoguo/recommender_with_chatgpt), where the prompts
and the Python scripts generated from ChatGPT are collected.

# Thoughts

* a technologist needs to understand the problem in the first place.
* chatgpt is not good at writing bug-free codes for a complex project. 
* collection and organization of prompts are important.