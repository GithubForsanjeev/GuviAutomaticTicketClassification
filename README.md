🤖 Automated Customer Ticket Triage and LLM Response Generator
This project implements an end-to-end customer support automation pipeline. It uses a Many-to-One Recurrent Neural Network (RNN) for automatic ticket classification and integrates the Google Gemini API to generate instant, empathetic customer acknowledgement replies.

🚀 Project Goal
The objective is to address the challenge of manually sorting thousands of daily support tickets. By automating classification and initial response generation, the system aims to reduce misclassification delays, lower operational costs, and instantly improve customer satisfaction.



✨ Key Features & Business Impact
Feature	Description	Business Use Case
Automatic Classification	
Uses a Many-to-One LSTM model to categorize ticket body text (

body) into the correct department (queue).


Automatically routes tickets to the correct department (e.g., Billing, Technical Support).

Generative AI Response	
Integrates the Gemini 2.5 Pro API to draft a polite, generic acknowledgement reply immediately after classification.


Reduces response times by pre-drafting acknowledgments and providing instant, empathetic replies.



Full Pipeline Automation	
Creates a prototype pipeline that classifies, routes, and replies to customer tickets, minimizing manual triage.



Leads to faster ticket resolution and significant cost optimization.



Export to Sheets
💻 Technical Stack

Deep Learning: RNN, LSTM, Keras/TensorFlow.



Generative AI: Google Gemini API (using google-genai SDK).



Natural Language Processing (NLP): Text Preprocessing, Tokenization, Padding.


Data: Hugging Face Datasets (Tobi-Bueck/customer-support-tickets).


Language: Python.

⚙️ Setup and Installation
1. Clone the Repository
Bash

git clone <YOUR_REPO_URL>
cd <your-project-directory>
2. Install Dependencies
Bash

pip install datasets pandas numpy scikit-learn tensorflow keras
pip install google-genai
3. Configure Gemini API Key
The project relies on the GEMINI_API_KEY environment variable. The genai.Client() will automatically pick this up.

For local execution (Terminal/Shell):

Bash

export GEMINI_API_KEY="YOUR_API_KEY_HERE"
For Jupyter/Colab Notebooks (Best Practice):

Python

import os
# Replace 'YOUR_API_KEY' with a SECURE method (e.g., reading from a local .env file or Colab Secrets)
os.environ['GEMINI_API_KEY'] = 'YOUR_API_KEY_HERE' 
📚 Data Source
The project uses the following public dataset:


Source: Hugging Face - Tobi-Bueck/customer-support-tickets.


Key Fields:


body: The customer's ticket text (Input).



queue: The target department label (Target).


Data Loading Command
You can load the dataset using the following commands:

Python

from datasets import load_dataset
ds = load_dataset("Tobi-Bueck/customer-support-tickets")
✅ Evaluation Metrics
Model success is measured across several dimensions:

Classification Model (RNN/LSTM)

Accuracy: Overall correctness of queue prediction.




Precision, Recall, F1-Score: Performance metrics, calculated per queue category, to understand model effectiveness across different departments.



Confusion Matrix: Used for diagnosing specific misclassifications between queues.

Generative AI Reply

Quality of Generated Replies: Subjective evaluation based on politeness, empathy, and helpfulness (acknowledgment and assurance).


🤝 Skills Taken Away
Text Preprocessing & Tokenization.

Sequence Modeling using RNN/LSTM.

Model Evaluation and Interpretation.

Integration of Machine Learning with Generative AI (Gemini 2.5 Pro API).

Prompt Engineering for structured LLM output.

📝 Project Deliverables

ticket_classification_lstm_model.h5: The trained LSTM model file.


tokenizer.pickle, label_encoder.pickle: Files for preprocessing new data.

Automatic_Ticket_Classification_with_LLM_Reply.ipynb: The end-to-end execution notebook.

Source code in Python for the full pipeline.
