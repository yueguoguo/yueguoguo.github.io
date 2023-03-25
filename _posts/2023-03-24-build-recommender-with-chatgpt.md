---
layout:     post
title:      "Build a collaborative filtering recommender with ChatGPT"
date:       2023-03-24 23:14:29
summary:    ChatGPT enhances productivity of data scientists and machine learning engineers.
categories: data science, software engineering, machine learning, chatgpt
---

<blockquote>
  <p>I've developed a lot of plugin systems, and the OpenAI ChatGPT plugin interface might be the damn craziest and most impressive approach I've ever seen in computing in my entire life..</p>
  <footer><cite title="Mitchell Hashimoto">"Mitchell Hashimoto"</cite></footer>
</blockquote>

# Background

ChatGPT does not create the excitement but also the panic to professionals who
are having the fear that the tool may become a replacement of humans. OpenAI
published [the
article](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://arxiv.org/pdf/2303.10130.pdf)
to debate on the impact of ChatGPT on the labor market. **Programming** and
**writing** are identified as those skills that *may have positive association
with exposures, implying the occupations that use these skills may be influenced
by ChatGPT. 

The work shared in this post conducts an experiment to learn how ChatGPT changes
my way of developing a data science or machine learning project. I chose a topic
that I am familiar with, **recommender system**, as it is a representative data
science problem that involves the typical steps of a data science project, for
illustration. [GPT-4](https://openai.com/product/gpt-4) is used primarily for
producing the codes as well as the document used in the project, while the
inputs are mostly my prompts to ChatGPT. 

## ChatGPT

ChatGPT is a chatbot developed by OpenAI, which uses the latest large language
model of GPT-4 for generating human-like dialogues when it is given "prompts". I
wrote a post that introduces the fundamentals about ChatGPT, and it can be found
[here](https://yueguoguo.github.io/chatgpt,/machine/learning,/technology,/finance/2023/01/26/chatgpt/)
- it may be a good reading material to understand ChatGPT. 

## Recommender system

A recommender system is a software that *can generates the user-preferred items
based on the historical user-item interactions or user-item attributes*.
Detailed introduction and code examples of recommender system can be found in
the [Microsoft Recommenders](https://github.com/microsoft/recommenders)
repository. 

Without loss of generity, the objective of the project illustrated in this post
is to build a collaborative filtering recommender which is one of the simplest
types of the recommenders. The algorithm used for the recommender is the
[SAR](https://github.com/microsoft/recommenders/blob/main/examples/02_model_collaborative_filtering/sar_deep_dive.ipynb)
algorithm. The data used for the recommender development is the [Movielens 100k
dataset](https://grouplens.org/datasets/movielens/100k/). The recommender
performance is evaluated by using the commonly used metrics such as [precision@k
and
recall@k](https://en.wikipedia.org/wiki/Evaluation_measures_(information_retrieval)).

Usually, building a simple collaborative filtering recommender system from
scratch may take hours. Considering the efforts on test development, system
integration, documentation, etc., there may be extra hours required. 

# Build a recommender

## Steps

The steps for developing the collaborative filtering recommender system are shown
below. It is worth noting that **in addition to the core function codes of the
recommender system, unit test development, system integration, document
development, etc., are also considered into the scope of the project. 

* Develop the function codes for the major components in the recommender system.
  * Obtain the dataset.
  * Do the split of the dataset into train and test sets.
  * Build the model with the SAR algorithm.
  * Evaluate the model with recall@k and precision@k metrics.
* Develop the unit tests.
* Integrate the individual functions into a pipeline script.
* Reorganize the repository.
* Develop the documentation.

In this project, the above tasks are accomplished by using ChatGPT. The detailed
prompts used for the above steps can be found in the prompts listed
[here](https://github.com/yueguoguo/recommender_with_chatgpt/blob/main/src/prompts.json).
The prompts are written in the [*act
as*](https://github.com/f/awesome-chatgpt-prompts) format, and executed
sequentially in ChatGPT to produce the corresponding output. The generated codes
and document are organized and placed into the raw files of the project, which
can then be run out-of-the-box.

## Time efforts

The time efforts of accomplishing the project were roughly recorded and listed
in the following table.  

| Task                          | Time effort |
| ----------------------------- | ----------- |
| Function development          | 2 minutes   |
| Unit test development         | 1 minute    |
| Pipeline integration          | 1 minutes   |
| Debug the codes               | 20 minutes  |
| Perform necessary refactoring | 2 minutes   |
| Organize project structure    | 3 minutes   |
| Documentation                 | 1 minutes   |

The total time efforts to finish the project was about **30 minutes**. Most of
the tasks did not take more than 3 minutes. Note that *debug the codes* is not
listed in the tasks aforementioned in the previoius sub-section but in fact it
took me the longest time as the codes generated from ChatGPT are not always
bug-free given the context in the prompts. 

# Discussions

There are some interesting findings during the development.

## Inaccuracy of the code generation

The utilities such as data download function, SAR algorithm implementation,
etc., in the latest [`recommenders`](https://pypi.org/project/recommenders/)
library with version 1.1.1 are not precisely generated in the codes by ChatGPT.
ChatGPT still gives me the old module implementation, e.g., it uses the library
module name of `reco_utils` (this was the one for the recommenders library when
I was still with Microsoft :)) instead of `recommenders`. It did the same even
if I explicitly stated in the prompts that the latest version should be used.

A similar issue regarding the `recommenders` library is that, by using the
prompt that asked ChatGPT to generate a `requirements.txt` file that lists the
most latest stable versions of the Python dependencies, it still gave me
`recommenders` with version of `0.7.0` instead of the latest `1.1.1`.

## Unit tests

I specify the unit tests code coverage to be at least 60%, and the test suites
gave me 85% which was quite impressive. This indicates that the language model
understands the code logic, and it developed the meaningful tests for the
functional codes. 

## Debugging

Debugging was the most frustrating process for the entire project. The codes
had bugs due to several reasons.

* The codes do not use the latest version of Python dependency. I.e.,
  `recommenders` 0.7.0 was used instead of 1.1.1. 
* When interacting with ChatGPT to fine-tune the codes, e.g., adding docstrings,
  reformating the codes by following PEP8, etc., if these asks are not
  immediately executed after the functional codes generation, the codes may be
  slightly changed such that they are not compatible with the ones that have
  been generated. For example, the function names, variable names, etc., can be
  changed. I have not found a way to help ChatGPT "memorise" what I have asked
  it to do - if the dialogue is "not-linear" it seems like ChatGPT loses its 
  track of the history, and thus makes mistakes. 
* When the generated codes are put together into the project directory, they are
  not well compatible due to the issues of import path, name of modules, etc.
  This requires extra efforts after the code generation to make sure that the
  entire end-to-end workflow works well. 

# Thoughts

In general, my gut feeling is that ChatGPT **greatly enhances my productivity on
those tasks that are repetitive**. Maybe I should improve my way of using it
(for example, the experience of development may be enhanced by using
[Copilot](https://github.blog/2023-03-22-github-copilot-x-the-ai-powered-developer-experience/))
but after this quick experiment **I have no fear of "being replaced by the
tool"**. Here are my reasons.

* Instead of several small prompts, I have tried arranging a big prompt but it
  did not produce anything useful. That is to say, before using ChatGPT, as a
  human expert in the domain, I still need to understand the *complexity* of the
  project regarding the implementation steps. Especially, the complexity may be
  extended when there are more asks to resolve finer-grained problems like
  improvement of model performance, optimization of pipeline performance, etc.
  Apparently, as a language model, ChatGPT does not have the capability to
  either think of or suggest such strategies to deal with the problem. What it
  does well is to follow the directional and concise prompt to produce the
  corresponding response. 
* **ChatGPT does not generate anything that is more than what is asked in the
  prompts**. Sometimes, the response generated from the model may contain some
  "bonus" information. For example, when I asked ChatGPT to develop a function
  that downloads Movielens dataset and returns a pandas dataframe, in addition
  to the function as per request, it also produces some notes to explain the
  implementation details (see blow).

  ```python
  import pandas as pd
  import urllib.request

  def download_movielens_data():
      url = 'http://files.grouplens.org/datasets/movielens/ml-100k/u.data'
      headers = ['user_id', 'item_id', 'rating', 'timestamp']
      data = pd.read_csv(urllib.request.urlopen(url), sep='\t', names=headers)
      return data
  ```

  > This function uses the urllib.request library to download the data from the
  > specified URL and reads it into a pandas dataframe using pd.read_csv(). We
  > specify that the data is tab-separated and provide the original headers as a
  > list to the names parameter. Finally, the function returns the resulting
  > dataframe.

  The notes are useful, but it is obvious that they do not generate any extra
  value to the function I asked it to develop. In comparison, when an
  experienced data scientist sees the function, he may raise suggestions such as
  *add a file path to allow saving data to local file*, *add exception handler*,
  *make the url string and data headers as global constants*, etc., which
  enhances readability and usability of the function, and these suggestions are 
  beyond the scope that is pre-defined by the prompts. 
* Due to the limitations above, for the time being, **ChatGPT does not perform
  well in handling a complicated code module where there are multiple functional
  units.** In the long-term run this will be definitely improved, and the prompt
  to build a recommender system can be as simple as "As a data scientist, can
  you build a collaborative filtering recommender system". But there will be
  still a "boundary" between **the human creativity** and **the AI-generated
  contents**, until the human brain is perfectly emulated by AI. 

In general, as for now, I am optimistic rather than pessimic about ChatGPT. It
enhances my productivity and let me spare my time to focus on the value-adding
work instead of the repetitive coding activities. Learning and leveraging the
tool is critical to the professionals like myself. Maybe today is still early to
see the disruption, the technology will soon make the significant differences on
human (programmer)'s experience on working.

# Code repository

The code repository can be found
[here](https://github.com/yueguoguo/recommender_with_chatgpt), where the prompts
and the Python scripts generated from ChatGPT are collected.
