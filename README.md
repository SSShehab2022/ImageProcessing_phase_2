# ImageProcessing_phase_2

# Pipelining steps:-
  - **Objective:-** Perform a Histogram of Oriented Gradients (HOG) feature extraction on a labeled training set of images and train a classifier Linear SVM classifier

## 1. Train the model:-
- By using dataset from net [https://s3.amazonaws.com/udacity-sdc/Vehicle_Tracking/vehicles.zip] for vehicles and [https://s3.amazonaws.com/udacity-sdc/Vehicle_Tracking/non-vehicles.zip] for non-vehicle.

  No. of car images: 8792

  No of non-car images: 8968

  Image shape: (64, 64, 3)

  The dataset is fairly balanced.
  
 ## 2. Feature Extraction Method:-
 - Methods for feature extraction are created in cell 6:-
   1. **bin_spatial()** computes binned colour features by scaling images down.
   2. **color_hist()** computes colour histogram features.
   3. **get_hog_features()** returns HOG features and visualisation.
   4. **extract_features()** wraps and combines the above functions. 
   
 ## 3. HOG Visualisation:-
 - Using **YCrCb** color channels as it results high accuracy in the classifier.
 - Selecting parameters by trial and error to optimize accuracy.
 
 ## 4. Data preparation:-
 - We apply a scaler to the feature vector.
 - Split the data into training/validation sets.
 
 ## 5. Classifier:-
 - In cell 11 I run the classifier on the dataset with a 0.989 accuracy and gave acceptable output.
 
 ## 6. Sliding Window Search:-.
 - Applying HOG window search routine which it is a region proposer that scans select portions of the image and checks for presence of a vehicle.
 - The cell size and cell position are determined by the way the road is laid out, and the distance of vehicles from the camera.

 ## 7. Heatmap results:-
 - The outputs of this heatmap are recorded and added to a queue of length n in **detect_history()** (cell 16).
 - By using this queue, I'm able to smooth my bounding boxes between frames. This step helps reduce false positives that would be mis-classified over          consecutive frames. The result is improved accuracy and a smoother overall result.

  
