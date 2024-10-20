# Vultr-Hackathon-
Virtual Friend AI is an intelligent companion that understands your emotions from text or speech. It entertains you by playing music, suggesting games, or offering activities based on your mood and interests. The AI learns from interactions to provide better responses and personalized entertainment over time.


# Virtual Friend Using AI

A Virtual Friend built using AI that detects user emotions based on text or speech input and provides personalized responses like music suggestions, games, and emotional support based on the user's mood.

## Features
- **Emotion Detection**: Detects user emotions (happy, sad, bored, etc.) using NLP and sentiment analysis.
- **Text and Speech Input**: Accepts user input via text or speech (converted to text).
- **Personalized Entertainment**: Suggests music, games, or other activities based on the detected emotion.
- **Machine Learning**: Learns user preferences over time to provide better suggestions.

# Tech Stack
- **Frontend**: React
- **Backend**: Node.js, Express
- **NLP**: Python (TextBlob for emotion detection)
- **Music API**: Spotify API for music recommendations
- **Speech-to-Text**: Google Cloud Speech-to-Text API (optional for speech input)
- **Database**: MongoDB (for user preferences and history)

# Getting Started

# Prerequisites
Make sure you have the following installed:
- [Node.js](https://nodejs.org/en/)
- [npm](https://www.npmjs.com/)
- [Python 3](https://www.python.org/)
- [MongoDB](https://www.mongodb.com/) (optional if you plan to use user preference storage)

# Installation

# 1. Clone the repository
git clone https://github.com/your-username/virtual-friend-ai.git
cd virtual-friend-ai

# 2. Install dependencies

# Frontend (React)
cd virtual-friend-frontend
npm install

# Backend (Node.js)
cd virtual-friend-backend
npm install

# Python (NLP)
Activate a virtual environment (optional but recommended):

python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

Install Python dependencies:

pip install textblob
python -m textblob.download_corpora


# 3. Set up Spotify API
To get music recommendations, you'll need to create a Spotify Developer account and set up an app to get your **Client ID** and 

**Client Secret**.

1. Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/applications).
2. Create a new app.
3. Get your **Client ID** and **Client Secret**.
4. Add them to the backend's environment variables.

# 4. Set up Environment Variables
Create a `.env` file in the `virtual-friend-backend/` directory with the following content:
SPOTIFY_CLIENT_ID=your-client-id
SPOTIFY_CLIENT_SECRET=your-client-secret

# 5. Run the project

# Frontend (React)
cd virtual-friend-frontend
npm start

# Backend (Node.js + Express)
cd virtual-friend-backend
node server.js

# Python (NLP Server)
python emotion_analysis.py


# Usage

1. Open the frontend in your browser at `http://localhost:3000`.
2. Type in a message or speak (if speech-to-text is implemented).
3. Based on your input, the backend will detect your emotion and suggest appropriate entertainment (e.g., music or games).

# Directory Structure
virtual-friend-ai/
│
├── virtual-friend-frontend/       # React frontend
│   ├── public/
│   ├── src/
│   └── package.json
│
├── virtual-friend-backend/        # Node.js backend
│   ├── server.js
│   ├── package.json
│   └── .env
│
├── emotion_analysis.py            # Python script for sentiment analysis
├── README.md
└── .gitignore

# Emotion Detection (NLP)
The emotion detection is handled by a Python script using **TextBlob** to analyze the polarity of the text and classify it as either **happy**, **sad**, **neutral**, etc.

Example of sentiment analysis:
from textblob import TextBlob

def detect_emotion(text):
    blob = TextBlob(text)
    polarity = blob.sentiment.polarity
    
    if polarity > 0.5:
        return 'happy'
    elif polarity < -0.5:
        return 'sad'
    else:
        return 'neutral'


# API Endpoints

- **POST /emotion**  
  Detects the emotion from the user’s input and returns a response.
  - **Request Body**: `{ "text": "your input text" }`
  - **Response**: `{ "reply": "response based on emotion" }`

Example:
```bash
curl -X POST http://localhost:5000/emotion -H "Content-Type: application/json" -d '{"text": "I am feeling happy"}'
```

### Future Enhancements
- **Voice Interaction**: Add Google Cloud Speech-to-Text for converting user speech into text input.
- **User Preference Storage**: Implement MongoDB to store user interaction history and preferences.
- **More Entertainment Options**: Add movie or book suggestions based on mood.

### Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

### License
This project is licensed under the MIT License.

### Key Points to Update:
1. Spotify API: Make sure you replace `your-client-id` and `your-client-secret` with actual credentials from the Spotify Developer Console.
2. Speech-to-Text: If you're adding speech input, you'll need to integrate Google Cloud Speech-to-Text API and mention it in the README.

This README.md provides an overview of the project, installation instructions, and details on how to run the system locally.
