# Image_Processing_RGB_to_Binary
## by YUNBLAK
### Image Processing for Making RGB Image to Binary Image

[**IMAGES ARE FROM NASA**]

This is an image processing method about that RGB images are changed to black and white. We use this technique because Sunspots are more clearly discovered and are a little easier to be calculated about their areas. The current HMI image has some contrast, so it can be a problem when calculating the area of the sunspots. We will calculate the area of the sunspot by KNN algorithm, and it is more helpful to calculate the area of the spot in a binary divided image.

### Original Image
![B002](https://user-images.githubusercontent.com/87653966/127762718-1305beb3-c8a4-4415-82b4-05b2831cc946.png)

### Before Noise Reductiong
![B001](https://user-images.githubusercontent.com/87653966/127762724-a1d69f03-f4c7-4ebd-b2c1-8f0e2dc0b929.png)
When we binarize the image before going through Noise Reduction, noise is also binarized and transformed similarly to Sunspot. This is an important factor that tells us why we should do Noise Reduction.

### After Noise Reduction
![B003](https://user-images.githubusercontent.com/87653966/127762722-dcaf38cc-5d8a-4c2b-b04a-4b3323b765bf.png)

#### This is a converting method in Python
    def convert2binary(self,img):
        gray_img = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
        binary_img = cv2.adaptiveThreshold(gray_img, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
                                       cv2.THRESH_BINARY_INV, 131, 15)
        return binary_img 
    
    # cv2.adaptiveThreshold(src, maxValue, adaptiveMethod, thresholdType, blockSize, C)
    # src – grayscale image
    # maxValue – Threshold
    # Adaptive Method – calculation method to determine the holding value
    # thresholdType – threshold type
    # blockSize – area size to apply thresholding
    # C – the value to subtract from the mean or weighted mean
    
    cv2.ADAPTIVE_THRESH_MEAN_C: The threshold is the average of the adjacent regions.
    cv2.ADAPTIVE_THRESH_GAUSSIAN_C: The threshold is the sum of the weights of the neighboring values whose weights are in the Gaussian window.
    
