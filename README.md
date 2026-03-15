# GestSpeak - Sign Language to Voice

> Breaking communication barriers for the deaf and mute community using real-time gesture recognition and voice synthesis.

![GestSpeak Demo](https://user-images.githubusercontent.com/72935128/206295487-0e25c737-9353-4e98-b8fb-0e5b38390cfb.png)

---

## 🌍 The Problem

Around **9 million people** worldwide are deaf and mute. While sign language bridges the communication gap within the community, most of the general population doesn't understand it - creating a persistent barrier in everyday interactions.

**GestSpeak solves this.** It translates real-time hand gestures into spoken words, enabling natural, unrestricted communication between sign language users and everyone else - no interpreter required.

---

## 💡 What It Does

GestSpeak uses a webcam to capture hand and body gestures in real time. A trained LSTM deep learning model recognizes the sign being performed and instantly converts it into a **voice output**, making communication seamless and accessible.

---

## 🏗️ System Architecture

```
Webcam Feed
     ↓
MediaPipe Holistic (Pose + Face + Hand Landmark Detection)
     ↓
Keypoint Extraction (1662 features per frame)
     ↓
Sequence Buffer (30 frames)
     ↓
LSTM Neural Network (action.h5)
     ↓
Predicted Sign Label
     ↓
Text-to-Speech Voice Output
```

---

## ⚙️ Technology Stack

| Layer | Technology |
|---|---|
| Gesture Detection | MediaPipe Holistic |
| Computer Vision | OpenCV |
| Deep Learning | TensorFlow / Keras (LSTM) |
| Keypoint Processing | NumPy |
| Visualization | Matplotlib |
| Voice Output | Text-to-Speech synthesis |
| Language | Python |

### Why LSTM?
Sign language is inherently **sequential** - the meaning of a gesture unfolds over multiple frames. LSTM (Long Short-Term Memory) networks are purpose-built for this kind of temporal pattern recognition, making them ideal for real-time sign detection.

---

## 🗂️ Project Structure

```
GestSpeak-Sign-Language-to-Voice/
│
├── Sign to Text.ipynb       # Data collection, keypoint extraction, model training
├── Sign to voice.ipynb      # Real-time inference with voice output
├── action.h5                # Pre-trained LSTM model
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/GestSpeak-Sign-Language-to-Voice.git
cd GestSpeak-Sign-Language-to-Voice
```

### 2. Install Dependencies

```bash
pip install opencv-python mediapipe tensorflow numpy matplotlib
```

### 3. Run Real-Time Inference

Open and run **`Sign to voice.ipynb`** in Jupyter Notebook. Make sure your webcam is connected.

```bash
jupyter notebook "Sign to voice.ipynb"
```

### 4. (Optional) Retrain the Model

To add new signs or retrain on custom data, open **`Sign to Text.ipynb`** and follow the data collection and training steps.

---

## 🔬 How It Works

### Step 1 - Landmark Detection
MediaPipe Holistic detects **33 pose landmarks**, **468 face landmarks**, and **21 landmarks per hand** from each webcam frame - capturing full-body gesture context.

### Step 2 - Keypoint Extraction
Each frame is reduced to a **1662-dimensional feature vector** combining pose, face, left hand, and right hand coordinates.

### Step 3 - Sequence Modeling
30 consecutive frames are buffered into a sequence and fed into the **LSTM model**, which identifies the temporal pattern of the gesture.

### Step 4 - Voice Output
The predicted sign label is passed to a text-to-speech engine, producing an **audible word or phrase** in real time.

---

## 📊 Model Details

| Parameter | Value |
|---|---|
| Architecture | LSTM (Long Short-Term Memory) |
| Input Shape | (30 frames × 1662 keypoints) |
| Actions Detected | hello, thanks, iloveyou |
| Training Sequences | 30 per action |
| Model File | `action.h5` |

---

## 🔮 Future Improvements

- Expand gesture vocabulary to cover full ASL alphabet and common phrases
- Mobile deployment for on-the-go accessibility
- Multi-language sign language support (ASL, BSL, ISL)
- Sentence-level prediction using contextual NLP
- Web-based interface for broader accessibility

---

## 🤝 Social Impact

GestSpeak directly addresses **UN Sustainable Development Goal 10 (Reduced Inequalities)** by empowering people with speech and hearing impairments to communicate independently - without relying on a human interpreter or specialized hardware.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
