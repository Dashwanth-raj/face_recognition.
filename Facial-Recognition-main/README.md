# Facial Recognition System

## Overview

This project implements a basic facial recognition system using Python and OpenCV. It consists of two main parts:

1.  **Face Data Collection (`Facial_Recognition_Part1.py`):** Captures and stores face images from a video source (typically a webcam).
2.  **Face Recognition (`Facial_Recognition_Part2.py`):** Trains a model on the collected face data and uses it to recognize faces in real-time.

## Dependencies

* Python 3.x
* OpenCV (`cv2`)
* NumPy (`numpy`)

## Setup

1.  **Install Dependencies:**

    ```bash
    pip install numpy
    pip install opencv-python
    ```

2.  **Download the Haar Cascade Classifier:**

    * Download the `haarcascade_frontalface_default.xml` file from the OpenCV GitHub repository or find it in your OpenCV installation.  This file is required for face detection.
    * Place the `haarcascade_frontalface_default.xml` file in the same directory as your Python scripts.

## Usage

### 1. Face Data Collection

1.  Run `Facial_Recognition_Part1.py`.
2.  The script will capture frames from your webcam and detect faces.
3.  Detected faces will be cropped, resized, converted to grayscale, and saved in the `faces/` directory.
4.  The script will continue capturing faces until 100 face images are collected or you press the 'Enter' key.
5.  Ensure that the `faces/` directory exists, or create it before running the script.

### 2. Face Recognition

1.  Run `Facial_Recognition_Part2.py`.
2.  The script will:
    * Load the face images from the `faces/` directory.
    * Train an LBPH face recognizer model on the loaded images.
    * Capture frames from your webcam.
    * Detect faces in the live video stream.
    * Attempt to recognize the detected faces using the trained model.
    * Display the video feed with a bounding box around the detected face, the recognition confidence, and a "Locked" or "Unlocked" status.
3.  Press 'Enter' to exit.

## Important Notes

* **Face Data:** The quality and quantity of face data in the `faces/` directory significantly impact the recognition accuracy.  Ensure you capture a variety of images with different expressions and lighting conditions.
* **Haar Cascade Classifier:** The `haarcascade_frontalface_default.xml` file is crucial for face detection.  Make sure it's in the correct location.
* **Confidence Threshold:** The confidence threshold (set to 75 in `Facial_Recognition_Part2.py`) determines how confident the model must be to consider a face "unlocked".  You may need to adjust this value for your specific use case.
* **LBPH Model:** This project uses the Local Binary Patterns Histograms (LBPH) algorithm for face recognition.  OpenCV provides other face recognition algorithms that you can experiment with.
* **Real-time Performance:** The real-time performance of the recognition depends on your system's processing power.

## Troubleshooting

* **"ImportError: No module named 'cv2'" or "'numpy'":** Make sure you have installed OpenCV and NumPy correctly.  See the "Setup" section.
* **"cv2.error: ( ... ) error: (-215:Assertion failed":** This usually means that the Haar cascade classifier file is not found.  Double-check the file path.
* **Low Recognition Accuracy:** This could be due to poor training data, insufficient training data, or an inappropriate confidence threshold.
* **Webcam Issues**: If you are having issues with the webcam, make sure that it is properly connected and not being used by another application.
