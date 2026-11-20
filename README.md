# EXP 07 - Record-HOUGH TRANSFORM
## NAME : ALAGESHWARI V
## REG NO :212224240010
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
image = cv2.imread('photo.png')  # Replace 'image.jpg' with your image path
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

## OUTPUT:

<img width="722" height="528" alt="image" src="https://github.com/user-attachments/assets/8648dd5b-696e-481d-be5d-f66f9cd017b9" />

<img width="702" height="527" alt="image" src="https://github.com/user-attachments/assets/a30f7313-a80b-4d09-b936-b89b0c03153c" />

<img width="702" height="527" alt="image" src="https://github.com/user-attachments/assets/9e07d27a-60e2-4ea3-a816-fb6ea20aaf59" />

<img width="691" height="531" alt="image" src="https://github.com/user-attachments/assets/575e4783-f369-418a-8350-2290a7698540" />

## RESULT:

The straight lines in the image are detected using the Canny edge detector and Hough Transform.
The detected lines are drawn in green on the original image, and the output images are displayed successfully.

