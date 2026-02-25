# README

## **i**

##### Contents of the file

1. Best_result_0_833.ipynb: 
This is the main notebook of the project. It includes the data loading and processing, our model architecture, training model, hyperparameter search, training done with our optimal hyperparameters, evaluation, submission file, confusion matrix and error analysis, Google Drive to load pth file and inference test.

2. train.csv which contains the training data
3. test.csv which contains the dataset without label for generating predictions
4. 0.833_best_model.pth which is the final trained model (too big to push on GitHub)
5. submission.csv (output) which contains the predictions made by our model
6. submission_postload.csv (output) which just creates an alternative submission files

## **ii**

Before running any cell, ensure that the following files are in the same folder:

1. Best_result_0_833.ipynb
2. train.csv
3. test.csv

All data is processed in the first two cells. In those cells, it prepares the data in the correct format, separates the data for training and evaluation:

##### **In the first cell**

In this cell, it imports all the required libraries, loads the data from the train.csv file. The data is split 80/20 (80% train, 20% validation). The training, validation and feature data is formatted into numpy arrays. Then, we converted the training and validation set features and labels to tensors. This was helpful to create Dataloaders later on.

##### **In the second cell**

Here the training and validation DataLoaders are created which essentially feeds the data into the model in mini-batches.

Now, all the data has been processed and ready to be used.

# **iii**

Our training model file is too large to push to GitHub, we includes special cells with clear comments labeled above, which downloads weights from Google Drive and then run the evaluation without retraining.

##### **PLEASE DO NOT USE "Run all", this is VERY IMPORTANT, FOLLOW THESE STEPS (ALL CELLS HAVE COMMENTS ABOVE TO PROVIDE FURTHER INSIGHT AND INSTRUCTIONS)**. The training and evaluation part of our code starts at the second cell: 

#### TRAINING MODEL FROM SCRATCH (RUN CELLS ONLY IF YOU HAVE ACCESS TO POWERFUL GPU)

##### **CELL #2:**

 This cell can also be run safely, this cell defines our training models.

##### **CELL #3:**

This cell is the hyperparameter search done using Optuna. This was done using a GPU (RTX4090) and ran overnight, do not run this cell.

##### **CELL #4:**

The following cell trains the model using the optimized hyperparameters found by the previous search done. This will take roughly an hour on google collab using the T4 GPU, and about 20 minutes on the RTX4090.

##### **CELL #5:**

**NOTE:** The current cell cannot be ran without the previous cell. The next cell visualizes the training process of our model by plotting the loss and accuracy curves throughout the epochs

#### TEST DATA APPLICATION

##### **CELL #6:**

This cell creates the submission file using the trained model.

#### EVALUATION

##### **CELL #7:**

This cell makes a confusion matrix and provides error analysis with the weakest and strongest classes.

#### PRETRAINED MODEL (RECOMMENDED)

##### **CELL #8:**

This cell simply saves the model.

#### These next cell can be SAFELY RAN ON ANY SYSTEM

##### **CELL #9:**

This cell downloads a model from Google Drive that we previously trained, since it was too big to push on GitHub. This loaded model can then be used for all the cells below.

##### **CELL #10:**

Once downloaded, this cell loads our model from pth file. This recreates the model from the previously downloaded pth file, utilizing the same architeture and weights.

##### **CELL #11:**

This cell provides a "sanity check" by running inference on validation data set to verify the original value.

#### TEST DATA APPLICATION FOR PRETRAINED

##### **CELL #12:**

Similarly, this cell runs inference on test data set and creates an alternative submissions file so that these results can be used to verify submission performances. This should take roughly 90 seconds on a CPU (tested on laptop Ryzen 7).

#### EVALUATION FOR PRETRAINED DATA

##### **CELL #13:**

Finally, the last cell is just the error analysis for the loaded model.
