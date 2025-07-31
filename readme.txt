Model Architecture
---------------------------------------------
The architecture consists of the following key components:

1. KANEncoder: Encodes the input features using multiple KAN layers, each followed by normalization.
2. Loss Functions:
   - CenterLoss: Encourages samples of the same class to be closer to their class center.
   - SupConLoss: Utilizes contrastive learning with label guidance to maximize the similarity between samples of the same class and minimize the similarity between samples of different classes.
   - Differentiable K-Shape Loss: Ensures that the learned cluster prototypes are close to the average feature representations of their corresponding clusters.

How to Run
---------------------------------------
1. Ensure that you have the required dataset files (Trace_TRAIN.tsv, Trace_TEST.tsv, etc.).
2. Modify the paths in the notebook if necessary.
3. Run the provided Jupyter notebooks (1KDiscShapeNet_Trace.ipynb, 2KDiscShapeNet_ECG200.ipynb, etc.) to train the model and evaluate the results.

jupyter notebook 1KDiscShapeNet_Trace.ipynb

Evaluation
-------------------------------------------
After training, the model's performance is evaluated using several clustering metrics:

- Adjusted Rand Index (ARI)
- Normalized Mutual Information (NMI)
- Silhouette Score

These metrics help assess the quality of the clustering produced by the model.

License
------------------------------------------------
This code is licensed under the MIT License. See the LICENSE file for more details.
************************************************************
The authors would like to express their sincere appreciation to the authors of KAN: Kolmogorov–Arnold Networks (ICLR 2025) for sharing their open-source implementation [https://github.com/KindXiaoming/pykan], which served as a valuable foundation for our model development. Their publicly available code significantly facilitated our research on extending and improving the KAN architecture.
