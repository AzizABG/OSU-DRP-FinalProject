# OSU-DRP-FinalProject

The [Directed Reading Program (DRP)](https://u.osu.edu/directedreadingprogram/) at the Ohio State University is organised by grad students in the Department of Mathematics. The DRP pairs undergraduate students with graduate mentors to complete semester long reading projects in mathematics.

After studying *Hands-on Machine Learning with Scikit-Learn, Keras & TensorFlow* by Aurélien Géron over the course of the semester, here we present our final project.

# Goals

In this project, we aim to classify a wine's quality using techniques we learned over the course of the DRP.

# Dataset

The [White Wine Quality dataset](https://archive.ics.uci.edu/ml/datasets/wine+quality) was taken from the UCI Machine Learning repository, and was first introduced in (Cortez, et al., 2009). It has 4898 data points with 11 numerical features and 1 categorical feature (quality). There are no missing values in the dataset.

# Exploratory Data Analysis (EDA)

In our EDA, we examined the relationships between feature, feature distributions, and outliers in the dataset.

The following figure contains a pairwise plot between all features in the dataset. This plot allows us to qualitatively choose combinations of features to test as new features on our models.
<p align="center">
  <img src="https://github.com/AzizABG/OSU-DRP-FinalProject/assets/19894910/a5542098-aafd-4826-9f64-be7470d04127" width="400" height="400"/>
</p>

Seen here is a histogram of all features in the dataset with bin size set to 50. With this graph, we could determine which features require transformation and scaling before they could be used. Based on this figure, candidates for transformation could include residual sugar (heavy tail), alcohol (multimodal), and sulphates (multimodal).

<p align="center">
  <img src="https://github.com/AzizABG/OSU-DRP-FinalProject/assets/19894910/5749e73c-e96b-4bbd-a245-421693ec00b8" width="550" height="500"/>
</p>

Viewing all features in the dataset as a box plot results in the figure on top. On the bottom is the same data but with outliers removed from the free sulfur oxide and total sufulr oxide features.

<p align="center">
  <img src="https://github.com/AzizABG/OSU-DRP-FinalProject/assets/19894910/38cf8318-9835-4964-b672-f8ed9f3dc1ec" width="600" height="400"/>
  <img src="https://github.com/AzizABG/OSU-DRP-FinalProject/assets/19894910/d9b85880-f67d-4161-bdb1-503634a50e5d" width="600" height="400"/>
</p>

# Models

Using the scikit-learn package, we trained three models on the dataset:
- A [SVM model](White_Wine_Quality_Prediction_SVM.ipynb) using a Gaussian RBF kernel with hyperparameters *c=100* and *gamma=0.93*, where *c* controls margin tolerance and *gamma* controls model regularization. Before training the model, some outliers were dropped and the data was scaled. (Specific details may be found in the linked notebook.)
- A [decision tree model](White_Wine_Quality_Prediction_Random_Forest.ipynb) ...
- A [random forest model](White_Wine_Quality_Prediction_Random_Forest.ipynb) with hyperparameters of *max depth=100* and *estimators=75*

The hyperparameters were chosen by handpicking and using grid search methods.

# Results

With our SVM model, we were able to achieve 69.0% accuracy, which beats the benchmark of 64.6% given in (Cortez, et al., 2009). Here is the corresponding confusion matrix: 
<p align="center">
  <img src="https://user-images.githubusercontent.com/74211589/236936922-f345ce21-e575-47ab-8de5-45f8df47e7d3.png" width="300" height="300"   />
</p>

With our decision tree model, we ...

Using the random forest model, we ...

# Improvements

- More sophisticated feature engineering may yield better classification.
- Other models or ensembles of models may be able to achieve better classification.
- A natural direction of exploration could be using neural networks, but the preliminary work done in (Cortez, et al., 2009) and [done by our graduate mentor](NN.ipynb) suggest that traditional methods like those we used may be more efficacious.

# References

- Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). Modeling wine preferences by data mining from physicochemical
properties. Decision Support Systems, 47(4), 547-553. https://doi.org/10.1016/j.dss.2009.05.016
- Géron, A. (2022). Hands-on Machine Learning with Scikit-Learn, Keras & TensorFlow (3rd ed.).  O’Reilly Media.
