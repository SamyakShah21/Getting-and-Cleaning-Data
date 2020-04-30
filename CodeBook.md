The __run_analysis.R__ script performs the data preparation and then followed by the 5 steps required as described in the course project’s definition.<br>
1. __The dataset:__
    - Dataset downloaded and extracted under the folder called _UCI HAR Dataset_.
2. __Assign each data to variables:__
    - _features <- features.txt_ : 561 rows, 2 columns
      The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
    - _activities <- activity_labels.txt_ : 6 rows, 2 columns
      List of activities performed when the corresponding measurements were taken and its codes (labels)
    - _subject_test <- test/subject_test.txt_ : 2947 rows, 1 column
      contains test data of 9/30 volunteer test subjects being observed
    - _x_test <- test/X_test.txt_ : 2947 rows, 561 columns
      contains recorded features test data
    - _y_test <- test/y_test.txt_ : 2947 rows, 1 columns
      contains test data of activities’code labels
    - _subject_train <- test/subject_train.txt_ : 7352 rows, 1 column
      contains train data of 21/30 volunteer subjects being observed
    - _x_train <- test/X_train.txt_ : 7352 rows, 561 columns
      contains recorded features train data
    - _y_train <- test/y_train.txt_ : 7352 rows, 1 columns
      contains train data of activities’code labels.
3. __Merges the training and the test sets to create one data set__
    - __X__ (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function
    - __Y__ (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function
    - __Subject__ (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function
    - __Merged_Data__ (10299 rows, 563 column) is created by merging Subject, Y and X using cbind() function

4. __Extracts only the measurements on the mean and standard deviation for each measurement:__
    - _TidyData_ (10299 rows, 88 columns) is created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

5. __Uses descriptive activity names to name the activities in the data set:__
    - Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the activities variable

6. Appropriately labels the data set with descriptive variable names
    - code column in TidyData renamed into activities
    - All Acc in column’s name replaced by Accelerometer
    - All Gyro in column’s name replaced by Gyroscope
    - All BodyBody in column’s name replaced by Body
    - All Mag in column’s name replaced by Magnitude
    - All start with character f in column’s name replaced by Frequency
    - All start with character t in column’s name replaced by Time

7. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
    - __FinalData__ (180 rows, 88 columns) is created by sumarizing TidyData taking the means of each variable for each activity and each subject, after groupped by subject and activity.
    - Export FinalData into _FinalData.txt_ file.
