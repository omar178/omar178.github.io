---
layout: post
title: "Pytorch or Tensorflow, Dynamic vs Static computation graph"
date: 2019-05-19 05:37:36
image: '/assets/img/'
description:
tags:
- Machine learning
categories:
twitter_text:
---


The main difference between frameworks that uses static computation graph like Tensor Flow, CNTK and frameworks that uses dynamic computation graph like Pytorch and DyNet is that the latter works as follows, a different computation graph is constructed from scratch for each training sample, forward and backward propagation are then take place so in another words the user is free to use different networks for each input sample but this of course will cost you a little overhead but don’t worry frameworks like DyNet has an optimized C++ backend and lightweight graph representation. Experiments show that DyNet’s speeds are faster than or comparable with static declaration toolkits while the static graph frameworks the graph is defined once and then the optimization graph compiler then produced optimization graph and all the training samples are then feed to this graph .On the one hand, once compiled, large graphs can be run efficiently
on either the CPU or a GPU, making it ideal for large graphs with a fixed structure, where only the inputs change between instances. However, the compilation step itself can be costly, and it makes the interface more cumbersome to work with

Now let go into details to know more about the differences between two paradigms.
Static declaration

Static declaration follows two steps:

    Definition of a computational architecture

in this step the user define the shape of the graph he wish to proceed with like for example take a 16*16 image and pass this image to 10 convolution layers, calculate the loss with this certain function and predict the class of a certain image.

    Execution of the computation

This step where the computation takes place ,The user then repeatedly pass data to the 16x16 matrix ,the library executes the previously declared computation graph. The predictions can then be used at test time, or at training time the loss can be calculated and back-propagated through

## Advantages

An obvious thing to know is that the graph once defined it can be used multiple times as fast as possible since actually we are not going to create anything new so this is super useful in large data-sets and could be very useful in training and testing speed. Second, the static computation graph can be used to schedule computation across a pool of computational devices so computational cost could be shared.

## Disadvantages

Different input size could be a problem so for example if your inputs are not restricted to 16*16 , it will be more difficult to define a single structure of identical computations.
Variably structured inputs/outputs: A more complicated case is when each input has not only a different size, but also a different structure for example your data may be has images,texts and structured tables.

However these difficulties we can avoid if we can declare a graph with unspecified size of input at declaration time and let the graph cope with the inputs as TensorFlow offers the dynamic rnn operation. While it is therefore possible to deal with variable architectures with static declaration in principle, it still poses some difficulties in practice:

Complexity of the computation graph implementation:

To support dynamic execution, the computation graph must be able to handle more complex data types (e.g., variable sized tensors and structured data), and operations like flow control primitives must be available as operations. This increases the complexity of computation graph formalism and implementation, and reduces opportunities for optimization.

## Difficulty in debugging:

While static analysis permits some errors to be identified during declaration, many logic errors will necessarily wait to be uncovered until execution (especially when many variables are left unspecified at declaration time), which is necessarily far removed from the declaration code that gave rise to them. This separation of the location of the root cause and location of the observed crash makes for difficult debugging.

## Dynamic Declaration

This performs a one step technique only so let recall our example of 16*16 image is loaded then passed to say 2 convolution layers then either compute the loss in case of training phase or compute the predictive probabilities in case of testing, the graph is created for each training instance so it should be light weighted .
## Credits

    https://arxiv.org/abs/1701.03980.
    Yoav Goldberg — Neural Network Methods in Natural Language Processing-Morgan & Claypool (2017) book.
