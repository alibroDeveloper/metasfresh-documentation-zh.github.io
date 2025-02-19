---
title: How do I specify the commission conditions?
layout: default
tags:
  - Contract Management
  - Commission Contracts
  - Setup
lang: en
sequence: 10
ref: commission_conditons_details
---

## Overview
In the commission conditions, you can determine the commission percentage to be deducted from the basis points (line amount in the sales order), and for which business partner group and/or product category commission is to be granted. In the case of <a href="Add_new_sales_partner#sp-hierarchy" title="Subordinate sales partners">sales partner hierarchies</a>, you can also specify whether the commission for each sales partner shall either be calculated based on the full basis points number or be obtained gradually by subtracting the percentage of the respective lower-level sales partner's commission points from the basis points.

## Requirements
- [Specify the commission amount using commission points in a so-called "commission product"](Commission_points_price).

## Steps
1. Open "Hierarchy commission settings" from the [menu](Menu).
1. [Create a new entry](New_Record_Window).
1. Give the settings entry a **Name**.
1. Tick the checkbox **Subtract commission from base**.
 >**Note:** In the case of sales partner hierarchies, the commission points of the higher levels are determined based on the difference between the (gradually reduced) basis points number and the percentage of the commission points of the respective lower levels.

1. The field **Points precision** specifies the number of decimal places to which commission points are rounded when calculated by the system.
1. In the field **Commission product**, enter a part of the name or number of the [product (e.g., *commission point*) used to specify the unit in which commission points are to be managed and settled](Commission_points_price) and click on the matching result in the <a href="Keyboard_shortcuts_reference#dropdown" title="Dynamic Search Box (Autocompletion)">drop-down list</a>.

### Commission percentage and further details
1. Go to the record tab "Settings detail" at the bottom of the page and click !["Add new"](assets/Add_New_Button.png). An overlay window opens up.
1. In the field **SeqNo**, enter a sequence number for commission details.
 >**Note:** The lower the sequence number of a line, the higher its precedence in the presence of similar commission details.

1. ***Optional:*** Select a **Business Partner Group** for which the commission shall be granted. To do so, enter a part of the name of the [business partner group](New_Business_Partner_Group) into the field and click on the matching result in the <a href="Keyboard_shortcuts_reference#dropdown" title="Dynamic Search Box (Autocompletion)">drop-down list</a>.
1. ***Optional:*** Select a **Product Category** for which the commission shall be granted. To do so, enter a part of the name of the [product category](NewProductCategory) into the field and click on the matching result in the <a href="Keyboard_shortcuts_reference#dropdown" title="Dynamic Search Box (Autocompletion)">drop-down list</a>.
 >**Note:** If neither a business partner group nor a product category is specified, the commission details are applied in general.

1. In the field **% of base points**, enter the percentage to be deducted from the basis points number (line amount in the sales order) for the commission.
1. Click "Done" to close the overlay window and add the commission details to the list.

## Next Steps
1. [Specify the contractual terms for commission contracts](Define_contractual_terms_commission).
1. [Create a commission contract for the sales partner](Create_commission_contract).
