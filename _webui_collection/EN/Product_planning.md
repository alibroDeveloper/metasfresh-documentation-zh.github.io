---
title: How do I set up product planning?
layout: default
tags:
  - Materials Management
  - Material Schedule
lang: en
sequence: 10
ref: product_planning
---

## Overview
Product planning is used to define what should happen automatically when an order is placed for a product whose inventory level is running low. A product can be a single finished product or consist of several components (see also: [Bill of Materials](Create_BOM)). In the event that the demand for the product or the individual components cannot be covered (completely), the product planning data specify whether new goods are to be **purchased** or **manufactured** in order to replenish the stocks and cover the demand. The [*Handling Unit Editor*](Menu) window provides you with an overview of the products in stock.

In addition, metasfresh's [*material schedule*](Material_schedule_basics) uses the product planning data to automatically monitor which products are in stock, have to be purchased or manufactured and then also automatically creates purchase orders or manufacturing orders.

## Requirements
- [Add a product](NewProduct) whose planning data you want to configure.

## Steps

### Configure Planning Data
1. Open "Product Planning" from the [menu](Menu).
1. [Create a new planning data entry](New_Record_Window).
1. In the field **Product**, enter a part of the [product](NewProduct) name or number and click on the matching result in the <a href="Keyboard_shortcuts_reference#dropdown" title="Dynamic Search Box (Autocompletion)">drop-down list</a>.
1. Pick a [**Warehouse**](Add_new_warehouse) where the product is kept in store.

#### a) For Purchasing
1. Tick the checkbox **Create Plan** if the product should be monitored by the material schedule and purchase orders be created automatically.
1. Set the field **Purchased** to *Yes*.
1. [metasfresh saves the progress automatically](Saveindicator).

#### b) For Manufacturing
1. Pick a [**BOM & Formula**](Create_BOM).
1. Pick a **Workflow**.
1. In the field **Resource**, pick a production resource.
1. Tick the checkbox **Create Plan** if the product and its BOM components should be monitored by the material schedule and manufacturing orders be created automatically.
1. Tick the checkbox **Complete Document** if the manufacturing order should be completed automatically.
1. Set the field **Manufactured** to *Yes*.
1. ***Optional:*** Enter a **Max. quantity per manufacturing order**, e.g., to ensure the traceability of certain manufacturing components.
 >**Note:** If the field remains empty or contains a value &#8924; 0, there is no limit on quantity.

1. [metasfresh saves the progress automatically](Saveindicator).

    | **Note:** |
    | :--- |
    | When completing a [sales order](SalesOrder_recording) for a product that is configured for manufacturing using planning data, a [manufacturing order](NewManufacturingOrder) is automatically created to meet demand and linked to the sales order. |

## Next Steps (optional)
- [Create automatic order checkup documents for controlled order processing](Automatic_order_checkup).
