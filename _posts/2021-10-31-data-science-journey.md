---
layout:     post
title:      Data Science Journey At Microsoft
date:       2021-10-31 22:30
summary:    A recap of the 5-year data scientist journey at Microsoft
categories: technology, data science, machine learning, career development
---

<blockquote>
  <p>Always remember that when it comes to markets, past performance is not a good predictor of future returns—looking in the rear-view mirror is a bad way to drive. Machine learning, on the other hand, is applicable to datasets where the past is a good predictor of the future.</p>
  <footer><cite title="François Chollet">François Chollet</cite></footer>
</blockquote>

![Redmond - 2017](https://github.com/yueguoguo/yueguoguo.github.io/raw/master/images/redmond_hq.JPG)
<font size="1">This is the first time I went to Microsoft Redmond campus. It was in the spring of 2017, which was my second year at Microsoft. I was astonished by the view and working environment of Redmond campus. What I will always recommend is <a href="https://dining.azurewebsites.net/34/">In.gredients</a> where you can have cheap but Michelin-quality food.</font>

## How the story began

**November 12th, 2021** marked my last day with Microsoft. I joined Microsoft as
a junior data scientist in 2016. Microsoft is my second company after I
graduated with the Ph.D. degree from Nanyang Technological University,
Singapore. My first company was Broadcom where I worked as a Product Engineer
for [wafer failure pattern
detection](https://ieeexplore.ieee.org/abstract/document/6932449). My title at
Broadcom was not "Data Scientist" though my job scope was completely about data
analytics and machine learning. That was when I started to learn about
industrial application of machine learning. Unlike many data scientists, I am
from an computer engineering background. In the last year of my Ph.D. and the
first several years of my industry career, I tried hard to develop the
statistical and analytical skills by reviewing my university courses, reading
books about data science and machine learning, attending conferences or meetups
to learn from experts, etc. 

When I just joined Microsoft as a Data Scientist, I think modelling is the
absolute core component of my job. After the first two years of various
engagements in the customer projects, I gradually realized that most data
scientists, including myself, in the industry do the "cool" work that prototyped
a nicely fitted model with unrealistically high-quality data without even
considering transforming the prototype into a production system. I suspect the
reasons behind this phenomenon are two fold: **users who "buy" the model do not
want to invest too much before they can see some appealing results; the
engineering platforms for applying data science into production is not powerful
nor standardized**. The observation forced me to rethink about the role of a
data scientist - I recognized the importance of combining software and computer
engineering with the machine learning to produce cool and, more importantly,
useable solutions, for users. 

At Microsoft, I was lucky to work with a team of talented people. I found a
great amount of interest similarities with my colleagues and that lead to
efficient ideation and execution. With their help, I participated in and
contributed to many impactful projects that created commercial value for
Microsoft customers. Below it is a selected list of such projects which
are publicly shareable (**we started open-source software development even
before Microsoft acquired GitHub!**).

* [Azure/AzureDSVM](https://github.com/Azure/AzureDSVM). This was the very first
  "product" I developed at Microsoft. It was under the guidance of my
  then-manager, Graham Williams who is one of the most renowed R experts in the
  world. AzureDSVM is an R package for operating [Azure Data Science Virtual
  Machines](https://azure.microsoft.com/en-us/services/virtual-machines/data-science-virtual-machines/)
  that can support large-scale parallel computing on cloud. This package greatly
  supports the R-language data scientists to run scalable analytical job on a
  remote cluster of Azure data science virtual machines with limited effort on
  upgront environment setup. I was thrilled to receive a lot of positive
  feedback from our technical sales colleagues and their customers. The work
  also helped me generate some "noise" in the R and data science community - I
  published several blog posts ([AzureDSVM: a new R package for elastic use of
  the Azure Data Science Virtual
  Machine](https://blog.revolutionanalytics.com/2017/05/azuredsvm-a-new-r-package-for-elastic-use-of-the-azure-data-science-virtual-machine.html)
  and [Parallelizing Data Analytics on Azure with the R Interface
  Tool](https://blog.revolutionanalytics.com/2016/12/azure-r-interface-tool.html))
  and presented several times at different conferences like Strata+Data,
  Microsoft MLADS, etc. 
* [Azure/AzureSMR](https://github.com/microsoft/AzureSMR). Around the same time
  of AzureDSVM, I joined the collaborative effort with other two colleagues,
  Alan Weaver and Hong Ooi from London and Melbourne, respectively, to develop
  AzureSMR, which is an R package that supports CRUD operations on more Azure
  resources than just the virtual machines. The package got a lot of attention
  of Microsoft customers whose technology stack is on R and Azure.
* [Microsoft/acceleratoRs](https://github.com/microsoft/acceleratoRs). After a
  number of successful customer engagements, I started to open source the
  collection of R-based data science and machine learning solutions for some
  commonly seen industrial problems. It was one of the first efforts from the
  Microsoft Singapore data science team that provides reusable and deployable
  end-to-end solution on cloud. It was the tipping point when my work is
  focused more on operationalization of a data science and machine learning
  system than just developing proof-of-concept.  
* [Microsoft/Recommenders](https://github.com/microsoft/recommenders). Microsoft
  Recommenders is not just a huge success for me and the team that I worked
  together with, it is also a big one for Microsoft that establishes the
  technological strength and reputation for its recommender system technology.
  The project started from almost nothing in 2018, and today it is **the most
  popular recommended system project on GitHub** (starred about **12k** times).
  Developing and leading the Microsoft Recommenders project was like start-up
  experience to which I was fully devoted with true passion for realizing crazy
  dreams. The impact of the project is definitely massive - with Microsoft
  Recommenders, the team has
  * **finished more than 10 commercial projects with Microsoft enterprise customers**, 
  * **published 3 top-tiered academic papers, i.e., [WWW
    20](https://dl.acm.org/doi/abs/10.1145/3366424.3382692), [KDD
    19](https://github.com/microsoft/recommenders#reference-papers), and [RecSys
    19](https://dl.acm.org/doi/10.1145/3298689.3346967)**,
  * **gave more than 10 tutorials at top-tiered industrial and academic conferences**,
  * **and collaborated with [75 contributors on
    GitHub](https://github.com/microsoft/recommenders/blob/main/AUTHORS.md)**. 

  Thanks to the continuous leadership of Tao Wu, Miguel Fierro, Andreas
  Argyriou, Scott Graham, and Jun Ki Kim, the Microsoft Recommenders project is
  still actively developed and well maintained. Collaborators from the Microsoft
  Research team led by Xing Xie, Jianxun Lian, and Fangzhao Wu, keep the
  freshness of the project by contributing the novel inventions of recommender
  system algorithms to it. The project keeps attractting contributions from
  community as well, and in turn, it provides research and development value to
  individuals and organizations from all across the world. 

There was much more interesting work done at Microsoft than what I have shared
above but due to the confidentiality I have to keep it disclosed. It was in
these projects where I grew my technical skills tremendously. Also from the
projects I learnt how to be a productive, empathetic, and humble individual as
well as a team lead. My perspective about data science and machine learning
became more practical than that in the years of Ph.D. **Doing "cool" stuff
should not be merely for being cool - instead, innovation in whichever form
should aim at providing value**. 

With the 5-year pragmatic experience as a data scientist at Microsoft, I have
built the confidence to create production-ready data science and machine
learning system for almost any given scenarios. However, what I am still lack of
is the **industry-specific domain knowledge** that can lower the barrier of
applying machine learning for real-world business problems. Microsoft is a great
company for learning and creating new technologies, but it might not be the
perfect place for delving into a domain (e.g., retailers work in the retail
domain and bankers work in the finance domain). Realizing the gap between the
pure technology and the real-world application initiated my thought about
seeking for a new endeavour outside.

!["Mini Le" - 2018](https://github.com/yueguoguo/yueguoguo.github.io/raw/master/images/minime.PNG)
<font size="1">"Mini Le" printed by using a 3D printer at the Garage in Microsoft New England office. It was in October of 2018. In the same week, the initial prototype of Microsoft Recommenders with a code name of "AirShip" was being developed by a team of data scientists and software engineers from Cambridge, London, and Singapore.</font>

## What's next

As I planned to leave Microsoft I started to think about my next stage of
career. I am very positive about the future of data science and machine
learning. Apparently, the potential of the technology has not yet been fully
exploited. This might be due to the lack of complete understanding of cerntain
problems as well as the inmaturity of the underlying technology that supports
the upper-level algorithmic implementations. **Maybe data scientist are no
longer the "sexiest" job (well this depends on how it is defined :)) - instead
of merely conceptualization and prototype development, data science and machine
learning requires more hands-on dirty work to help tackle the real problems that
companies care about**. 

The anticipation of an even larger scale of applications of data science,
machine learning, and AI in the industrial problems directs me to consider
exploring the following areas. These areas are also where I personally think the
data science and machine learning will experience further development
in the next a few years or even decades. 

### Industry-specific applications

I am a strong believer in applicable data science, machine learning, and AI in
transforming the contemporary industries. Compared to the technology companies
like Microsoft, Google, Facebook (now Meta), etc., who have already practiced
data science and machine learning in the core business (advertisement, search
engine, cloud computing, etc.) for ages, traditional corporations in the
industry sectors other than software or internet has just got started and still
suffer from building an productive system that can help boost the revenue or
reduce the operational cost. It's commonly seen in enterprises tha constructing
a data science and machine learning system incurs high-cost of both
infrastructure and human resources without signifant return-of-investment due to
the lack of the expertise and experience.

[Gartner predicts that 85% of the machine learning projects will
fail](https://www.gartner.com/en/newsroom/press-releases/2018-02-13-gartner-says-nearly-half-of-cios-are-planning-to-deploy-artificial-intelligence).
I have experienced failure projects at Microsoft for quite a few times. Usually
the failures are due to **unclear definition of machine learning and data
science problems, incompleteness of data governance system, lack of proper use
of MLOps, limited resonance between technology system and business requirement,
bad design of human-machine interaction**. For industrial applications, it is
pivotal to make a strategic plan and form up a team with diversified specialties
(i.e., data scientists, machine learning engineers, cloud system architects,
etc.) in the first place before going directly to development. As an experienced
data scientist, I am looking forward to providng in-depth knowledge and
expertise about building an effective data science and machine learning system
from both a strategic and engineering perspective in the next role. Especially,
it would be ideal that the domain knowledge in a particular sector is
combinationally applied into the technological system that I build. While the
technological progression is often abrupt and distructive, that of an industry
domain may be slow. The knowledge that is useful to an industry domain is
accumulative and it cannot be easily overthrown. 

### Productionizable system at scale

Unlike years ago when a prototype of support vector machine classifier could
generate buzz, nowadays, productionization of an entire end-to-end pipeline is
required as a standard outcome of machine learning projects. I have not
sufferred much from transferring my mind-set from algorithm-oriented approach to
production-oriented one thanks to the training in computer engineering. At work,
I always found it necessary to help customers to build a working system that has
well-defined run-time topology and convenient APIs. 

In fact, building a scalable machine learning system for production is not that
easy. It is truly a combination of arts from different disciplines. In the first
a few years when I worked with customers on the "big data" project, scalability
is the key ask because not many systems can survive with the rapid growth of
data volume and velocity. That was when I started to learn [Apache
Spark](https://spark.apache.org) and applied it to many of my projects. Today,
Spark has already become a standard for building scalable machine learning
system. However, there are many new technologies sprouting out for fulfilling
the newly coming requirements of a production-grade machine learning system.
Based on my observation and understanding, I summarize a few technical
specifications of a machine learning system that should be taken into
consideration for productionization.

* **Scalability of compution and data storage**. For many industrial
  applications, the data size is significantly large. This requires the backbone
  of the machine learning system to be substantially powerful. Usually,
  distributed computing framework/platform (e.g., Apache Spark for bulk data,
  [Apache Kafka](https://kafka.apache.org/) for streaming data,
  [Horovod](https://horovod.ai) for deep learning, etc.) and database (e.g.,
  geographically replica of data) are useful to build up such powerful back end
  systems. In addition to the offline computing and data persisting, online
  computing needs to be scalable. Technologies like
  [Kubernetes](https://kubernetes.io),
  [Swarm](https://docs.docker.com/engine/swarm/), etc., server to such demand.
  Nowadays, with the help of the cloud platform, many of the distributed systems
  can be deployed without efforts. Many tutorials can be found on internet
  (e.g., [scalable machine learning on
  Azure](https://docs.microsoft.com/en-us/azure/architecture/data-guide/big-data/machine-learning-at-scale),
  [building scalable machine learning on
  AWS](https://aws.amazon.com/blogs/machine-learning/building-a-scalable-machine-learning-pipeline-for-ultra-high-resolution-medical-images-using-amazon-sagemaker/),
  etc.) for learning.
* **Real-time data processing, feature engineering, and model serving**. Most of
  the existing machine learning systems are still operated in an offline mode. I
  have seen a pressing demand of real-time machine learning system from the
  customers that I have worked with. The requests are especially from the
  domains like retail, entertainment, etc., where processing data, training
  model, and generating prediction results should happen within milli seconds to
  allow large scale service online ([in the Instagram Explorer recommender
  system, 90 million model predictions are performed within one
  second](https://ai.facebook.com/blog/powered-by-ai-instagrams-explore-recommender-system/)).
  Real-time machine learning system is more sophisticated than the offline one.
  The state-of-the-arts approach relies on not just a low-latency front-end
  which is developed with a compiled language for model serving, but also a
  real-time data processing and feature engineering pipeline that guarantees
  fast operation of the entire pipeline. A good insight about real-time machine
  learning can be found
  [here](https://huyenchip.com/2020/12/27/real-time-machine-learning.html). It
  is worth mentioning that there are quite a number of novel technologies
  drawing attention in the recent years. Examples of such technologies include
  but are not limited to [feature
  store](https://www.tecton.ai/blog/what-is-a-feature-store/), [data
  streaming](https://www.tibco.com/reference-center/what-is-data-streaming),
  [model
  compression](https://medium.com/gsi-technology/an-overview-of-model-compression-techniques-for-deep-learning-in-space-3fd8d4ce84e5),
  etc., all of which contribute to improving the real-time capability of a
  machine learning system. 
* **MLOps for reliable and efficient machine learing system**. [Many of my
  successful projects prove to me that MLOps is an important practice that
  builds reliable and efficient machine learning
  system](https://www.forbes.com/sites/forbestechcouncil/2019/04/03/why-machine-learning-models-crash-and-burn-in-production/?sh=2f30d8c82f43).
  It is estimated that the market value of MLOps can be sized up to **125
  billion** dollars according to [a recent
  study](https://neu.ro/2021-mlops-platforms-vendor-analysis-report/).
  Developing a completed and proper MLOps system can be as complex as doing the
  same thing for the machine learning system itself. The core tasks for MLOps
  are usually **data sanity check, data governance, feature store and
  management, CI (continuous integration) / CT (continuous train) / CD
  (continuous delivery), health monitoring, unit/integration/smoke testing,
  etc**. For example, in Microsoft Recommenders, the team developed a robust
  build pipeline that assures the quality of the committed changes in the source
  library codes and the example notebook codes. The tests run against the
  example data to make sure the results generated are within expectation before
  the codes are checked in. In the production system, there may be more tasks
  for practicing MLOps in a machine learning pipeline. It was fortunate that I
  have been trained in nearly all of my data science and machine learning
  projects for applying the MLOps methodology. MLOps will continue to be an
  important topic for my endeavor with any new roles in the machine learning
  area.

![Tattooed Laptop - 2019](https://github.com/yueguoguo/yueguoguo.github.io/raw/master/images/laptop.JPG)
<font size="1">My second last laptop with tons of "tattoos" sticked on the surface. The photo was taken in the brand new Microsoft office in Singapore which was opened in 2019. I used the laptop to access virtual machines on Azure for development.</font>

### Beyond the convention

There is a group of technologies that I am keen on seeing their success
application. I have either self studied or practiced these technologies during
my work at Microsoft but have limited chances to put them into a production
system. These technologies may not strictly fall into any sub-category of data
science and machine learing but I do see their potential value in the near
future.

* **Reinforcement learning**. [In many application scenarios like online
  personalization, algorithmic trading, gaming, etc., reinforcement learning
  exhibits the power to overcome the challenges that traditional machine
  learning techniques cannot tackle
  with](https://towardsdatascience.com/applications-of-reinforcement-learning-in-real-world-1a94955bcd12).
  I used to lead a project that uses the [OpenAI Gym
  framework](https://gym.openai.com) for reinforcement learing based recommender
  system. Compared to the conventional approach, the reinforcement
  learning-based method has less restricted assumption on the static data
  samples for model training - it directly gets input from front-end queries and
  dynamically produces outputs based on a "rewarding" mechanism. The modeling
  philosophy of a reinforcment learning framework is more close to the reality
  where responses are **in time**, so it is useful for many different types of
  problems where fast and accurate responses are required. There are already
  great attempts to apply reinforcement learning technologies into real-world
  systems (e.g., [Azure
  Personalizer](https://azure.microsoft.com/en-us/services/cognitive-services/personalizer/),
  [Bonsai](https://www.microsoft.com/en-us/ai/autonomous-systems-project-bonsai?activetab=pivot%3aprimaryr7),
  [automous data center
  cooling](https://deepmind.com/blog/article/safety-first-ai-autonomous-data-centre-cooling-and-industrial-control),
  etc.). It will surely enjoy an even larger scale of applications in the near
  future when the computating efficiency is further improved. 
* **Generative artificial intelligence**. Synthetic data techniques become more
  and more useful, given that raw data for building machine learning systems are
  always difficult to acquire or cleanse (this is usually due to regulation,
  compliance, accessity to data, etc.). Generative AI resolves the shortage
  problem of data, especially the labelled data, such that even if without
  collecting large volume of data a model can still be reliably built. [It is
  predicted that by 2030 most data used in AI will be artificially
  generated](https://blogs.nvidia.com/blog/2021/06/08/what-is-synthetic-data/).
  Often a data synthetic tool requires deep domain knowledge and rigorous
  mathematical techniques. In addition, it needs iterations of validation
  against the ground truth data to make sure that the data quality from the
  synthetic tools is within expectation.
* **Ethical machine learning**. Ethics remain a problem for applicable machine
  learning and AI models. Debiasing the prediction or classification results
  generated from a model sometimes can be a severe moral affair. As a
  consequence, it is important for not just the developers including data
  scientists, algorithm engineers, researchers, etc., but also the ordinary
  people to understand how a model is created by certain algorithmic derivation
  and how certain forms of data are used for such creation. [China has recently
  started a new regulation that controls the abuse of AI algorithms for end
  users](https://www.reuters.com/technology/china-issues-draft-guidelines-internet-recommendation-algorithms-2021-08-27/).
  The aim of such regulation is that users should be given the options to
  understand if they are surfaced with algorithms that push advertisements,
  content, etc. [Earlier, American companies like Facebook (now Meta)
  experienced the scandal that the user data were used for political
  advertising](https://en.wikipedia.org/wiki/Facebook–Cambridge_Analytica_data_scandal).
  There is no reason for blaming the technologies for the negative societal
  impact. As developers the technolgies should be properly used and well
  regulated. 

## Close

I find it hard to put all my learning during the last 5 years and my
expectations for the future into a blog post. Working in such a great company is
definitely one of the most memorable periods of my life time (let me speak on
behalf of the old me :)). I would like to close this article with a great
analogy from Mu Li who is a researcher from Amazon - [he interpretes life as a
stochastic gradient descent process where the aim is to find the optimal point
gradually](https://zhuanlan.zhihu.com/p/414009313). Philosophically, this is a
great summary of how I gradually approach the career pursuit step by step. The
original post is in Chinese and below it is the translation on my own: 

* Life needs a goal. 
* The goal should be big enough.  
* Walking towards the goal should be non-stop.
* The process might be suffering.
* Sometimes it is fine to relax.
* It is also fine to look around.
* The process can be either slow or fast, so there is no need to worry.
* The initial point is important.
* The goal is reachable even if it is far away.
* Every process is unique.

The last but not the least, my sincere thanks go to all the amazing people that
I have met or worked with during the 5 years at Microsoft. I truly appreciate
all the learning from you.
