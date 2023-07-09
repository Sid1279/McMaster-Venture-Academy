# Lane Detector
This project demonstrates lane detection in videos using OpenCV and basic computer vision techniques. The goal is to detect and overlay lane boundaries in a video stream.

## Libraries
- `cv2 ` (OpenCV): Used for image and video processing, including edge detection, image manipulation, and line detection.
- `numpy` (NumPy): Used for numerical operations and array manipulation.
- `PIL` (Pillow): Used for reading and manipulating images.
- `matplotlib.pyplot` (Matplotlib): Used for image visualization and plotting.

## How it works
The code performs the following steps to detect and overlay lane boundaries in a video:
1. Canny Edge Detection
   - The canny() function converts the input image to grayscale and applies a Gaussian blur to reduce noise. Canny edge detection is then performed to detect edges in the image.
2. Region of Interest Selection
   - The region_of_interest() function creates a mask to define the region of interest in the image where the lane boundaries are expected.
   - The mask is created as a triangle shape at the bottom center of the image.
   - The masked image is obtained by applying the mask to the Canny edge-detected image.

3. Hough Line Detection
   - The houghLines() function applies the Hough transform to the cropped Canny image to detect lines. Detected lines are returned as a set of endpoints.

4. Line Averaging and Drawing
   - The average_slope_intercept() function calculates the average slope and intercept for left and right lane boundaries.
   - Lane lines are then created by extrapolating the averaged slope and intercept values.
   - The display_lines() function overlays the detected lane lines on a black image.
   - The addWeighted() function combines the lane lines with the original frame to create a final output image.

5. Video Processing Loop
   - The main program reads frames from a video using cv2.VideoCapture().
   - For each frame, the lane detection pipeline is applied to detect and overlay lane boundaries.
   - The processed frame is displayed, and the resulting frames are stored in an array.
   - The program terminates when the 'q' key is pressed or when the video ends.


## Usage
1. Ensure that the required libraries (cv2, numpy, PIL, matplotlib.pyplot) are installed.
   ``` shell
   pip install opencv-python numpy PIL matplotlib
   ```
   
3. Prepare/capture a video file for lane detection. Update the cap = cv2.VideoCapture("test2.mp4") line with the path to your video file.
4. Run the code, and the lane detection process will begin.
5. The program will display the processed frames in a new window, showing the lane boundaries overlaid on the original video frames.
6. Press the 'q' key to stop the program or wait until the video finishes.
