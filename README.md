# Lane-Detection
![](Preview01.gif)

In this project, we've been working on defining simple functions to detect lane lines on the road in videos.

The steps we've taken to achieve the outcome in the gif above were:
1. Choosing the best color space to highlight the lanes as best as possible. We've chosen HLS color space.
<img width="734" alt="hls" src="https://user-images.githubusercontent.com/83698104/118475072-17b28c80-b70c-11eb-8911-b085dcb7e131.png">

2. Since the lane colors changed to green and blue, we then set up the lower and upper threshold to select only the color pixels we're interested in.
3. Converting HLS images into gray scale.
4. Smoothing the edges.
<img width="734" alt="Smoothed" src="https://user-images.githubusercontent.com/83698104/118475546-ade6b280-b70c-11eb-8059-450e53872570.png">

5. Canny Edge Detection

   - If a pixel gradient is higher than the upper threshold, the pixel is accepted as an edge.
   - If a pixel gradient value is below the lower threshold, then it is rejected.
   - If the pixel gradient is between the two thresholds, then it will be accepted only if it is connected to a pixel that is above the upper threshold.
   - Canny recommended the upper:lower ratio between 2:1 and 3:1.
   - If the high threshold is too high, we'll see no edges.
   - If the low threshold is too low, we'll see too much noise

6. Selecting the region of interest (to focus the lane detection on the region where the lanes actually are)
7. Hough transform for recognizing lines in the image by use of parameters like minimum gap between lane pixels and maximum gap.
8. Extrapolating and averaging the detected lines.
<img width="734" alt="detected_extrapolated" src="https://user-images.githubusercontent.com/83698104/118476017-4a10b980-b70d-11eb-97eb-55afa5830e1f.png">

9. Defining the final pipeline that takes video, performs lane detection and outputs the images with detected lanes.
