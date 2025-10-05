# 🤖 Automated Customer Ticket Triage and LLM Response Generator

This project implements an end-to-end customer support automation pipeline. It uses a **Many-to-One Recurrent Neural Network (RNN)** to automatically classify ticket body text and integrates the **Google Gemini API** to generate instant, empathetic customer acknowledgement replies.

-----

## 🚀 Project Goal

The objective is to address the challenge of manually sorting thousands of daily support tickets. By automating classification and initial response generation, the system aims to reduce misclassification delays, lower operational costs, and instantly improve customer satisfaction.

-----

## ✨ Key Features & Business Impact

| Feature | Description | Business Use Case |
| :--- | :--- | :--- |
| **Automatic Classification** | Uses a Many-to-One RNN/LSTM model  to categorize ticket body text (`body`)  into the correct department (`queue`). | Automatically routes tickets to the correct department (e.g., Billing, Technical Support, Account Services). |
| **Generative AI Response** | Integrates the Gemini 2.5 Pro API to draft a polite, generic acknowledgment reply. | Reduces response times by pre-drafting acknowledgments and providing instant, empathetic replies to customers. |
| **Full Pipeline Automation** | Creates a prototype pipeline that classifies, routes, and replies to customer tickets minimizing manual triage. | Leads to faster ticket resolution and significant cost optimization. |

-----

## 💻 Technical Stack

  * **Deep Learning:** RNN, LSTM, Keras/TensorFlow.
  * **Generative AI:** Google Gemini API (using the `google-genai` SDK).
  * **Natural Language Processing (NLP):** NLP, Text Preprocessing & Tokenization.
  * **Data:** Hugging Face Dataset.
  * **Language:** Python.

-----

## ⚙️ Setup and Installation

### 1\. Install Dependencies

```bash
pip install datasets pandas numpy scikit-learn tensorflow keras
pip install google-genai
```

### 2\. Configure Gemini API Key

The project relies on setting the Google Gemini API key securely. The `genai.Client()` will attempt to automatically pick this up from the environment variable named `GEMINI_API_KEY` or `GOOGLE_API_KEY`.

**For local execution (Terminal/Shell):**

```bash
export GEMINI_API_KEY="YOUR_API_KEY_HERE"
# Note: Ensure API keys are kept secure and not committed to source control.
```

**For Jupyter/Colab Notebooks:**

```python
import os
# Recommended: Use a secure method like Colab Secrets to store and retrieve your key.
# e.g., os.environ['GEMINI_API_KEY'] = userdata.get('GEMINI_API_KEY') 

from google import genai
# The client automatically uses the environment variable:
# client = genai.Client()
```

-----

## 📚 Data Source

The project uses the following public dataset:

  * **Source:** Hugging Face - `Tobi-Bueck/customer-support-tickets`.
  * **Key Fields:**
      * `body`: The customer's ticket body text (Input).
      * `queue`: The target department label (Target).

### Data Loading Command

You can load the dataset using the following commands:

```python
from datasets import load_dataset
ds = load_dataset("Tobi-Bueck/customer-support-tickets")
```

-----

## ✅ Evaluation Metrics

Model success is measured across several dimensions:

### Classification Model (RNN/LSTM)

  * **Classification Accuracy**
  * **Precision, Recall, and F1-Score** (per queue category)
  * **Confusion Matrix** (for understanding misclassifications)

### Generative AI Reply

  * **Quality of Generated Replies** (manual/subjective evaluation for politeness and helpfulness).

-----

## 📝 Project Deliverables

  * **Source Code** (Python, PyTorch/Keras for RNN model + Google Gemini integration).
  * **Documentation** (Project report with methodology, dataset explanation, results).
  * **Trained Model** files.
  * **Sample Outputs** (predicted queue + Google Gemini-generated reply).
