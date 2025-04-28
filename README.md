## Real-Time Fire Detection and Alert System

This Python script combines a simple convolutional neural network (CNN) with live webcam monitoring to detect fire and immediately notify via sound, email, and geolocation.

Purpose as a mini project. was just introduced to CNN and model training.

**Key Functionality**  
- **Model Definition & Training**: Builds a Keras Sequential CNN (Conv2D → MaxPooling → Flatten → Dense → Sigmoid) and trains it on a directory of fire vs. non-fire images for 15 epochs.  
- **Live Prediction Loop**: Captures frames from the default webcam, resizes and normalizes them, and runs the trained model to classify each frame as “fire” or “no fire.”  
- **Threshold-Based Alerting**: If the model’s fire probability exceeds a configurable threshold (default 0.3), the system:  
  - Emits an audible beep via winsound  
  - Retrieves the current public IP geolocation using geocoder.ip('me')  
  - Sends an email notification (with subject, body, and recipient configurable) using smtplib and the EmailMessage API  
- **Graceful Shutdown**: Displays the camera feed in a window titled **Camera Feed** and exits cleanly when the user presses **q**.

**Dependencies**  
- OpenCV (`cv2`) for video capture, frame processing, and display  
- NumPy (`numpy`) for array manipulation  
- TensorFlow/Keras (`keras`) for defining, compiling, and training the CNN  
- Winsound (`winsound`) for system beeps on Windows  
- Geocoder (`geocoder`) for IP-based latitude/longitude lookup  
- Standard libraries: `smtplib`, `email.message`, `os`

**Usage**  
1. Organize your training images under `Downloads/train/fire_dataset/` with subfolders for each class.  
2. Run the script to train the model: it will automatically load, compile, and fit for 15 epochs.  
3. After training, the `predict_fire_from_camera()` function starts the webcam monitor. Adjust the `threshold` argument as needed.  
4. Watch the console for “Fire Detected” messages; check your inbox for alert emails.  
5. Press **q** in the video window to stop the application.
