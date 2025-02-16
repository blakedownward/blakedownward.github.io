---
layout: post
title: PALETTEYES - AI Colour Palette Tool
image: "/posts/paletteyes-home-page-image.png"
tags: [Flask, Clustering, Transformer, NLP, Power BI]
---

PALETTEYES is a smart AI Colour Palette Tool for extracting colours from images, and generating colour palettes from natural language prompts. 

> **Tip:** View and use the tool at [PALETTEYES.com](https://paletteyes.com "Inspiration Through Colour, One Palette a Time")

---

### Extract Palette From Image

#### Overview

<img src="{{site.url}}\img\posts\paletteyes-extract-palette-from-image.png" width="600" style="float:right;">

The Paletteyes' colour extractor offers a quick and simple method for capturing colours from inspiring images.

Simply:
- Select your photo or image
- Click "Upload"
- Review the extracted palette
- Mix-and-Match colours from the *complementary* palettes (optional)
- Copy and save your palette to use in your designs


#### How Does It Work?

Under the hood, Paletteyes' colour extraction feature utilises a modified ***K-means clustering*** algorithm 
to discover distinct groups of dominant colours in an image. 

The ***K-means*** algorithm is an unsupervised machine learning technique which can be leveraged 
for clustering similar data points on an ad-hoc basis. The flexibility of this algorithm to deal with 
unseen data makes it a great choice to get up and running quickly, but it does come with its drawbacks.

*Issue #1:* Pre-defined value for **K**  
Paletteyes has been restricted to output palettes with just five colours. This restriction provides users with 
consistent number of outputs and minimises the computational load - but it does come at a cost. Setting "k=5" is 
unlikely to be the optimal solution for the infinite variety of images it may come across, but this is a simplifying 
assumption that balances returning a reasonable number of colours, in a reasonable amount of time.


*Issue #2:* Black and White dominance  
Many colourful images will actually be dominated by blacks and whites. Although these are critical "colours" 
in any designer's toolkit, allowing blacks and whites to form the outputted palette could effectively reduce the 
number of extracted colours to just three. 


*Issue #3:* Unobserved Centroids  
One aspect of **K-means clustering** which could lead to a poor user experience is the fact that cluster centroids 
are at points which have been calculated to minimise the overall error. In other words, centroids are calculated based 
on the sample of observations, but they may not actually be found in the sample. This could lead to serious confusion 
when dealing with colour extraction because it may output colours that are bot found within the target image.

This issue is overcome by searching for each centroid's nearest observed colour in the image. This is done in practice 
by measuring the Euclidean distance between each centroid and all unique colours found in the image.


*Issue #4:* Variations in Results  
Another feature of the **K-means clustering** algorithm is that it initialises with randomly placed centroids. This can lead 
to inconsistent and perhaps even unexpected results when running the function on the same image multiple times. Setting a "fixed" 
*random seed* was considered, however it was decided against due to this being more of an "artistic" than "scientific" tool. 


### Generate Palette From Prompt

#### Overview

<img src="{{site.url}}\img\posts\paletteyes-generate-palette-from-prompt.png" width="600" style="float:right;">

The Paletteyes Colour Palette Generator offers a fun and novel way to create palettes from natural language prompts.

Simply:
- Input a prompt
- Click "Generate"
- Wait a moment for Paletteyes to "think" about your request
- Mix-and-Match colours from the *complementary* palettes (optional)
- Copy and save your palette to use in your designs


#### How Does It Work?

Generating a palette of colours from a natural language prompt can be broken-down to two main processes:  
1) Representing the semantic meaning of the prompt with a vector of embeddings.
2) Generating a combination of colours that best "fit" the embeddings.

The first part of this process is handled by a pre-trained sentence transformer ('all-MiniLM-L6-v2') which takes an input of any length 
and returns a vector of 384 embeddings to represent the semantic context of the input. 

The second part of this process leverages a supervised machine learning network known as a "Multi-Headed Transformer", 
which can be trained to reduce a vector of 384 embeddings down to just 15 (3 "RGB" values for each of the 5 output colours).
This training process relies on having a dataset of appropriately labelled palettes so the model can learn the underlying 
connections between an embedding and a collection of colours.

#### Alternative approaches

A Transformer is not the only way we can achieve the second part of this process. Simple implementations of a Multi-Layered 
Perceptron (MLP) or a 1D Convolutional Neural Network (CNN) could be explored for reducing model size and inference time. 
Alternatively, more sophisticated (and complicated) approaches like a Variational Auto-Encoder (VAE) or a Generative Adversarial Network (GAN) 
might be able to learn more complex semantic mappings when compared to MLPs or CNNs. At the end of the day, selecting a 
Transformer for this task strikes a balance between "ease of implementation" and "quality of output" - making it a great 
choice for a baseline model and setting initial benchmark results.

