# DeepAsana: A CNN-RNN Based Yoga Pose Classifier

## Overview

**DeepAsana** is a deep learning-based system designed to classify yoga asanas from videos. The project leverages **Convolutional Neural Networks (CNNs)** for frame-wise feature extraction and **Recurrent Neural Networks (RNNs)** for modeling temporal dependencies between frames. This hybrid architecture allows the system to accurately recognize dynamic yoga poses from video sequences.

The model is trained on a dataset of full HD yoga videos, where each video represents a specific asana. The system processes each video by extracting frames, feeding them through a CNN to extract spatial features, and then sequences those features into an RNN to capture the motion and posture transitions over time.

---

## Table of Contents

* [Project Structure](#project-structure)
* [Technologies Used](#technologies-used)
* [Model Architecture](#model-architecture)
* [Dataset](#dataset)
* [How It Works](#how-it-works)
* [How to Use](#how-to-use)
* [Results](#results)
* [Limitations](#limitations)
* [Future Work](#future-work)
* [License](#license)

---

## Technologies Used

### Machine Learning Techniques:

* **CNN (Convolutional Neural Network)** – for extracting spatial features from individual video frames
* **RNN (Recurrent Neural Network)** – for modeling temporal dependencies in frame sequences
* **Sequence Classification** – to identify the overall asana from frame sequences

### Libraries & Tools:

* **TensorFlow / Keras** – deep learning framework used to build and train models
* **OpenCV** – for video loading, frame extraction, and visualization
* **NumPy** – numerical operations and frame handling
* **Matplotlib / Seaborn** – result visualization and evaluation
* **Google Colab** – training and experimentation environment

---

## Model Architecture

* **Input**: Sequence of frames extracted from yoga videos
* **Stage 1 – CNN**: Pre-trained or custom CNN to extract feature vectors from each frame
* **Stage 2 – RNN**: LSTM layer(s) to learn temporal relationships between frames
* **Output**: Softmax layer predicting the class (yoga asana)

```
Video → Frames → CNN (per frame) → Feature Sequences → RNN → Asana Class
```

---

## Dataset

* Stored in: `/content/drive/MyDrive/NN/Data/Yoga_videos/`
* **Structure**: Each subfolder is named after an asana and contains multiple videos of that pose
* **Format**: Full HD videos recorded via phone camera
* **Labels**: Derived from folder names

Example:

```
Yoga_videos/
├── Tadasana/
│   ├── tadasana1.mp4
│   └── tadasana2.mp4
├── Vrikshasana/
│   ├── vriksha1.mp4
│   └── vriksha2.mp4
```

---

## How It Works

1. **Video Preprocessing**:

   * Videos are read using OpenCV
   * Frames are extracted and resized
   * Normalization is applied

2. **Feature Extraction**:

   * Each frame is passed through a CNN model (e.g., MobileNet/Custom)

3. **Temporal Modeling**:

   * Frame features are fed into an RNN (LSTM) to capture pose dynamics

4. **Prediction**:

   * The final LSTM output is passed through a dense + softmax layer
   * Prediction is visualized or overlaid on the original video

---

## How to Use

### 1. Clone the Repository

```bash
git clone https://github.com/your_username/DeepAsana.git
cd DeepAsana
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Prepare Your Dataset

Organize your dataset in the following format:

```
Data/
├── Asana1/
│   ├── video1.mp4
├── Asana2/
│   ├── video1.mp4
```

Update the dataset path in the notebook or script accordingly.

### 4. Train the Model

Open the notebook (`notebook.ipynb`) in Google Colab or locally and run all cells.

### 5. Predict on a Video

Use the `predict_on_video.py` script or the notebook to:

* Load your trained model
* Select a video
* Generate predictions with overlay

---

## Results

| Metric              | Value                           |
| ------------------- | ------------------------------- |
| Training Accuracy   | xx%                             |
| Validation Accuracy | xx%                             |
| F1 Score            | xx%                             |
| Classes             | 5 (Tadasana, Vrikshasana, etc.) |

Sample Output:

* Input: Yoga video
* Output: Labeled video with predicted asana (e.g., “Vrikshasana” displayed on each frame)

---

## Limitations

* Only trained on a limited number of yoga asanas
* Does not perform real-time classification (static processing)
* Cannot give feedback on incorrect posture
* Performance depends on video quality and clarity

---

## Future Work

* Extend to **real-time webcam-based classification**
* Integrate **pose estimation (e.g., MediaPipe)** for feedback/correction
* Expand dataset with more asanas and multiple participants
* Deploy as a web or mobile app with a friendly interface
