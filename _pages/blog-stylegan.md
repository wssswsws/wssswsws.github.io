---
layout: single
permalink: /blog/stylegan/
title: "StyleGAN: A Short Tutorial and What I Learned in PURM"
author_profile: true
excerpt: "A StyleGAN tutorial and notes on a PURM privacy audit. Under construction."
---

**Under construction.** I am expanding this tutorial and preparing a separate public cat generator.

## The short version

A generative adversarial network trains two models together: a **generator** makes images from random inputs, while a **discriminator** tries to tell generated images from training images. StyleGAN adds a mapping network that turns a random latent vector into an intermediate representation. The synthesis network uses that representation to control image features at different scales. [StyleGAN's original paper](https://arxiv.org/abs/1812.04948) explains the architecture; [StyleGAN3](https://nvlabs.github.io/stylegan3/) addresses aliasing that can make image details appear stuck to pixel coordinates during transformations.

This is a model of an image distribution, not a database lookup. Still, a generated image can resemble training data, especially when the training set is small. Visual realism and privacy therefore need separate evaluations.

## My PURM work

During my [PURM research](https://curf.upenn.edu/content/penn-undergraduate-research-mentoring-program-purm) in Kai Wang's lab at Children's Hospital of Philadelphia, I worked on multimodal rare-disease research and trained a conditional StyleGAN3 pilot for synthetic facial images. I also worked on a privacy audit asking whether generated images or model scores could reveal information about the training set. This is unpublished work on sensitive patient data, so the patient images and audited model remain internal.

## A separate public demo

I want to build a [cat generator on this site (under construction)](/stylegan-cats/) inspired by [These Cats Do Not Exist](https://thesecatsdonotexist.com/). The goal is visibly higher-quality images using a publicly releasable model; I will compare outputs before claiming an improvement. The demo does not use the PURM model or patient images.
