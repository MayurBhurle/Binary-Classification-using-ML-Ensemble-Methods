# Locally-Weighted-Ensemble-Algorithm
The Locally Weighted Ensemble Algorithm was implemented on the 20 Newsgroup dataset and achieved an accuracy of over 75% for 3 out of 6 cases. The algorithm was originally developed by Jing Gao, Wei Fan, Jing Jiang and Jiawei Han as described in the research paper "Knowledge transfer via multiple model local structure mapping, 2008". 


1 Introduction
The Locally Weighted Ensemble (LWE) is a novel algorithm that combines multiple models to make predictions. It is useful in
transfer learning problems where training and test domains are different. The LWE assigns weights to individual models based
on their local behaviors at each test example, which allows it to adapt to different test examples.
The motivation behind this project is to improve the prediction accuracy in situations where the training and test domains
differ, a common scenario in many real-world applications. This report provides an overview of the project, detailing the
different steps in the algorithm, the experiments conducted and results.
The report is structured as follows: Section 2 surveys the relevant literature focussing on Sample Selection Bias and Covariate
Shift , Section 3 describes the proposed project, Section 4 provides details on the dataset used, Section 5 outlines the
experiment performed, Section 6 presents the results, Section 7 discusses future work, and Section 8 concludes the report.

2 Methods and Approaches

Clustering Manifold Assumption: The researchers assume that the dataset follows the clustering manifold assumption
according to which for a sample x if the neighbouring points belong to class y then the sample x also belongs to class y.
The LWE uses a graph-based approach to approximate the optimal per example weight under the “clustering-manifold”
assumption that P(x) is related to P(y|x). It constructs two graphs for each test example and a base model to be combined,
and approximates the model weight as the similarity between the local structures around the test example in the two graphs.
The LWE also includes a local structure-based adjustment mechanism to handle cases where the concepts carried by all the
models conflict with the actual concept at the test example, meaning the average similarity value is lesser than a given
threshold value.
This report discusses the Locally Weighted Ensemble (LWE) framework, a technique for combining multiple models in
situations where the training and testing data come from different distributions (known as transfer learning). Here we'll focus
on two key aspects of LWE: graph-based weight estimation and local structure-based adjustment. These steps play a crucial
role in assigning appropriate weights to different models and potentially adapting predictions based on local information.
The Challenge: Conflicting Models and Uncertain Regions

This scenario involves two training datasets with conflicting decision boundaries and a test set with a V-shaped boundary.
Simply combining the training data or the trained models (M1 and M2) would lead to inaccurate predictions in the uncertain
regions (R1 and R2) of the test set.
The ideal solution would be a "locally weighted" ensemble framework that assigns higher weights to models based on their
performance in specific regions of the test set. For example, M1 should have a higher weight in R1 and M2 in R2. This approach leverages the strengths of each model in areas where they excel. The following sections introduce the Locally
Weighted Ensemble (LWE) framework, which dynamically adjusts weights based on local model behavior.


