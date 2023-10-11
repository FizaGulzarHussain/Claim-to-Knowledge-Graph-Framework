# Claim-to-Knowledge-Graph-Framework
In this research project, we built the claim news headlines dataset. We also proposed a methodology from claim detection to a Knowledge graph (KG) construction framework.
## Dataset: 
Dataset is saved in dataset folder with name "Claim News Headline Dataset". This dataset is generated from news headlines of ARY and Express Tribune News Website. The dataset size is 5200 claims headlines and 52 are non-claims.
## Methodology
The input dataset is news headlines. Then, claim classification is performed as a binary task on headlines. The claim headlines are passed to the OpenIE system for triple generation. These triples are filtered and linked to DBpedia through entity linking. The final triples are stored in the knowledge graph for downstream tasks. The methodology steps are:
1. Claim Classification
2. OpenIE triples extraction
3. Triple Filtering
4. Entity Linking
5. KG Construction
### Claim Classification
We use the five algorithms: SVM, Gaussian Naive Bayes, Logistic Regression, decision tree, and Ada Boost classifier. We combine TF-IDF features with numerical features (headline length, no. of nouns, no. of verbs) and use the combined features in machine learning classification models.
### OpenIE triples extraction
Baseline Model is Dependency Parsing and Three Deep Learning Models are:
1. OpenIE6: https://github.com/dair-iitd/openie6
2. IMOJIE: https://github.com/dair-iitd/imojie
3. Gen2OIE: https://github.com/dair-iitd/moie
### Triple Filtering
First, we created a lexicon of the most frequent 100 nouns from the claim dataset. Then we extracted noun phrases from triples arguments. We match the lexicon with filtered triples. If there is a match between the lexicon noun and an arguments noun phrase, we keep the triple; otherwise, we discard it.
### Entity Linking
We link the filtered triples with the DBpedia knowledge base for entity disambiguation. We use the Falcon tool for this purpose. 
### KG Construction
The linked triples were saved with DBpedia URIs. We use the Neo4j database for triples storage.


## Results of ML Algorithms on claim classification on the News Headline built corpus: (Accuracy)
1. SVM: 96%
2. Logistic Regression: 95.2% 
3. Naive Bayes: 93%
4. AdaBoost: 95.3%
5. Decision Tree: 95.1 %


## Results of OpenIE models on the News Headline built corpus:
1. Baseline Model - Dependency Parsing: 39.7 % F1
2. OpenIE6: 65.9 % F1
3. IMOJIE: 54.4 % F1
4. Gen2OIE: 62.2 % F1
