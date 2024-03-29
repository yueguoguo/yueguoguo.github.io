---
layout:     post
title:      "Single responsibility"
date:       2023-03-01 23:14:29
summary:    Single responsibility principle keeps codes regular and clean
categories: data science, software engineering, machine learning, design pattern, principles
---

<blockquote>
  <p>Gather together those things that change for the same reason, and separate those things that change for different reasons.</p>
  <footer><cite title="Uncle Bob (Robert Martin)">"Uncle Bob (Robert Martin)"</cite></footer>
</blockquote>

# Introduction

**Single responsibility** is a well-known principle used in developing computer
software. The principle originates from [Robert
Martin](https://en.wikipedia.org/wiki/Robert_C._Martin). It is a general
principle that applies to any software design. The core idea of single
responsibility is that *a module should be responsibility to one, and only one,
actor.* There are a few ways to interpret this idea. For example, Martin
explained the principle with "a class should have only one reason to change". 

There are many benefits of following the single responsibility principle in 
software development.

1. It enhances modularization.
2. It favors unit test.
3. It improves code readability.
4. It mitigates ambiguity and confusion.

Practicing the single responsibility principle is vital to developing data
science and machine learning software. The single responsibility principle can
be illustrated on three folds. 

## "Different problems have different objects" 

A "problem" may be defined with different scopes, but in general, different
problems need to be implemented in different objects however they are big or
small. For example, an object can be created to deal with database-related
operation, and another object can be created to handle model training and model
scoring. *"Database-related operations"* and *"machine learning model-related
operations"* are considered to be two different sets of problems so they require
different objects. 

For example, [`scikit-learn` applies single responsibility in implementing the
base `Estimator` or
`Transformer`](https://scikit-learn.org/stable/developers/develop.html). That
is, these base classes have the standardized structure such as the methods of
`fit`, `predict`, `score`, etc., which are the most relevant "roles" to an
`Estimator` or `Transformer`. The classes or functions for other atomic
operations are implemented as separate entities. 

Similar idea can be seen in the deep learning packages like `torch`. [The
`nn.Module` implements the neural network topology, but it does not incorporate
the training
component](https://pytorch.org/docs/stable/generated/torch.nn.Module.html). This
is because a separate module takes the "responsibility" for optimizing the loss
of a model defined in the `nn.Module`.

## "Focus on one if there are multiple types of sub-problems to resolve"

A lot of times the object can be made obscure when there are functionalities
being added to it that may exceed its pre-defined scope. If there is an object
that is supposed to handle multiple different sub-problems, it may be reasonable
to split the scope of the object and apply the splits to only the sub-problems,
respectively.

A very representative example to illustrate this principle is the *write*
functions used for saving the `pandas` dataframe. Though the write operation can
be considered as one problem, it may have sub-problems that write the dataframe
to different types of output formats, i.e., `csv`, `parquet`, etc. And
therefore, there are different dedicated methods of the `pandas.DataFrame`
object to handle these `sub-problems`. That is, for saving to `csv`, `to_csv` is
used, and for saving to `parquet`, `to_parquet` is used.

## "Add only the necessary functionalities to the object"

It happens frequently that unnecessary functionalities are added to an object,
which makes the object less maintainable. Considering a class where the
unnecessary emthods are added, the cost will be not merely the implementation of
the additional methods but also the unit tests and integration tests that may
apply.

Sometimes, it is indeed hard to tell whether the functionalities are required or
not. The usual way of dealing with such situation is that the responsibility can
be "propagated" to or "passed" from by using other auxiliary objects. This idea
can be seen in many commonly used design pattern such as *"strategy"* - it
implements the *"context"* that controls the actual behavior of the object. The
unnessary components of a "strategy" can then be put into the "context" so that
whenever there is a change of the context, the actual strategy is also affected.
And as a result, the context and the strategies can be implemented and
maintained separately.

# Case study: recommender system

The following demonstrates the use of the "single-responsibility" principle in
designing a recommender system.

## Recall and rerank

In a recommender system, a commonly seen architecture pattern is
["recall-rerank"](https://developers.google.com/machine-learning/recommendation/dnn/re-ranking)
- the former does large-scale retrieval of relevant items and the latter reranks
the relevant items with detailed contextual information for recommending to
users. A possible design of such system is a `Recommender` class, where the
"recall" stage and the "rerank" stage are added as methods for performing
respective tasks. The high-level code example is shown as below. 

```python
class Recommender():
    def recall(self):
        print("Do recall")
    
    def rerank(self):
        print("Do rerank)
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

The above detailed design leads to a possible implementation of the `recall` in
an actual `Recommender` class that inherits the abstract one. The codes can be
found below

```python
def recall(
    self,
    users,
    items,
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
    model = Algorithm(**algorithm_parameters).fit(user_item_interactions)

    # Generate the relevant items.
    recalled_items = model.predict(users, items, threshold, item_per_user)

    return recalled_items


class Algorithm():
    """Implementation of the algorithm that builds the recall model
    """
    def fit(self, data):
        ...

    def predict(self, data, *args, **kwargs):
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
    model = None

    def build_model(
        self,
        user_item_interactions,
        **algorithm_parameters
    ):
        """Build the model to perform recall operation
        """
        self.model = Algorithm(**algorithm_parameters).fit(user_item_interactions)

    def generate_items(
        self,
        users,
        items,
        threshold,
        item_per_user,
    ):
        """Use the pre-built model to generate the recalled items.
        """
        if self.model is not None:
            # Generate the relevant items.
            recalled_items = self.model.predict(users, items, threshold, item_per_user)
        else:
            raise ValueError("The model should be built in the first place")

        return recalled_items
```

Similarly, `Rerank` can be implemented as a different class with detailed
attributes and methods that a specific to rerank stage. The `Recommender` class
encapsulates the high-level steps of `recall` and `rerank` by adding the
`Recall` and `Rerank` object to propagate the "responsibility" of each to an
upper level, and then the `Recommender` object harness the run of recall stage
or rerank stage. Any logic changes in either `recall` or `rerank` is not
reflected in the code of `Recommender`.

```python
from typing import Union


class Recommender():
    def __init__(self, recall: Recall, rerank: Rerank):
        self.recall = recall
        self.rerank = stage
```

And the recall and rerank operations will be run as

```python
# Initialize a recommender
recommender = Recommender(Recall(), Rerank())

# Build model
recommender.recall.build_model(user_item_interactions, **algorithm_parameters)

# Do recall
recall_items = recommender.recall.generate_items(users, items, threshold, item_per_user)
```

## Data preservation

It is common that the items generated from one of the stages are cached into a
database for later reference. A tendency of implementing such is to add a method
into the `Recall` or `Rerank` class for preserving data. 

```python
def write_items(self, items, connection_string: str):
    """write the items to a database.

    Args:
        items: the items to write to the database.
        connection_string: the connection string for the database to write results.
    """
    # build_db_connection is a function that returns the generator to perform
    # write operation under the context managed by the connection.
    with build_db_connection(connection_string) as conn:
        write_data(items, conn)
```

After adding `write_items` method, the `Recall` class has multiple types of
sub-problems, i.e., 1) builds a recall model and generates the recall items and
2) save the items to the database. This breaks the single responsibility of the
class in a way that the two types of problems have minimal overlap in terms of
functionalities and implementation, but changing one of the two will lead to the
change of the entire class. 

A better choice is to have a separate class of `RecommenderDataManager` where 
there are methods to support data read and write. The `RecommenderDataManager`
may be used as a generic object at the `Recommender` class level, to handle the
data read/write related operations.

```python
class RecommenderDatabaseManager:
    def __init__(self, connection_string):
        self.connection_string = connection_string
    
    def write_items(self, items):
        """Write items to the database

        Args:
            items: the items to write.

        Notes:
            The items are assumed to be written to a default table
        """
        with build_db_connection(self.connection_string) as conn:
            write_data(items, conn)

    def read_items(self):
        """Read items from the database

        Notes:
            The items are read from the default table
        """
        with build_db_connection(self.connection_string):
            items = read_data(conn)
```

In actual use, it becomes

```python
data_manager = RecommenderDatabaseManager(connection_striing)

# Write recall items
data_manager.write_items(recall_items)

# Read recall items
data_manager.read_items()
```

To support the rerank data read/write operation, a parameter of table may be
added in the methods of `RecommenderDatabaseManager` to filter the target tables
in the database.

## Making the hollistic pipeline

Usually, before either the recall or the rerank stage, possibly, there may be
data pre-processing steps, e.g., feature engineering; after generating the
results, sometimes the items need to be post-procssed, e.g., business rules may
apply to the items before they are recommended. An anti-pattern approach is to
add the `pre_process` and `post_process` methods to the `Recall` class, for
preprocessing and post processing, respectively. 

However, these two methods do not add help to the existing methods `build_model`
and `generate_items` directly. This is because the methods in the `Recall` class
are already self-consistent in terms of functionality provided the input data
and parameters. In this case, the `pre-process` and `post-process` methods are
not necessary to be added to the `Recall` class. A better choice is that the
two methods can be implemented as standalone classes or functions to serve for
the purposes of preprocessing and post-processing, respectively. 

The following shows an example of the function implementation and its workflow
in combination with the `Recall` class.

```python
def pre_process(user_item_interactions):
    """Preprocess function for user-item interactions
    """
    # Do some preprocessing
    return user_item_interactions


# Preprocess data.
user_item_interactions = pre_process(user_item_interactions)

# Build recall model
recall = Recall()
recall.build_model(user_item_interactions, **parameters)
```

By doing this, the functionalities of preprocessing and the actual recall are
separated for single responsibilities.

# References

1. Martin, Robert C. (2005). "The Principles of OOD". butunclebob.com. 
1. Andreas Argyriou, Miguel Gonzalez-Fierro, and Le Zhang, "Microsoft Recommenders:
Best Practices for Production-Ready Recommender Systems".
1. Pandas Development Team, "Pandas", url: https://doi.org/10.5281/zenodo.3509134, Zenodo, 2020
1. Refactoring guru, "Strategy in Python".