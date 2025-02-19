---
title: How do I set up outbound documents for dunning?
layout: default
tags:
  - Accounting
  - Dunning
  - Setup
lang: en
sequence: 20
ref: outbound_documents_config_dunning
---

## Overview
You need to set up outbound documents for dunning so the created dunning letters will be listed under "Outbound Documents" in the menu where you can then continue to process them either one by one or collectively.

## Steps
[Follow these instructions](Outbound_Documents_Config) and pick the **Table** *Dunning type* and the **Print Format** *Mahnbrief (swat)*.
 >**Note:** Should the print format not be available, then [add a new one](Add_print_format) and use the **Table** *C_Dunning_Header_v* and the **Jasper Process** *Mahnbrief (Jasper)*.

## Example
![](assets/Outbound_documents_config+dunning.gif)
