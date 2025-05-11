# Invoicing

## Overview
The invoicing process involves reviewing completed orders, normally from the previous day.  
Completed orders have a **Pending Invoice** status.

If the order transactions look correct, the order is approved for processing.  
Order transactions can also be updated if required before approving.

Alternatively, the order can be placed on **Hold** if further investigations are needed.

Once the review process is complete and the required invoices have been approved, the approved invoices can be selected and an **Invoice Batch** is created.

Initially, invoice batches have a **New** status, allowing for a final review and checks before exporting to the Accounting system.

Once exported, the invoice batch has a status of **Fully Processed**.

## Stages
- [Invoice Review](invoice-review.md)
- [Invoice Batches](invoice-batches.md)
- [Exceptions](invoice-exceptions.md)
- [Accounting Periods](invoice-accounting-periods.md)

  
````bash 
Completed Orders (Pending Invoice Status)
          |
          v
   Review Order Transactions
       /    |    \
Approve   Update   Hold
   |        |       |
   v        v       v
Approved Orders     Orders On Hold
          |
          v
Select Approved Orders
          |
          v
Create Invoice Batch
          |
          v
Invoice Batch (New Status)
          |
          v
Final Review and Checks
          |
          v
 Are there Exceptions?
    /          \
  Yes           No
  |              |
Manage         Export to
Exceptions     Accounting System
  |              |
  v              v
(Back to      Status: Fully
Final Review)  Processed
                   |
                   v
        Assign to Accounting Period

 ````