# Currency Converter Application

## Author Information

- **Name:** Juan Vicente Herrera Ruiz de Alejo
- **GitHub:** [@juanviz](https://github.com/juanviz)
- **Role:** Author and Maintainer
- **Affiliation:** ICAI

## License
This project is licensed under the MIT License - see the [MIT License](https://opensource.org/licenses/MIT) for details.

## Overview

This is a simple Python web application built with Flask that converts currency amounts between multiple currencies through an intuitive web interface. It supports conversions between EUR, USD, and GBP with predefined exchange rates.

## Installation

To run the application locally, install the required dependencies:

```sh
pip install -r requirements.txt
```

## Local Usage

Run the development server with:

```sh
python currency_converter.py
```

Then, open your browser at `http://127.0.0.1:5000/` and use the interface to perform currency conversions.

## Deployment on Google App Engine

This application can be easily deployed to Google App Engine. Follow these steps:

### Prerequisites

- A Google Cloud Platform (GCP) account with billing enabled
- Google Cloud SDK installed on your machine
- Docker installed (optional, for local testing)

### Deployment Steps

1. **Authenticate with Google Cloud:**
   ```sh
   gcloud auth login
   gcloud config set project YOUR_PROJECT_ID
   ```

2. **Create an `app.yaml` file** (if not present) in the project root:
   ```yaml
   runtime: python311
   env: standard
   
   handlers:
   - url: /.*
     script: auto
   ```

3. **Deploy to App Engine:**
   ```sh
   gcloud app deploy
   ```

4. **Access your application:**
   Once deployment is complete, your application will be available at:
   ```
   https://YOUR_PROJECT_ID.appspot.com
   ```

### Environment Configuration

The application uses Flask's built-in development server. For production deployments on App Engine, ensure your `currency_converter.py` follows this pattern:

```python
if __name__ == '__main__':
    app.run(host='0.0.0.0', port=8080, debug=False)
```

### Important Notes for App Engine

- The application runs on port 8080 by default in App Engine
- Ensure the `requirements.txt` file contains all dependencies (Flask)
- The `app.yaml` configuration file is required for deployment
- Standard Environment provides free tier quotas for testing

## Technical Details

- **Framework:** Flask
- **Language:** Python 3.11+
- **Supported Currency Pairs:** EUR/USD, USD/EUR, EUR/GBP, GBP/EUR, USD/GBP, GBP/USD
- **Exchange Rates:** Static rates (configurable in the application)
