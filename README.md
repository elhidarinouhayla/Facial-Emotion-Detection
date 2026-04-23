# Facial Emotion Detection


A robust web service for real-time facial emotion recognition. This project leverages a Convolutional Neural Network (CNN) to classify facial expressions from uploaded images and stores the results in a PostgreSQL database.

---

##  Features

- **Face Detection**: Utilizes OpenCV's Haar Cascade to accurately locate faces in images.
- **Emotion Recognition**: Classifies faces into 7 categories: `Angry`, `Disgust`, `Fear`, `Happy`, `Neutral`, `Sad`, and `Surprised`.
- **API Endpoints**:
    - `POST /predict_emotion`: Upload an image (JPEG/PNG) to get an instant emotion prediction.
    - `GET /predictions`: Retrieve a history of all analyzed images and their predicted emotions.
- **Database Integration**: Automatically stores prediction results, confidence scores, and timestamps using SQLAlchemy.

---

##  Tech Stack

- **Framework**: FastAPI
- **Deep Learning**: TensorFlow, Keras, OpenCV
- **Database**: PostgreSQL (SQLAlchemy ORM)
- **Data Processing**: NumPy, Pandas, Matplotlib

---

##  Project Structure

```text
.
├── DL/                     # Deep Learning components
│   ├── detect_and_predict.py # Emotion detection logic
│   ├── emotion_cnn_model.keras # Pre-trained CNN model
│   ├── haarcascade.xml      # Haar Cascade for face detection
│   └── emotion_cnn_model.ipynb # Training notebook
├── models/                 # Database & API schemas
│   └── model.py            # SQLAlchemy & Pydantic models
├── config.py               # Environment configuration
├── database.py             # Database connection setup
├── main.py                 # FastAPI application entry point
├── requirements.txt        # Project dependencies
└── README.md               # Project documentation
```

---

##  Installation & Setup

### 1. Clone the repository
```bash
git clone https://github.com/elhidarinouhayla/Facial-Emotion-Detection.git
cd Facial-Emotion-Detection
```

### 2. Configure Environment Variables
Create a `.env` file in the root directory with your PostgreSQL credentials:
```env
USER=your_db_user
PASSWORD=your_db_password
HOST=localhost
PORT=5432
DATABASE=facial_emotion_db
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the Application
```bash
uvicorn main:app --reload
```
The API will be available at `http://localhost:8000`. You can access the interactive documentation at `http://localhost:8000/docs`.

---

##  API Usage

### Predict Emotion
- **Endpoint**: `/predict_emotion`
- **Method**: `POST`
- **Payload**: Form-data with key `file` (Image)
- **Response**:
```json
{
  "id": 1,
  "emotion": "happy",
  "confidence": 98.45,
  "created_at": "2024-04-08T12:00:00Z"
}
```

### Get All Predictions
- **Endpoint**: `/predictions`
- **Method**: `GET`
- **Response**: List of prediction records.

---

##  Testing

To run the tests:
```bash
pytest
```

---
