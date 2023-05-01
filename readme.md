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

Item features were prepared in a similar way to user features due to the later use of the scalar product of features to train the recommender.

#### Item features #1

Item features are One-Hot Encoded.

#### Item features #2

Three bucket features, `length_of_stay_bucket`, `room_segment` and `n_people_bucket`, were replaced with numerical data before bucketing.
