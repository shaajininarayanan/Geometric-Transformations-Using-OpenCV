# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation
- Image Scaling (Resizing)
- Image Shearing
- Image Reflection (Flipping)
- Image Rotation

---

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

---

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Read the input image in color mode.

### Step 3: Image Translation

- Create a translation matrix to shift the image
- Move the image 50 pixels to the right and 80 pixels down
- Apply transformation using `cv2.warpAffine()`
- Display original and translated images

### Step 4: Image Scaling

- Resize the image to 0.5× (downscale)
- Resize the image to 2× (upscale)
- Use `cv2.resize()`
- Display original, downscaled, and upscaled images

### Step 5: Image Shearing

- Create transformation matrices for:
  - Horizontal shearing
  - Vertical shearing
- Apply transformations using `cv2.warpAffine()`
- Display original and sheared images

### Step 6: Image Reflection

- Perform flipping using `cv2.flip()`:
  - Horizontal reflection
  - Vertical reflection
  - Both axes
- Display all reflected images

### Step 7: Image Rotation

- Create rotation matrices for:
  - 45° rotation
  - 90° rotation
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`
- Display original and rotated images

---

## Program

### Developed By:

**Name:** Shaajini N

### Register No:

**212225040395**

### Program 1: Image Translation

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread(r"C:\Users\acer\images\Boy.jpg")

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    h, w = img.shape[:2]

    M = np.float32([[1, 0, 50], [0, 1, 80]])
    translated = cv2.warpAffine(img, M, (w, h))

    plt.figure(figsize=(10, 4))

    plt.subplot(1, 2, 1)
    plt.imshow(img)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.imshow(translated)
    plt.title("Translated Image")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

### Program 2: Image Scaling

```python
import cv2
import matplotlib.pyplot as plt

img = cv2.imread(r"C:\Users\acer\images\Boy.jpg")

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    downscaled = cv2.resize(img, None, fx=0.5, fy=0.5)
    upscaled = cv2.resize(img, None, fx=2, fy=2)

    plt.figure(figsize=(12, 4))

    plt.subplot(1, 3, 1)
    plt.imshow(img)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 3, 2)
    plt.imshow(downscaled)
    plt.title("Downscaled (0.5x)")
    plt.axis("off")

    plt.subplot(1, 3, 3)
    plt.imshow(upscaled)
    plt.title("Upscaled (2x)")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

### Program 3: Image Shearing

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread(r"C:\Users\acer\images\Boy.jpg")

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    h, w = img.shape[:2]

    horizontal_matrix = np.float32([
        [1, 0.3, 0],
        [0, 1, 0]
    ])

    vertical_matrix = np.float32([
        [1, 0, 0],
        [0.3, 1, 0]
    ])

    horizontal = cv2.warpAffine(
        img, horizontal_matrix, (w, h)
    )

    vertical = cv2.warpAffine(
        img, vertical_matrix, (w, h)
    )

    plt.figure(figsize=(12, 4))

    plt.subplot(1, 3, 1)
    plt.imshow(img)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 3, 2)
    plt.imshow(horizontal)
    plt.title("Horizontal Shearing")
    plt.axis("off")

    plt.subplot(1, 3, 3)
    plt.imshow(vertical)
    plt.title("Vertical Shearing")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

### Program 4: Image Reflection

```python
import cv2
import matplotlib.pyplot as plt

img = cv2.imread(r"C:\Users\acer\images\Boy.jpg")

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    horizontal = cv2.flip(img, 1)
    vertical = cv2.flip(img, 0)
    both = cv2.flip(img, -1)

    plt.figure(figsize=(12, 4))

    plt.subplot(1, 4, 1)
    plt.imshow(img)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 4, 2)
    plt.imshow(horizontal)
    plt.title("Horizontal Flip")
    plt.axis("off")

    plt.subplot(1, 4, 3)
    plt.imshow(vertical)
    plt.title("Vertical Flip")
    plt.axis("off")

    plt.subplot(1, 4, 4)
    plt.imshow(both)
    plt.title("Both Axes Flip")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

### Program 5: Image Rotation

```python
import cv2
import matplotlib.pyplot as plt

img = cv2.imread(r"C:\Users\acer\images\Boy.jpg")

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    h, w = img.shape[:2]

    M45 = cv2.getRotationMatrix2D(
        (w // 2, h // 2), 45, 1
    )

    M90 = cv2.getRotationMatrix2D(
        (w // 2, h // 2), 90, 1
    )

    rotated45 = cv2.warpAffine(img, M45, (w, h))
    rotated90 = cv2.warpAffine(img, M90, (w, h))

    plt.figure(figsize=(12, 4))

    plt.subplot(1, 3, 1)
    plt.imshow(img)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 3, 2)
    plt.imshow(rotated45)
    plt.title("Rotation 45 Degrees")
    plt.axis("off")

    plt.subplot(1, 3, 3)
    plt.imshow(rotated90)
    plt.title("Rotation 90 Degrees")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

---

## Output

### Image Translation

- Original image is displayed
- Translated image (shifted right and down) is displayed

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/37b52263-4c77-4ae3-9628-8580e7dab0a5" />


### Image Scaling

- Original image is displayed
- Downscaled image (0.5×) is displayed
- Upscaled image (2×) is displayed

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/5e83714e-4f87-4eed-9f1f-fb7bc0736331" />


### Image Shearing

- Original image is displayed
- Horizontally sheared image is displayed
- Vertically sheared image is displayed

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/7eb5b9ff-0f26-4921-b1ca-04393ab6a562" />


### Image Reflection

- Original image is displayed
- Horizontally flipped image is displayed
- Vertically flipped image is displayed
- Both-axis flipped image is displayed

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/4fc3e6a4-e21b-42fd-999d-948035f64844" />


### Image Rotation

- Original image is displayed
- 45° rotated image is displayed
- 90° rotated image is displayed

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/a3d98fcf-f5bd-452a-a103-47bae55976c4" />


---

## Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
