# AI Healthcare Automation Dashboard

## Overview

This project is a Streamlit-based web application that provides an AI-powered dashboard for healthcare automation. It integrates Hugging Face's language models to analyze clinical data and generate insights across four key features: Automated Triage, Medication Adherence, Mental Health Crisis Detection, and Clinical Report Generation. The dashboard includes interactive visualizations, animations, and automated actions like sending emails/SMS notifications and generating PDF reports.

The application aims to assist healthcare professionals by prioritizing patients, improving medication compliance, detecting mental health risks, and standardizing clinical reports.

## Features

- **Automated Triage System**: Analyzes emergency room intake notes to determine urgency, recommend tests, and suggest diagnoses. Includes analytics on case distribution and processing times.
- **Medication Adherence Assistant**: Processes prescriptions to create schedules, assess adherence risks, and send reminders via email/SMS using SMTP and Twilio.
- **Mental Health Crisis Detector**: Scans patient journals for risk indicators, assesses suicide risk, and recommends interventions with automated alerts.
- **Clinical Report Generator**: Converts unstructured notes into structured JSON reports and exports them as PDFs using ReportLab.
- **Dashboard Analytics**: Real-time metrics and charts (using Plotly) for each feature, with fallback default data.
- **Custom UI**: Modern interface with animations (Lottie), custom CSS, and responsive layout.
- **API Integration**: Uses Hugging Face Inference API for AI-generated responses.

## Prerequisites

- Python 3.8+
- A Hugging Face account with access to a language model API (e.g., for text generation).
- Twilio account for SMS notifications.
- Gmail account for SMTP email (or any SMTP server).
- Internet access for API calls and Lottie animations.

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/chamseddinedoulaEsprit/medical-workflows.git
   ```

2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

   If `requirements.txt` is not provided, install the following packages manually:
   ```
   pip install streamlit pandas plotly reportlab requests smtplib twilio streamlit-lottie
   ```

3. Configure API keys and credentials:
   - Open the main Python file (e.g., `app.py`).
   - Set the Hugging Face API details:
     ```python
     API_URL = "https://api-inference.huggingface.co/models/your-model-name"  # e.g., "gpt2" or a fine-tuned model
     headers = {
         "Authorization": "Bearer YOUR_HUGGINGFACE_API_TOKEN",
         "Content-Type": "application/json"
     }
     ```
   - Set Twilio credentials for SMS:
     ```python
     account_sid = "YOUR_TWILIO_ACCOUNT_SID"
     auth_token = "YOUR_TWILIO_AUTH_TOKEN"
     ```
   - Set SMTP details for email (default uses Gmail):
     ```python
     sender_email = "yourgmail@gmail.com"
     sender_password = "your-app-password"  # Use app password for Gmail
     ```

   **Note**: For security, use environment variables or a `.env` file instead of hardcoding credentials.

## Usage

1. Run the Streamlit app:
   ```
   streamlit run app.py
   ```

2. Access the dashboard in your browser at `http://localhost:8501`.

3. Navigate via the sidebar to select a feature.
   - Enter patient data in the text area.
   - Click the analysis button (e.g., "Analyze Clinical Note").
   - View AI-generated outputs, analytics charts, and take actions like exporting PDFs or sending notifications.

4. For notifications (in Medication Adherence):
   - Provide patient email and phone.
   - Click "Send notification and make reminders" to trigger email/SMS.

## Configuration Notes

- **Hugging Face API**: The app uses a generic text generation model. For better accuracy, use a medically fine-tuned model (e.g., BioGPT). Adjust `max_length` and `temperature` in API calls as needed.
- **Lottie Animations**: URLs are placeholders; replace with actual Lottie file URLs if needed.
- **Analytics Data**: Fetched dynamically via API; falls back to hardcoded defaults if parsing fails.
- **PDF Generation**: Uses ReportLab to create downloadable PDFs for reports.
- **Custom CSS**: Embedded in the app for styling; modify the `<style>` block for UI changes.

## Dependencies

- streamlit
- pandas
- plotly-express
- reportlab
- requests
- smtplib
- twilio
- streamlit-lottie
- json, datetime, io (standard libraries)

## Limitations

- This is a prototype and not intended for real medical use without validation by professionals.
- API calls may fail due to rate limits or network issues; error handling is included.
- No persistent storage; session state is used for temporary data.
- Analytics are simulated; integrate with real databases for production.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request. For major changes, open an issue first.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For questions, contact [your.email@example.com](mailto:your.email@example.com).
