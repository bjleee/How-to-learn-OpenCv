# How-to-learn-OpenCv

## Chapter 1: Read Images Videos and Webcams

- To initialise object and read file 

```ç++
string path = "";
Mat img = imread(path);
```

- Handle base case: empty file

```
if (img.empty()) return -1;
```

## Chapter 2: Basic Functions

- cvtColor(para1, para2, para3) -> convert image to another image 
	- para1: img want to convert
	- para2: img will be converted into
	- para3: color will set up
```
cvtColor(img, imgGray, COLOR_BGR2GRAY);
```

- GaussianBlur(para1, para2, para3, para4) -> blur the image given and generate new one
	- para1: img want to be blurred
	- para2: new img store blurred one
	- para3: size of kernel used for blurring
	- para4: standard deviation of kernel along the X-axis

```
GaussianBlur(img, imgBlur, Size(3, 3), 3, 0);
```

- Canny(para1, para2, para3, para4) -> use after blurring image to <strong>find edge in image</strong>
	- para1: img that blurred
	- para2: new img to store 
	- para3: Đây là ngưỡng dưới cho thuật toán hysteresis trong phát hiện cạnh Canny. Bất kỳ pixel nào có độ lớn gradient lớn hơn ngưỡng dưới này sẽ được coi là một pixel thuộc cạnh mạnh và được giữ lại.
	- para4: Đây là ngưỡng trên cho thuật toán hysteresis trong phát hiện cạnh Canny. Bất kỳ pixel nào có độ lớn gradient lớn hơn ngưỡng trên này cũng sẽ được coi là một pixel thuộc cạnh mạnh và được giữ lại.

```
	Canny(imgBlur, imgCanny, 25, 75);
```


- dilate(para1, para2, para3) -> increasing the thickness
! Should be used after Canny the image(find edge of image)
	- para1: img that be canny
	- para2: new img store
	- para3: specify structure of kernel (a rectangle with specific size)
```
	Mat kernel = getStructuringElement(MORPH_RECT, Size(3,3)); <para3>
	dilate(imgCanny, imgDia, kernel);
```
- erode(para1, para2, para3) -> decreasing the thickness 
! Should be used after Canny the image(find edge of image)
	- para1: img that be canny/dilated
	- para2: new img store
	- para3: specify structure of kernel (a rectangle with specific size)
```
	Mat kernel = getStructuringElement(MORPH_RECT, Size(3,3));
	erode(imgDia, imgErode, kernel);
```

## Chapter 3: Resize and Crop

- resize(para1, para2, para3)
 	- para1: img we want to resize
	- para2: img that will become
	- para3: size of img 
	- para4(optional): when you dont know the size of img, you can use like this code to scale the size
```
	Mat imgresize;
	resize(img, imgresize, Size(), 0.5, 0.5);
```
By default, if you know what size you want to use you can do like this
```
	Mat imgresize;
	resize(img, imgresize, Size(640,480));
```

- To crop the image, you have to create size of rectangle and use img(roi) to crop the size
	- roi = Rect(x-axis, y-axis, lech bao nhieu so vs x, lech bao nhieu so voi y)
