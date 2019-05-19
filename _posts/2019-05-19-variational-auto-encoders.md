---
layout: post
title: "Variational auto-encoders"
date: 2019-05-19 05:40:51
image: '/assets/img/'
description:
tags:
categories:
twitter_text:
---
This is my explanation of Tutorial on Variational Autoencoders
by CARL DOERSCH, Carnegie Mellon / UC Berkeley

They are called auto-encoder only because the training objective in the end includes an encoder and a decoder but they are a little bit different from sparse auto-encoders and denoising auto-encoders
VAE simply works as follows:

what VAE actually does is that it tries to learn a function after fitting to a certain data for example this function is g ( z ) = z/10 + z/ || z || (a function that draws a ring)so VAE try to learn g( z ) , so the first question that comes to my mind when first seeing this equation is how we will choose values for z variable which btw called latent variable and the answer is very simple, WE DON'T! it's been assumed that if z is 2D normally distributed then g ( z ) for any z will form a ring in the end so for example let's if our data is full of human faces and we try to apply this technique to generate human face and we learned an equation from the data we are given with the values of z which is the independent pixels of our images, i.e pixels of cheeks,eyes, hair and noise in the end it could actually generate a face as long as we know the equation to do so.
Now let's move on to the second interesting part of the paper which is trying to maximize the probability of P ( X ) ≈ 1/n ∑ i P ( X | Zi ) here X represent the data-set that we are trying to generate our faces from and z the variables for the equation we have chosen so in another words we are trying to maximize the probability that this is what we generated is a face so we can use stochastic gradient descent for this.
Setting up the objective
so for most variables of z the P(X/z) will be nearly zero i.e in the process of generating image faces .The key idea behind the variational
autoencoder is to attempt to sample values of z that are likely to have
produced X, and compute P ( X ) just from those. This means that we need a
new function Q ( z | X ) which can take a value of X and give us a distribution
over z values that are likely to produce X.
log P ( X ) − D [ Q ( z | X )k P ( z | X )] = E z ∼ Q [ log P ( X | z )] − D [ Q ( z | X )k P ( z )]
this equation relates lots of known terms to us now! left hand side as a whole is the part we need to maximize includes log P(x) being a face image and we need to minimize an error term which we can achieve by optimizing the right hand side using stochastic gradient descent.
## Process
so this is a plot that illustrate the total process, now it looked more as auto-encoders having encoder function Q and a decoder function P. The 2 functions u(X)and Σ(X) implemented via the neural network then we take z samples from those function and feed them to the decoder function then we compute the loss which is the distance between the input images and the generated ones.
## Optimzation:
log P ( X ) − D [ Q ( z | X )k P ( z | X )]] =E z ∼ Q [ log P ( X | z )] − D [ Q ( z | X )k P ( z )]] .
this is the equation we need to optimize and when comes to optimization we are talking about see what cause a change in a variable that is being effected by another variable so we are talking about derivative but in many directions which is a gradient and btw we can compute the gradient for 1 z that produce 1 x and then take the average of total samples. back propagation takes place in sampling the z values

## Testing
in testing time we simply remove the encoder and feed z values to the decoder which has the equation learned to generate face images as our example says.
Conditional variational auto-encoders
lets say we have a dataset that has several classes but it happens that we have a problem that we have a class that has less data points than the other classes so we could use several class imbalance alleviation techniques but no we could as well use CONDITIONAL VARIATIONAL AUTO-ENCODERS.
The solution is to use a regressor that minimizes the distance between the generated image and X which is the class we need to generate samples from so given an input X and an output Y, we want to create a model P ( Y | X )
which maximizes the probability of the ground truth.
log P ( Y | X ) − D [ Q ( z | Y, X )k P ( z | Y, X )] =
E z ∼ Q (·| Y,X ) [ log P ( Y | z, X )] − D [ Q ( z | Y, X )k P ( z | X )]
here's the new equation the only difference from the above equation is that now we need to maximize the term log P (Y | X ) so we added the class we need to generate images from.

## Practical work
I will borrow this paragraph from the paper as I found it super clear and important.
In practice, the model seems to be quite insensitive to the dimensionality
of z, unless z is excessively large or small. Too few z's means the model can
no longer capture all of the variation: less than 4 z dimensions produced
noticeably worse results. Results with 1,000 z's were good, but with 10,000
they were also degraded. In theory, if a model with n z's is good, then a
model with m >> n should not be worse, since the model can simply learn
to ignore the extra dimensions. However, in practice, it seems stochastic
gradient descent struggles to keep D[ q ( z | X )|| P ( z )] low when z is extremely
large.
remember that z is the samples we get from the function u(X)and Σ(X). z should be the samples that capture all the variations in the data and it makes our life much easier than that if we took the full data to the next step.
THANKS !
