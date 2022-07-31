# LetsGrowMore Internship: Data Science
# Beginner Task 1: Image to pencil sketch with python
*submitted by* **Ashwath B **

---
Description
    
  We need to read the image in RBG format and then convert it to a grayscale image. This will turn an image into a classic black and white photo. Then the next thing to do is invert the grayscale image also called negative image, this will be our inverted grayscale image. Inversion can be used to enhance details. Then we can finally create the pencil sketch by mixing the grayscale image with the inverted blurry image. This can be done by dividing the grayscale image by the inverted blurry image. Since images are just arrays, we can easily do this programmatically using the divide function from the cv2 library in Python.

## Import all libraries

import cv2
from google.colab.patches import cv2_imshow
import matplotlib.pyplot as plt

## Read the image

img=cv2.imread('IMG-20220207-WA0010.jpg')

cv2_imshow(img)

## Store as RGB format

RGB_img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.imshow(RGB_img)
plt.axis(False)
plt.savefig('temp.png')
plt.show()

## Convert into Grayscale image

gray_scale_image=cv2.cvtColor(RGB_img, cv2.COLOR_BGR2GRAY)
cv2_imshow(gray_scale_image)

## Invert the Grayscale image 

inverted_image = cv2.bitwise_not(gray_scale_image)
cv2_imshow(inverted_image)

## Blur the inverted image

img_smoothing = cv2.GaussianBlur(inverted_image, (21, 21),sigmaX=0, sigmaY=0)
cv2_imshow(img_smoothing)

## Create pencil sketch by using divide function on grayscale image by blurry image

def pencil_sketch(x,y):
  return cv2.divide(x, 255 - y, scale=250)

pencil_sketch=pencil_sketch(gray_scale_image, img_smoothing)
cv2_imshow(pencil_sketch)

## Final Conversion of RGB image to pencil sketch

cv2_imshow(img)
cv2_imshow(pencil_sketch)

# **Thank you!!**

---

