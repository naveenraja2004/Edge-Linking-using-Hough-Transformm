# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

##program

```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Replace with your image path
image = cv2.imread('PHOTO 1.jpg') 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)
# Detect lines using the probabilistic Hough transform
lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)

# Draw the lines on the original image
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)

# Displaying results using Matplotlib
plt.figure(figsize=(12, 12))

# Input Image and Grayscale Image
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Input Image')
plt.axis('off')

plt.subplot(2, 2, 2)
plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')

# Canny Edge Detection Output
plt.subplot(2, 2, 3)
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detector Output')
plt.axis('off')

# Hough Transform Result
plt.subplot(2, 2, 4)
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('off')

# Display all results
plt.show()

```
## Output


### Input image and grayscale image
![output](./p1.png)
![Screenshot 2024-10-03 113420](https://github.com/user-attachments/assets/586e9b19-70a8-44f6-9940-73c0a1c91319)

![Screenshot 2024-10-03 113412](https://github.com/user-attachments/assets/70ca37e8-17b5-4ff4-93d3-67d3f7c28db4)

### Canny Edge detector output
![output](./p2.png)

![Screenshot 2024-10-03 113430](https://github.com/user-attachments/assets/cb71f3c0-cc94-44f2-8b35-454c57eaed34)

### Display the result of Hough transform
![output](./p3.png)

![Screenshot 2024-10-03 113441](https://github.com/user-attachments/assets/54589e13-5438-482d-8c59-89fdaaf5c6e4)
