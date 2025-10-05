# 🤖 Automated Customer Ticket Triage and LLM Response Generator

[cite\_start]This project implements an end-to-end customer support automation pipeline[cite: 40]. [cite\_start]It uses a **Many-to-One Recurrent Neural Network (RNN)** to automatically classify ticket body text [cite: 7] [cite\_start]and integrates the **Google Gemini API** to generate instant, empathetic customer acknowledgement replies[cite: 8].

-----

## 🚀 Project Goal

[cite\_start]The objective is to address the challenge of manually sorting thousands of daily support tickets[cite: 5]. [cite\_start]By automating classification and initial response generation, the system aims to reduce misclassification delays, lower operational costs, and instantly improve customer satisfaction[cite: 6, 14].

-----

## ✨ Key Features & Business Impact

| Feature | Description | Business Use Case |
| :--- | :--- | :--- |
| **Automatic Classification** | [cite\_start]Uses a Many-to-One RNN/LSTM model [cite: 29] [cite\_start]to categorize ticket body text (`body`) [cite: 23, 54] [cite\_start]into the correct department (`queue`)[cite: 24, 55]. | [cite\_start]Automatically routes tickets to the correct department (e.g., Billing, Technical Support, Account Services)[cite: 10]. |
| **Generative AI Response** | [cite\_start]Integrates the Gemini 2.5 Pro API [cite: 35, 66] [cite\_start]to draft a polite, generic acknowledgment reply[cite: 36]. | [cite\_start]Reduces response times by pre-drafting acknowledgments [cite: 11] [cite\_start]and providing instant, empathetic replies to customers[cite: 14]. |
| **Full Pipeline Automation** | [cite\_start]Creates a prototype pipeline that classifies, routes, and replies to customer tickets[cite: 40], minimizing manual triage. | [cite\_start]Leads to faster ticket resolution [cite: 11] [cite\_start]and significant cost optimization[cite: 13]. |

-----

## 💻 Technical Stack

  * [cite\_start]**Deep Learning:** RNN [cite: 49][cite\_start], LSTM [cite: 49][cite\_start], Keras/TensorFlow[cite: 66].
  * [cite\_start]**Generative AI:** Google Gemini API [cite: 49, 66] (using the `google-genai` SDK).
  * [cite\_start]**Natural Language Processing (NLP):** NLP [cite: 49][cite\_start], Text Preprocessing & Tokenization[cite: 26].
  * [cite\_start]**Data:** Hugging Face Dataset[cite: 51].
  * [cite\_start]**Language:** Python[cite: 66].

-----

## ⚙️ Setup and Installation

### 1\. Install Dependencies

```bash
pip install datasets pandas numpy scikit-learn tensorflow keras
pip install google-genai
```

### 2\. Configure Gemini API Key

[cite\_start]The project relies on setting the Google Gemini API key securely[cite: 72]. The `genai.Client()` will attempt to automatically pick this up from the environment variable named `GEMINI_API_KEY` or `GOOGLE_API_KEY`.

**For local execution (Terminal/Shell):**

```bash
export GEMINI_API_KEY="YOUR_API_KEY_HERE"
# [cite_start]Note: Ensure API keys are kept secure and not committed to source control[cite: 72].
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

[cite\_start]The project uses the following public dataset[cite: 50]:

  * [cite\_start]**Source:** Hugging Face - `Tobi-Bueck/customer-support-tickets`[cite: 51].
  * **Key Fields:**
      * [cite\_start]`body`: The customer's ticket body text (Input)[cite: 23, 54, 60].
      * [cite\_start]`queue`: The target department label (Target)[cite: 24, 55, 61].

### Data Loading Command

You can load the dataset using the following commands:

```python
from datasets import load_dataset
ds = load_dataset("Tobi-Bueck/customer-support-tickets")
```

-----

## ✅ Evaluation Metrics

[cite\_start]Model success is measured across several dimensions[cite: 41]:

### Classification Model (RNN/LSTM)

  * [cite\_start]**Classification Accuracy** [cite: 42]
  * [cite\_start]**Precision, Recall, and F1-Score** (per queue category) [cite: 43]
  * [cite\_start]**Confusion Matrix** (for understanding misclassifications) [cite: 44]

### Generative AI Reply

  * [cite\_start]**Quality of Generated Replies** (manual/subjective evaluation for politeness and helpfulness)[cite: 45].

-----

## 📝 Project Deliverables

  * [cite\_start]**Source Code** (Python, PyTorch/Keras for RNN model + Google Gemini integration)[cite: 66].
  * [cite\_start]**Documentation** (Project report with methodology, dataset explanation, results)[cite: 67].
  * [cite\_start]**Trained Model** files[cite: 67].
  * [cite\_start]**Sample Outputs** (predicted queue + Google Gemini-generated reply)[cite: 68].
