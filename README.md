# *Social Distancing Detector*  

Social distancing is crucial to preventing the spread of disease. Using computer vision technology based on OpenCV and YOLO-based deep learning, we are able to estimate the social distance of people in video streams.

Social distancing is arguably the most effective nonpharmaceutical way to prevent the spread of a disease — by definition, if people are not close together, they cannot spread germs.

**NOTEBOOK**:  [![Nbviewer](https://github.com/jupyter/design/blob/master/logos/Badges/nbviewer_badge.svg)](https://nbviewer.jupyter.org/github/shejz/social-distancing-detector/blob/main/Social_Distancing_Detector.ipynb)

## **The steps involved in an OpenCV-based social distancing application:**:
1. Using the YOLO object detector to detect people in the frame from your video file or directly from your webcam.
2. Determining the centroids for each detected person
3. Computing the pairwise distances between all centroids
4. Checking to see if any pairwise distances were < N pixels apart, and if so, indicating that the pair of people violated social distancing rules

![](https://i.postimg.cc/j2jJkKpJ/steps.jpg)

## **Limitations and future improvements:**

1. Social distancing detector did not leverage a proper camera calibration, meaning that we could not (easily) map distances in pixels to actual measurable units (i.e., meters, feet, etc.). Therefore, the first step to improving our social distancing detector is to utilize a proper camera calibration. Doing so will yield better results and enable you to compute actual measurable units (rather than pixels).
2. Consider applying a top-down transformation of your viewing angle. From there, you can apply the distance calculations to the top-down view of the pedestrians, leading to a better distance approximation.
3. Improve the people detection process. OpenCV’s YOLO implementation is quite slow not because of the model itself but because of the additional post-processing required by the model. To further speedup the pipeline, consider utilizing a Single Shot Detector (SSD) running on your GPU — that will improve frame throughput rate considerably.

## **Detecting people in images and video streams**

Using the YOLO object detector to detect people in our video stream. Where the red boxes represent people who are too close to one another.

![](https://i.postimg.cc/Px68NKVs/sc.jpg)
