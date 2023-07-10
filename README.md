# Fedarated_Learning---Ditto
Explored a machine learning paradigm called Federated learning(FL). FL aims to learn a global machine-learning model collaboratively from data generated
by and residing on several remote devices or clients locally. FL stands to produce highly accurate statistical models by aggregating knowledge from disparate data sources while preserving data privacy.

However, the resulting systems should be accurate and satisfy several pragmatic constraints such as fairness, robustness, and privacy. Simultaneously satisfying these varied
constraints can be exceptionally difficult.

T. Li, S. Hu, A. Beirami, and V. Smith. Ditto: Fair and robust federated learning through personalization. In International Conference on Machine Learning, pages 6357–6368. PMLR, 2021

The work focuses on issues of accuracy, fairness, and robustness in FL. The authors investigate a simple scalable technique that satisfies all the above three constraints. They identify statistical heterogeneity as the root cause for tension between these constraints which in itself is a key to the solution. In particular, they suggest that methods for personalized FL1 may provide inherent benefits in terms of fairness and robustness.

After reading the paper, completed few of the tasks 

1. Reproduce its results. In this task, reproduced the robustness, fairness, and accuracy results on the Fashion MNIST (FMNIST) and FEMNIST (skewed) Datasets provided in Appendix C of the paper. Using the value of lambda given in the paper for these datasets.
2. Executed other two baselines (additional to Ditto), L2SGD and EWC.
3. The DITTO algorithm tries to achieve personalization using Algorithm 1 given in the paper. Developed another possible algorithm (say FedAvgPer) that works as follows:
- After a global model is learned in simple vanilla federated averaging. The final global model is shared with the clients.
- Now, clients will directly run a few local epochs on their own data and update model parameters. This will add each client’s own personal touch. (We are not adding any constraints of the combined loss objective and regularization between the local and global models as in Ditto).
-  Now, after updating model parameters locally, each client has its own personalized FL model.
Compared FedAvgPer with Ditto and other existing baselines in above task, i.e., reproduce all the results gathered in the previous task with this updated approach. Is FedAvgPer better than Ditto

Prepared a report with the tables and figures of reproduced results.

4. Considering another dataset called the ADULT dataset available at https://archive.ics.uci.edu/ml/datasets/adult. It is a census dataset usually used to predict whether income exceeds 50K per year. Let us consider a scenario where we have clients in different countries/regions, each generating their own data. To mimic this scenario, divide the complete dataset into clients based on column ‘native-country’. Further, consider a fairness metric called Equal Opportunity. Equalized opportunity means matching the true positive rates (TPR) for different values of a protected/sensitive attribute such as for ADULT dataset matching TPR for income prediction for different values of gender. If for both MALE and FEMALE, the TPR rates are same then the model is fair otherwise its unfair. Here, the fairness criteria has been evaluated based on the sensitive attribute column ‘gender’ in the dataset.

So I created a new loss function considering the combination of accuracy and Equal Opportunity fairness metrics (considering gender) for improving personalization and
fairness performance. 

5. In real-world decision-making systems, classification models must not only be accurate but also indicate when they are likely to be incorrect. Specifically, a model should provide a calibrated confidence measure in addition to its prediction. In other words, the probability associated with the predicted class label should reflect its ground truth correctness likelihood. Good confidence estimates for the predicted label provide a valuable extra bit of information to establish trustworthiness with the user – especially for neural networks, whose classification decisions are often difficult to interpret. A metric to analyze the level of calibration of a model is Maximum Calibration Error (MCE).
   
Made a report the MCE for different personalized models obtained using DITTO

- The research paper is available at https://arxiv.org/pdf/2012.04221.pdf.
- The code which we are using for the research paper is available at https://github.com/litian96/ditto.
- This was done under a researchh assignment of Machine Learning course (CS503)
