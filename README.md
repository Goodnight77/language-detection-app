# ML FastAPI Docker Heroku Deployment

## Project Overview

This project demonstrates a machine learning model deployed using FastAPI, Docker, and Heroku.  The model performs language detection.

## Features

* **Language Detection:**  Accurately identifies the language of input text.
* **FastAPI Backend:**  Provides a RESTful API for easy model access.
* **Docker Containerization:** Enables consistent and reproducible deployment across different environments.
* **Heroku Deployment:**  Simplifies deployment to the cloud.


## Installation

This project uses `pip` for dependency management.  Ensure you have Python 3.7+ installed.

1. **Clone the repository:**
   ```bash
   git clone <repository_url>
   cd ml-fastapi-docker-heroku
   ```

2. **Create a virtual environment (recommended):**
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. **Run the application:**
   ```bash
   uvicorn app.main:app --reload
   ```
   This will start the FastAPI server.  You can then send POST requests to the `/predict` endpoint with the text you want to analyze.  The response will contain the predicted language.

2. **Example using `curl`:**

   ```bash
   curl -X POST -H "Content-Type: application/json" -d '{"text": "Hello, world!"}' http://localhost:8000/predict
   ```

3. **Docker Build and Run (Optional):**
   ```bash
   docker build -t app-name .
   docker run -p 80:80 app-name
   ```

4. **Heroku Deployment (Optional):**
   Follow Heroku's deployment guide.  The `heroku.yaml` file provides configuration for deployment.  You will need a Heroku account.
```bash
heroku login
heroku create app-name
heroku git:remote app-name
heroku stack:set container
git push heroku main
```

**Note:**  The trained model (`trained_pipeline-0.1.0.pkl`) is assumed to be present in the `app/model/` directory.  Ensure you have this file before running the application.  Refer to `Language Detection.ipynb` for details on model training.
