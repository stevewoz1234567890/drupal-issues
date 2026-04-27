# **token** + **book** for **D12** — [#3586686](https://www.drupal.org/project/token/issues/3586686) (Slack)

**Context:** **berdir** @’d **smustgrave** about [Drupal 12 compatibility in **token**](https://www.drupal.org/project/token/issues/3586686). Now that [**book**](https://www.drupal.org/project/book) is a **contrib** module (no longer in **core** in the D12 line), book-related **token** definitions and tests that **lived in token** are the last major obstacle to **green** tests on D12 (per the thread). It is **unclear** whether those **tokens** still behave correctly on the **new** **book** major after **API** changes.  

## Proposal (thread)

- **Move** book-specific **token** code and tests from [**token**](https://www.drupal.org/project/token) into [**book**](https://www.drupal.org/project/book).  
- In **token**, add **version** **checks** so those definitions are **not** **double**-**registered** once **book** past a to-be-decided `x.y.z` ships the integration.  
- **Coordinate** with **book** **maintainers** and **smustgrave** in **#3586686** **.  

**Issue:** https://www.drupal.org/project/token/issues/3586686  

## Use

- D12 porting: when a **core**-only integration moves to **contrib**, **re-home** the glue code in the owning project first.  
- Follow **#3586686** for how **duplication** and **version** gating are resolved.  
