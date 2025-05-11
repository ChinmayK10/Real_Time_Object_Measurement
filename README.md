# Object Dimension Measurement using OpenCV and A4 Reference
This project is a computer vision-based object dimension measurement system that utilizes an A4 paper as a reference object for real-time or static image analysis using OpenCV. It extracts contours, detects quadrilateral shapes, warps the perspective to a calibrated plane, and overlays real-world dimensions (in centimeters) of detected objects based on pixel-to-metric scale mapping.

## Features
-Supports both real-time webcam feed and static image input.

-Uses A4 paper (210mm × 297mm) as a known reference for dimension calibration.

-Extracts quadrilateral contours with configurable filtering.

-Applies perspective transformation to warp the image to a top-down view.

-Measures and overlays length and width of objects in centimeters.

-High accuracy enabled by Gaussian blur, Canny edge detection, dilation, erosion, and arc-length approximation.

-Modular utility functions in utlis.py for reusable computer vision workflows.

## Requirements
Python 3.6+
OpenCV (opencv-python)
NumPy

## How It Works
1. Calibration with A4 Paper
The system assumes an A4 paper in the scene as a size reference.

Detects the largest quadrilateral contour that matches the paper dimensions.

Warps the perspective using the paper's corners to normalize measurements.

2. Object Detection
Searches for contours within the warped frame (i.e., within the A4 boundary).

Filters based on area and polygon vertex count (usually 4 for rectangles).

Calculates real-world width and height using pixel-distance scaling.

3. Visualization
Draws contours and arrows indicating object dimensions.

Annotates the image with the measured values (in cm).

Displays both the original and warped/processed frames.

## File Structure
.
├── main.py              # Main script for webcam/image-based measurement
├── utlis.py             # Utility functions for image processing
├── README.md            # Project documentation

# Usage
## Webcam Mode
Ensure a webcam is connected and an A4 paper is placed flat in the frame.
## Static Image Mode
Edit main.py:

webcam = False
path = "path/to/your/image.jpg"
