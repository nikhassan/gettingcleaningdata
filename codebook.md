# Code Book for the Tidy Dataset
## Reading the data
I used read.table() to read the two data training and test data sets X_train.txt and X_test.txt  using option sep="" to read lines containing any any number of space 
Using dim() to view the data characteristics, I decide that the data can be merged row-wise using rbind()
## Selecting features
Based on the instruction to extract only the measurements on the mean and standard deviation for each measurement I first read into index the features from features.txt and use grepl to select which feature contains the expression "mean" or "std" in their names. I use the row numbers as a vector (rowvector) to act as an index to pick the right features
## Naming the activities
To get the type of activities and their description (e.g. standing) I read the y_test.txt, y_train.txt and activity_labels.txt files
## Append activity descriptions to activity type and append to data file
I use dplyr function left_join() to append activity descriptions to type of activities and merge the two files into a single file to later append using cbind() to the main data file meanstd
## Append subject ids into main data file
I read in subject_train.txt subject_test.txt to get the subject ids, merge the training and test subjects and append to the main data file
## Create descriptive feature names
I load the selected features into Excel and use find and replace to rename the features using more descriptive names
E.g. "tBodyAcc-mean()-X" is "renamed	Mean Body Acc X-Axis" and "fBodyAccJerk-meanFreq()-X" is renamed "Fourier Trans Mean Freq Bdy Jerk X-Axis". I then convert the selected features into a character vector and then append to them, three additional features "subject, act type and description". I can now rename all columns using names()
## Create a second independent tidy data set with the average of each variable for each activity and each subject.
To create the average of the averages, I use aggregate) function and group by the activity id and the subject id, and use mean as the function.
