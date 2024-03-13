# Lane Detector
This project demonstrates lane detection in videos using OpenCV and basic computer vision techniques. The goal is to detect and overlay lane boundaries in a video stream.

## Libraries
- `cv2` (OpenCV): Used for image and video processing, including edge detection, image manipulation, and line detection.
- `numpy` (NumPy): Used for numerical operations and array manipulation.
- `PIL` (Pillow): Used for reading and manipulating images.
- `matplotlib.pyplot` (Matplotlib): Used for image visualization and plotting.

## Usage
1. Ensure that the required libraries (cv2, numpy, PIL, matplotlib.pyplot) are installed.
   ``` shell
   pip install opencv-python numpy PIL matplotlib
   ```
   
2. Prepare/capture a video file for lane detection. Update the cap = cv2.VideoCapture("test.mp4") line with the path to your video file.
3. Run the code, and the lane detection process will begin.
4. The program will display the processed frames in a new window, showing the lane boundaries overlaid on the original video frames.
5. Press the 'q' key to stop the program or wait until the video finishes.