---
layout:     post
title:      Cloud for elastic data science 
date:       2017-05-23 21:43:29
summary:    Explosions of random thoughts.
categories: data science, cloud
---

The way of doing data science is dramatically impacted by cloud
computing technology. I may not be the right person to predicate but
when I joined Microsoft and started to work with Graham Williams, a
veteran of data science, I got to know how significant the revolution
cloud has brought to data science community.

Years ago, to experiment with a random forest algorithm, researchers
had to configure computing clusters by hand. Now it has become so easy
that in 5 minutes a data scientist can deploy a Linux based virtual
machine on cloud, where mainstream data science tools and software are pre-installed.
That is handy! It not merely saves the engineering efforts in setting up
a working environment that data scientists are comfortable with, but
also ecnonomizes the cost of administrating computing resources. 

[Microsoft Azure Data Science Virtual Machine](http://aka.ms/dsvm) is
such a virtual working space available on Azure cloud. It avails an
elastic use of cloud computing resources to do nearly anything about
data science. It is scalable - there are various options of machine
sizes that one can scale the deployed machine up or down with. The
cutting-edge toolkits and frameworks for big data and deep learning,
such as TensorFlow, Spark, etc., are available off-the-shelf. By
deploying machine incorporated with application-specific processor such
as GPU, data scientists can conveniently toy up with DSVMs for either
experimenting or prototyping their ideas.

Azure DSVM is an excellent fit for doing elastic data science on cloud.
It is charged in a "Pay-As-You-Go" scheme, meaning that one only gets
charged when using the machine. Imagine the data science project which
normally consists of several sub-sections, each of which there is a
specific data science task to finish, DSVM greatly resolves the issue
in allocating computing resources corresponding to requirement of each
sub projects. DSVM is agile so that a machine does not have to be alive
all the time. It is fired up on demand, and generates cost only being used. 
To illustrate, the following depict a 

[pipeline](./images/architecture)
