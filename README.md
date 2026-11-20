# EXP-1-Image-Handling-and-Pixel-Transformations-Using-OpenCV
### Name : Santhosh V
### Reg no: 212224230251

## AIM

To perform basic image-processing operations on an input image using
Python and OpenCV, including drawing shapes and text, color-space
conversion, pixel modification, resizing, cropping, flipping, and saving
the processed image.

## Input Image

<img width="814" height="937" alt="photo" src="https://github.com/user-attachments/assets/19023887-1238-4e94-ac24-7d9eba68b760" />



## PROCEDURE

1.  Import the required libraries: OpenCV (`cv2`) and Matplotlib
    (`matplotlib.pyplot`).
2.  Read the input image `Qno. 1.jpg` from the local directory using
    `cv2.imread()`.
3.  Convert the image from BGR to RGB format and display the original
    image.
4.  Draw a line from the top-left to the bottom-right of the image.
5.  Draw a circle at the center of the image, draw a rectangle around
    the image, and add the text **OpenCV Drawing**.
6.  Convert the RGB image into HSV, grayscale, and YCrCb color spaces
    and display each result.
7.  Convert the HSV image back into RGB format and display it.
8.  Access the pixel at coordinate `(100, 100)` and print its value.
    Modify the required pixel or region to white.
9.  Resize the original image to half its width and height.
10. Crop a region of interest (ROI) from the image and display it.
11. Flip the original image horizontally and vertically and display both
    results.
12. Save the final processed image using `cv2.imwrite()`.



## PROGRAM

### 1. Import Libraries and Display Original Image

```python
import cv2
import matplotlib.pyplot as plt

# Read the image
img = cv2.imread('my.jpeg', cv2.IMREAD_COLOR)

# Convert BGR to RGB
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display original image
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')
plt.show()
```

### 2. Drawing a Line

```python
image = cv2.imread('my.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

line_img = cv2.line(img_rgb, (0, 0), (900, 1200), (255, 0, 0), 10)

plt.imshow(line_img)
plt.title("Image with Line")
plt.axis('off')
plt.show()
```

### 3. Drawing a Circle

```python
image = cv2.imread('my.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

circle_img = cv2.circle(img_rgb, (450, 400), 250, (255, 0, 0), 10)

plt.imshow(circle_img)
plt.title("Image with Circle")
plt.axis('off')
plt.show()
```

### 4. Drawing a Rectangle

```python
image = cv2.imread('my.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

rectangle_img = cv2.rectangle(img_rgb, (100, 50), (750, 600), (0, 0, 255), 10)

plt.imshow(rectangle_img)
plt.title("Image with Rectangle")
plt.axis('off')
plt.show()
```

### 5. Adding Text to Image

```python
image = cv2.imread('my.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

text_img = cv2.putText(
    img_rgb,
    "OpenCV Drawing",
    (10, 30),
    cv2.FONT_HERSHEY_SIMPLEX,
    1,
    (0, 0, 0),
    10
)

plt.imshow(text_img)
plt.title("Image with Text")
plt.axis('off')
plt.show()
```

### 6. Color Space Conversion

```python
image = cv2.imread('my.jpeg')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
plt.show()

# RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
plt.show()

# RGB to Grayscale
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
plt.show()

# RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
plt.show()

# HSV to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
plt.show()
```

### 7. Pixel Transformation

```python
image = cv2.imread('my.jpeg')

# Modify pixel region to white
image[200:600, 200:800] = [255, 255, 255]

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Modified Image")
plt.axis("off")
plt.show()
```

### 8. Resizing Image

```python
image = cv2.imread('my.jpeg')

print(image.shape)

# Resize image to half size
resized_image = cv2.resize(image, (768 // 2, 600 // 2))

resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

print(resized_image_rgb.shape)

plt.imshow(resized_image_rgb)
plt.title("Resized Image")
plt.axis("off")
plt.show()
```

### 9. Cropping Image (ROI)

```python
image = cv2.imread('my.jpeg')

print(image.shape)

# Crop a region of interest
roi = image[50:350, 50:350]

roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest")
plt.axis("off")
plt.show()
```

### 10. Horizontal Flip

```python
image = cv2.imread('my.jpeg')

flipped_horizontally = cv2.flip(image, 1)

flipped_horizontally_rgb = cv2.cvtColor(
    flipped_horizontally, cv2.COLOR_BGR2RGB
)

plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()
```

### 11. Vertical Flip

```python
flipped_vertically = cv2.flip(image, 0)

flipped_vertically_rgb = cv2.cvtColor(
    flipped_vertically, cv2.COLOR_BGR2RGB
)

plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
plt.show()
```

### 12. Saving Processed Image

```python
cv2.imwrite("processed_image.jpg", image)

print("Image saved successfully")
```


## OUTPUT

The following outputs are obtained after executing the program:

### 1.  Original input image displayed.
<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/e08c53ab-157a-4776-80a1-70e69f27dd10" />



### 2.  Image with a diagonal line drawn from top-left to bottom-right.

<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/41c7552f-8f36-494f-a9f7-0fb5fa6afa59" />


### 3.  Image with a circle at its center.

<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/efd4109e-dd32-4469-bb98-4fefabaf8e3f" />


### 4.  Image with a rectangular border.

<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/eebef5f4-ae3a-4991-abaf-ffef40c57d87" />


### 5.  Image displaying the text **OpenCV Drawing**.

<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/478f0c69-9e37-4614-9750-ea820bacf5c6" />


### 6.  HSV, grayscale, and YCrCb versions of the image.

<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/58338876-07df-4748-a211-3ed3cfe528dd" />

<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/2a1ff003-8145-400b-a486-279b669d68f4" />

<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/0cd344f3-6cc8-4db7-af30-e1f04d586950" />


### 7.  Image converted from HSV back to RGB.

<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/dbe0cfd0-b493-4162-b65b-5afb15a68f5c" />


### 8.  Image with the selected pixel changed to white.

<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/b52cfc26-5eae-472b-bbc7-9aa9ad35a995" />

### 9.  Resized image with half the original width and height.

<img width="493" height="410" alt="download" src="https://github.com/user-attachments/assets/a487934c-e3ed-4e8f-a4a0-93ffc37859f0" />


### 10. Cropped region of interest (ROI).

<img width="389" height="410" alt="download" src="https://github.com/user-attachments/assets/4e34790f-4692-4c72-af4d-a266eeb999f2" />


### 11. Horizontally flipped image.

<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/18546643-6fd4-422a-9e70-454392adcbeb" />


### 12. Vertically flipped image.
<img width="341" height="410" alt="download" src="https://github.com/user-attachments/assets/a6a7c018-5fc6-4a0f-85b6-5c61010cc7e3" />




## RESULT

Thus, basic image-processing operations such as image loading,
displaying, drawing, color-space conversion, pixel modification,
resizing, cropping, flipping, and saving were performed successfully
using Python and OpenCV.
