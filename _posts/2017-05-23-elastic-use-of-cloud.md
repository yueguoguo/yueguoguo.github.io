---
layout:     post
title:      Cloud for elastic data science 
date:       2017-05-23 16:43:29
summary:    Operationalization with Azure Data Science Virtual Machine.
categories: data science, cloud, azure, data science virtual machine
---

> "Everything Should Be Made as Simple as Possible, But Not Simpler." 
> - Albert Einstein

The way of doing data science is dramatically impacted by cloud
computing technology: 

Years ago, to experiment with a random forest algorithm, researchers
had to configure computing clusters by hand, which usually means weeks or months
of system engineering and probably endless efforts in communication with IT department. 
Now it has become so simple that in 5 minutes a data scientist can deploy a Linux based virtual
machine on cloud, where mainstream data science tools and software are pre-installed.
That is handy! It not merely saves the engineering efforts in setting up
a working environment that data scientists are comfortable with, but
also ecnonomizes the cost of administrating computing resources. 

[Microsoft Azure Data Science Virtual Machine](http://aka.ms/dsvm) is
a virtual working space available on Azure cloud which by and large brings the following
benefits for elastic data science on cloud:

* Scalability. There are various options of machine
sizes on Azure to scale up or down a DSVM. 
* Flexibility. The cutting-edge toolkits and frameworks for big data and deep learning,
such as TensorFlow, Spark, etc., are available off-the-shelf on DSVMs for toying
up machine learning experiments.
* Cost effectiveness. DSVM is agile such that it does not have to be alive
all the time in a data science project. It is charged in a "Pay-as-you-go" scheme, 
and generates cost only being used. 

The following diagram depicts an illustrative resource planning
scenario of a heterogeneous set of DSVMs for flight delay prediction.

It is worth mentioning DSVMs in the piepline can be operationalized programmatically 
in R with minimal efforts in manual setup. 

![pipeline](https://github.com/yueguoguo/yueguoguo.github.io/blob/master/images/architecture.png)

Details can be found at
[GitHub
repository](https://github.com/Microsoft/acceleratoRs/flightDelayPredictionWithDSVM)
