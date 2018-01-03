## Advanced Lane Finding

# 1. Camera calibration 
 The following two functions have been used to compute the camera calibration.
 1. findChessboardCorners 
 2. calibrateCamera 
 We use the around 20 images of the chess board taken using the camera in different angles and orientations.
 The array of points  conatining the image points and the object points corresponding to the internal corners on the chess-board are found using the findChessboardCorners. These points are inturn fed into the calibrateCamera function to compute the camera calibration.
 The following are the output of of the findChessboardCorners drawn on the chess-board images which are used for calibration.
 ![alt tag](https://github.com/raghu467/Advanced_lane_detection_p4/blob/master/Readme_images/1.Draw_corners.png)
 
 
 The following are the test_image and the corresponding un-distorted image(Result of the undistort functionality of the pipeline)
 ![alt tag](https://github.com/raghu467/Advanced_lane_detection_p4/blob/master/Readme_images/2.1chess_board_undistort.png)
 
 
 # IMAGE PROCESSING PIPELINE
 
 
 ## 1.Un-distort 
 The following is the output of the undistort (This function can be found in the jupyter notebook file under section(In [64]))
 The camera calibration matrix mtx and dist are used along with the opencv function undistort to un-distort the image.
 ![alt tag](https://github.com/raghu467/Advanced_lane_detection_p4/blob/master/Readme_images/3.%20Distor_un_Distort.png)
 
 

## 2.unwarp
 The following is the output of the unwarp (This function can be found in the jupyter notebook file under section(In [117]))
 
 ![alt tag](https://github.com/raghu467/Advanced_lane_detection_p4/blob/master/Readme_images/4.distort_unwrap.png)
 
 In this step we use getPerspectiveTransform to transfor the src points on the images bounding the lane to change the perspective using  the warpPerspective function from the  cv2 library.
 
The src and dst points are hardcoded in the code to the following values.

src_pts = np.float32([(575,464),
                  (704,464), 
                  (250,680), 
                  (1040,680)])
dst_pts = np.float32([(450,0),
                  (w-450,0),
                  (450,h),
                  (w-450,h)])
 
 The bounding box defining the src points on the image are drawin the image displyed above.
## 3.Tresholding 
The following is the output of the treshold stage<br>

 ![alt tag](https://github.com/raghu467/Advanced_lane_detection_p4/blob/master/Readme_images/5.pipeline_output_all_images.png)<br>
 
 I have experimented with several combinations of thresholding techniques and finally used lab_bthresh and hls_lthresh (This function can be found in the jupyter notebook file under section(In [112]))<br>

## 4. Lane detection

The functions Find_Lanes_Sliding_window is present in the section In [263] in the jupyter notebook.
In this function we first detect the histogram of the binarywarped image which is the output of the previous step.
Now we that we have histogram we find the local maxima on the left and right half of the histogram. The x cordinate of the left maxima and right (base x locations for left and right lanes).

![alt tag](https://github.com/raghu467/Advanced_lane_detection_p4/blob/master/Readme_images/5.1.4.histogram.png)<br>
![alt tag](https://github.com/raghu467/Advanced_lane_detection_p4/blob/master/Readme_images/5.1.1.histogram.png)<br>
 
 
The function then identifies 10 windows from which to identify lane pixels, each one centered on the midpoint of the pixels from the window below. We follow this procedure by moving the window up-wards till we reach the top of the image. Pixels belonging to each lane line are identified and the Numpy polyfit() method fits a second order polynomial to each set of pixels. The image below demonstrates how this process identifies the lanes.

![alt tag](https://github.com/raghu467/Advanced_lane_detection_p4/blob/master/Readme_images/5.2.lane_lines_sliding_window.png)<br>





 
