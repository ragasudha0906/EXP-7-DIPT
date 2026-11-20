# EXP 07 - Record-HOUGH TRANSFORM
## NAME : RAGASUDHA R
## REG NO :212224230215

## AIM

To detect straight lines in an input image using the Canny edge detector and the Probabilistic Hough Transform (HoughLinesP) in OpenCV.

## PROCEDURE

1. *Start* the program and import the required libraries (cv2, numpy, and matplotlib.pyplot).
2. *Load* the input image using cv2.imread().
3. *Convert* the loaded BGR image into a grayscale image using cv2.cvtColor().
4. *Detect edges* in the grayscale image using the Canny edge detector (cv2.Canny()).
5. *Apply Hough Transform* (cv2.HoughLinesP()) on the edge-detected image to find the start and end coordinates $(x_1, y_1, x_2, y_2)$ of straight line segments.
6. *Draw the detected lines* onto the image using cv2.line() for each set of coordinates.
7. *Display* the original image, grayscale image, Canny edge image, and the final image with detected lines using matplotlib.pyplot.imshow().
8. *Stop* the program.

## CODE
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
# Step 2: Load the image using imread() from cv2 module
image = cv2.imread('photo.jpeg')  # Replace 'image.jpg' with your image path
# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert image to RGB for displaying
plt.title("Input Image")
plt.axis('off')
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)  # Canny edge detection with threshold values 50 and 150
# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
# Step 5: Using the HoughLinesP(), detect line coordinates for every point in the image
# The parameters of HoughLinesP are: image, resolution, threshold, minLineLength, maxLineGap
lines = cv2.HoughLinesP(edges, 1, np.pi / 180, 100, minLineLength=50, maxLineGap=10)
# Step 6: Using a for loop, draw the lines on the original image using the detected coordinates
# The lines variable contains the endpoints of the detected lines
for line in lines:
    x1, y1, x2, y2 = line
    cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)
# Display the result of Hough Transform (Image with lines)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Image with lines drawn
plt.title("Result of Hough Transform")
plt.axis('off')
```
## OUTPUT

<img width="925" height="552" alt="image" src="https://github.com/user-attachments/assets/51d9dc90-a17e-4b8a-8446-1d91ecaa2324" />
<img width="971" height="557" alt="image" src="https://github.com/user-attachments/assets/af9bad2d-bee5-4aea-9111-b0274df77594" />
<img width="1016" height="560" alt="image" src="https://github.com/user-attachments/assets/1366b6d0-14d0-47f9-bcc3-8edb1e570156" />
<img width="912" height="561" alt="image" src="https://github.com/user-attachments/assets/24ea8e55-0a00-4889-b888-c0f663442ffb" />

## RESULT

The straight lines in the image are detected using the Canny edge detector and Hough Transform.
The detected lines are drawn in green on the original image, and the output images are displayed successfully.
