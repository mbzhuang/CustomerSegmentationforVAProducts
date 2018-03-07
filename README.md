# Customer Segmentation for Variable Annuity Products


## Project Introduction 
A variable annuity(VA) is a contract between a customer and an insurance company. With a VA, the insurance company agrees to make periodic payments to the customer in the future. As the growth of total sales of variable annuity (VA) in U.S. market, insurance companies face big challenges in terms of pricing their products due to the great uncertainties of policyholders’ behaviors. This project offers predictive analysis of customers’ behaviors for our project sponsor Milliman, one of the world’s largest providers of actuarial and related products and services, and provide the sponsor reasonable customer segmentation suggestions to differentiate profitability of policyholders for their client insurers, the results will guide insurers’ product design and marketing,

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
## Conclusions
* High dimensional data clustering. Our study showed that KMeans algorithm performs not as good on high dimensionality. This is probably because euclidean distance is problematic with high dimensionality.
* We reduced data dimension from the original 1063 to 514 by feature screening, and then reduced to 75 via LASSO, and continue reduced to 44 via grouping and PCA transformation. Finally, we selected 20 features based on the interpretability of the features.
* We have imputed missing values of the data set using low rank representation method.
Our clustering results on high and medium dimension suggest that optimal K could be 6-9, specifically, our study on the first two principal components suggest K to be 8.
* When comparing different clustering algorithms, fussy Kmeans, Ward, and regular Kmeans are the top three algorithms in terms of cluster silhouette score. Ward, being an hierarchical clustering algorithm, has much longer runtime and is difficult to scale to large data set. 
* Customer segmentation to differentiate profitability:

## Future work
* In this study, the quality of clusters is measured by internal metric, the compactness and separation of clusters (silhouette and elbow method). External metric, associated with profitability projection, is recommended to be included in the evaluation of clustering algorithm as well. 

* Clustering algorithms that are based on distance metric is favorable because of its interpretability. There is clear limitations for applying such models to high dimensional data because euclidean distance is problematic with high dimensionality. Entropy based and subspace clustering is recommended to use for future work.

* Besides application to high dimensional data, scalability to large data sets is also found to be crucial for a clustering algorithm to perform well in this study. Future work is recommended to study the scalability to large data sets of clustering algorithms.
