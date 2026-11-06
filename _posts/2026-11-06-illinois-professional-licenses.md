---
layout: post
title: "Exploring Professional Licenses in Illinois"
date: 2026-11-06
permalink: /hw7/
---

# Exploring Professional Licenses in Illinois

For this assignment, I used an Illinois professional licensing dataset to look at which license categories show up most often and how their statuses compare. I made both charts in Python using Pandas and Altair.

[**The Data**](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/licenses_fall2022.csv) | [**The Analysis**](https://github.com/yashnayadav12/yashnayadav12.github.io/blob/main/python_notebooks/IS445_Altair_Homework.ipynb)

## Plot 1: Which types of licenses appear most often?

<div id="vis1" style="max-width:100%;overflow-x:auto;"></div>

For my first chart, I wanted to see which professional license categories appeared most often in the dataset. I made a horizontal bar chart because some of the license names are long, and this layout makes the categories easier to read and compare. The y-axis shows the license description, which is **nominal (N)**, and the x-axis shows the number of records, which is **quantitative (Q)**. I used the same blue color for every bar instead of a color scheme because color does not represent a separate variable in this chart. In my Python notebook, I removed rows with missing descriptions or statuses, counted the records in each category, and kept the ten categories with the most records. These are counts from the dataset, not the total number of people working in each profession in Illinois.

## Plot 2: How do license statuses compare?

<div id="vis2" style="max-width:100%;overflow-x:auto;"></div>

For my second chart, I wanted to compare the license statuses within those same ten categories. I used a **100% stacked horizontal bar chart** so that categories with different numbers of records could still be compared by percentage. The y-axis is the license description (**nominal, N**), the x-axis is the share of records (**quantitative, Q**, normalized to 100%), and the colors represent the license status group (**nominal, N**). I chose blue for **Active**, gold for **Not renewed**, and gray for **Other** so the groups would be easy to distinguish. In Python, I cleaned the original status labels, grouped the less common statuses into **Other**, and counted records for each status within each license category. These statuses describe license records, not whether someone currently has a job.

**Interactivity:** I added a clickable legend to the second chart. When I click **Active**, **Not renewed**, or **Other**, that status stands out while the other parts of the bars fade. I can also Shift-click to highlight more than one status. I think this makes the chart easier to explore because I can focus on one status across several categories without losing the overall comparison. This interaction goes beyond basic zooming or panning.

<script src="https://cdn.jsdelivr.net/npm/vega@6"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@6"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@7"></script>
<script>
  vegaEmbed('#vis1', '{{ "/assets/plots/chart1.json" | relative_url }}', {actions: false})
    .catch(error => { console.error(error); document.querySelector('#vis1').textContent = 'Chart 1 could not load.'; });
  vegaEmbed('#vis2', '{{ "/assets/plots/chart2.json" | relative_url }}', {actions: false})
    .catch(error => { console.error(error); document.querySelector('#vis2').textContent = 'Chart 2 could not load.'; });
</script>
