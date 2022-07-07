---
layout:     post
title:      Implant software engineering mindset into data science
date:       2017-05-23 16:43:29
summary:    The contemporary data science work requires more rigorous engineering mindset for delivering value with efficiency.
categories: data science, software engineering, machine learning, mindset
---

<blockquote>
  <p>Everything should be made as simple as possible, but not simpler.</p>
  <footer><cite title="Albert Einstein">Albert Einstein</cite></footer>
</blockquote>

# Background

It was recognized by industrial practitioners that engineering plays a growingly
significant role in data science. Taking a look at the tasks a data scientist
takes nowadays, it is seen that the primary goal is not merely demonstrating the
value of a statistical or machine learning algorithms in solving a well
conditioned technical problem, but also a full-fledged system that works with
much more sophisticated context from both technical and business perspectives.

Software engineering is hence important to transform the data science output to
applicable software products. For companies, perhaps there are still dedicated
roles of software engineers (in many circumstances it is called "machine
learning engineer") who handle the productionization of a data science or
machine learning model, the skill sets that data scientists should have grow
broader than ever before. More importantly, the mindset shift that converges the
development practices of data science models to favour productionization becomes
vital.

It is worth mentioning that the post try not to give a conclusion that
"A" is superior to "B" or something similar. 

# Implanting software engineering into data science

Based on my personal experience, as well as the good learning materials shared
by the experts, there are multiple keys to "implanting" the software engineering
mindset into data science paradigm.

## Principle and practice

There are quite a few principles and good practices that are widely applied in
the software development, whose value might not have been well recognized by 
data scientists.

### Coding conventions

I personaly felt reluctant to follow a verbose coding guidelines - it seems not
worthwhile of particular attention to using snake or camel style in the codes.
The benefits of developing standardized codes start to glow when a group of
software engineers, data scientists, researchers, etc., work on the same
project. Unfollowing the same conventions may lead the same code base to look
like being developed by using different languages even though it is not.

As the most popular programming languages used in data science, Python has an
explicit guidelines to program "pythonic" codes, see
[PEP8](https://peps.python.org/pep-0008/). Companies sometimes have their own
style but in general they share mostly the same. For example. Google has its
guidelines for Python (see
[here](https://google.github.io/styleguide/pyguide.html)). Linting or formatting
tools like `black`, `autopep8`, etc., help improve Python code styles.

Programming "pythonic" codes helps enhance readability, and thus it greatly
improves the process of smoothly transform the "experimental" codes that data
scientists develop to production-ready codes that are to deploy onto the server.

### Design pattern

The contemporary software is developed by using object-oriented programming
(OOP) language, and the OOP characteristics gives the possibility to develop
reusable and modular patterns (apparently anti-patterns co-exist) that nicely
excels in resolving particular types of problems. There are formalized design
patterns that are generically used in software engineering tasks. It is recently
discussed in the industry that in data science or machine learning tasks,
certain design patterns can be applied and they enhance reusability of certain
re-occurring solutions.

The Google Cloud team proposed the machine learning design patterns in the
[book](https://github.com/GoogleCloudPlatform/ml-design-patterns). With the codes,
it covers the basic best practices to handle the common tasks in building machine
learning system such as data representation, problem representation, etc.

In the repository
[ml-design-patterns](https://github.com/msaroufim/ml-design-patterns), the
authors proposed design patterns that are commonly seen in machine learning
development. For example, the pattern that is used in the well-known
`scikit-learn` package, called "learning pattern" by the authors, represent a
typical way to wrap a machine learning algorithm that may involve supervised
training and then inferencing operations. 

```python
class Model:
    def __init__(self):
        self.model = nn_model()
        self.loss_function = subtract/square_loss/l1 

    def fit(self, data):
        # 1. Compute forward function
        output = self.model(data) 

        # 2. Get loss
        loss = self.loss_function(data)

        # 3. Update model
        self.model.update(loss)
    
    def update(self, loss):
        # 1. Compute gradients with autograd
        self.model.weights = ...   

    def predict(self, data):
        prediction = self.model(data)
```

The `Model` object can also be extended by inheriting the attributes and methods
from the base class with modifications, to support various application
scenarios.

It is also discussed in the recent
[post](https://eugeneyan.com/writing/design-patterns/) by Eugene Yan that some
design patterns used in the popular packages like pytorch, gensim, huggingface,
etc., supports convenient data loading. The key takeaways from these examples
are that these reusable design patterns as code templates greatly help data
scientists and software developers to code for production; the patterns are also
extensible and flexible to support various domains (e.g., conventional machine
learning, natural language processing, image processing, etc.) with high quality
and well-defined structure. 

### Just-in-time compiling

Viewed from a computer architecture's perspective, most of the tools that data
scientists use, e.g., Python, R, etc., sits above the compiler layer, which do
not require compilation before being executed. Along with the progressive
upgrade of the modern web/mobile application in terms of scalability and data
volume, the requirement of the data science or machine learning engines that
backbone these applications need to meet the pressing engineering
specifications. 

Data science and machine learning models developed by purely Python or R codes
may not suffice. The core components that run the critical job, e.g., model
inferencing, need to be compiled into a form that is close to machine codes to
achieve the maximum computational efficiency. 

Knowing that this may not fall into the portfolio of most data scientists, it is
still worth gaining some knowledge about the low-level representation of codes
in order to fill the gap between experimentation and production. In fact, most
of the machine learning packages implement the key model parts in a comiling
language, e.g., `tensorflow`, `pytorch`, etc. In addition, there are handy tools
or framework help refactor a vanila Python codes into a compiled version to
achieve fast speed. 

[`tvm`](https://github.com/apache/tvm) is a compiling framework that accelerates
execution efficiency of deep learning model on any hardware target.
Conveniently, instead of rewriting or refactoring the models that data
scientists experiment with, the Python API of `tvm` can be leveraged to avail
low-level compiling to achieve production-read implementation. See the below
editted example from `tvm`'s document.

```python
from tvm.driver import tvmc

# Load a ONNX-formatted model object, which is saved after a model training
# by using a deep learning framework and converted to the ONNX format.
model = tvmc.load("my_model.onnx")

# Compile the model object to a low-level representation. Multiple targets can 
# be specified. Here, the "llvm" target is used to represent the compiled 
# version of the model object.
package = tvmc.compile(model, target="llvm")

# The compiled object can then be run over a target type of hardware, e.g. cpu.
result = tvmc.run(package, device="cpu")
```

Similar tools of such are
[DLIR](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://pacman.cs.tsinghua.edu.cn/npc2018/papers/DLIR.pdf),
[MLIR](https://mlir.llvm.org/).

Another commonly used package for compiling Python codes in general is `numba`.
`numba` translates Python code to low-level intermediate representation by LLVM,
such that the original Python code, after compilation, runs as fast as C or
Fortran code on the target hardware platform. It is convenient to data
scientists in development because refactoring conventional Python codes to
`numba`-compatible codes require merely an addition of the decorator. See the
below example from the `numba` official document.

```python
from numba import jit
import random

@njit
def monte_carlo_pi(nsamples):
    acc = 0
    for i in range(nsamples):
        x = random.random()
        y = random.random()
        if (x ** 2 + y ** 2) < 1.0:
            acc += 1
    return 4.0 * acc / nsamples
```

The first run of the above codes will trigger a compilation which then allows
the next run to use the compiled version directly.

### MLOps

Similar to DevOps, MLOps is more of a philosophy and practice to properly manage
the life cycle of the deployed machine learning models. Data scientists'
participating into the MLOps practices are significantly important though quite
a lot of times the important is neglected.

Ideally, the hollistic platform or framework of MLOps is established by the
machine learning architects or engineers, while the data scientists experiment
and develop the models by using the pre-defined interfaces, pipelines, and
conventions. For example, upon releasing a model, the data scientists are
supposed to provide

* Unit tests with pre-determined coverage and pass rate to guarantee the
  reliability and robustness of model related codes against various corner
  testing cases. Conducting [Test-Driven Developement
  (TDD)](https://en.wikipedia.org/wiki/Test-driven_development) might be
  necessary to some circumnstances when data scientists develop critical
  components for the machine learning system.
* [Smoke testing](https://en.wikipedia.org/wiki/Smoke_testing_(software)) with
  an end-to-end run of model training and inferencing.
* Properly developed model performance evaluation metrics and integration
  testing codes to calculate the metrics against sample data.

The evaluation process enables a Continuous Integration and Continuous Delivery
(CI/CD) practice on the MLOps platform to make sure that that the entire journey
of exploration, experimentation, development, and deployment are organically
connected to yield high-performance productionization with efficiency.

# References

