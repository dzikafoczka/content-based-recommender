# Content-Based Recommender - Project I

Department of Mathematics and Computer Science, Adam Mickiewicz University, 2023

Author: Paweł Łączkowski

## Project description

The main goal of the project was to create a content-based recommender for hotel data (room recommendations) whose @HR10 metric score would be higher than the amazon recommender.

To complete this task, the following subtasks had to be accomplished:
1. Proper preparation of training data (data preprocessing).
2. Preparation of user features.
3. Preparation of item features.
4. Creating a recommender.
5. Tuning the recommender.
6. Evaluation of the recommender.

## Preparation of training data (data preprocessing)

The entire process of preparing training data can be found in the file `project_1_data_preparation`.

It covers the creation of new features based on available data, such as a `length_of_stay`, and the bucketing of important features.

## Preparation of user features

The task was to extract numerical features for users from the data that could be used to train the recommendation model.

There are two different approaches to preparing training data for users in this repository.

#### User features #1

In the first case, user features are distributions of individual item features for all items with which that user interacted.

#### User features #2

TO DO

## Preparation of item features

The task was to extract numerical features for items from the data that could be used to train the recommendation model.
