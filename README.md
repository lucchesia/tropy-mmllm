
# Tropy API Multimodal Large Language Models

This repository provides an experimental pipeline integrating Tropy’s API with multimodal large language models, enabling advanced transcription analysis, image-based document interpretation, and rich metadata summarization.

The project adapts and extends concepts from Taylor Arnold and Lauren Tilton’s [Explainable Search and Discovery of Visual Cultural Heritage Collections with Multimodal Large Language Models](https://2024.computational-humanities-research.org/papers/paper28/) to support transparent metadata creation and explainable AI summaries in cultural heritage contexts. It is designed to support the DH2025 workshop *Transcribing the Vatican Archives: Contextualization, Limits, and Opportunities*, led by Anita Lucchesi and Sean Takats.

---

## 🚀 Features

* **Direct Tropy Integration:** Uses the local Tropy API to fetch items, photos, and transcriptions.
* **AI-Powered Photo Summaries:** Generates scholarly-level summaries of individual photos, prioritizing transcriptions and using visual context carefully.
* **Item-Level Syntheses:** Combines photo summaries into a single item-level overview, including suggested titles.
* **Embeddings & Metadata:** Creates vector embeddings for advanced search and analysis.
* **Smart Note Creation:** Automatically writes AI-generated summaries as notes in Tropy.
* **Checkpoints & Clean Slate:** Supports checkpointing, re-runs, and cleaning AI-generated content as needed.

---

## ⚙️ Setup

### Install Python dependencies

```bash
pip install -r requirements.txt
```

### Configure API Key

Set your Google API key for Gemini (e.g., in a `.env` file):

```bash
export GOOGLE_API_KEY="your-key-here"
```

---

## 🗺️ Quick Start

1. Start your Tropy project and enable the API server.
2. Run the analysis notebook (`tropy-mmllm_analysis.ipynb`) to select items and generate summaries.
3. Review AI-generated notes directly inside Tropy.
4. Use the optional clean-up tool to remove AI notes if desired.
