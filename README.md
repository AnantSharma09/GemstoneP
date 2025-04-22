## Gemstone Price Prediction
## Gemstone Price Prediction

This repository contains a Flask web application and machine learning pipeline that predicts the price of gemstones based on their physical characteristics. Given inputs such as carat, dimensions (x, y, z), depth, table, cut, color, and clarity, the app returns a predicted price using a pre-trained machine learning model.

### Features

- **Web Interface**: A simple and responsive Flask-based front-end to input gemstone attributes and display predictions.
- **Machine Learning Pipeline**: A modular pipeline using scikit-learn to preprocess inputs and predict prices with a trained model.
- **Serialization**: Models and preprocessors are saved as artifacts (`model.pkl` and `preprocessor.pkl`) for easy loading in production.
- **Flash Messages**: User-friendly alerts and prediction results displayed on the front-end.

### Prerequisites

- Python 3.10+ (or compatible)
- `venv` for virtual environment management

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/AnantSharma09/GemstoneP.git
   cd GemstoneP
   ```

2. **Create and activate a virtual environment**
   ```bash
   python -m venv venv
   # On Windows (Git Bash)
   source venv/Scripts/activate
   # On macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set environment variables**
   For development mode (enables debug and auto-reload):
   ```bash
   # On Windows
   set FLASK_ENV=development
   # On macOS/Linux
   export FLASK_ENV=development
   ```

### Running the Application

1. Ensure your virtual environment is activated.
2. Start the Flask server:
   ```bash
   flask run
   ```
3. Open your browser and navigate to `http://127.0.0.1:5000/`.
4. Enter the gemstone attributes in the form and click **Predict your Gemstone Price**.

### Project Structure

```
GemstoneP/
├── app.py                 # Main Flask application entry point
├── requirements.txt       # Python dependencies
├── templates/
│   └── home.html          # Jinja2 template for the home page
├── static/styles/         # CSS and static assets
│   └── styles.css
├── src/
│   └── pipeline/
│       ├── predict.py     # Defines CustomData and PredictPipeline classes
│       └── artifacts/     # Serialized model and preprocessor (model.pkl, preprocessor.pkl)
└── venv/                  # Virtual environment (excluded from version control)
```

### Model and Preprocessor

- `artifacts/model.pkl`: Pre-trained machine learning model (e.g., XGBoost/CatBoost).
- `artifacts/preprocessor.pkl`: Preprocessing pipeline (e.g., StandardScaler, encoders).

These files are loaded by `PredictPipeline` to transform input data and produce predictions.

### Customizing and Retraining

1. Modify or extend the dataset preprocessing in `src/pipeline/predict.py`.
2. Train your own model and save it as `model.pkl` using:
   ```python
   import pickle
   with open("artifacts/model.pkl", "wb") as f:
       pickle.dump(your_trained_model, f)
   ```
3. Similarly, save the preprocessor pipeline:
   ```python
   with open("artifacts/preprocessor.pkl", "wb") as f:
       pickle.dump(your_preprocessor, f)
   ```
4. Restart the Flask app to serve your new model.

### Contributing

Contributions are welcome! Please open an issue or submit a pull request with your improvements.

### License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

