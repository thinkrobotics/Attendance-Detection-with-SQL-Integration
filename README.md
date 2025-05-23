# Face Detection and Recognition with MTCNN and OpenCV

This Python script provides a full pipeline for face detection and recognition using the MTCNN detector and OpenCV's LBPH (Local Binary Patterns Histograms) face recognizer. It captures photos from a webcam, trains a recognizer on the captured faces, and detects faces in real time, logging detections to a SQLite database.

## Features

- Face detection using MTCNN (Multi-task Cascaded Convolutional Networks)
- Face recognition using OpenCV's LBPHFaceRecognizer
- Real-time webcam-based detection and recognition
- SQLite database logging of detected faces and timestamps
- Simple user interaction via keyboard commands

## Requirements

- Python 3.x
- OpenCV (`opencv-contrib-python` for face recognition module)
- MTCNN
- NumPy
- SQLite3 (standard with Python)

## Installation

Install the required packages using pip:

```bash
pip install opencv-contrib-python mtcnn numpy
```

## How It Works

### 1. Capturing Photos

Run the script and enter your name when prompted. Press:

- `s` to start capturing your face images.
- `e` to stop capturing.

The images will be saved in a folder `dataset/{your_name}`.

### 2. Training the Recognizer

Once photo capturing is complete, the script automatically:

- Loads all grayscale face images from the `dataset` folder.
- Labels them numerically.
- Trains an LBPH face recognizer on this data.
- Saves the trained model as `face_model.yml`.

### 3. Detecting Faces

After training, the script activates webcam-based detection and recognition:

- Faces are detected in real time.
- Each detected face is converted to grayscale and recognized using the trained model.
- If confidence is high (less than 70), the name and timestamp are logged into `face_detection.db`.
- The detected face is annotated in the webcam feed with a green rectangle and name.

Press `q` to quit face detection.

## Output Files

- `dataset/`: Folder containing captured face images.
- `face_model.yml`: Trained LBPH face recognition model.
- `face_detection.db`: SQLite database logging detections.

## Notes

- Make sure your lighting is good while capturing images.
- Capture multiple images (20–30) for better training accuracy.
- MTCNN might detect false positives in low-light or noisy conditions.

## License

MIT License
