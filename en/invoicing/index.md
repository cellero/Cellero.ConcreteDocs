# Overview
The invoicing process involves reviewing completed orders, normally from the previous day.  
Completed orders have a **Pending Invoice** status.

If the order transactions look correct, the order is approved for processing.  
Order transactions can also be updated if required before approving.

Alternatively, the order can be placed on **Hold** if further investigations are needed.

Once the review process is complete and the required invoices have been approved, the approved invoices can be selected and an **Invoice Batch** is created.

Initially, invoice batches have a **New** status, allowing for a final review and checks before exporting to the Accounting system.

Once exported, the invoice batch has a status of **Fully Processed**.

# Stages
- [Invoice Review](invoice-review.md)
- [Invoice Batches](invoice-batches.md)
- [Exceptions](invoice-exceptions.md)
- [Accounting Periods](invoice-accounting-periods.md)


```mermaid
flowchart TD
    A[Completed Orders (Pending Invoice Status)] --> B{Review Order Transactions}
    B -->|Approve| C[Approved for Invoicing]
    B -->|Update| B
    B -->|Hold| D[Set to Hold Status]

    C --> E[Select Approved Orders]
    E --> F[Create Invoice Batch]
    F --> G{Invoice Batch Status}
    G -->|New| H[Final Review and Checks]
    H --> I{Exceptions?}

    I -->|Yes| J[Manage Exceptions]
    J --> H

    I -->|No| K[Export to Accounting System]
    K --> L[Status: Fully Processed]
    L --> M[Assign to Accounting Period]



 