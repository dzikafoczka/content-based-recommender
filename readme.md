# Content-Based Recommender - Project I

Department of Mathematics and Computer Science, Adam Mickiewicz University, 2023

Author: Paweł Łączkowski

## Project description

The main goal of the project was to create a content-based recommender for hotel data (room recommendations) whose @HR10 metric score would be higher than the amazon recommender.

To complete this task, the following subtasks had to be accomplished:
1. Preparation of data (data preprocessing).
2. Preparation of user features.
3. Preparation of item features.
4. Creating a recommender.
5. Tuning the recommender.
6. Evaluation of the recommender.

## Preparation of training data (data preprocessing)

The entire process of preparing data can be found in the file `project_1_data_preparation`.

It covers the creation of new features based on available data, such as a `length_of_stay` or `weekend_stay`, and the bucketing of important features.

## Preparation of user features

The task was to extract numerical features for users from the data that could be used to train the recommendation model.

There are two different approaches to preparing training data for users in this repository.

Both approaches are in separate files `project_1_recommender_and_evaluation - user-item features #1` and `project_1_recommender_and_evaluation - user-item features #2`.

#### User features #1

In the first case, user features are distributions of individual item features for all items with which that user interacted.

In general, the data shows what proportion of all user interactions were, for example, `Christmas term` or `Weekend Stay` interactions.

#### User features #2

In the second case, the three bucket features, `length_of_stay_bucket`, `room_segment` and `n_people_bucket`, were replaced with numerical data before bucketing and then averaged for each user against all his interactions. These features were also scaled using `StandarScaler`.

For the other features, the distribution was taken as in the `user features #1`.

## Preparation of item features

The task was to extract numerical features for items from the data that could be used to train the recommendation model.

There are two different approaches to preparing training data for users in this repository.

Both approaches are in separate files `project_1_recommender_and_evaluation - user-item features #1` and `project_1_recommender_and_evaluation - user-item features #2`.

Item features were prepared in a similar way to user features due to the later use of the scalar product of features to train the recommender.

#### Item features #1

Item features are One-Hot Encoded.

#### Item features #2

Three bucket features, `length_of_stay_bucket`, `room_segment` and `n_people_bucket`, were replaced with numerical data before bucketing.

## Creating a recommender.

The recomender is included in two files - `project_1_recommender_and_evaluation - user-item features #1` and `project_1_recommender_and_evaluation - user-item features #2`.

They differ slightly, and the differences are due to different approaches to preparing user features and the items on which they are trained.

In both cases, the scalar product of user and item features is used.

The recomender fitting works as follows:
1. Prepare users and items features.
2. Generate negative interactions.
3. Prepare input for training machine learning model.
4. Train machine learning model.

Several different machine learning models used to train the recommender are prepared:
1. Linear Regression.
2. SVR.
3. Random Forest.
4. XGBoost.
5. Simple Neural Network.
6. Cat Boost Regressor.

The recomendations work as follows:
1. Prepare users and items features.
2. Calculate score (predict values) for input data.
3. Get highest scores from list.
4. Return `n` items with highest score.

## Tuning the recommender.

Recommender tuning involves properly training the machine learning models used to predict scores.

Many tunings have been performed for all the models mentioned above (only a small part of the tuning process is included in files).

#### LinearRegressionCBUIRecommender

Tuned hyperparameters:
1. `n_neg_per_pos` - number of negative interactions per positive one (1-10).

#### SVRCBUIRecommender

Tuned hyperparameters:
1. `n_neg_per_pos` - number of negative interactions per positive one (1-10).
2. `C` - regularization parameter.
3. `kernel` - kernel type.

#### RandomForestCBUIRecommender

Tuned hyperparameters:
1. `n_neg_per_pos` - number of negative interactions per positive one (1-10).
2. `n_estimators` - number of trees in the forest.
3. `max_depth` - maximum depth of the tree.
4. `min_samples_split` - minimum number of samples required to split an internal node.

#### XGBoostCBUIRecommender

Tuned hyperparameters:
1. `n_neg_per_pos` - number of negative interactions per positive one (1-10).
2. `n_estimators` - number of boosting stages to perform. 
3. `max_depth` - maximum depth of the individual regression estimators.
4. `min_samples_split` - minimum number of samples required to split an internal node.
5. `learning_rate` - learning rate parameter.

#### NeuralNetworkCBUIRecommender

Tuned hyperparameters:
1. `n_neg_per_pos` - number of negative interactions per positive one (1-10).
2. `epochs` - number of epochs of the training process.

#### CatBoostRegressorCBUIRecommender

Tuned hyperparameters:
1. `n_neg_per_pos` - number of negative interactions per positive one (1-10).
2. `iterations` - maximum number of trees.
3. `l2_leaf_reg` - regularization parameter.
4. `learning_rate` - learning rate parameter.
5. `depth` - depth of the tree.

## Evaluation of the recommender.

The final results are as follows (models whose results were unsatisfactory were omitted):

#### User and Item Features #1

| **Recommender**                  | **HR@10** |
|----------------------------------|-----------|
| LinearRegressionCBUIRecommender  | 0.209776  |
| RandomForestCBUIRecommender      | 0.187373  |
| XGBoostCBUIRecommender           | 0.210115  |
| CatBoostRegressorCBUIRecommender | 0.217583  |
| AmazonRecommender                | 0.185336  |

#### User and Item Features #2

| **Recommender**                  | **HR@10** |
|----------------------------------|-----------|
| LinearRegressionCBUIRecommender  | 0.071623  |
| XGBoostCBUIRecommender           | 0.102172  |
| CatBoostRegressorCBUIRecommender | 0.202308  |
| AmazonRecommender                | 0.185336  |

## Conclusion

`User and Item Features #1` turned out to be much better than the `User and Item Features #2` and produced satisfying results on most models.

The CatBoost model achieved the best score of 0.217583, beating amazon's recommender score by 0.032247 points.

## Project requirements

Project is written in python. 

Requires:
1. python version 3.8 or higher.
2. [Anaconda](https://www.anaconda.com/products/individual).
3. [Git](https://git-scm.com/downloads)

All the necessary dependencies can be found in the file `requirements.txt` or `environment.yml`.

To run the project:
1. Fork this repository.
2. Clone your repository.
          <pre>git clone <i>your_repository_address</i></pre>
3. Create conda environment.
          <pre>conda env create --name <i>name_of_environment</i> -f environment.yml </pre>
4. Activate your environment.
          <pre>conda activate <i>name_of_environment</i></pre>
5. Launch jupyter notebook.
          <pre>jupyter notebook</pre>
6. Enjoy!
