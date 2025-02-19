---
title: How do I clone document data?
layout: default
tags:
  - A Beginner's Guide to metasfresh
  - Usage
  - Actions
lang: en
sequence: 40
ref: clone_record_window
---

## Overview
When creating a document with similar or identical data as in an existing document, you do not want to lose time by recording it all over again. Instead, to make things easier you can use the *cloning feature* to duplicate the entire existing document data of a window along with all associated subtabs.<br>
Cloning works for all master data and documents such as [sales orders](SalesOrder_recording), [purchase orders](CreatePurchaseOrder), [product prices](Clone_product_prices), etc.

## Steps
1. Use the [menu](Menu) to navigate to the document you want to clone (e.g., a [sales order](SalesOrder_recording)) and open it in the [detailed view](ViewModes#detailed-view).
1. Open the [actions menu](StartAction#actions-menu) ![](assets/actionsmenu_WebUI.png) and click "Clone".
1. The entire cloned document will open up in the same browser tab.
 >**Note 1:** Except for variable data, such as serial numbers or search keys (product numbers, document numbers, etc.), all data are duplicated unaltered.<br><br>
 >**Note 2:** Completed documents, such as sales orders, are cloned as drafts so they can be modified if necessary, and then have to be [completed manually](DocumentProcessingComplete) again.

## Example
![](assets/clone_record_window.gif)
