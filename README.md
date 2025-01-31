# Sentiment Analysis API

## Installation

1. Clone the repository:
```
git clone https://github.com/your-username/sentiment-analysis-api.git
```

2. Navigate to the project directory:
```
cd sentiment-analysis-api
```

3. Install the required dependencies:
```
pip install -r requirements.txt
```

4. Start the FastAPI server:
```
uvicorn main:app --reload
```

The API will be available at `http://localhost:8000`.

## Usage

1. To authenticate, send a POST request to `/token` with the following form data:
```
username: admin
password: admin123
```

This will return an access token that you can use to authenticate subsequent requests.

2. To analyze a CSV file, send a POST request to `/analyze` with the following headers:
```
Authorization: Bearer <access_token>
```
and include the CSV file as the request body.

The API will return a JSON response with the sentiment analysis results.

## API

### Endpoints

- `POST /token`: Authenticate and obtain an access token.
- `POST /analyze`: Analyze a CSV file containing text data.

### Request and Response Schemas

**POST /token**
- Request: `username` and `password` form data
- Response: `access_token` and `token_type`

**POST /analyze**
- Request: CSV file
- Response: JSON object with `results` and `summary` fields

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Create a new Pull Request

## License

This project is licensed under the [MIT License](LICENSE).

## Testing

To run the tests, execute the following command:
```
pytest
```