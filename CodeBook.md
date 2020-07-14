
## The run_analysis.R script performs the download and preparation of data to then apply the 5 actions required by the course project.
 
### 0. Download the dataset 
    Dataset downloaded and extracted under the folder called UCI HAR Dataset
    
   Assign each data to variables
    features <- features.txt  
    activities <- activity_labels.txt  -- corresponding measurements (labels)
    subject_test <- test/subject_test.txt
    x_test <- test/X_test.txt  -- recorded features test data
    y_test <- test/y_test.txt  -- test data of activities labels
    Subject_train <- test/subject_train.txt
    x_train <- test/X_train.txt   -- recorded features train data
    y_train <- test/y_train.txt   -- train data of activities labels

### 1. Merges the training and the test sets to create one data set
    X (10299 rows, 561 columns) created by merging x_train and x_test using rbind() function
    Y (10299 rows, 1 column)    created by merging y_train and y_test using rbind() function
    subject (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function
    Merged_Data (10299 rows, 563 column) is created by merging Subject, Y and X using cbind() function

### 2. Extracts only the measurements on the mean and standard deviation for each measurement
TidyData (10299 rows, 88 columns) subsetting of Merged_Data, only with columns: subject, and the measurements on the mean and standard deviation (std)
    
### 3. Uses descriptive activity names to name the activities in the data set
Replaced with corresponding activity, taken from second column of the activities, the Entire (variable) in code column to the TidyData.

## 4. Appropriately labels the data set with descriptive variable names
    Code column in TidyData renamed into activities
    The Acc in column’s rename Accelerometer
    The Gyro in column’s rename Gyroscope
    The BodyBody in column’s rename Body
    The Mag in column’s rename Magnitude
    The character f in column’s rename Frequency
    The character t in column’s rename Time

## 5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
    FinalDataSet file have (180 rows, 88 columns) and was created by sumarizing TidyData.
    Take the means of each variable for each activity and each subject, after groupped by subject and activity.
    Export FinalDataSet into FinalDataSet.txt file.
