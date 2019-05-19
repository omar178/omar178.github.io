---
layout: post
title: "Hidden units"
date: 2019-05-19 23:01:09
image: '/assets/img/'
description:
tags:
- Machine learning
categories:
twitter_text:
---
# Rectified Linear Units
Rectified linear units use the activation function g ( z ) = max { 0 , z }, they are much like linear units except the fact that it has a threshold of zero so any input that is less that zero is dumped to zero and this actually make derivative across active units(of non zeros) is high with respect to other dead units of values x = 0, d/dx = 0 so here this situation could be useful as the optimizing algorithm as SGD will follow along with units that contain active information and will leave alone the dead units but this also considered as a set back as the gradients at the dead units will not go forward in learning

## Solution
Three generalizations of rectified linear units are based on using a non-zero
slope α i when z i < 0: h i = g(z , α ) i = max(0, z i ) + α i min (0, z i ). Absolute value
rectification fixes α i = −1 to obtain g(z) = | z | . It is used for object recognition
from images, A leaky ReLU fixes α i to a small value like 0.01 while a parametric ReLU or PReLU
treats α i as a learnable parameter

# Logistic Sigmoid and Hyperbolic tangent
    g ( z ) = σ ( z )
    g ( z ) = tanh( z )
they are closely related because tanh(z) = 2 σ (2 z ) − 1
sigmoidal
units saturate across most of their domain—they saturate to a high value when
z is very positive, saturate to a low value when z is very negative, and are only
strongly sensitive to their input when z is near 0. The widespread saturation of
sigmoidal units can make gradient-based learning very difficult. For this reason,
their use as hidden units in feedforward networks is now discouraged

# Credits
Deep learning book by Ian Goodfellow and Yoshua Bengio and Aaron Courville
