KrushiMitra AI ​
AI-powered crop disease detection and farming assistance for Indian
farmers
KrushiMitra AI is a mobile-first agriculture project designed to help
farmers---especially in Maharashtra---identify possible crop diseases
and pest problems early. It combines crop-image analysis with weather
information and simple, local-language farming guidance.
Project status: Hackathon prototype / work in progress. Model
predictions and recommendations should be verified before making
important farming decisions.

Table of Contents
Problem
Our Solution
Main Features
How It Works
Technology Stack
AI Model and Dataset
Proposed Architecture
Project Structure
Getting Started
Development Roadmap
Limitations and Safety
Future Improvements
Contributing
Team and Contact

Problem
Farmers may lose crops because diseases and pests are not identified
early. Expert help may be difficult to access, weather can increase
disease risk, and farmers may not receive clear guidance about
prevention and treatment.

Our Solution
KrushiMitra AI aims to make crop-health support easier to access. A
farmer can select a crop, upload or capture a crop image, review the
AI's possible diagnosis, check relevant weather information, and get
easy-to-understand guidance. The long-term goal is to support early
action, reduce avoidable crop loss, and encourage responsible pesticide
use.

1. Farmer Dashboard
Simple home screen with crop and crop-health summaries.
Weather information and quick access to key features.
Easy navigation designed for mobile users.

2. Crop Selection
Select the crop before scanning.
Crop selection helps provide more relevant results and advice.

4. Crop Disease and Pest Scanner
Capture a photo or upload an existing image.
Analyze the image with an AI image-classification model.
Show the predicted class and confidence when available.

4. Diagnosis and Guidance
Explain the possible disease or pest in simple language.
Present possible symptoms and suggested next steps.
Include prevention advice and safety reminders.
Keep the result clear that an AI prediction is not a guaranteed
diagnosis.

5. Weather-Based Risk Support
Display weather information when a weather API is configured.
Future risk analysis can combine crop, weather, location, and other
environmental signals.
Weather-based risk estimates require validation with reliable local
data.

6. Krushi AI Chatbot
Intended to answer common agriculture questions in simple language.
Planned topics include crop care, symptoms, prevention, weather, and
general farming practices.
Responses should be grounded in trusted agricultural sources.

7. Local-Language Support
Planned language support includes Marathi, Hindi, and English.
Language availability depends on the current implementation.

8. Future Officer Dashboard
Planned dashboard for authorized agricultural officers.
Potential features include outbreak reports, risk-area maps, case
follow-up, and aggregated crop-health trends.

How It Works
Choose a crop: The farmer selects the crop they want to check.
Add a photo: The farmer captures or uploads an image of the
affected plant.
Analyze the image: The AI model predicts a possible disease or
pest class.
Review the result: The app displays the prediction and available
confidence information.
Check context: Weather and other information can help add
context to the result.
Take informed action: The farmer reviews prevention or treatment
guidance and contacts an agricultural expert when needed.

Technology Stack
The project has used or proposed the following technologies. Actual
availability depends on which modules have been connected in the current
build.
Area                                Technology
Farmer mobile app                   Flutter and Dart
AI image model                      TensorFlow / Keras, EfficientNetB0
Model development                   Python and Google Colab
Backend API (planned/proposed)      Python and FastAPI
Data and authentication (proposed)  Supabase; other services may be
evaluated as needed
Weather information                 Weather API integration
Officer dashboard (planned)         React or another web frontend

Source control Git and GitHub

AI Model and Dataset
An experimental crop-pest image classifier has been trained using
EfficientNetB0.
Recorded training setup: - Classes: 132 - Total images: 55,864 -
Training split: 44,691 images - Validation split: 5,586 images -
Test split: 5,587 images - Input image size: 224 × 224 pixels -
Framework: TensorFlow / Keras - Recorded validation accuracy
during fine-tuning: approximately 61.44%
These figures describe the recorded experiment, not a guarantee of
real-world performance. Accuracy can vary by crop, disease, image
quality, lighting, and field conditions. Before deployment, test the
model on independent, locally collected field images and evaluate
per-class precision, recall, confusion matrix, and confidence
calibration.

A model file mentioned during development was:
krushimitra_pest_final_model.keras
​
The model file is not included in this README. Keep large model files
and datasets in suitable storage rather than committing them to Git
unless the repository is specifically configured for them.
Proposed Architecture

Farmer
  |
  v
Flutter Mobile App
  |-- Crop selection
  |-- Camera / image upload
  |-- Diagnosis and advice
  |-- Weather and chatbot screens
  |
  v
Backend API (planned)
  |-- Input validation
  |-- AI model inference
  |-- Weather / context integration
  |-- Advisory service
  |
  +------> AI Image Model (EfficientNetB0)
  |
  +------> Database / Storage (as configured)
  |
  +------> Weather API (when configured)

Future: Officer Dashboard
  |-- Reports and follow-up
  |-- Aggregated risk areas
  |-- Outbreak monitoring

  Project Structure
The exact folders may differ in the current repository. A possible
organization is:
KrushiMitra-AI/
├── farmer_app/          # Flutter mobile application
├── backend/             # API and application logic
├── ai_model/            # Model code, evaluation, and inference
├── officer_dashboard/   # Future web dashboard
├── docs/                # Architecture and project documentation
├── .gitignore
└── README.md

Do not create empty folders just to match this example; adapt it to the
actual project.

Getting Started
Requirements
Git
Flutter SDK and Dart
Android Studio or another supported Flutter development environment
Python, if you are running the AI model or backend locally
API credentials for external services, only if those integrations
are enabled
1. Clone the repository
Replace the placeholder with the actual GitHub repository URL:
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_PROJECT_FOLDER>

2. Run the Flutter app
Open a terminal in the Flutter app directory:
cd farmer_app
flutter pub get
flutter doctor
flutter run
​
If the Flutter app is located at the repository root, run these commands
from the root instead. Fix any environment issues reported by
flutter doctor.

3. Run the backend (if implemented)
If the backend contains a requirements.txt file, create a virtual
environment and install dependencies:
Windows PowerShell
cd backend
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
​
Start the server using the command documented in the backend code. For a
FastAPI app whose entry point is main.py, this may be:
uvicorn main:app --reload

The command above only applies if the project actually has a FastAPI
application at backend/main.py.

4. Configure environment variables
Create a local .env file only if the project requires one. Add the
required API keys and configuration values there. Never commit API
keys, passwords, access tokens, or private credentials to GitHub. Add
.env to .gitignore.

5. Model setup
If you are running inference locally, place the trained model where the
inference code expects it and configure the model path. Install the
dependencies specified by the AI module. Training and inference setup
may be different, so follow the instructions in that module.

Development Roadmap

Define the crop-health problem and solution concept.

Build an experimental EfficientNetB0 image-classification model.

Complete and test the mobile dashboard and crop-selection flow.

Connect image upload to model inference.

Display clear diagnosis results and confidence information.

Integrate weather data and handle API failures.

Build a reliable agriculture chatbot using trusted sources.

Add Marathi, Hindi, and English language support.

Test with real field images across different lighting and
backgrounds.

Add feedback and expert-review workflows.

Develop an officer dashboard and outbreak reporting, if
required.

Test privacy, security, usability, and performance before wider
release.
Checkboxes should be updated as each item is implemented and tested.

Limitations and Safety
An image model can make incorrect predictions, especially for
unfamiliar crops, mixed infections, poor-quality photos, or field
conditions unlike its training data.
A model's confidence score is not the same as a confirmed diagnosis.
Do not apply pesticides based only on an AI prediction. Confirm the
issue with a qualified agricultural expert or local agricultural
department.
Follow product labels, local regulations, protective-equipment
instructions, and recommended dosage guidance.
Weather-based risk estimates depend on data quality and should not
be presented as certain predictions.
Protect farmers' personal data and location. Collect only what the
app needs and explain how it is used.

Future Improvements
Improve model performance with verified field images from
Maharashtra.
Add multi-disease detection and crop-specific severity estimation.
Support offline or low-bandwidth use where practical.
Add voice input and audio responses for accessibility.
Improve weather-based risk alerts and location-aware advisories.
Enable expert validation, farmer feedback, and case tracking.
Build a map-based view of confirmed reports while protecting user
privacy.

Contributing
Contributions and suggestions are welcome.
Create a fork or a feature branch.
Make a focused change.
Test the change on the relevant module.
Submit a pull request with a clear description of what changed.
Please avoid committing secrets, private farmer information, or large
datasets without permission.

Team and Contact
Project: KrushiMitra AI\
Focus: Early detection and management of crop diseases and pest
infestations\
Primary audience: Indian farmers, with an initial focus on
Maharashtra

team details 
karan pansari : 8208655810
kaushal galphade : 84019 13687
tanay patil : 99706 20864
yash patil : 94047 96074
Devesh zine : 86240 92412
