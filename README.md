# Inventory Reporting & Stock Reconciliation Case Study

![Power BI Dashboard](Inventory%20Reporting.png)

## Overview

This project explores inventory reporting, stock reconciliation, and reporting confidence within an ERP-style operational environment.

The case study was built around a synthetic inventory dataset containing 24 SKUs and was designed to examine a common operational reporting problem:

> What happens when the system says one thing and the operation says another?

At headline level, the stock position appeared reassuring.

System available stock and operationally available stock were almost identical.

However, once the analysis moved below the total level, 16 of the 24 reviewed SKUs showed a difference.

The project therefore developed from a simple stock-reporting exercise into an investigation of:

* system stock,
* operationally available stock,
* quarantined stock,
* unposted receipts,
* unposted production issues,
* physical stock counts,
* Unit of Measure,
* transaction timing,
* and stock-control process.

The analysis demonstrates a practical business intelligence workflow:

Inventory dataset → Power BI analysis → exception testing → root-cause investigation → operational recommendations

The project is designed as a portfolio case study suitable for:

* SME inventory and warehouse environments,
* ERP / SAP-style reporting demonstrations,
* stock reconciliation analysis,
* operational reporting and decision support,
* Power BI portfolio work,
* finance / operations control discussions,
* and stock-process improvement conversations.

---

# The Problem

Headline stock totals can appear correct while individual products still contain material differences.

The initial review covered 24 SKUs.

At total level:

* System On Hand: approximately 3.7K units
* System Available: approximately 2.1K units
* Operationally Available: approximately 2.1K units
* Net difference between system and operational availability: 9 units

On the surface, the position looked reasonable.

However:

* 16 of the 24 SKUs showed an individual difference;
* the largest positive difference was 40 units;
* the largest negative difference was 30 units.

This raised a more useful business question:

> If the total looks right, can the stock still be trusted at product level?

The analysis therefore moved away from simply checking whether the grand total reconciled.

Instead, it focused on understanding why individual products differed and whether those differences were expected, explainable, or required further investigation.

---

# The Approach

The analysis was deliberately completed in stages.

This reflects how stock discrepancies should normally be investigated in practice: test the most likely explanation first, then follow the exceptions that remain.

## Stage 1: Compare System and Operational Availability

The first stage compared:

* System On Hand
* System Available
* Operationally Available
* Quarantined Quantity

System Available was defined as:

> Stock On Hand minus stock allocated to open orders

Operationally Available stock also considered stock that could not currently be used operationally, including quarantined stock.

The initial comparison showed that although the total position looked close, 16 SKUs did not reconcile individually.

This established the first reporting-confidence issue.

---

## Stage 2: Test the Most Likely Explanations

The next step was to test the obvious explanations before assuming the data was wrong.

For negative differences, quarantined stock was reviewed.

A negative difference should normally be explainable where stock exists in the system but is not operationally available because it has been quarantined.

Of the 13 negative differences identified:

* 7 reconciled exactly to quarantined stock;
* 6 remained unexplained.

For positive differences, unposted receipts were reviewed.

Of the 7 positive differences:

* 6 were explained by unposted receipts;
* one remained unexplained.

At this stage:

* 16 differences had originally been identified;
* 9 were explained by expected business conditions;
* 7 required further investigation.

---

## Stage 3: Investigate the Remaining Exceptions

The remaining seven exceptions were then traced back through the operational process.

The analysis reviewed:

* timing of the stock count;
* warehouse issues and receipts;
* production stock movements;
* physical count records;
* counting sheets;
* Unit of Measure;
* and physical recounts.

Four of the remaining differences were explained by production stock that had already been issued operationally but had not yet been posted in the system.

The remaining three required physical-count investigation.

This identified:

* one Unit of Measure / counting interpretation issue;
* one physical count surplus;
* one physical count shortage.

At this point, the remaining seven exceptions had been explained.

---

# The Solution

The Power BI report was designed to support a staged investigation rather than simply present stock totals.

The reporting structure moved through four questions:

1. Does the headline position look reasonable?
2. Which individual SKUs do not reconcile?
3. Can the obvious business conditions explain the difference?
4. What caused the remaining exceptions?

This approach separates normal operational differences from exceptions that genuinely require investigation.

The analysis therefore demonstrates that reporting confidence depends on more than calculation accuracy.

It also depends on the processes that create the data.

---

# Dashboard Highlights

## Headline Inventory View

The first dashboard view shows:

* System On Hand
* System Available
* Operationally Available
* Largest Positive Difference
* Largest Negative Difference
* Number of SKUs Reviewed
* Number of SKUs with a Difference

The important finding was:

> The total position looked reasonable, but two-thirds of the reviewed SKUs contained an individual difference.

This is a useful example of why aggregate accuracy does not always create operational confidence.

---

## Stock Difference Investigation

The next stage compares individual SKU differences against:

* quarantined quantity;
* unposted receipts;
* and expected operational behaviour.

This separates expected differences from unexplained exceptions.

The first investigation reduced the exception population from 16 SKUs to seven.

---

## Exception Investigation

The final investigation follows the remaining differences into the underlying process.

The identified causes included:

* production issues not yet posted;
* physical count shortages;
* physical count surplus;
* Unit of Measure / counting interpretation.

The exception values were also compared with the value of the affected stock.

For the investigated items, the exception impact ranged from approximately:

* 3.85%
* to 13.33%

of the affected stock value.

This showed that although the remaining exceptions were small in number, their impact was not necessarily insignificant.

---

# Key Findings

## 1. Aggregate Accuracy Can Hide SKU-Level Problems

The net difference across the sample was only 9 units.

That could easily create confidence in the overall stock position.

However, 16 of the 24 reviewed SKUs showed an individual difference.

The total therefore concealed a much less consistent product-level picture.

---

## 2. Not Every Difference Is an Error

Many of the differences had reasonable operational explanations.

Quarantined stock explained several negative differences.

Unposted receipts explained most positive differences.

This is important because exception reporting should not treat every difference as evidence that something has gone wrong.

The useful work is separating:

* expected differences;
* timing differences;
* process exceptions;
* and genuine errors.

---

## 3. Transaction Timing Matters

Four of the remaining exceptions were caused by production stock that had already been issued operationally but had not yet been posted into the system.

This means the system and the warehouse were effectively describing different points in time.

The reporting issue was therefore not simply calculation accuracy.

It was also transaction timing.

---

## 4. Physical Count Controls Matter

The investigation also identified physical-count issues.

A recount confirmed that some of the original stock-count results were incorrect.

This demonstrates that reporting accuracy begins before the data reaches Power BI.

If the physical process is unreliable, the dashboard can only report that uncertainty more neatly.

---

## 5. Unit of Measure Can Change the Meaning of a Count

One investigated item showed a Unit of Measure issue.

The system stored the item using `each` as the standard Unit of Measure, while the count sheet recorded packs containing several individual items.

The quantity recorded was therefore technically understandable but operationally inconsistent with the system definition.

This reinforces the importance of clear Unit of Measure information during stock counts.

---

# Operational Recommendations

The analysis led to several practical recommendations.

## 1. Review the Stock-Taking Process

Review the stock-count process from start to finish.

Particular attention should be given to:

* timing;
* transaction posting;
* stock movement during the count;
* count-sheet design;
* Unit of Measure;
* verification;
* system entry;
* and reconciliation.

---

## 2. Control Stock Movement During Counts

Where operationally practical, stock movements should be temporarily frozen while a physical count is taking place.

If stock continues to move while counting is underway, the system and physical count may represent different points in time.

If a full stock freeze is not practical, movements during the count should be tightly controlled and documented.

---

## 3. Complete Transactions Before Counting

Receipts, issues and transfers should be posted before the stock count begins wherever possible.

This reduces the risk of the physical stock position and ERP stock position becoming misaligned because of unposted transactions.

---

## 4. Standardise Count Sheets

Count sheets should use a clear and consistent format.

At minimum they should show:

* SKU;
* location;
* product description where useful;
* Unit of Measure;
* and count entry fields.

Consider hiding the expected system quantity during the physical count.

This can help reduce the risk that the expected quantity influences the physical count.

---

## 5. Use Independent Verification Where Appropriate

Not every item needs to be counted twice.

However, independent verification should be considered where the:

* stock value is high;
* operational risk is high;
* item has a history of discrepancies;
* or the count result appears unusual.

This could include a second counter or an independent recount.

---

## 6. Enter and Reconcile Counts Promptly

Physical count results should be entered into the system as soon as practical after counting.

Discrepancies should then be reviewed before normal stock movement resumes.

Long delays between:

* counting;
* system entry;
* posting;
* and reconciliation

increase the opportunity for timing differences and uncertainty.

---

## 7. Consider More Frequent Cycle Counts

Higher-value or repeatedly problematic items may benefit from more frequent cycle counting rather than relying only on periodic full stock takes.

This allows recurring exceptions to be identified and investigated earlier.

---

# What the Analysis Tells Us

The analysis started with a reporting difference.

The investigation showed that the causes came from several different parts of the process:

* expected stock conditions;
* posting delays;
* transaction timing;
* physical counting;
* and Unit of Measure.

The main conclusion is therefore not simply that the stock numbers contained differences.

It is that reporting confidence depends on the quality of the operational process that produces those numbers.

> A technically correct report cannot remove uncertainty created earlier in the process.

The next piece of work would not necessarily be another dashboard.

It would be to reduce the number of opportunities for those differences to arise in the first place.

---

# Data Limitations

This case study uses a synthetic inventory dataset created for analytical and portfolio purposes.

It is intended to demonstrate a realistic stock-reporting and reconciliation process rather than represent a live company or ERP database.

The analysis therefore does not prove:

* the performance of a real warehouse;
* financial loss;
* control failure within a real organisation;
* or stock accuracy within a specific ERP implementation.

The dataset was designed to contain realistic operational scenarios including:

* quarantined stock;
* unposted receipts;
* unposted production issues;
* allocations;
* physical-count differences;
* and Unit of Measure issues.

The value of the case study is in the analytical method:

> identify the difference → test the expected explanation → investigate the exceptions → recommend practical controls

---

# Demo

The repository includes or can include:

* inventory source dataset
* Power BI report
* Power BI dashboard screenshots
* completed case study PDF
* dataset documentation
* DAX calculations
* and operational recommendations

Suggested walkthrough order:

1. Review the source dataset
2. Review the inventory definitions
3. Open the Power BI report
4. Review the headline inventory page
5. Review the SKU-level differences
6. Review the quarantine and receipt reconciliation
7. Review the remaining exception investigation
8. Read the completed case study PDF
9. Review the operational recommendations

---

# How to Run

## Requirements

* Power BI Desktop
* CSV or Excel version of the inventory dataset

## Steps

1. Download or clone the repository

```bash
git clone <repository-url>
