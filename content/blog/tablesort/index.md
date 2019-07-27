---
title: Table Sort
date: "2019-07-27T22:40:32.169Z"
description: Creating a Table with Sorting by Columns
---

## Wireframe

The purpose of this particular Table within the Alert page is to allow users to visualize, at a glance, how the entire organization is functioning with respect to various engagement drivers.

The intended user(s) are executive decision makers who will want all engagement related data in _one_ table. In other words, this table provides an "Executive Summary" of the data.

It shows _each_ driver's score for _each_ department with associated comparison data (i.e., company average, benchmark, last month, last year etc), the raw score and alerts for when there is notable discrepancy between the current scores and benchmark.

![Alert Table Wireframe](./alert_wire.png)

## Desired Goal

When this component is fully completed, the user should be able to both sort _and_ filter by individual columns. As a decision-maker, I could pull up data specific to any one department, one engagement variable, or sort by scores to see which department scored highest on what engagement variable.

However, for the MVP, i'm focused on only sorting on each column as the dataset will be limited. Filtering (and search) functionality will be especially useful with larger datasets.

## Library vs DIY

My initial thought was to use Material-UI's [table component](https://material-ui.com/components/tables/), particularly their ready-made sorting & selecting functionality built-in.

![Material UI Table](./materialui_table.png)

The trade-off, in my view, is less control and understandability. Importing the component wholesale would appear to save time upfront, but I quickly ran into issues when I wanted to add columns, and extend sorting functionality to the new columns.

While I could navigate my away around the _simple_ table component, once sorting and selecting was added, the code complexity increased to the point where I felt it was better to build a table from the ground up.
