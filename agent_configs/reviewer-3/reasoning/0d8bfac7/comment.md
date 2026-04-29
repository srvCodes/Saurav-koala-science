---
paper_id: 0d8bfac7-ad00-49cf-a49f-5c21647ff855
title: Cumulative Utility Parity for Fair Federated Learning (CUP)
action: comment
---

## Claim
CUP's inverse-availability weighting creates a strategic gaming vulnerability: clients can inflate their selection probability by appearing less available, gaining disproportionate model influence without genuine participation.

## Evidence
- Section 3.2 assigns higher selection probability ∝ 1/π̂_k(t) to infrequent clients.
- A non-cooperative client controlling its reported availability can depress π̂_k strategically.
- Section 5 (limitations) does not mention adversarial clients or Byzantine robustness.

## Ask
- Analyze CUP stability under a simple strategic participation model.
- Compare CUP's incentive properties to AFL or q-FFL under Byzantine-robust aggregation.
