---
layout:     post
title:      Domain-driven development of data-centric applications
date:       2023-10-01 16:43:29
summary:    some summary
categories: software engineering, machine learning, design pattern
---

<blockquote>
  <p>Everything should be made as simple as possible, but not simpler.</p>
  <footer><cite title="Albert Einstein">Albert Einstein</cite></footer>
</blockquote>

# What is domain-driven development (DDD)

With the proliferation of AI technology, lots of tasks that used to be
significant challenges become easy to cope with. Nevertheless, despite the
astonishing capability of generalization by leveraging the contemporary deep
learning techniques, quite a portion of the problems in different industrial
domains still require domain knowledge. DDD has been around for ages. It was
coined by xxx in the book of. The book gave a clear definition of DDD and how
the principle can be used in the modern software design and implementation.

# Ubiquitous language

*Ubiquitous language* plays the core role in DDD. It's usually hard to synergize
a cross-domain ubiquitous language that servers to all purpose. 

## Business-to-tech domain translation

The biggest challenge usually lies in the translation from the business request
to the technical problem. And it can be quite repetitive and iterative. A good
translation usually requires practice with team in understanding the problem
precisely - example techniques of [event
storming](https://en.wikipedia.org/wiki/Event_storming), [requirement
engineering](https://en.wikipedia.org/wiki/Requirements_engineering), [business
process modelling](https://en.wikipedia.org/wiki/Business_process_modeling).

Given the complexity of the data-intensive or AI-centric applications, usually,
the requirements of the entire system have to be broken into several components.
For example, at the ETL layer, the queries may be suggested by the business to
extract data insights. 

**Business**: 

> "I want to have the average purchases of all products between 2022 and 2023."

**Data engineer**: 
```sql
  SELECT AVG(purchase_amount) AS average_purchases
  FROM product_table
  WHERE purchase_date BETWEEN '2022-01-01' AND '2023-12-31';
```

At the application layer, machine learning models may be advised by the business for
predictive analysis.

**Business**:

> "I want a service to predict how much sales the sub-branch of the store can make in the next 5 days."

**Data scientist**:

```python
from sklearn.linear_model import LinearRegression

# Train a linear regression model
model = LinearRegression()
model.fit(x_train, y_train)

# Make predictions on the testing data
predictions = model.predict(df_test[['day_of_week']])
```

The nature of *business-to-tech* translation is to conver the plain language
that describes a business problem into a technical prototype or implementation.
Usually a program manager, product manager, or product owner severs as the
middle-layer to translate such requirements. The [*intelligent
agent*](https://en.wikipedia.org/wiki/Intelligent_agent) that is powered by the
large language model (LLM) technologies, may help enhance the efficiency and
effectiveness, as most of the mapping between human descriptions and technical
implemetnations can be "predicted" by the LLM. 

Most of the LLM models are generic - they have been trained on the massive
public data. It's an art to leverage LLM for producing useful results ([prompt
engineering](https://en.wikipedia.org/wiki/Prompt_engineering)). Nevertheless,
producing domain-specific results from a pre-trained LLM to translate business
requirements to technical implementation may need "customization" of the generic
models by techniques like
[fine-tuning](https://en.wikipedia.org/wiki/Fine-tuning_(deep_learning)),
[retrieval augmented
generation](https://blogs.nvidia.com/blog/what-is-retrieval-augmented-generation/),
[mixture of experts](https://en.wikipedia.org/wiki/Mixture_of_experts),
[knowledge base](https://en.wikipedia.org/wiki/Knowledge_base).

## Tech-to-tech translation

# Data model, data lineage, and data mesh

It's not just about data representation, it's also a matter of the flow in
sharing the data model related information among the domain experts and the
developers.

# Microservice

Abstract layer of the modular module can be implemented as microservices.
