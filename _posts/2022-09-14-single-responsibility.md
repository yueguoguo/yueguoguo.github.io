---
layout:     post
title:      Single responsibility in machine learning
date:       2022-07-07 23:14:29
summary:    Single responsibility principle keeps codes regular and clean
categories: data science, software engineering, machine learning, design patter, principles
---

# Introduction

**A class should have only one reason to change.**

# Case study

## Different problems have different objects

A "problem" may be defined with different scopes, but in general, different
problems need to be implemented in different objects however they are big or
small. For example, in a recommender system, a commonly seen architecture
pattern is "recall-rerank" - the former does large-scale retrieval of relevant
items and the latter reranks the relevant items with detailed contextual
information for recommending to users. A possible design of such system is a
`Recommender` class, where the "recall" stage and the "rerank" stage are added
as methods for performing respective tasks. The high-level code example is shown
as below. 

```python
from abc import ABC, abstractmethod


class Recommender(ABC):
    @abstractmethod
    def recall(self):
        pass
    
    @abstractmethod
    def rerank(self):
        pass
```

Apparently, if there are details to add into the `Recommender` class, it will
make it look "bloated". For example, the recall stage requires the input of
`users`, `items`, and the user-item interactions, i.e.,
`user_item_interactions`, to get the similar items that a user has interacted
from the `items` pool. With the input data, the actual "recall" operation to
generate the relevant items may be powered by a `model` trained by the
interation data with an algorithm, which generates the quantitative measure
which decides the output of `recall`. That is, if the measure is higher than a
threshold, the item is considered to be relevant. The parameter of
`item_per_user` determines how many items for each user need to be recalled. 

The above detailed design leads to a possible implementation of the `recall`
method as below.

```python
def recall(
    self,
    users,
    items,
    algorithm,
    user_item_interactions,
    threshold,
    item_per_user,
    **algorithm_parameters
):
    """Recall method

    Args:
        users: a list of users to generate recall items for.
        items: a list of candidate items.
        algorithm: an algorithmic class for recalling items.
        user_item_interactions: user item interaction data.
        threshold: threshold for generating relevant items.
        item_per_user: number of recalled items for each user.
        algorithm_parameters: parameters of the recall algorithm.
    """
    # Train the recall model.
    model = algorithm(**algorithm_parameters).fit(user_item_interactions)

    # Generate the relevant items.
    relevant_items = model(users, items, threshold)

    # Filter out the recalled items.
    recalled_items = filter_items(relevant_items, item_per_user)

    return recalled_items


def filter_items(relevant_items, item_per_user):
    ...
```

It is obvious that the above implementation will break the single responsibility
principle for the class of `Recommender`. This is because

* the workflow in either `recall` or `rerank` is only applicable to itself,
   respectively,
* anything changed in either `recall` or `rerank` leads to a change in the
   entire object of `Recommender`. 

An advisable approach to mitigate the issue is to separate the stages and
implement them as single classes. That is

```python
class Recall():
    def __init__(self):
        self.model = None

    def build_model(self, algorithm, user_item_interactions, **algorithm_parameters):
        self.model = algorithm(**algorithm_parameters).fit(user_item_interactions)

    def generate_recall_items(
        self,
        users,
        items,
        threshold,
        item_per_user,
    ):
        if self.model is not None:
            # Generate the relevant items.
            relevant_items = self.model(users, items, threshold)

            # Filter out the recalled items.
            recalled_items = filter_items(relevant_items, item_per_user)
        else:
            raise ValueError("The model should be built in the first place")

        return recalled_items
```

Similarly, `Rerank` can be implemented as a different class with detailed
attributes and methods that a specific to rerank stage. 

## Focus on one if there are multiple types of sub-problems to resolve.

## Group only the relevant operations into one object.

# Conclusion

# References