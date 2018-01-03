## Advanced Lane Finding

# 1. Camera calibration 
 The following two functions have been used to compute the camera calibration.
 1. findChessboardCorners 
 2. calibrateCamera 
 We use the around 20 images of the chess board taken using the camera in different angles and orientations.
 The array of points  conatining the image points and the object points corresponding to the internal corners on the chess-board are found using the findChessboardCorners. These points are inturn fed into the calibrateCamera function to compute the camera calibration.
 The following are the output of of the findChessboardCorners drawn on the chess-board images which are used for calibration.
 ![alt tag](https://github.com/raghu467/Advanced_lane_detection_p4/tree/master/Readme_images/1.Draw_corners.png)
 
 The following are the oroginal image and the un-distorted.
 
 ![alt tag](https://github.com/raghu467/Advanced_lane_detection_p4/tree/master/Readme_images/2.un-distorted.png)
 
 The following are the test_image and the corresponding un-distorted image
 
 ![alt tag](https://github.com/raghu467/Advanced_lane_detection_p4/tree/master/Readme_images/3.un-distorted.png)
 
 
 
  
 
