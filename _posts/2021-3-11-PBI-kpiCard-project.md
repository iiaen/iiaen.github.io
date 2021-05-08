---
layout: post
title: Building your own custom viz for Power BI with pbiviz
categories: [Projects, Power BI, TypeScript, JavaScript]
excerpt: KPIs or BANs are the most important elements of any dashboard, what can you do when the default KPI viz in Power BI does not meet your requirements?
---

The **KPIs** or **BANs** are the most important elements of any dashboard. [[Source]](https://www.tableau.com/about/blog/2017/6/eye-tracking-study-5-key-learnings-data-designers-everywhere-72395)  

However just providing a BAN (Big-Ass-Number) without any other comparisons or benchmarks will only be of limited use. For example the `monthly sales KPI` might include any combination of the following: 
1. benchmark against previous period
2. benchmark against budgeted sales
3. YTD sales if there are no separate card or tile
4. for single same-store sales analysis, the mean or median sales of comparable stores to check if selected store is above or below average  

But building an entire row of KPIs with all of their corresponding benchmarks is quite a hassle in Power BI so I was intrigued when I came across this [tutorial](https://docs.microsoft.com/en-us/power-bi/developer/visuals/develop-circle-card). A custom viz would mean that creating and managing these KPIs would be easier! No more grouping elements together, setting up conditional formatting a dozen of times, resizing and moving tons of elements around whenever there is a change in layout or user requirements.  

This was my first foray into TypeScript/JavaScript, and this is a rough draft of the design specifications:
- the 'KPI Card' will be made up of two rows, with the BAN on top and the benchmarks on the bottom row
- can accept 1 to 3 benchmarks
- the text colour of the benchmarks will have to be conditionally formatted
- the benchmarks will each have their own prefixes. I usually use unicode symbols `e.g. 📅` but also will use text from time to time `e.g. PM` (abbreviation for Previous Month) 
 
<p>&nbsp;</p>
This is how the end product looks like, `visualization fields pane` looks like that:  
![Alt text](https://raw.githubusercontent.com/iiaen/iiaen.github.io/master/images/post_images/PBI-kpiCard-fields.png "Visualization Fields")  
The main BAN measure field goes in the `measure data` section while the benchmarks can go into the `Comparison 1`,  `Comparison 2` and `Comparison 3` sections. I haven't figured out how to hide the 'Category Data' yet. 
  
<p>&nbsp;</p>
The `formatting pane` looks like this, with font size controls and options for colour coding and number formatting:  
![Alt text](https://raw.githubusercontent.com/iiaen/iiaen.github.io/master/images/post_images/PBI-kpiCard-gif.gif "Formatting Pane")  
  
<p>&nbsp;</p>
Here are a few cards that were made with the custom viz:  
![Alt text](https://raw.githubusercontent.com/iiaen/iiaen.github.io/master/images/post_images/PBI-kpiCard-sample.png "Samples")

<p>&nbsp;</p>
There are a few improvements that I would like to add to the next version of this mini project including features like font family selection but that's it for now! Thanks for reading!
