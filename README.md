# vulnerabilityClustering

Common Vulnerabilities and Exposures (CVE) is a list of publicly disclosed vulnerabilities and exposures that is maintained by MITRE.The list of vulnerability ID (CVE ID) and CVE descriptions are extracted by using NVD website
CVE ID description is clustered by using machine learning approach and tagged accordingly as Remote Code Execution(RCE) , Privilege Escalation(PE), Denial of Service(DOS), WebApp & others.

##### Data Extraction
The list of CVE Ids are given as inputs to the given website which outputs the details of the ID as a webpage which is then extracted using Beautiful Soup. Beautiful Soup is a Python package for parsing HTML and XML documents (including having malformed markup, i.e. non-closed tags, so named after tag soup). It creates a parse tree for parsed pages that can be used to extract data from HTML, which is useful for web scraping. The data extracted is saved into a data frame.
The CVE ID are also used to obtain Exploit id using a CVE- exploit id map database. The exploit is used to extract data from the Exploit-DB. Similarly, exploit details are extracted and saved into the database.

##### Preprocessing
The documents are then Preprocessed and cleaned using NLTK a package used for NLP to remove stop words, lemmatize words and remove special characters. 
The data can then be vectorized either as Word2Vec matrix or as a TfIdf matrix using only numbers instead of words for further analysis and prediction. 

##### Clustering
The documents are then clustered using KMeans algorithm.
The K-means algorithm in data mining starts with a first group of randomly selected centroids, which are used as the beginning points for every cluster, and then performs iterative (repetitive) calculations to optimize the positions of the centroids It halts creating and optimizing clusters when either the centroids have stabilized — there is no change in their values because the clustering has been successful, the defined number of iterations has been achieved.

##### Observations
1. The graph above is the clustering obtained while using a word2vec vector. While it does output well defined clusters it does not capture the intricacies of the dataset. Hence this vectorization does not support this dataset. Moreover the word clouds generated for each cluster are very similar to each other  and hance are not well clustered.
2. The graph above is the clustering obtained while using a Tf Idf vector. While it does not output well defined clusters it does capture the intricacies of the dataset. However two clusters correspond to the same class when comparing with the actual tags, ie. Cluster 1 and 2 correspond to WebApps. And Cluster 0 represents remote attacks and finally Cluster 3 combines both Local and DOS attacks. The word clouds are well defined and differences between the attacks can be observed.

# exploitLabeling

Learn the labeled pattern on Exploit description and predict the new Exploit descriptions

##### Preprocessing
The documents are then Preprocessed and cleaned using NLTK a package used for NLP to remove stop words, lemmatize words and remove special characters. 

##### Vectorization
The data can then be vectorized as a TfIdf matrix using only numbers instead of words for further analysis and prediction. 

##### Classification:

The following classifiers were used to classify the data to choose a model that performed well with the given data.
•	The Dummy Classifier gives a measure of “baseline” performance — i.e. the success rate one should expect to achieve even if simply guessing.
•	Gaussian Naive Bayes is a variant of Naive Bayes that follows Gaussian normal distribution and supports continuous data.
•	Random forests or random decision forests are an ensemble learning method for classification, regression and other tasks that operate by constructing a multitude of decision trees at training time and outputting the class that is the mode of the classes or mean/average prediction of the individual trees.
•	A Bagging classifier is an ensemble meta-estimator that fits base classifiers each on random subsets of the original dataset and then aggregate their individual predictions (either by voting or by averaging) to form a final prediction.
