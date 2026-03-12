# System Architecture

The Handwritten Digit Recognizer uses a decoupled architecture, separating the Deep Learning training pipeline from the real-time inference Graphical User Interface. 

## Architectural Flow

```mermaid
graph TD
    subaxis1(Training Pipeline)
    A[MNIST Dataset] -->|Load & Normalize| B(Data Preprocessing)
    B --> C{CNN Architecture}
    C -->|Conv2D + MaxPool| D[Feature Extraction]
    D -->|Flatten + Dense| E[Classification Layers]
    E -->|Save Weights| F[(mnist.h5)]

    subaxis2(Inference Engine & GUI)
    G[User Input] -->|Draws Digit| H(Tkinter Canvas)
    H -->|Click 'Recognise'| I(win32gui Bounding Box Capture)
    I -->|ImageGrab| J{Image Preprocessing}
    J -->|Resize 28x28 & Grayscale| K(Normalized Vector)
    F -.-> L
    K --> L[Keras Model Inference]
    L -->|Softmax Probabilities| M[Prediction Result on GUI]

    style F fill:#f9f,stroke:#333,stroke-width:2px
```

### Components Details

1. **Training (`train_digit_recognizer.py`)**:
   - Downloads the standard MNIST dataset consisting of 60,000 training and 10,000 testing images.
   - Defines a Convolutional Neural Network (CNN) with Adadelta optimizer.
   - Saves the trained model to `mnist.h5`.

2. **Inference/GUI (`gui_digit_recognizer.py`)**:
   - **Canvas Tracking**: A 300x300 pixel area capturing mouse inputs.
   - **Window Rectangulation**: `win32gui.GetWindowRect()` captures global display coordinates to take a screenshot of precisely the canvas area using `ImageGrab`.
   - **Prediction Mapping**: Outputs the predicted digit label and a confidence score percentage.
