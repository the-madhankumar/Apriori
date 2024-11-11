# Apriori Algorithm - README

The **Apriori Algorithm** is a popular method in association rule mining used to extract frequent itemsets from a dataset and identify association rules. It is widely used in market basket analysis to identify frequently purchased items together, helping businesses make data-driven decisions about product placement, promotions, and recommendations.

---

## Overview

The Apriori algorithm operates on transactional data (e.g., a list of products bought in a transaction) to discover frequent itemsets. Frequent itemsets are groups of items that appear together often enough to meet a user-defined minimum support threshold. From these frequent itemsets, the algorithm then generates association rules with a specified confidence threshold, indicating the likelihood of items being purchased together.

### Key Terms

- **Support**: The proportion of transactions that contain a particular itemset.
- **Confidence**: The likelihood that a transaction containing one item also contains another.
- **Frequent Itemsets**: Sets of items that meet the minimum support threshold.
- **Association Rules**: Rules derived from the frequent itemsets to show relationships between items.

---

## Algorithm Outline

The Apriori algorithm proceeds in three main steps:

1. **Generate Candidate Itemsets**: 
   - Start with individual items and expand to larger itemsets by self-joining frequent itemsets from the previous step.
2. **Prune Infrequent Itemsets**: 
   - For each candidate, calculate its support. If the support is below the minimum threshold, remove the itemset.
3. **Generate Association Rules**: 
   - Using the frequent itemsets, generate rules that meet the minimum confidence threshold.

---

## Implementation Guide

### Functions Overview

1. **`apriori(itemSetList, minSup, minConf)`**: 
   - Main function that processes the dataset with specified support and confidence thresholds.
2. **`getUnion(itemSet, length)`**: 
   - Joins itemsets to create larger candidate sets.
3. **`pruning(candidateSet, prevFreqSet, length)`**: 
   - Removes itemsets that contain infrequent subsets.
4. **`getAboveMinSup(itemSet, itemSetList, minSup, globalItemSetWithSup)`**: 
   - Filters itemsets to retain only those meeting the minimum support threshold.
5. **`associationRule(freqItemSet, itemSetWithSup, minConf)`**: 
   - Generates rules from frequent itemsets that meet the confidence threshold.

### Example Usage

Given a dataset in the form of transactions, the algorithm can be run with the following structure:

```python
# Sample dataset as list of sets
transactions = [
    {'Milk', 'Bread', 'Butter'},
    {'Beer', 'Bread'},
    {'Milk', 'Bread', 'Eggs', 'Beer'},
    # more transactions
]

# Parameters
min_support = 0.4  # Minimum support threshold
min_confidence = 0.6  # Minimum confidence threshold

# Running Apriori
frequent_itemsets, rules = apriori(transactions, min_support, min_confidence)
```

### Output

- **Frequent Itemsets**: Itemsets meeting the support threshold.
- **Rules**: Association rules with confidence values.

---

## Practical Applications

- **Market Basket Analysis**: Identify product combinations frequently bought together.
- **Recommendation Systems**: Recommend items based on prior purchases.
- **Fraud Detection**: Identify patterns in transactional data for anomaly detection.

---

## References

- Agrawal, R., & Srikant, R. (1994). Fast Algorithms for Mining Association Rules. *Proceedings of the 20th International Conference on Very Large Data Bases* (VLDB '94).
- [PLOS ONE Journal on Apriori Algorithm](https://journals.plos.org/plosone/article/file?id=10.1371/journal.pone.0230124&type=printable)
