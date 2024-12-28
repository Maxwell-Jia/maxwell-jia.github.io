---
title: "Mask Dice Loss: A Novel Solution for Imbalanced Time-Series Anomaly Detection"
date: 2024-03-21
draft: true
tags: ["time-series"]
categories: [""]
hideToc: false
math: true
---

If you’ve ever worked on detecting rare events in time-series data (like anomalies in sensor readings, fraudulent transactions, or even cosmic phenomena like stellar flares), you know how frustrating it can be. Most of the time, your model is drowning in a sea of normal data, completely ignoring the rare events that actually matter.

That’s where **Mask Dice Loss** comes in. The loss function is proposed in the paper [FCN4Flare: Fully Convolution Neural Networks for Flare Detection](https://arxiv.org/abs/2407.21240).

In this post, I’ll guide you through why imbalanced data is such a pain, how traditional loss functions fail us, and how Mask Dice Loss steps up to solve the problem. By the end, you’ll see how this simple yet powerful tweak can give your model the focus it needs to detect those elusive anomalies.

In this post, we will focus on the problem of detecting stellar flares. 

# Problem definition

The crux of our task lies in predicting the probability that each flux value in a given light curve belongs to a flare event. To accomplish this, we employ neural networks denoted by $f(X|\Theta)$, where $X=\lbrace x_i \in \mathbb{R} \mid i=1, 2, \cdots, T\rbrace$ represents the input light curve with a length of $T$. Our objective is to generate a probability vector $P=\lbrace p_i \in [0, 1] \mid i=1, 2, \cdots, T\rbrace$, where $p_i$ signifies the likelihood that the flux value $x_i$ is part of a flare event.

