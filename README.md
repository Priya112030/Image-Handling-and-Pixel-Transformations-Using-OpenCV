# Image-Handling-and-Pixel-Transformations-Using-OpenCV
## NAME : PRIYA B
## REG.NO : 212224230208
## AIM:

Write a Python program using OpenCV that performs the following tasks:

1. Read and display an image.
2. Adjust the brightness of an image.
3. Modify the image contrast.
4. Generate a third image using bitwise operations.


## Software Required:

- Anaconda - Python
- Jupyter Notebook (for interactive development and execution)
- OpenCV
- NumPy


## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (photo.p.jpeg) into B, G, R components and display the channels.


## Program:
```
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('photo.p.jpeg', cv2.IMREAD_COLOR)
# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original image")
plt.axis('off')  # Removes axis ticks and labels
plt.show()

# 1.Draw a line from the top-left to the bottom-right of the image
# Load the image
image = cv2.imread('photo.p.jpeg')
# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
# Draw a line from top-left to bottom-right
line_img = cv2.line(img_rgb, (0, 0), (768, 600), (255, 0, 0), 2) # cv2.line(image, start_point, end_point, color, thickness)
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('off')  
plt.show()

# 2.Draw a circle at the center of the image.
# Load the image
image = cv2.imread('photo.p.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
circle_img = cv2.circle(img_rgb,(400,300),150,(255,255,0),10) # cv2.circle(image, center, radius, color, thickness)
plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()

# 3.Draw a rectangle around  the whole image
# Load the image
image = cv2.imread('photo.p.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img.shape
# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (768, 600), (0, 255, 255), 10)  # cv2.rectangle(image, start_point, end_point, color, thickness)
plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()

# 4.Add the text "OpenCV Drawing" at the top-left corner of the image.
# Load the image
image = cv2.imread('photo.p.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
# Add text to the image
text_img = cv2.putText(img_rgb, "PRIYA B", (50,100), cv2.FONT_HERSHEY_SIMPLEX, 3, (0, 255, 255), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)
plt.imshow(text_img, cmap='viridis')  
plt.title("IMAGE WITH TEXT")
plt.axis('off')  
plt.show()

# 5.Convert the image from RGB to HSV,GRAY,YCrCb,RGB
# Load the image
image = cv2.imread('photo.p.jpeg')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
# Original RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
# HSV Image
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)
# YCrCb Image
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")

# Modify a block of pixels (300x300) to white, starting from (200, 200)
image[200:500, 200:500] = [255, 0, 255]  # Rows: 200-499, Columns: 200-499
# Convert BGR to RGB for displaying with Matplotlib
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("off")
plt.show()

#  6.Resize the original image to half its size and display it.
# Load the image
image = cv2.imread('photo.p.jpeg')
image.shape
# Resize the image to half its size
resized_image = cv2.resize(image, (768 // 2, 600 // 2))  # (new_width, new_height)
# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)
resized_image_rgb.shape
# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
# Load the image
image = cv2.imread('photo.p.jpeg')
image.shape
# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349
# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)
# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()

# 7.Flip the original image horizontal,vertical and display it.
# Load the image
image = cv2.imread('photo.p.jpeg')
# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)
# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)
# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)
# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)
# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
```

## Output:
<img width="266" height="407" alt="image" src="https://github.com/user-attachments/assets/f2bfb2eb-97eb-4447-8992-57c595dbcf9c" />

<img width="242" height="426" alt="image" src="https://github.com/user-attachments/assets/ce458824-1c2a-4f94-9c67-14d78e76b2c8" />

<img width="240" height="427" alt="image" src="https://github.com/user-attachments/assets/0d867ed3-6306-454f-800a-c41a7e73add9" />

<img width="256" height="417" alt="image" src="https://github.com/user-attachments/assets/6f137f84-20f4-4c4b-91fe-bf6cc7b723d9" />

<img width="240" height="422" alt="image" src="https://github.com/user-attachments/assets/4c84fb41-ef24-483c-803b-3cb5efd2fe6f" />

<img width="252" height="448" alt="image" src="https://github.com/user-attachments/assets/2a09eb91-3bb2-4b1d-99ad-c577d58e58cf" />

<img width="256" height="445" alt="image" src="https://github.com/user-attachments/assets/250b8b42-fd1a-4852-890d-fa8d02172c35" />

<img width="242" height="415" alt="image" src="https://github.com/user-attachments/assets/c1ccb938-13a9-4092-baed-3955c658b516" />

<img width="236" height="438" alt="image" src="https://github.com/user-attachments/assets/b2cc2049-c2d5-4807-a104-b1c7c4812416" />

<img width="251" height="450" alt="image" src="https://github.com/user-attachments/assets/b2e1e0c5-eac0-45bf-82fc-23c07f645dcf" />

<img width="297" height="413" alt="image" src="https://github.com/user-attachments/assets/3701dcb2-592e-40f1-9dca-0b838b73432c" />

<img width="490" height="406" alt="image" src="https://github.com/user-attachments/assets/5b102639-d294-4355-bd4c-333acc4d0e76" />

<img width="402" height="422" alt="image" src="https://github.com/user-attachments/assets/300c25f0-a4e2-4430-9a52-cb2d5a96524c" />

<img width="236" height="421" alt="image" src="https://github.com/user-attachments/assets/b7c872ae-bff8-42e1-b473-f3f3179dce14" />

<img width="246" height="452" alt="image" src="https://github.com/user-attachments/assets/d18da92b-e5df-425d-9d5a-41487a080658" />


## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.




