# Cursor Controller 

This script allows you to control your computer's cursor and perform clicks using hand gestures captured through your webcam. It utilizes the OpenCV and PyAutoGUI libraries along with the HandTrackingModule from the CVZone library.

## How It Works 🔧

This script utilizes computer vision and hand-tracking techniques to control the computer's cursor and perform clicks using hand gestures captured through the webcam. Here's an overview of how the script works:

1. The script captures frames from the webcam using OpenCV and resizes them to match the screen resolution using PyAutoGUI.

2. It uses the HandDetector class from the HandTrackingModule to detect and track the landmarks of a single hand in each frame. The hand landmarks include the positions of the fingers, palm, and other important points on the hand.

3. For the detected hand, the position of the tip of the index finger is considered the cursor position. By mapping the position of the finger relative to the bounding box of the hand, the script calculates the corresponding cursor position on the screen.

4. The script determines the number of fingers held up using the HandDetector class. Based on the finger count, different actions are performed:

   - If 0 to 4 fingers are held up, the script moves the cursor to the corresponding screen position. It uses the PyAutoGUI library to control the cursor movement.
   - If all 5 fingers are held up, the script performs a mouse click at the current cursor position using the pyautogui.click() function.

5. The finger count is displayed on the image frame using OpenCV. It helps visualize finger detection and tracking.

6. The script continues to loop through frames from the webcam until the 'q' key is pressed, at which point the script terminates.

Please ensure that your webcam is properly set up, and there is sufficient lighting for accurate hand detection and tracking. Position your hand within the camera's view to interact with the script effectively.

Feel free to modify the script and experiment with different parameters to customize the behaviour according to your needs :)