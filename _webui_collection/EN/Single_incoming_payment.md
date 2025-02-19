---
title: How do I post a payment against a single invoice?
layout: default
tags:
  - Accounting
  - Receivables and Payables
  - Incoming Payments (Accounts Receivable)
lang: en
sequence: 10
ref: single_incoming_payment
---

## Overview
After receiving a payment, you can enter the amount as an *Incoming Payment* in metasfresh, whereby the associated invoice will automatically receive the status *Paid*. To do so, please proceed as follows:

## Requirements
- Make sure to have an outstanding [invoice](Invoice_SalesOrder).

## Steps
1. Open "Payment" from the [menu](Menu).
1. [Add a new payment entry](New_Record_Window).
1. In the field **Business Partner**, enter a part of the [business partner](New_Business_Partner) name or number and click on the matching result in the <a href="Keyboard_shortcuts_reference#dropdown" title="Dynamic Search Box (Autocompletion)">drop-down list</a>.
1. Select the **Document Type** *Incoming Payment*.
1. Enter the **Invoice** for which you have received the payment.
 >**Note:** Hit [`SPACE`](Keyboard_shortcuts_reference) to see a selection of available outstanding invoices of the business partner.

1. The **Payment amount** and the **Currency** are taken over automatically from the invoice, but can also be changed manually if required.
1. [Complete the document](DocumentProcessingComplete).
1. [Jump into the field](Jumpto) **Invoice** to review the invoice status, ***or alternatively***, go to the record tab "Allocations" and [zoom into](Zoom_into_table_field) the field in the column **Invoice** of the allocation line.

## Next Steps (optional)
- [Manually allocate a single payment to multiple invoices](Incoming_payments_manual_allocation).

## Example
<kbd><img src="assets/single_incoming_payment.gif" alt="GIF: Single incoming payment"></kbd>
