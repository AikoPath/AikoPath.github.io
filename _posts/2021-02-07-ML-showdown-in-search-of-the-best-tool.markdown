---
layout: post
title:  "An ML showdown in search of the best tool (2019)"
permalink: /ml-showdown-in-search-of-the-best-tool/
tags: AI Artificial-Intelligence ML Machine-Learning
---

Ever [burgeoning digital data](https://www.forbes.com/sites/bernardmarr/2018/05/21/how-much-data-do-we-create-every-day-the-mind-blowing-stats-everyone-should-read/#6e6be51160ba) combined with [impressive research](http://www.wildml.com/2017/12/ai-and-deep-learning-in-2017-a-year-in-review/) has lead to a rising interest in Machine Learning or ML, which has further powered a vibrant ecosystem of technologies, frameworks, and libraries in the space. So, today, when technologists are trying to solve a problem leveraging ML, the sheer volume of possible approaches can leave them overwhelmed. This is exactly why I decided to lift the dense fog from around the current ML landscape by delving into this tech and its popular subset, deep learning.

I have employed a data-driven approach and have created a ranking system where each ML tech is rated on certain features. This should help decide what works best for a technologist’s use case scenario. I also restricted my analysis to the most popular technologies that, at the time of writing this paper, enjoyed no less than a 6.500 stars (for deep learning) or 1.300 stars (for statistical learning and shallow neural networks) on Github.

<p style="font-size: 1.3rem;">
Here are the factors that I took into consideration for my data-driven analysis
</p>

* **Ease of setup**: A new technology can set the mood for the entire development journey which is why you need to weigh the difference between a simple pip/brew/conda/apt-get install, and building a tool and its dependencies from source.
* **Usability**: The learning curve coupled with the tool’s intuitiveness are good indicators of an ‘easy or tough application’. But, these are rather subjective factors because they are determined by one’s own level of experience as well.
* **Adoption rate within the community**: Popularity can hint at a tool doing something right. That popularity is also an indicator for the community support one can expect when running into problems while working with the said tool.
* **Degrees of freedom**: Some models’ parameters might need specificity while others allow for flexibility. An example of this is the number of possible infrastructure configurations. And, this could be a deterrent or not depending on one’s use.

<p style="font-size: 1.3rem;">
Now, let’s look at the devised ranking system based on the above-discussed parameters
</p>

This rating system will help one arrive at meta conclusions regarding the technology into consideration. In other words, it will help one make broad decisions regarding their development path, but the finer points will depend on the definition of the task laid out before them.

### The machine learning tech showdown

Based on the qualifiers/factors discussed above, I have plotted technologies on a grid. Additionally, in spite of deep learning being a subset of ML, both enjoy different use cases, especially due to their GPU support. Which is also why I have split the two into separate categories. Let’s go over the grid’s coordinates -
* The **y-axis** shows increasing degrees of freedom
* The **x-axis** shows increasing degrees of adoption within the tech community
* **Size of bubbles** correlates with usability. The easier to use, the bigger the bubble.


[![The ML tech showdown](/assets/img/ml-showdown/ml-tech-showdown.png "The ML tech showdown")](/assets/img/ml-showdown/ml-tech-showdown.png)

**A few broad observations:**

* [Scikit-learn](http://scikit-learn.org/stable/) sees high adoption from the tech community. The most probable reason is a powerful Python interface that allows tweaking of models across multiple parameters.
* [MLlib](https://spark.apache.org/mllib/) and [H2O](https://www.h2o.ai/) should be considered when working with [Spark](https://spark.apache.org/). Spark does come with MLlib and has a higher level wrapper called [SparkML](https://spark.apache.org/docs/1.2.2/ml-guide.html) that supports the same. In some cases, H2O offers a suitable solution and can be used alongside MLlib or added when needed.
* [Weka’s](https://www.cs.waikato.ac.nz/ml/weka/) interface makes it the easiest to use but, it isn’t popular within the tech community. Interestingly, one should also note that Weka offers additional data mining features.
* [PyBrain’s](http://pybrain.org/) development has been discontinued apart from 10 small bug fixing commits over the last two and a half years.

## ML tools scalability

For those of you whose main concern is the tech/tool’s scalability, this perspective of the landscape could help -

[![ML tools/tech scalability](/assets/img/ml-showdown/ml_tool_scalability.png "ML tools/tech scalability")](/assets/img/ml-showdown/ml_tool_scalability.png)

* The **y-axis** shows increasing degrees of freedom
* The **x-axis** shows increasing degrees of the tech’s scalability
* **Size of bubbles** correlates to usability. The easier to use, the bigger the bubble.
* The **color of the bubbles** are indicative of the tech’s adoption within the community

**A few broad observations:**

* H2o, MLlib, and [Mahout](https://mahout.apache.org/) can be integrated with Spark and run on top of a HDFS cluster
* In spite of Scikit-learn offering both, the highest degree of freedom and adoption rate, it’s limitation is when working with large amounts of data. It is also limited in terms of scalability because of limited memory and resource capacity.

## The deep learning tech showdown
If deep neural networks are what one is looking for, scalability is never going to be a problem, because it’s a default feature of almost all deep learning tech.

Most of the frameworks that I have analyzed in this section are open sourced. Companies like Google, Facebook, and Microsoft handle large amounts of data that reveal powerful insights, and it serves the parent companies well to have the larger tech community work on their respective frameworks and make improvements on them.

[![The Deep Learning tech showdown](/assets/img/ml-showdown/dl-tech-showdown.png "The Deep Learning tech showdown")](/assets/img/ml-showdown/dl-tech-showdown.png)

* The **y-axis** shows increasing degrees of freedom
* The **x-axis** shows increasing levels of adoption by the tech community
* **Size of bubbles** correlates to usability. The easier to use, the bigger the bubble.
* **The color of the bubbles** are indicative of how easy the tech is during setup

**A few broad observations:**

* [Tensorflow](https://www.tensorflow.org/) is the most popular framework, and contributing factors are the clean and comprehensive Python API, the multiple language wrappers and the several optimizations that are crucial to working with distributed infrastructure. Also, Google’s Tensorflow displays the maturity that comes from being in the market for more than two years. However, a negative is the steep learning curve needed to master the framework.
* [Keras](https://keras.io/) is not necessarily a deep learning framework, but a wrapper for several frameworks; a higher level interface if you will. Keras allows for the quick building of deep learning prototypes on top of frameworks and ensures an easy interface built on powerful optimizations. In fact, combining Tensorflow with Keras is quite popular. This is a key factor for the frameworks in the middle of the chart, that fight for attention.
* [Caffe2](http://caffe2.ai/) is a fairly new re-implementation of [Caffe](http://caffe.berkeleyvision.org/). And, I foresee Caffe2 joining the ‘attention seeking’ group soon especially since its Github repository got merged with the one of PyTorch. The original Caffe framework is still popular when it comes to image processing.
* University of Montreal’s [Theano](http://www.deeplearning.net/software/theano/) that has been around for a while recently lost support in the overcrowded market
* [PyTorch](https://pytorch.org/), a re-implementation of [Torch](http://torch.ch/), is slowly set to replace Tensorflow in academic research. This is because the ML library is implementing the latest research results faster than its competitors.
* [DL4J](https://deeplearning4j.org/) is, as the name suggests, a library for Java but has severe competition because most of the other frameworks also offer a Java interface
* [Microsoft Cognitive Toolkit](https://www.microsoft.com/en-us/cognitive-toolkit/) has a low rating when it comes to setup. For a fair comparison, I installed all the frameworks on Ubuntu Linux because not all (mentioned) frameworks support Windows. A Windows installation might probably be trouble-less in this case.

Interestingly, the path to success is not always obvious when it comes to ML and deep learning tech. More often than not, experimentation or trial and error will identify which model in combination with what hyperparameter offer the best results. For example, deciding if a Bidirectional Recurrent Neural Network, BRNN performs better than a Long Short Term Memory Network, LSTM in one’s use case can only be determined by trying out different combinations of the above and comparing results, which points to the fact that the deciding factor for or against a tool is its ability to enable fast prototyping.

There is also the approach of fine-tuning a model’s every little parameter that will obviously ensure more options available on hand, which in turn guarantee a great end result. It is therefore advisable that one is open to exploring different tools at different phases of the project.

## Finally, let’s look deep learning tech during a project’s life cycle.

[![Deep Learning during a project’s life cycle](/assets/img/ml-showdown/dl-lifecycle.png "Deep Learning during a project’s life cycle")](/assets/img/ml-showdown/dl-lifecycle.png)


There is some work being done in the space of framework interoperability solutions. [ONNX](https://onnx.ai/) is a pertinent example. Short for Open Neural Network Exchange, it’s a unified format to define a neural network model. Currently Caffe2, [Microsoft Cognitive Toolkit](https://www.microsoft.com/en-us/cognitive-toolkit/), [MXNet](https://mxnet.apache.org/), and PyTorch store their network description in the ONNX format. Additionally, there are other ways to convert one frameworks’ format to another.

Facebook, which is responsible for two of the frameworks I have analyzed; Caffe2 and Pytorch,  is making use of this interoperability feature. PyTorch is used for prototyping and research, and the model is then moved to Caffe2 during production. To make things easier, Facebook merged the GitHub repositories of both, and this is a first step in the direction of merging both the frameworks into one.

Even though MxNet supports ONNX, it tries to address the need for switching frameworks by offering options at different parts of the product life cycle. It has a built-in higher-level interface, which allows for fast prototyping and fine-tuning.

Lastly, but not least are the set of tools to the extreme left of the graph. These are various as-a-service solutions offered by cloud providers, and they offer specialized solutions like Optical Character Recognition, Landmark Detection, Face Detection, Text and Speech Translator, Speaker Recognition, etc. They don’t usually allow one to train a model and are more an API to upload files to and receive a JSON containing the analyzed data. Also, they are paid for offerings and one’s data is accessible by the parent companies.

I’d like to reiterate that the graphs or diagrams that I have put together are a depiction of the current landscape based on what I have deemed meaningful criteria. The dynamic nature of technology requires that one use these ranking systems only as a starting point or a guideline, for their own analysis. I’d suggest one starts off with these factors; project lifecycle phase, scalability and community support, and depending on their use case they might want to include specific features to better arrive at the right choice for their particular requirement.

(This article has originally been published on [ThoughtWorks.com](https://www.thoughtworks.com/insights/blog/machine-learning-showdown-best-tool))
