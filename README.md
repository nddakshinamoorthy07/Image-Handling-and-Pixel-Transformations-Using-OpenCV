# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

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
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** DAKSHINA MOORTHY N D
- **Register Number:** 212224230049

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("boy.jpg", cv2.IMREAD_GRAYSCALE)
```

#### 2. Print the image width, height & Channel.
```
height, width = img.shape

print("Width :", width)
print("Height:", height)
print("Channel: 1")
```

#### 3. Display the image using matplotlib imshow().
```
plt.imshow(img, cmap="gray")
plt.title("Grayscale Image")
plt.axis("off")
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```
cv2.imwrite("boy.png", img)
print("Image saved successfully.")
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```
img_gray = cv2.imread("boy.png", cv2.IMREAD_GRAYSCALE)
img_color = cv2.cvtColor(img_gray, cv2.COLOR_GRAY2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```
plt.imshow(img_color)
plt.title("Colour Image")
plt.axis("off")
plt.show()

height, width, channel = img_color.shape

print("Width :", width)
print("Height:", height)
print("Channel:", channel)
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```
cropped = img_color[150:450, 200:500]

plt.imshow(cropped)
plt.title("Cropped Image")
plt.axis("off")
plt.show()
```

#### 8. Resize the image up by a factor of 2x.
```
resized = cv2.resize(
    img_color,
    None,
    fx=2,
    fy=2,
    interpolation=cv2.INTER_LINEAR
)

plt.imshow(resized)
plt.title("Resized Image (2x)")
plt.axis("off")
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```
flipped = cv2.flip(cropped, 1)

plt.imshow(flipped)
plt.title("Horizontally Flipped Image")
plt.axis("off")
plt.show()
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```
flipped = cv2.flip(cropped, 1)

plt.imshow(flipped)
plt.title("Horizontally Flipped Image")
plt.axis("off")
plt.show()
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```
image = cv2.imread('boy.jpg') 

img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)


# Display the image
plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('off')  
plt.show()
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```
rect_color = (255, 0, 255)

cv2.rectangle(
    img_rgb,
    (250, 180),
    (500, 450),
    rect_color,
    3
)
```

#### 13. Display the final annotated image.
```
plt.imshow(img_rgb)
plt.title("Annotated City Image")
plt.axis("off")
plt.show()
```

#### 14. Read the image ('Boy.jpg').
```
img = cv2.imread("boy.jpg")
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 15. Adjust the brightness of the image.
```
# Create a matrix of ones (with data type float64)

matrix = np.ones(img.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```
img_brighter = cv2.add(img, matrix)
img_darker = cv2.subtract(img, matrix)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(img_darker, cv2.COLOR_BGR2RGB))
plt.title("Darker Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(img_brighter, cv2.COLOR_BGR2RGB))
plt.title("Brighter Image")
plt.axis("off")

plt.show()
```

#### 18. Modify the image contrast.
```
# Create two higher contrast images using the 'scale' option
# with factors of 1.1 and 1.2 (without overflow fix)

img_higher1 = cv2.convertScaleAbs(img, alpha=1.1, beta=0)
img_higher2 = cv2.convertScaleAbs(img, alpha=1.2, beta=0)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(img_higher1, cv2.COLOR_BGR2RGB))
plt.title("Contrast 1.1")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(img_higher2, cv2.COLOR_BGR2RGB))
plt.title("Contrast 1.2")
plt.axis("off")

plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```
B, G, R = cv2.split(img)

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(B, cmap="gray")
plt.title("Blue")

plt.subplot(1,3,2)
plt.imshow(G, cmap="gray")
plt.title("Green")

plt.subplot(1,3,3)
plt.imshow(R, cmap="gray")
plt.title("Red")

plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```
merged_rgb = cv2.merge((R, G, B))

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(1,2,2)
plt.imshow(merged_rgb)
plt.title("Merged RGB")

plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

H, S, V = cv2.split(hsv)

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(H, cmap="gray")
plt.title("Hue")

plt.subplot(1,3,2)
plt.imshow(S, cmap="gray")
plt.title("Saturation")

plt.subplot(1,3,3)
plt.imshow(V, cmap="gray")
plt.title("Value")

plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```
merged_hsv = cv2.merge((H, S, V))
merged_bgr = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2BGR)

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(1,2,2)
plt.imshow(cv2.cvtColor(merged_bgr, cv2.COLOR_BGR2RGB))
plt.title("Merged HSV")

plt.axis("off")
plt.show()
```

## Output:
- **i)** Read and Display an Image.
- <img width="671" height="525" alt="image" src="https://github.com/user-attachments/assets/3eeedd78-d5cd-40d4-a030-0f0bbce153df" />
<img width="675" height="530" alt="image" src="https://github.com/user-attachments/assets/915705d8-a55d-4f11-bd16-0b8781a2b6b3" />

<img width="667" height="540" alt="image" src="https://github.com/user-attachments/assets/651e01e8-cd49-4eb7-844e-1715fad674b0" />

<img width="653" height="533" alt="image" src="https://github.com/user-attachments/assets/dbe3c41b-f4b6-4c23-b131-8c64fde873f5" />

<img width="697" height="497" alt="image" src="https://github.com/user-attachments/assets/f5f359b1-8570-43aa-8687-b3abf8099b29" />

<img width="660" height="513" alt="image" src="https://github.com/user-attachments/assets/674420fe-4eab-4ef4-9b29-9f825d982028" />

<img width="710" height="526" alt="image" src="https://github.com/user-attachments/assets/7ad51062-53f5-4942-b32a-be6b9b79cf1c" />

<img width="512" height="525" alt="image" src="https://github.com/user-attachments/assets/80c9e3c0-e572-42ac-b913-123f070a5d7a" />

<img width="647" height="462" alt="image" src="https://github.com/user-attachments/assets/2700ca2a-9ce7-4958-8960-f2dea5a83a30" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

