---
layout: post
title: "Optimization Algorithms"
date: 2018-09-08 03:32:44
image: '/assets/img/'
description: 'First steps to learning'
tags:
- Machine learning
- Algorithms
categories:
- I love Jekyll
twitter_text: 'How to install and use this template'
---

In this article i am gonna explain briefly what are the ups and downs for each optimization algorithm i will be explaining. Thanks to Stanford channel who have given me the chance to have a better intuition about all these interesting concepts so that i would be able to share it with you guys.

First i think we should talk about Gradient descent so the process here is that we are having some values in like 1m directions and these values are the input let’s say pixels in case of images multiplied by the weigh matrix and we are trying to go in direction where your loss is decreased significantly as shown here

It’s as simple as that calculate the gradients in all directions (gradient is just the derivative i.e slope but regards several variables) as i said we have like 1m dimensions and then take find the largest slope and just take the negative direction of that so in the end your heading down the hill which is your aim.

  Here a demonstration shows how to calculate the gradient vector , you will have to take the sum of all weights in their state of no movements in any direction and subtract it from W+h where h is the change we have made in certain direction in this case we have taken the direction towards 0.34 by learning rate = 0.0001 (how big is our step) and the result form that is the gradient in only 1 direction !! Yes you will have to compute that in all direction

That could be an issue in Gradient descent so you will have to run through all your data to make one step down the Hill. !! congratulation that all for gradient descent you are now familiar how things work.

Solution?!

Stochastic Gradient Descent

    The case in SGD is that instead of running through all the data which is definitely could be large we will take only a small batch ,may be 64, 128 and approximate the sum of data to update to any direction.but !

Problem 1

    if you think of it as long as you are moving horizontally your loss will update slowly as your target is to go just as quickly as possible to the smiling face at the center but at the same time if vertically your loss will update quickly so that could be a problem when choosing SGD as our optimization algorithm

or what if it reaches a local minima or a saddle point as you can the slope is near to zero so our loss wouldn’t update at all so it stuck!! could be a problem ?
## SGD with momentum
introduced the velocity to the equation let's see.
So it's no longer depends on the gradients only it's now depend on a new parameter called velocity and the term velocity actually is the sum of the previous gradients the model passed so the sum will never be equal zero and it will update faster than the normal SGD
and this actually solved the problems of sticking in a local maxima but actually we have another problem is that as i stated earlier the model is prone to move faster or slower depends on the direction (explained in Problem 1 figure) so what do you think will be a solution for that
## AdaGrad
Solution for problem 1So what is this picture telling us , so simple just look at x and consider it you step so we will move in the negative direction of the derivative divided by square the gradient so let's think about that if this value is big as in the vertical direction the value of x will be small so small steps will be taken while if the value of square gradient is so small let's consider the horizontal direction at the circle curves then the value of x will be large enough to update faster , Simple you have solved the problem of different update ratios regarding different directions.
We are done with all science the other two algorithms are just a mixture of some of these we have talked about before
## RMSprop
Just added decay_rate term to ensure that the grad_square won't be zero in any situation
Adam
Adam is just mixing the momentum and the AdaGrad by calculating the momentum to achieve speed in updating and dividing by the square gradient to address the problems of different updates in different directions but wait one second what happen in the first iteration let's think the values of first_moment and second_moment will be very close to zero so we will add a bias term to solve this.
Solved !!
we have reached the end of this tutorial if you like it please upvoted it, i will be posting so many tutorials on several concepts and projects covering Machine learning and Deep learning
THANKS
