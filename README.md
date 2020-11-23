# -Getting-and-Cleaning-Data-Course-Project-
@@ -13,30 +13,23 @@ The following files from the initial dataset is used:
  6. ***train/y_train.txt*** - activity (from 1 to 6) for each measurement from the train set
  7. ***test/y_test.txt*** - activity (from 1 to 6) for each measurement from the test set

Merges the training and the test sets to create one data set.
Extracts only the measurements on the mean and standard deviation for each measurement. 
Uses descriptive activity names to name the activities in the data set
Appropriately labels the data set with descriptive variable names. 
From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.


## How script works
Script involves the following stages:

1. Downloads to R ids and descriptions for features being measured in experiment from file ***features.txt***.

2. Independently loads complete data for train and test sets. Let's revoke these loading process considering train set:
2. Independently loads complete data for train and test sets. Let's revoke these loading process considering train set:  
    a. Firstly loads the measurements from ***X_train.txt*** as a data frame  
    b. For these data frame column names are updated to be more user friendly using features description loaded on the previous stage. (**STEP 5**: *Appropriately label the data set with descriptive variable names* of Course Project  
    b. For these data frame column names are updated to be more user friendly using features description loaded on the previous stage. (**STEP 4**: *Appropriately label the data set with descriptive variable names* of Course Project  
    c. activity labels and subjects for measurements are also loaded from files ***train/y_train.txt*** and ***train/subject_train.txt*** and added to data frame as a separated columns.

  Similar steps is being made for test dataset and finally 2 rows of 2 data frames are merged together to form are data frame with complete data (STEP 1 of assignment)
  Similar steps are made for test dataset and finally 2 rows of 2 data frames are merged together to form are data frame with complete data (**STEP 1**: *Merge the training and the test sets to create one data set* of assignment)

3. To extract measurements that involves only mean and standard deviation values script uses grep, that finds column names that includes "mean()" or "std()" (also columns activity and subject are added to filtered data frame, since they are important). After that all new data frame with only necessary columns is created. (STEP 2 of assignment)
3. To extract measurements that involves only mean and standard deviation values script uses grep, that finds column names that includes "mean()" or "std()" (also columns activity and subject are added to filtered data frame, since they are important dimensions). After that all new data frame with only necessary columns is created. (**STEP 2**: *Extract only the measurements on the mean and standard deviation for each measurement* of assignment)

4. To provide descriptive values for activity labels a new variable "activitylabel" is added to dataset, that is a factor variable with levels mentioned in file activity_labels.txt (STEP 3 of assignment)
4. To provide descriptive values for activity labels a new variable *"activitylabel"* is added to dataset, that is a factor variable with levels mentioned in file activity_labels.txt (**STEP 3**: *Use descriptive activity names to name the activities in the data set* of assignment)

5. Approriate names for dataset variables were assigned on the step 2.b (STEP 4)

6. Creates a melted data frame using activity label and subject as ids, after that mean values for all variables are calculated grouped by activity and subject using dcast() function and tidy data frame is created. (STEP 5)
5. Creates a melted data frame using activity label and subject as ids, after that mean values for all variables are calculated grouped by activity and subject using dcast() function and tidy data frame is created. (**STEP 5**: *Create a second, independent tidy data set with the average of each variable for each activity and each subject*)
