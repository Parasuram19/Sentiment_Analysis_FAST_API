# Sentiment Analysis API Documentation

## Overview
A FastAPI-based API that performs sentiment analysis on text data from CSV files. Features JWT authentication, sentiment scoring using TextBlob, and visualization capabilities.

## Installation

```bash
pip install -r requirements.txt
```

## API Endpoints

### Authentication
**POST `/token`**
- Authenticates users and returns JWT token
- Body: `username`, `password` (form data)
- Returns: `{access_token: string, token_type: string}`

### Analysis
**POST `/analyze`**
- Analyzes sentiment from CSV file
- Headers: `Authorization: Bearer {token}`
- Body: CSV file with columns:
  - `id`: Unique identifier
  - `text`: Text for analysis
  - `timestamp`: Optional datetime
- Returns:
```json
{
  "results": [
    {
      "id": string,
      "text": string,
      "sentiment": "positive|negative|neutral",
      "polarity": float,
      "subjectivity": float,
      "timestamp": string|null
    }
  ],
  "summary": {
    "total": int,
    "positive": int,
    "negative": int,
    "neutral": int
  }
}
```

## Security
- JWT-based authentication
- Token expiry: 30 minutes
- Default credentials:
  - Username: admin
  - Password: admin123

## Frontend
Access the dashboard at `/static/index.html`
- File upload interface
- Interactive charts
- Tabular results view

## Development
```bash
uvicorn sentiment_analysis:app --reload
```

## Error Handling
- 400: Invalid file format
- 401: Authentication failed
- 500: Server processing error

## Dependencies
- fastapi
- python-multipart
- python-jose
- passlib
- pandas
- textblob
- uvicorn
- python-dotenv
- bcrypt
