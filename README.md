# Marketing-Budget-Optimization-using-Mixed-Integer-Programming

This project details the process of optimizing a marketing budget, starting with an initial budget of $10 million to be allocated across 10 different platforms (Print, TV, social media, etc.) to maximize the total Return on Investment (ROI).

The problem evolves through several stages of increasing complexity:

## 1. Initial LP Model (Concave ROI)

The project first assumes a non-increasing (concave) ROI, where the return diminishes as the investment in a platform increases. This is modeled as a straightforward Linear Program (LP) with a total budget cap, per-platform spending limits, and specific allocation rules between platform groups.

## 2. MIP Model (Non-Concave ROI)

The problem is then updated with a new ROI dataset that is not non-increasing. This non-concave return function breaks the LP model, as it might incorrectly skip investment tiers. To solve this, the model is reformulated as a Mixed-Integer Program (MIP) using Special Ordered Sets (SOS2) to correctly model the tiered returns.

## 3. Minimum Investment Constraint

A real-world constraint is added. For each platform, the company must either invest $0 or invest at least a specified minimum amount. This "all-or-nothing" rule is incorporated into the MIP using binary (on/off) variables for each platform.

## 4. Multi-Period Dynamic Budget

The model is expanded to a 12-month planning horizon. The budget becomes dynamic: an initial $10M budget is increased each month by 50% of the return generated in the previous month. This is solved by running 12 consecutive MIPs, with the output of one month feeding into the budget for the next.

## 5. Stability Constraint (Modeling Concept)

Finally, the concept of a "stable" budget is introduced, defined as an allocation where the spending for any single platform does not change by more than $1M from one month to the next. This report identifies that the dynamic solution is not stable and outlines the modeling approach required to enforce stability: solving a single, large-scale MIP for the entire year, with new constraints linking the spending decisions of consecutive months.
