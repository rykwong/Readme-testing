# How to use the Sankey plugin

![](RackMultipart20220811-1-tgekad_html_df0352d5d5edb19c.png)

## Introduction

Sankey visualizations are traditionally used when you want to show process flow. For example, you want to see how users are transitioning through a web site – "what page do they visit most before clicking checkout?". Or, you want to know how prospects are moving through a sales process – "where are we getting stuck?" or "what role are we meeting with that most often leads to advancing the sales stage?".

Sankeys are also good at showing contributions. For example "which product lines are the major contributor of sales for the West region?" And, "for each of the product lines, which age range demographic buys them the most?" Product line, region, and demographics are all connected, much like a process flow, which makes Sankey a good visualization choice.

## Instructions

1.
### Starting point to build a Sankey – Raw Table

We start with a table that has no groupings. Group by as many columns as you like. Each grouping becomes a Sankey column.

![](RackMultipart20220811-1-tgekad_html_5aa3cdcae3cdd44d.png)

Recommended: 3-5 groupings is ideal.

A grouped column should have low cardinality, between 2 and 15 unique values. Use "Column Details" to check uniqueness.

Potential grouping columns boxed in orange.

Potential measure boxed in red. Pick one measure.

1.
### Grouped Columns map to Sankey columns (nodes)

In this example, the Sigma table has 5 groupings (orange boxes) and 4 grouping calculations (red boxes). The top level grouping (product type) doesn't have a calculation.

![](RackMultipart20220811-1-tgekad_html_4b78437720736441.png)

Each grouping maps to a Sankey column, indicated by arrows. A column is made up of nodes (e.g. Arts & Entertainment). Nodes in one column are connected to nodes in another column using edges (lines). The edge thickness and value is determined by the aggregate on the "to" (right) side of the edge pair.

Note, only sum() is supported for the value columns. In this example, the formula for each of the calculated columns is "sum(revenue)".

1.
### Setting the Sankey plugin properties

Grouping columns (orange boxes) go into "DIMENSION"

Grouping calculations (red boxes) go into "MEASURES"

Notes:

- The ordering is very important.
- The first column (PRODUCT TYPE in this example) does not have a corresponding calculation.
- There will always be one fewer measure. E.g. if you have 5 dimensions, there will be 4 measures (n-1).

![](RackMultipart20220811-1-tgekad_html_df0d695f48e5e516.png)

1.
### Group Aggregates map to Sankey lines (edges)

This example shows the edge connecting nodes "Arts & Entertainment" (left) → "18-35" (right). The aggregate on the right for "18-35" ("Age Group Revenue") is used to determine the thickness of the line.

1.
### Sankey edges automatically aggregate multiple values for like pairs ![](RackMultipart20220811-1-tgekad_html_8e4d3f33089bea72.png)

As we get deeper into the grouping hierarchy (groupings to the right), we see repeating pairs.

For example, "18-35 → Cash" exists multiple times, once for each product type. These are automatically aggregated into a single edge for readability.

The boxed values for Purch Method Revenue are aggregated into a single edge.

![](RackMultipart20220811-1-tgekad_html_873f8c8ebefd2fcd.png)

## Plugin Details

Source Code: [https://github.com/ja2z/sankey.git](https://github.com/ja2z/sankey.git)

Plugin URL: [https://sigma-sankey-ja2z.netlify.app/](https://sigma-sankey-ja2z.netlify.app/)

Registering the plugin in Sigma:

![](RackMultipart20220811-1-tgekad_html_ac74106be3817d89.png)
