---
layout: post
author: ewd
tags: [ "python", "diffeq", "modeling", "biotech"]
excerpt_separator: <!--more-->
---

The SIR model is an example of a compartmental model used to simplify the mathematical modeling the spread of infectious diseases.  While the SIR model gets a lot of attention for its use as a toy model for testing implementations, or demonstrating the power of ODEs for modeling nonlinear systems, it's a surprisingly good fit for actual data.

![SIRS Model for epidemiology of Influenza B in 2007](/assets/images/2007-Influenza-B-Prediction.png)

<!--more-->

As a note, I'm making use of the [XKCDify package](http://jakevdp.github.io/blog/2012/10/07/xkcd-style-plots-in-matplotlib/) for Python to generate the figures in this post.  It is a deliberate design decision to give the blog a less polished feel as these are just sketches of ideas.

The data for this, and the remaining examples in this post, are drawn directly from the CDC.  I'm currently focusing heavily on problems of interest to the CDC and the study of epidemics and pandemics, so this post is partially just a product of my recent data dive.  The [Epidemiology and Prevention Branch in the Influenza Division](https://www.cdc.gov/flu/weekly/overview.htm) of the CDC has some excellent open data sets on Influenza available, so it's pretty simple to look at different outbreaks over time.

![Overview of the 2007 Influenza Outbreak in Region 5](/assets/images/2007-Influenza-B-Overview.png)

The figure above is an overview of the incidence of various strains of influenza witnessed by the CDC during 2007 for Region 5.  Most of the historical data at the CDC is broken into these regions, with more recent data also available at the state level, so it requires aggregating the us as follows:

![Region map as defined by HHS](/assets/images/regionsmap.jpg)
