# Customer Segmentation for Variable Annuity Products


## Project Introduction 
A variable annuity (VA) is a contract between a customer and an insurance company. With a VA, the insurance company agrees to make periodic payments to the customer in the future. As total sales of VA in U.S. market grows, insurance companies face big challenges in terms of pricing their products due to the great uncertainties of policyholders’ behaviors. This project offers predictive analysis of policyholders’ behaviors to our project sponsor, Milliman. Milliman is one of the world’s largest providers of actuarial and related products and services. We here provide the sponsor reasonable customer segmentation suggestions to differentiate profitability of policyholders for their client insurers. The results will guide insurers’ product design and marketing, and make better estimation on the cost to provide a current product.

## Objectives
1. Compare different clustering algorithms and study the impact of high dimension on clustering performance.
2. Customer segmentation analysis to distinguish their profitability.

## Data
The data is provided by the sponsor, Milliman. It has more than 4 million row and 1063 variables. Data sources include insurance company and third party, which are primarily consumer, mortgage, credit, census, and health data.

## Methods
1. Feature Selection

    Feature Screening, remove irrelevant and correlated features.
    LASSO, select features having predicting power.
    PCA (filter model), dimension reduction.
    Wrapper model, order features based on their cluster differentiability.
    
2. Data Preparation

    Apply Generalized Low Rank Model on High-dimensional Data to reduce dimensionality and impute missing values.

![picture](Figure/readme_fig1.png|width=100)
![Alt text](Figure/readme_fig2.png?raw=true "Title")

3. Model Selection

    Applied 10 different clustering algorithms range from basic K-Means, K-Means extensions to hierarchical clustering, kernel-based clustering, density-based clustering and probabilistic model using existing packages.
    Self-implemented K-Means, K-Medians, K-Harmonic Means and K-Prototype clustering algorithms from scratch. 

4. Determination of Optimal K

    Elbow Method
    To define clusters such that the explained variance (between-cluster sum of squares/total sum of squares) is maximized.
    Average Silhouette Score Analysis
    Silhouette coefficient is calculated using the mean intra-cluster distance and the mean nearest-cluster distance for each sample. Average silhouette measures how close each point in one cluster is to points in the neighboring clusters and thus provides a way to assess clustering performance. 

## Results

## Conclusions
* The missing value imputation and feature selection methods were successful for subsequent clustering.
* When comparing different clustering algorithms in low dimension, fuzzy K-Means, Ward, and regular K-Means are the top three algorithms in terms of silhouette score. Ward, being an hierarchical clustering algorithm, has much longer runtime and is difficult to scale to a large data set. 
* Our study showed that K-Means algorithm did not perform as well on high dimensionality. This is probably because euclidean distance is problematic with high dimensionality. We introduced an subspace clustering algorithm, Entropy weighting K-Means (EWKM) to handle high dimensionality.
* We applied two methods based on internal metrics to determine optimal K, elbow and average silhouette score methods. Our clustering results on high and medium dimension suggest that optimal K could be 6-10, specifically, our study on the first two principal components suggest K to be 9. 
* Most clustering algorithms only handle numerical data, we introduced K-Prototype algorithm to handle both numerical and categorical data. However, it is not necessary after our feature selection, which ended up with all numerical variables. 

## Future work
* In this study, the quality of clusters is measured by internal metric, the compactness and separation of clusters (silhouette and elbow method). External metric, associated with profitability projection, is recommended to be included in the evaluation of clustering algorithm as well. 

* Clustering algorithms that are based on distance metric is favorable because of its interpretability. There are clear limitations for applying such models to high dimensional data. Entropy based subspace clustering is recommended to use for future work.

* Besides application to high dimensional data, scalability to large data sets is also found to be crucial for a clustering algorithm to perform well in this study. Future work is recommended to study the scalability to large data sets of clustering algorithms.

## Project Structure
```
Customer Segmentation for Variable Annuity Products/  
  |- LICENSE
  |- README.md
  |- Comparing different clustering algorithms final.ipynb
  |- Determine the number of clusters elbow method KMeans final.ipynb
  |- Determine the number of clusters elbow method Fuzzy KMeans final.ipynb
  |- Determine the number of clusters silhouette analysis KMeans final.ipynb
  |- Determine the number of clusters silhouette analysis KProto final.ipynb
  |- PosterPresentations.pptx
  |- cluster.csv
  |- h2o_glrm_sampled_dataset.ipynb
  |- .ipynb_checkpoints
     |-Feature Selection with PCA -- Sha-checkpoint.ipynb
     |-Iterated feature selection using K-means - Sha-checkpoint.ipynb
     |-Iterated feature selection using K-means-checkpoint.ipynb
     |-K-medians clustering-checkpoint.ipynb
     |-centroidsClustering-Copy1-checkpoint.ipynb
  |- Figures/
     |-algorithm_compare.png
     |-high_dimension_elbow.png
     |-high_dimension_silhouette.png
     |-medium_dimension_elbow.png
     |-medium_dimension_silhouette.png
     |-low_dimension_elbow.png
     |-low_dimension_silhouette.png
     |-PCAK6.png
     |-PCAK7.png
     |-PCAK8.png
     |-PCAK9.png
     |-PCAK10.png
     |-obj_vs_iter.png
     |-obj_vs_k.png
  |- KPrototype/
  |- algorithms/
     |-FuzzyKMeans.ipynb
     |-K-medians clustering.ipynb
     |-K-prototype-final.ipynb
     |-centroidsClusering.ipynb
     |-k-harmonic clustering.ipynb
     |-KMeans.ipynb
  |- dataMunging/
     |-DataMunging-Python.ipynb
  |- doc/
     |-Capstone_proposal.docx
     |-project_plan.xlsx
  |- featureEngineering/
    |-Feature+selection-wrapper-KMeans-inertia-final.ipynb
    |-Feature+selection-wrapper-KMeans-silhouettes-final.ipynb
    |-Kmeans_LASSOSelectedFeatures.ipynb
    |-LASSOFeatureSelection_CleanedData.ipynb	
  |- finalModel/
    |-KMeans_h2o.ipynb
    |-KMeans_vs_EWKMDemo.pdf
    |-ewkm.ipynb
    |-plot_ewkm_R.ipynb
    |-plot_kmeans_R.ipynb
  |- glrm/
    |-.ipynb_checkpoints/
      |-17features_profiling_imputed-checkpoint.ipynb
      |-17features_profiling_original-checkpoint.ipynb
    |-17features_profiling_imputed.ipynb
    |-17features_profiling_original.ipynb
    |-h2o_glrm_all.ipynb
    |-imputationResultDemo.pdf
```
