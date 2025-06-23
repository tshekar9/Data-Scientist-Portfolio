## Market Basket Analysis of Drug Prescription Data 

### Tejaswini Shekar

![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)

### Goal of Analysis

The goal of the analysis is to identify relationships between the prescribed drugs and utilise this information to drive strategic decision-making in the hospital. 
Knowing which drug combinations are prescribed together most frequently can help ensure that the hospital pharmacy always has adequate inventory. 
Also, the relationships between the prescribed drugs can provide insight into any underlying trends in patient illnesses and potential areas that healthcare professionals can further investigate.

### What is Market Basket Analysis?

Market basket analysis is a data mining technique that finds the strength of product relationships by looking at previous transactions and identifying trends/patterns. 
It is based on association rules and is used for product placement in stores, product bundling, and customer retention.
The Apriori algorithm is one association rule mining method that works by pruning. 

The Apriori algorithm uses the Apriori principle. Its parameters are support, lift and confidence. 
The algorithm generates frequent itemsets from the data based on whether they have a support value greater than the minimum threshold value provided, called the "minsup". Then, it generates association rules from these itemsets. 
The Apriori principle states that all subsets of frequent itemsets must also be frequent. It is a result of the anti-monotone property of support, which means that if we drop an item from a set, the support value of the new itemset generated will either be the same or greater. 
For example, if the set {Drug_1, Drug_2} has a support value less than the minsup, any set (e.g. {Drug_1, Drug_2, Drug_3}) containing that subset will also have a support value below the minimum threshold.
This principle makes searching for association rules in the data set more efficient. 

The steps of analysis using the Apriori algorithm include itemset generation followed by rule generation. 

The expected outcome is to obtain a table of association rules for the prescribed drugs and rank these rules by lift to find the top three. 
The top rules will show which drugs have the strongest associations/relationships and can be used to drive decision-making in the hospital. 

### Analysis Results - Support, Confidence, and Lift

The results of the analysis show that the top three rules, ranked by lift, are
1. If carvedilol, then lisinopril (support: 0.039195, confidence: 0.225115, lift: 2.291162)
2. If lisinopril, then carvedilol (support: 0.039195, confidence: 0.398915, lift: 2.291162)
3. If glipizide, then carvedilol (support: 0.022930, confidence: 0.348178, lift: 1.999758)

**Support:**
Support is the frequency of occurrence of an itemset. It is the fraction of transactions in which the itemset is seen.
The support value helps in identifying rules worth considering for further analysis. If a rule has a very low support, there isn't enough information on the relationship between the items and therefore no conclusions can be drawn from it. 
I used a minimum support threshold value of 0.02 in the Apriori algorithm to obtain the most frequent itemsets from the data.

**Confidence:**
Confidence is the liklihood of occurrence of the consequent Y, given that the antecedent X is already present. 
It is the conditional probability that drug Y will also be prescribed given that drug X is already prescribed, or, the fraction of X-containing prescriptions that also have drug Y. 
However, the confidence of any rule with a frequently occurring consequent will be high, regardless of what the antecedent is. This drawback is overcome by using lift.  

**Lift:**
Lift is the conditional probability of a consequent Y given antecedent X, divided by the frequency of occurrence of Y. 
It can also be expressed as the Confidence of {X}->{Y} over Support of Y. 
If the rule "If X -> Then Y" is true, then the value of lift will be greater than 1. A minimum lift threshold value of 1 was set when generating the association rules.

The first 2 of the top 3 rules have the same lift (2.291162) because they have the same itemsets (antecedent and consequent are interchanged and this does not affect calculation of lift). The third top rule has a lift of 1.999758. 

The first rule can be interpreted as *linsinopril being 2.29 times more likely to be prescribed when the patient has been prescribed carvedilol*, and vice versa where *carvedilol is 2.29 times more likely to be prescribed when the patient has been prescribed linsinopril.*
The third rule indicates that *carvedilol is 1.9997 times more likely to be prescribed when glipizide has been prescribed.*

### Practical Significance of Findings and Next Course of Action

Based on the results of the analysis, it is clear that carvedilol and lisinopril are often prescribed together. 
This makes sense logically since they are both medications used in the treatment of cardiovascular diseases. 
A patient with heart disease or any cardiovascular illness may need a combination of medications to treat their condition, and this is reflected in the analysis results. 
The third rules shows that glipizide, an anti-diabetic medication, is prescribed with carvedilol often as well. 
This is also no surprise since diabetes increases the risk for cardiovascular illnesses, and patients with one condition may also have the other.

Practically, these results indicate that the hospital drug dispensary should keep carvedilol and lisinopril in inventory together, as one is usally prescribed along with the other and a low stock of carvedilol probably means a low stock of lisinopril as well. 
This will ensure that patients get all their medications efficiently and in a timely manner. 

Another point of practical significance is that based on the pattern of drug prescription, doctors can conclude that many patients suffering from cardiovascular illnesses may also need to be routinely tested for diabetes.

The next course of action would be to delve deeper into the top association rules and uncover more patterns in drug prescriptions. 
These insights can aid in efficient management of hospital drug inventory and provide additional insight into the trends of illnesses among patients. 
I would also recommend that the hospital implement a policy of routine testing of blood sugar levels for all patients with chronic cardiovascular disease for early detection of diabetes. 
