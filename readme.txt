KDiscShapeNet A Structure-Aware Time SeriesClustering Model withSupervisedContrastive Learning
==================================================
Overview
-----------------
KDiscShapeNet is a clustering method built on the foundation of the Kan Network (KAN), a deep learning model designed to process and cluster sequential data. This method is enhanced with Supervised Contrastive Loss (SupCon), Center Loss, and Differentiable K-Shape to improve performance, stability, and flexibility in clustering tasks.

This implementation leverages multiple datasets, including the Trace, ECG200, ItalyPowerDemand, Beef, SonyAIROBotSurface1, GunPoint, and StarLightCurves datasets, to demonstrate the method’s application. It uses advanced techniques for feature normalization, model training, and evaluation, including the use of t-SNE for visualization of clustering results and multiple clustering evaluation metrics such as Adjusted Rand Index (ARI), Normalized Mutual Information (NMI), and Silhouette Score.

Key Features
---------------------------------------
- Kan Network (KAN): A neural network-based clustering method that captures complex, non-linear relationships in data.
- Supervised Contrastive Loss (SupCon): An enhancement to contrastive learning that incorporates label information to better distinguish between classes.
- Center Loss: A regularization technique that minimizes the distance between class centers and sample features.
- Differentiable K-Shape: A novel loss function that ensures the cluster prototypes are learned in a differentiable manner, enabling end-to-end training.
- t-SNE Visualization: A dimensionality reduction technique to visualize high-dimensional data and its clusters.

Dependencies
---------------------------------------
Ensure the following libraries are installed with the specified versions:

- numpy == 1.21.5
- torch == 1.10.0
- scikit-learn == 0.24.2
- matplotlib == 3.4.3
- seaborn == 0.11.2
- tqdm == 4.62.3
- scipy == 1.7.3

These libraries can be installed using pip:

pip install numpy==1.21.5 torch==1.10.0 scikit-learn==0.24.2 matplotlib==3.4.3 seaborn==0.11.2 tqdm==4.62.3 scipy==1.7.3

Additionally, ensure that pykan is available for use. The code expects KANLayer from pykan_local/kan.
Before running the project, the KAN network must be deployed first.


Dataset
---------------------------------
The method uses the following datasets, consisting of training and testing data in TSV format. The load_trace_dataset() function loads and normalizes the dataset.

- Trace Data: Trace_TRAIN.tsv, Trace_TEST.tsv
- ECG200 Data: ECG200_TRAIN.tsv, ECG200_TEST.tsv
- Italy Power Demand: ItalyPowerDemand_TRAIN.tsv, ItalyPowerDemand_TEST.tsv
- Beef Data: Beef_TRAIN.tsv, Beef_TEST.tsv
- Sony AIBO Robot Surface: SonyAIROBotSurface1_TRAIN.tsv, SonyAIROBotSurface1_TEST.tsv
- GunPoint Data: GunPoint_TRAIN.tsv, GunPoint_TEST.tsv
- StarLightCurves Data: StarLightCurves_TRAIN.tsv, StarLightCurves_TEST.tsv
-ETTh1 & ETTh2: Hourly-level datasets monitoring oil temperature and variants of load (e.g., high useful load, high useless load) from July 2016 to July 2018.
-ETTm1 & ETTm2: 15-minute interval datasets similar to ETTh1 and ETTh2, providing higher temporal resolution data.

Dataset Format
-------------------------------
Each file has the following columns:

1. Label: Integer indicating the class of the sample.
2. Features: Multiple columns containing the feature vectors.

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
