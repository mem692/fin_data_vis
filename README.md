# Enhancing Storytelling on Financial Data Dashboards

# Introduction

Aswath Damodaran, in his recent *Narrative and Numbers*, laments the limits of big data. The extent of data itself is not an issue; indeed, data permeates our lives. A few clicks or smartphone presses, and the din of data overwhelms us. The problem, as Damodaran puts it:

> "[O]ur decision making has become even more simplistic and irrational because we have all this data at our disposal. ... (A)s numbers come to dominate so many business discussions, people are trusting them less, not more, and falling back on stories."

This observation is troubling for business decision makers seeking data-driven strategy. As we strive to become John Stuart Mill's *homo economicus*, we can easily fall back on heuristics and narratives to help us as *homo sapiens* make sense of dumbfounding complexity. However, Damodaran rightfully argues that we should not be averse to narratives. Narratives provide structure and order and can help explain decisions in very powerful ways.

Balance comes in utilizing the strengths of both data's insights and narratives' structure without over-reliance on both. Financial data dashboards provide a unique opportunity to enforce this balance. Dashboard engineers are forced to communicate large amounts of information in a small amount of space. How can decision makers construct narratives from dashboards? Here, I present some ideas for space-constrained visualizations that can both communicate insights and provide clues for potential narratives. 

## In this project

This project contains a Jupyter notebook with visualizations built on data for non-commercial use. Visualizations are also included in the GitHub README for reference.

Data Sources: 

* Federal Reserve Bank of St. Louis' FRED
* Quandl API
* AlphaAdvantage API
* Morningstar
* MSCI
* S&P Dow Jones Indices

# Project Setup

# Visualizing Economic Indicators

## Line and Area Plots

![Line Plot](/Images/indi_line.png)

![Area Plot](/Images/indi_m2.png)

## Rolling Yield Curve

![Rolling Yield Curve](/Images/indi_yields.png)

## Towards Indicator Narratives

### A Typical Indicator Dashboard Gauge

![CPI Gauge](/Images/indi_cpi.png)

### Enhancing Indicator Dashboard Gauges

![Rolling CPI Gauge](/Images/indi_cpi_enhanced.png)

# Visualizing Absolute Returns

## Histograms

![Histograms](/Images/abs_hists.png)

## Towards Narratives with Absolute Returns

### Enhancing Histograms with Violin Plots

![Violin Plots](/Images/abs_violin.png)

### The Humble Z-Score as Storyteller

![Violin Plots with Z-Scores](/Images/abs_violinz1.png)
![Violin Plots with Z-Scores](/Images/abs_violinz2.png)

# Visualizing Relative Returns

## Growth of Dollar Amount

![Growth of 10K](/Images/rel_g10k.png)

## Periodic Table of Returns

![Periodic Table](/Images/rel_periodic.png)

## Visual Cues as Narrative Clues

![Vertical Bar](/Images/rel_vertical_bar.png)

# Conclusion