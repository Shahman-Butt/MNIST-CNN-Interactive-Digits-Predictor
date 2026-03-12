# Handwritten Digit Recognizer



A sophisticated **Deep Learning Neural Network** application with an interactive GUI, built to recognize handwritten digits in real-time. This project implements a Convolutional Neural Network (CNN) trained on the MNIST dataset, providing high-accuracy predictions through a custom-built Tkinter drawing interface.

---

## 🎯 Key Features

- **High-Accuracy Recognition**: Utilizes a customized CNN architecture for robust digit classification.
- **Interactive GUI**: Features a real-time drawing canvas built with Tkinter.
- **Instant Inference**: Processes the user's drawing, normalizes it, and predicts the digit instantaneously.
- **Pre-trained Model Integration**: Automatically loads a saved `mnist.h5` model to avoid retraining on every run.
- **Screen Grabbing Pipeline**: Captures the exact localized region of the canvas using `win32gui` and `ImageGrab`.

---

## 🛠️ Technologies Used

- **Programming Language**: Python 3.x
- **Deep Learning Framework**: Keras (with TensorFlow backend)
- **GUI Library**: Tkinter
- **Image Processing**: Pillow (PIL), NumPy
- **System Automation**: win32gui

---

## 🏗️ Project Architecture

The system is divided into two decoupled modules:
1. **Model Training Pipeline (`train_digit_recognizer.py`)**: Responsible for data loading, preprocessing, CNN definition, training, validation, and serialization.
2. **Inference Engine & GUI (`gui_digit_recognizer.py`)**: Responsible for user interaction, localized image capture, image normalization, and real-time model prediction.

---

## ⚙️ How the System Works

1. **Drawing Phase**: The user draws a digit (0-9) on the Tkinter canvas.
2. **Capture Phase**: The system extracts the specific bounding box of the canvas from the screen.
3. **Preprocessing Pipeline**: The captured RGB image is resized to `28x28` pixels, converted to grayscale, reshaped to `(1, 28, 28, 1)`, and normalized (divided by 255.0).
4. **Prediction**: The pre-trained Keras model predicts the probabilities for each class. The class with the highest probability is returned as the final prediction along with the confidence score.

---

## 📋 Installation Instructions

### Prerequisites
- Python 3.7 or higher
- Windows OS (required for `win32gui` screen grabbing functionality)

### Setup Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/Shahman-Butt/HandWritten-Digit-Recognizer.git
   cd HandWritten-Digit-Recognizer
   ```
2. Create and activate a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   venv\Scripts\activate
   ```
3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

---

## ▶️ How to Run the Project

1. Ensure the `mnist.h5` model file is present in the root directory.
2. Run the graphical interface application:
   ```bash
   python gui_digit_recognizer.py
   ```
3. Draw a digit on the canvas and click **"Recognise"** to see the model's prediction and accuracy.
4. Click **"Clear"** to reset the canvas for a new digit.

*(Optional)* To retrain the model from scratch, execute:
```bash
python train_digit_recognizer.py
```

---

## 📁 Code Structure Explanation

```
HandWritten-Digit-Recognizer/
├── gui_digit_recognizer.py    # Main GUI application and inference logic
├── train_digit_recognizer.py  # CNN model architecture and training script
├── mnist.h5                   # Pre-trained Keras model weights
├── requirements.txt           # Python dependencies and libraries
├── Demo.mp4                   # Video demonstration of the application
└── README.md                  # Project documentation
```

---

## 🧠 Key Algorithms / Technical Concepts

- **Convolutional Neural Networks (CNN)**: The model uses dual `Conv2D` layers (32 and 64 filters) with ReLU activation, combined with `MaxPooling2D` for spatial downsampling and feature extraction.
- **Regularization**: `Dropout` layers (0.3 and 0.5) are implemented to prevent overfitting during training.
- **Categorical Crossentropy**: Used as the loss function for multi-class classification (10 digit classes).
- **Adadelta Optimizer**: An adaptive learning rate method used to optimize the neural network's weights.
- **Image Normalization**: Ensures the user's freehand drawing matches the exact statistical distribution of the MNIST dataset.

---

## 🖼️ Example Output

*(See the `Demo.mp4` file included in the repository for a full visual walkthrough of the application in action.)*

---

## 🚀 Future Improvements

- [ ] **Cross-Platform Support**: Replace `win32gui` with a platform-independent canvas extraction method to support macOS and Linux.
- [ ] **Data Augmentation**: Implement image translation and rotation during training to improve inference robustness on off-center drawings.
- [ ] **Brush Size Tuning**: Dynamically adjust the drawing brush size to better mimic the stroke width of the original MNIST dataset.
- [ ] **Web Interface**: Port the local Tkinter application to a modern web framework (e.g., Flask/React) for broader accessibility.

---

## 👥 Author Information

**Shahman Butt**
- GitHub: [@Shahman-Butt](https://github.com/Shahman-Butt)
