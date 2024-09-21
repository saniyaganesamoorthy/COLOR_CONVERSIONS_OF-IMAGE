## Developed By : ADCHAYA KIRUTHIKA M.S
## Register Number : 212223230005
# COLOR_CONVERSIONS_OF-IMAGE
## AIM
To write a python program using OpenCV to do the following image manipulations.

i) Read, display, and write an image.

ii) Access the rows and columns in an image.

iii) Cut and paste a small portion of the image.

iv)To perform the color conversion between RGB, BGR, HSV, and YCbCr color models.


## Software Required:
Anaconda - Python 3.7
## Algorithm:
### Step1:
Choose an image and save it as a filename.jpg ,
### Step2:
Use imread(filename, flags) to read the file.
### Step3:
Use imshow(window_name, image) to display the image.
### Step4:
Use imwrite(filename, image) to write the image.
### Step5:
End the program and close the output image windows.
### Step6:
Convert BGR and RGB to HSV and GRAY
### Step7:
Convert HSV to RGB and BGR
### Step8:
Convert RGB and BGR to YCrCb
### Step9:
Split and Merge RGB Image
### Step10:
Split and merge HSV Image

# Program:

## 1) Read and display the image
```
image = cv2.imread('lokesh2.jpg')
image_resized = cv2.resize(image, (500,500))
plt.imshow(image_resized)
plt.show()
```
![1](https://github.com/user-attachments/assets/c92ec084-41a4-47d0-ac6c-d7324005c14d)

<br>
<br>

### 2)Draw Shapes and add text

### a)Draw line from top-left to the bottom-right

```
image1=image_resized.copy()
res = cv2.line(image1,(0,0),(500,500),(200,100,205),10)
cv2.imshow('Image Window', res)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![2](https://github.com/user-attachments/assets/e5db8a1b-da6c-4ded-baac-d85ed563d883)


### b) Draw a circle at the centre of the image
```
image2=image_resized.copy()
res1=cv2.circle(image2,(250,225),150,(240,0,0),10)
cv2.imshow('Image Window', res1)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![3](https://github.com/user-attachments/assets/2e227ec1-f7b7-4522-bdd2-e8f2c88a6c8b)


### c)Draw a rectangle around a specific region in interest
```
image3=image_resized.copy()
start=(180,150)
stop=(320,400)
color=(100,255,100)
thickness=10
res2=cv2.rectangle(image3,start,stop,color,thickness)
cv2.imshow('Image Window', res2)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![4](https://github.com/user-attachments/assets/1676775d-2899-48a8-85e2-c42e2b7cb489)

<br>
<br>

### d)Add the text "OpenCV Drawing" at the top-left corner of the image

```
image4=image_resized.copy()
org=(10,30)
fontface=cv2.FONT_HERSHEY_SIMPLEX
fontScale=1
res3=cv2.putText(image4,"OpenCV Drawing",org,fontface,fontScale,(255,0,0),2)
cv2.imshow('Image Window', res3)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![5](https://github.com/user-attachments/assets/d9f64fe3-5d9b-461c-ad46-b90e808e2077)

## 3)Image color conversion

### a) RGB TO HSV

```
image5=image_resized.copy()
hsv_image = cv2.cvtColor(image5, cv2.COLOR_RGB2HSV)
cv2.imshow('HSV Image', hsv_image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![6](https://github.com/user-attachments/assets/3a1d0801-6bdf-43a8-a439-3af9e7888bea)


### b) RGB TO GRAY
```
image6=image_resized.copy()
gray_image = cv2.cvtColor(image6, cv2.COLOR_RGB2GRAY)
cv2.imshow('GrayScale Image', gray_image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![7](https://github.com/user-attachments/assets/cf7fba9a-3152-49b5-bd67-4e50d0cd64a9)


### c) RGB TO YCrCb
```
image7=image_resized.copy()
ycrcb_image = cv2.cvtColor(image7, cv2.COLOR_RGB2YCrCb)
cv2.imshow('YCrCb Image', ycrcb_image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![8](https://github.com/user-attachments/assets/31b09942-4535-4adf-99f7-9a36726e86a9)


### d)HSV TO RGB

```
rgb_image=cv2.cvtColor(hsv_image, cv2.COLOR_HSV2RGB)
cv2.imshow('RBG Image', rgb_image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![9](https://github.com/user-attachments/assets/de7d7fa0-54e8-4787-8637-038360fd3519)


## 4) Access and manipulate image pixels

### a)Accessing pixel at cooridinate (100,100)

```
image8=image_resized.copy()
(b,g,r)=image8[100,100]
print(f"Red: {r}\nGreen: {g}\nBlue: {b}")
```
![10](https://github.com/user-attachments/assets/825bf576-cfbb-4acf-ab05-513c2c27290c)

### b)Modify the color of the pixel at coordinate(200,200) to white

```
image8[200,200]=(255,255,255)
(b,g,r)=image8[200,200]
print(f"Red: {r}\nGreen: {g}\nBlue: {b}")
```
![11](https://github.com/user-attachments/assets/68d9368c-ab71-4244-b9c1-78f881c4610f)

## 5) Image Resizing
```
image9=image_resized.copy()
resized_image=cv2.resize(image9,(image9.shape[0]//2,image9.shape[1]//2))
cv2.imshow('Original image',image_resized)
cv2.imshow('Resized image',resized_image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![12(1)](https://github.com/user-attachments/assets/4b9772aa-48da-4996-bae1-fed4e7d7360f)

![12(2)](https://github.com/user-attachments/assets/2b216b51-d717-4345-b7f9-6f123ea97aa8)

## 6) Image Cropping

```
image10=image_resized.copy()
x, y = 50, 50
width, height = 250, 250
roi = image10[y:y + height, x:x + width]
cv2.imshow('CROPPED IMAGE', roi)
cv2.waitKey(0)
cv2.destroyAllWindows()

```
![13](https://github.com/user-attachments/assets/e55a5ea5-4769-40b0-a44c-6c3d8984759a)

## 7) Image Flipping

### a) Flip the original image horizontally and display it.
```
image11=image_resized.copy()
res=cv2.rotate(image11,cv2.ROTATE_180)
cv2.imshow('ORIGINAL IMAGE',image11)
cv2.imshow('FLIPPED IMAGE', res)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![14(1)](https://github.com/user-attachments/assets/3d55eb8a-927d-4fe6-a254-077f0baa69e7)

![14(2)](https://github.com/user-attachments/assets/d82ee346-753a-40cf-96c8-1f7a2c991052)

### b) Flip the original image vertically and display it.

```
image12=image_resized.copy()
res=cv2.rotate(image12,cv2.ROTATE_90_CLOCKWISE)
cv2.imshow('ORIGINAL IMAGE',image12)
cv2.imshow('FLIPPED IMAGE', res)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![15(1)](https://github.com/user-attachments/assets/97201f25-6357-40af-9664-2cca0d7bc3bd)

![12(2)](https://github.com/user-attachments/assets/0b676c9d-0b15-47e8-a5d0-9fb046a96029)

## 8) Write and Save the Modified Image
```
image13=image_resized.copy()
cv2.imwrite('lokesh2.jpg',image13)
```
![16](https://github.com/user-attachments/assets/1ff60820-94d4-4f73-8496-d9050c549889)


## Result:
Thus the images are read, displayed, and written ,and color conversion was performed between RGB, HSV and YCbCr color models successfully using the python program.







