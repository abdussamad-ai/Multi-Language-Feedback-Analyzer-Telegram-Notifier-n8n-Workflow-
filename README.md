# Multi-Language Feedback Analyzer & Telegram Notifier (n8n Workflow)

This repository contains an automated **n8n workflow** that analyzes multi-language customer feedback using Google Gemini AI, parses and structures the response via custom JavaScript, filters it using conditional logic, and instantly dispatches alerts to **Telegram**.

---

## 🛠️ Workflow Architecture & Data Flow

The workflow consists of the following connected nodes:

1. **Manual Trigger (`When clicking ‘Execute workflow’`)**: Initiates the workflow manually.
2. **Edit Fields (`Set Node`)**: Injects sample customer feedback text for processing.
3. **Google Gemini AI**: Analyzes the feedback text to determine language, translation, sentiment, sentiment score, category, and a one-sentence summary.
4. **Code in JavaScript**: Runs a custom script to clean the raw AI output (stripping markdown code blocks like ```json) and extracts the `sentiment` field into a valid JSON structure.
5. **If Node**: Evaluates whether the extracted `sentiment` equals `Negative` using strict expression matching (`{{ $json.sentiment }}`).
6. **Telegram Node**: Automatically sends a formatted notification message to a specified Telegram chat/group based on the conditional output.

---

## 📂 Files Included in this Repository

* **`My workflow 7 (2).json`**: The complete, exportable n8n workflow file containing all configured nodes, parameters, and connection mappings.

---

## 🚀 How to Import and Use This Workflow in n8n

1. Download or clone this repository to your local machine.
2. Open your self-hosted or cloud-based **n8n** instance.
3. Click on **Add workflow** (or options menu `...` in the top right corner) and select **Import from File**.
4. Upload the `My workflow 7 (2).json` file provided in this repository.
5. Configure your respective credentials:
   * **Google Gemini API Credentials** for the Gemini AI node.
   * **Telegram API Credentials (Bot Token & Chat ID)** for the Telegram node.
6. Click **Execute Workflow** to test the automation!

---

## 📝 License
This project is open-source and available under the [MIT License](LICENSE).
