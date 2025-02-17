---
layout: post
title: PALETTEYES - AI-Powered Colour Palette Generation
image: "/posts/paletteyes-home-page-image.png"
tags: [Flask, Clustering, Transformer, NLP, Power BI, PyTorch]
---

Paletteyes is an API and web app designed to generate and extract colour palettes from images and natural language prompts. It provides designers, developers, and branding professionals with an intelligent, data-driven way to create visually harmonious colour schemes.

> **Tip:** Try for yourself at [PALETTEYES.com](https://paletteyes.com "Inspiration Through Colour, One Palette a Time")

---

#### **Overview**

<img src="{{site.url}}\img\posts\paletteyes-extract-palette-from-image.png" width="600" style="float:right;">

The project integrates machine learning and advanced clustering techniques to offer two core functionalities:

1. **Extract Palette from Image** - Uses k-means clustering to identify dominant colours in an image, with optimisations to enhance realism and usability.
2. **Generate Palette from Prompt** - A transformer-based model trained on labeled colour palettes to generate perceptually balanced color schemes from text descriptions.

Beyond these, Paletteyes enables users to refine their palettes with a colour picker tool and receive automatically suggested harmonious palettes based on their selections.

---

#### **Business Impact**

**1. Enhancing Design Efficiency for Developers & Creatives**\
Choosing the right colour scheme is a major pain point in web and graphic design. Paletteyes streamlines this process by generating colour schemes that are:

- Data-driven yet intuitive, reducing time spent on trial-and-error.
- Inspired by real-world environments (via image extraction), helping businesses create designs that align with their physical brand presence.

For example, as a freelance web developer, I extracted a colour scheme from a photo of a client’s workspace, ensuring their website design perfectly matched their brand identity. This eliminated what can be a lengthy process of back and forth between designer and client over colour choices, and significantly sped up the design process.

**2. Improved Usability with Smart Colour Extraction**\
Standard k-means clustering can produce misleading results by selecting colours that don’t actually appear in an image. I implemented several optimizations to improve accuracy and usability:

- **Nearest Observed Colour Matching**: Ensures extracted colours exist in the original image (as would be expected by the user).
- **Exclusion of Non-Impactful Colours**: Automatically removes blacks and whites,  preventing dominant but non-useful colours being included in the palette.
- **Optimized Data Sampling**: Uses only unique colours for clustering, making the process more likely to return perceptually obvious, but less-dominant colours.

These enhancements result in more relevant colour palettes that align with user expectations, helping to increase adoption and usability.

**3. Loss Engineering for Creative/Subjective Applications**\
One of the most technically challenging (and rewarding) aspects of Paletteyes was defining a loss function for the "Palette from Prompt" model. Initially, a blend of Mean Squared Error (MSE) and Cosine Similarity was used, but it struggled to generate perceptually coherent palettes for unseen prompts. Being a subjective/perceptual task, perceptual metrics would be key for the model to learn what makes a palette "look" good.

To improve this, I developed a novel loss function incorporating a weighted suite of perceptual metrics such as; contrast, harmony, and brightness. This:

- Reduced training time and improved convergence.
- Enhanced palette quality for novel prompts, ensuring even abstract inputs result in aesthetically pleasing palettes.
- Allowed the model to understand and balance key design principles automatically.

As a result, Paletteyes can generate high-quality palettes even from unconventional prompts, positioning it as a valuable tool for designers and AI-driven creativity.

---

#### **Technical Implementation Highlights**

<img src="{{site.url}}\img\posts\paletteyes-generate-palette-from-prompt.png" width="600" style="float:right;">


- **Machine Learning Techniques**: K-means clustering, transformer-based text-to-palette generation.
- **Custom Engineering**: Perceptual loss function design for improved model performance.
- **Scalability & Deployment**: Serverless deployment on GCP Cloud Run.
- **Extensibility**: Published an open-source Python package (pyletteyes) to support colour-related computations across projects. This is a lightweight package for working with colours and palettes as objects, offering simplified methods for type/string conversions (RGB-HSL-Hex-rgbString), colour conversions (darken, complementary, analogous), and palette scoring metrics (contrast, harmony, brightness balance).

---

#### **Future Potential & Applications**

Paletteyes is more than just a tool - it represents a shift towards AI-assisted design workflows. Future expansions could include:

- API integrations with design tools like Canva, Figma or Adobe XD.
- Expanded dataset training for even more nuanced palette generation.
- Real-time user feedback to refine results based on design preferences.

Blending AI with human creativity, Paletteyes helps designers to work faster, make informed colour decisions, and create visually compelling projects with ease.







