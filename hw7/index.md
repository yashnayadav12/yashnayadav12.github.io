---
layout: page
title: "Exploring Professional Licenses in Illinois"
permalink: /hw7/
---


For this assignment, I used an Illinois professional licensing dataset to look at which types of licenses appear most often and how their statuses compare. I created two charts using Python, Pandas, and Altair.

[**The Data**](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/licenses_fall2022.csv) | [**The Analysis**](https://github.com/yashnayadav12/yashnayadav12.github.io/blob/main/python_notebooks/IS445_Altair_Homework.ipynb)

## Plot 1: Which types of licenses appear most often?

<div id="vis1" style="max-width:100%;overflow-x:auto;"></div>

For my first chart, I wanted to see which professional license categories appeared most often in the dataset. I made a horizontal bar chart because some of the license names are long, and this layout makes them easier to read and compare. The y-axis shows the license description, which is nominal (N), and the x-axis shows the number of records, which is quantitative (Q). I used the same blue color for every bar because color does not represent a separate variable here. In Python, I removed rows with missing descriptions or statuses, counted the records in each category, and selected the ten categories with the most records. These counts represent records in the dataset, not the total number of people working in each profession.

## Plot 2: How do license statuses compare?

<div id="vis2" style="max-width:100%;overflow-x:auto;"></div>

For my second chart, I wanted to compare license statuses across those same ten categories. I used a 100% stacked horizontal bar chart because the categories have different numbers of records, and percentages make the comparisons easier. The y-axis shows the license category (nominal, N), the x-axis shows the percentage of records (quantitative, Q), and the colors represent license status (nominal, N). I chose blue for Active, gold for Not renewed, and gray for Other to make the different groups easy to distinguish. In Python, I cleaned the status labels, grouped less common statuses into Other, and counted how many records belonged to each status group within each license category.

## Interactivity

I added a clickable legend to the second chart so viewers can focus on one status at a time. For example, clicking Active highlights that status and fades the other groups. I can also Shift-click to highlight multiple statuses. I think this makes the chart easier to explore because it lets viewers compare specific statuses without losing the overall picture.

<script src="https://cdn.jsdelivr.net/npm/vega@6"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@6"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@7"></script>

<script>
  vegaEmbed('#vis1', '{{ "/assets/plots/chart1.json" | relative_url }}', {actions: false})
    .catch(error => {
      console.error(error);
      document.querySelector('#vis1').textContent = 'Chart 1 could not load.';
    });

  vegaEmbed('#vis2', '{{ "/assets/plots/chart2.json" | relative_url }}', {actions: false})
    .catch(error => {
      console.error(error);
      document.querySelector('#vis2').textContent = 'Chart 2 could not load.';
    });
</script>
