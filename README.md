This project was done as part of the IE506-Machine-Learning-Principles-and-Techniques course (an Institute Elective Course), under the guidance of Prof. P. Balamurugan, IEOR Dept., IIT Bombay.

**Description:**
**1.**
In this project I have implemented Locally Weighted Ensemble Algorithm for Binary Classification Task on text data. The Locally Weighted Ensemble Algorithm was implemented on the 20 Newsgroup dataset and achieved an accuracy of over 75% for 3 out of 6 cases. The 20 Newsgroups dataset comprises approximately 20,000 newsgroup documents evenly distributed across 20 different topics. It's a widely used benchmark for text classification tasks in machine learning. The 20 news articles were divided into 4 categories "R", "S", "T" and "C" , the model was trained and tested on any two of these categories for an experiment. 


The algorithm was originally developed by Jing Gao, Wei Fan, Jing Jiang and Jiawei Han as described in the research paper "Knowledge transfer via multiple model local structure mapping, 2008". Please read the "project report. pdf" for detailed description and refer the ".ipynb" files for the python code. The 6 different ipynb files represent 6 different experiments with the 20 newsgroup dataset.

The Locally Weighted Ensemble (LWE) is a novel algorithm that combines multiple models to make predictions. It is useful in
transfer learning problems where training and test domains are different. The LWE assigns weights to individual models based
on their local behaviors at each test example, which allows it to adapt to different test examples.
The motivation behind this project is to improve the prediction accuracy in situations where the training and test domains
differ, a common scenario in many real-world applications. The uploaded report (project report.pdf) provides an overview of the project, detailing the
different steps in the algorithm, the experiments conducted and results. Viewer is advised to read the research paper "Knowledge transfer via multiple model local structure mapping, 2008" for in-depth  understanding of the LWE algorithm.


**2. **
After successful implementation of LWE algo on 20 newsgroup dataset, which is text data, the objective was extended to test the performance on LWE algorithm on **time series data**(in this case stock market data). The LWE algorithm failed to deilver satisfactory performance on time series data so a new algorithm was developed called **Confidence based Ensemble Algorithm** which unlike LWE, gave weightage on the basis of Confidence(probability) instead of similarity. Furthermore, similar to LWE algorithm,  in order to improve the accuracy of Confidence based Ensemble Algorithm I tried to combine the predictions made by Confidence based Ensemble Algorithm with the prediction made by KNN algorithm, on the basis of a treshold(probability of correct classifcation = 0.4 or 0.5 or 0.6) . However it was found that KNN did not help in the improvement of predictions, as with the increasing threshold(p) the accuracy kept dropping.

The data used is the price history and trading volumes of the  stocks related to Finance, IT, Autobile and Energy companies in the index NIFTY 50 from NSE (National Stock Exchange) India.  The data spans from 1st January, 2000 to 30th April, 2021. The dataset was downloaded from Kaggle repository(https://www.kaggle.com/datasets/rohanrao/nifty50-stock-market-data). The csv files named as ['bajaj', 'axis', 'hdfc', 'icici', 'tcs', 'wipro', 'infosys', 'hcl'] are used for trainig and testing.

The Confidence based Ensemble Algorithm (using three base models a.CNN b.LSTM  c. CNN) was developed in order to precisely classify the data related to a particular company into one of the four categories(Finance, IT, Autobile and Energy). Confidence based Ensemble Algorithm is a binary classification algorithm. For example , the model can be trained on price history and trading volumes of the  stocks related to Finance, IT companies(which does not contain TCS and HDFC data) and if I give it a test data consisting of datapoins from both TCS and HDFC, then it can correctly classify which of those fall in Finance category and which of them fall in IT category( with a 76% accuracy for IT vs Finance case with Bajaj and TCS as test datasets). The "Confidence based ensemble algo for Finance_vs_IT.ipynb" contains the necessary code and the "confidence based ensemble algorithm.pdf" contains the algorithm and results of the experiments.

Broadly the Confidence based ensemble algorithm optimizes transfer learning by dynamically assigning weights to base models based on their prediction accuracy. For each data point in the test set, it evaluates the predictions and associated probabilities from multiple base models. If any model predicts correctly, the one with the highest probability for the correct class is given full weightage. If no correct predictions are made, the model with the highest probability for the true label is selected. This results in a model_weights matrix, indicating the selected model for each data point. The algorithm then computes final probabilities and combines them with k-means clustering predictions. If the highest probability exceeds a threshold(p), the model's prediction is used; otherwise, the clustering(KNN) prediction is used. The final step involves calculating the accuracy and mean squared error of the combined predictions against true labels. This approach ensures robust and accurate predictions in transfer learning scenarios with varied training and test datasets.

Thank you 

Mayur Bhurle, Roll No. 23M1027, M.Tech., Educational Tech., IIT Bombay.

