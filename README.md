# Enhancing Storytelling on Financial Data Dashboards

# Introduction

Aswath Damodaran, in his recent *Narrative and Numbers*, laments the limits of big data. The extent of data itself is not an issue; indeed, data permeates our lives. A few clicks or smartphone presses, and the din of data overwhelms us. The problem, as Damodaran puts it:

> "(O)ur decision making has become even more simplistic and irrational because we have all this data at our disposal. ... (A)s numbers come to dominate so many business discussions, people are trusting them less, not more, and falling back on stories."

This observation is troubling for business decision makers seeking data-driven strategy. As we strive to become John Stuart Mill's *homo economicus*, we can easily fall back on heuristics and narratives to help us as *homo sapiens* make sense of dumbfounding complexity. However, Damodaran rightfully argues that we should not be averse to narratives. Narratives provide structure and order and can help explain decisions in very powerful ways.

Balance comes in utilizing the strengths of both data's insights and narratives' structure without over-reliance on both. Financial data dashboards provide a unique opportunity to enforce this balance. Dashboard engineers are forced to communicate large amounts of information in a small amount of space. How can decision makers construct narratives from dashboards? Here, I present some ideas for space-constrained visualizations that can both communicate insights and provide clues for potential narratives. 

## In this project

This project contains a Jupyter notebook with visualizations built on data for non-commercial use. Visualizations are also included in the GitHub README for reference.

# Project Setup

# Visualizing Economic Indicators

Economic indicators provide the backbone for dashboards providing a macro outlook. They benefit top-down research greatly. Many practitioners need only a snapshot of the indicator data with the latest observation. 

## Line and Area Plots

Most indicator data providers (and FRED especially) rely on line graphs to display economic time series. Here is an example for crude oil prices:

![Line Plot](/Images/indi_line.png)

An area plot for quantity amounts can also be built quite simply in Python.

![Area Plot](/Images/indi_m2.png)

## Rolling Yield Curve

However, the tools allowed by Python provide for more information to be conveyed succinctly. Treasury yield curves in particular suffer from a dearth of innovative presentations. A yield curve at one point in time is not particularly informative. Many practitioners turn to line graphs of treasury term differentials (especially the 2s-10s difference) and rely on that time series. This ignore a lot of information in the shape of the yield curve. Curve inversions, flattening, and steepening do not occur only in 2s-10s. 

The below example shows how a dashboard can support greater understanding in a small format. The graph displays the most recent yield curve in the darkest color and fades as it goes further back in time. This allows one to see changes in the entire curve across time. With the greater amount of data, one can research narratives behind curve movements with more information at the outset. 

Here, we see a large amount of movement in the middle of the curve relative to movement at higher durations. At 2, 3, and 5 years, yields shifted direction dramatically twice. Interested parties can immediately look for primary or secondary market activity to find any causes that might provide insight.

![Rolling Yield Curve](/Images/indi_yields.png)

## Towards Indicator Narratives

### A Typical Indicator Dashboard Gauge

Other economic indicators converted from line plots to smaller formats provide the latest observation with perhaps some context. The Consumer Price Index (CPI) is an extremely important data point for decision makers, but its movements can be obscured by simplicity. The below gauge includes the latest observation in red and the one standard deviation band around the mean year-over-year index change. This gives some context, but very little.

![CPI Gauge](/Images/indi_cpi.png)

### Enhancing Indicator Dashboard Gauges

As with the yield curve, changes over time provide information that can suggest or disprove narratives quickly. Python can easily combine the time element of line plots with a gauge in a manner shown below. The gauge includes the same information but adds the most recent observations in a easily understood visual format. 

Above, the latest observation provided some information. Change in the CPI tended to be elevated relative to recent history. Here, we can see that the change is elevated, has remained elevated recently, and the change has increased significantly. Now the YoY change is above the US Federal Reserve's target of 2%, and the trend is increasing. That additional information provided by a gashboard gauge affect the narrative behind research and decisions greatly.

![Rolling CPI Gauge](/Images/indi_cpi_enhanced.png)

# Visualizing Absolute Returns

## Histograms

Absolute returns, often represented with a single number, should always have some context. A single number tells very little. A visual distribution of returns reveals skewness and kurtosis quickly, and everyone in the industry needs frequent reminders that assuming a normal distribution is a questional proposition at best.

Unfortunately, representing distributions is often delegated to a histogram. Python can generate this easily, as below, but can do so much more.

![Histograms](/Images/abs_hists.png)

## Towards Narratives with Absolute Returns

### Enhancing Histograms with Violin Plots

Violin plots from the Seaborn library are easily constructed and visualize return distributions using Kernel Density Estimators. A dataset of currency returns in USD is represented below. The plot combines the KDEs of violin plots with "swarm plots," which stack points on the graph to represent observation clustering. In addition, the red dot on each axis represents the latest observation.

This plot conveys an enormous amount of information. The latest value is provided for each currency, but the historical distributions overlayed show how often that value occurs. In addition, it is striking how non-normal these distributions are. Leptokurtotic may be a term easily forgotten after basic statistics, but the plots below help drive home how common it is. Major market moves grab headlines and public attention, but how do we define "major"? That matters a great deal for decision makers. 

![Violin Plots](/Images/abs_violin.png)

### The Humble Z-Score as Storyteller

We can easily add one more datapoint to enhance violin plots further. A z-score adds additional context to an observation by communicating how far it is from the mean. This deepens the amount of information communicated because even a distribution cannot tell the entire story.

Below, the recent moves in NZD and AUD seem to be more significant because they lie further from the large clusters around what appear to be means. Without a z-score, it might be assumed that these are major market moves. However, the move in HKD, though closer to its historical mean, might have a much more interesting story. The z-score on this plot, emphasized by color deepening, stands out. A practitioner without this information might miss a narrative formed or forming with HKD in this case.

![Violin Plots with Z-Scores](/Images/abs_violinz1.png)

The below plot includes data from market indicies representing four asset classes - the S&P 500 Index for US equity, the MSCI ACWI ex-US Index for non-US equity, the Bloomberg Barclays US Aggregate Index for US fixed income, and the S&P GSCI Commodity Index for commodities. 

Again, this plot emphasizes the power and importance of context. A persistent bull market does not change a negatively skewed history. Further, leptokurtotis in asset class return distributions is often forgotten. And even though the absolute returns on other asset classes look farther from the mean, the added z-score on this plot shows that the movement on the US Aggregate might be much more interesting. All of this, communicated succinctly, can tune, encourage, or even form narratives for decision makers.

![Violin Plots with Z-Scores](/Images/abs_violinz2.png)

# Visualizing Relative Returns

## Growth of Dollar Amount

Comparing investment opportunities involves comparing ex-post performance, and many visualizations use that amount to compare performance across. Fortunately, Python allows for easy construction of this. The below visualization involves an hypothetical $10,000 exchanged for various currencies and the performance of that exchange over time.

![Growth of 10K](/Images/rel_g10k.png)

## Periodic Table of Returns

The growth of a dollar amount often emphasizes the final amount. This was deliberately excluded from the above visualization - exactly how much information does the chart inform the viewer? The intervening periods have a lot of noise and are very difficult to compare, especially with the large amount of data.

Separating the time period into discrete periods helps alleviate this. The below table separates the time period into calendar years and ranks the returns of each currency for the year. Maintaining colors for each currency helps the viewer track the rank of each currency across time. A dashboard can even keep the line plot if deemed appropriate.

![Periodic Table](/Images/rel_periodic.png)

## Visual Cues as Narrative Clues

Perhaps the most compelling use of effective visualizations for relative return comparisons is colormaps. Python and third-party library allow for deployment of pre-built or custom colormaps with ease. This enables a wide range of comparison across investments or asset classes. The below vertical bar graph uses a custom colormap with more intense colors for higher moves, cueing the viewer to significant moves in returns.

![Vertical Bar](/Images/rel_vertical_bar.png)

# Conclusion and Further Steps

Decision makers should no longer be content with sub-par visualizations and data dashboards. Balancing data with storytelling enables more effective, data-driven decisons. This analysis proposes ideas that combine statistics and plotting for achieving that balance. As narratives rise in importance, effective data communication has to rise in importance, as well. 

The possibilities of Python visualizations extend further than this analysis suggests. Additional work would include interactive widgets and tools, such as Plotly and Bokeh. Increasing the amount of data and datasets would also allow for experimenting with visualizations appropriate for other areas, such as yield spreads and premiums, contango and backwardation analysis, and portfolio optimization.

## Data Sources

* Federal Reserve Bank of St. Louis' FRED
* Quandl API
* AlphaAdvantage API
* Morningstar
* MSCI
* S&P Dow Jones Indices