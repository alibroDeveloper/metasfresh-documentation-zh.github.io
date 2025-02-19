---
title: How do I specify the time frame conditions of a contract?
layout: default
tags:
  - Contract Management
  - Setup
lang: en
sequence: 20
ref: define_contract_period
---

## Overview
In metasfresh, time frame conditions of a contract include the term duration, term of notice, contract renewals, etc. All these conditions can be defined in the window "Contract Period".

## Steps

### Specify the conditions for the Contract Period
1. Open "Contract Period" from the [menu](Menu).
1. [Create a new entry](New_Record_Window).
1. Give the contract period a **Name**.
1. Pick a **Calendar**.
1. Define a **Term Duration** and a **Term Unit**, e.g., "1 Year".
1. Define a **Term of Notice** and a **Term of Notice Unit**, e.g., "1 Month".

#### Additional settings (optional)
1. Define a **Subscription Interval** and a **Subscription Unit**, e.g., "2 Weeks".
 >**Note:** This is the frequency of the shipments of a sales order during the contract period.

1. In the field **Extension Type**, pick the way to automatically extend a contract after it expires.
1. In the field **Next Contract Terms**, you can select the follow-up contract for the expired one.

### <a name="transition-conditions">Specify the Transition Conditions</a>
The transition conditions determine at what moment before the end or change of a contract the contractual party may perform a status change, such as the termination of the contract.

1. Go to the record tab "Transition Conditions" at the bottom of the page and click !["Add new"](assets/Add_New_Button.png). An overlay window opens up.
1. Define a **Deadline** and a **Deadline Unit**, e.g., "1 Month".
1. Pick the **Action** *Status Change*.
1. Pick the **Contract Status** *Terminated*.
1. Click "Done" to close the overlay window and add the transition conditions to the record tab.

### Complete the document
- [Complete the document](DocumentProcessingComplete).

## Example
<kbd><img src="assets/Define_contract_period.gif" alt="GIF: How to specify the time frame conditions of a contract"></kbd>
