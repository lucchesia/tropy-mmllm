
# Tropy API Multimodal Large Language Models

A toolkit for enriching [Tropy](https://tropy.org) archival collections with AI-generated summaries and semantic embeddings using multimodal large language models (MMLMs).

This project adapts and extends concepts from Taylor Arnold and Lauren Tilton’s [Explainable Search and Discovery of Visual Cultural Heritage Collections with Multimodal Large Language Models](https://2024.computational-humanities-research.org/papers/paper28/), tailored for transparent metadata creation and explainable AI summaries in cultural heritage contexts. It was developed to support the DH2025 workshop *Transcribing the Vatican Archives: Contextualization, Limits, and Opportunities*, led by Anita Lucchesi and Sean Takats.

---

## 🚀 Features

### Core Capabilities
* **Multi-Model Support:** Choose between Google Gemini, OpenAI GPT-4, or Anthropic Claude
* **Direct Tropy Integration:** Uses Tropy’s local REST API to fetch items, photos, and transcriptions
* **AI-Powered Photo Summaries:** Generates scholarly-level photo summaries, prioritizing transcriptions while leveraging image context
* **Item-Level Syntheses:** Combines photo summaries into comprehensive item overviews with suggested titles
* **Semantic Embeddings:** Creates vector embeddings for advanced search, clustering, or recommendation tasks
* **Smart Note Creation:** Automatically saves AI-generated summaries as notes in Tropy with clear formatting

### Processing Features
* **Flexible Selection:** Process entire collections, specific items, or items in lists
* **Batch Processing:** Efficiently handles large collections with configurable batch sizes
* **Checkpoint System:** Interrupt and resume processing safely
* **Rate Limiting:** Respects API limits for stable operation
* **Clean Slate Tool:** Easily remove AI-generated notes if needed

---

## 📋 Requirements

* **Tropy** (latest version) with REST API enabled
* **Python 3.8+**
* **Jupyter Notebook** or **JupyterLab**
* **API Key** for at least one AI provider (Google, OpenAI, or Anthropic)

---

## ⚙️ Setup

### 1. Clone the Repository

```bash
git clone https://github.com/lucchesia/tropy-mmllm.git
cd tropy-mmllm
```

### 2. Set up Python Environment with Astra UV

[Astra UV](https://github.com/astral-sh/uv) is a fast Python package installer and resolver.

#### **Windows**

```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"

uv venv
.venv\Scripts\activate
uv pip install -r requirements.txt
uv pip install notebook
```

#### **macOS**

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
# Or using Homebrew
brew install uv

uv venv
source .venv/bin/activate
uv pip install -r requirements.txt
uv pip install notebook
```

#### **Linux**

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh

uv venv
source .venv/bin/activate
uv pip install -r requirements.txt
uv pip install notebook
```

### 3. Configure API Keys

Create a `.env` file in the project root:

```bash
# Google Gemini
GOOGLE_API_KEY="your-google-api-key-here"

# OpenAI
OPENAI_API_KEY="your-openai-api-key-here"

# Anthropic Claude
ANTHROPIC_API_KEY="your-anthropic-api-key-here"
```

**Get keys here:**
- **Google AI Studio:** https://makersuite.google.com/app/apikey
- **OpenAI:** https://platform.openai.com/api-keys
- **Anthropic:** https://console.anthropic.com/


---

## 🗺️ Quick Start

1. **Start Jupyter Notebook**

```bash
jupyter notebook
```

2. **Open the notebook**: `tropy-mmllm-analysis-multimodels.ipynb`
3. **Configure your AI provider** (Cell 2)
4. **Select items to process** (Cell 8)
5. **Run processing** (Cell 12)
6. **Attach item summaries** (Cell 13)
7. **Review AI-generated notes in Tropy**


### DH2025 Source Sample

For the DH2025 workshop, we selected a focused source sample from the [Serie Ebrei](https://www.vatican.va/roman_curia/secretariat_state/sezione-rapporti-stati/archivio-storico/serie-ebrei/serie-ebrei_it.html) of the Vatican Apostolic Archive, comprising files 001, 035, 067, 068, 148, and 149.

This subset was chosen to represent different thematic strands within the series while keeping a practical scale for live demonstration and hands-on analysis. The sample includes **1,389 photos**, distributed across **112 items** in Tropy, providing an ideal balance between richness and manageability for exploring multimodal summarization, metadata enrichment, and digital archival workflows.

The source sample is available for download here: [Google Drive - DH2025 Source Sample](https://drive.google.com/drive/folders/1FHK9q-j9ZpsWKCXxaBkuaxjUc3nIIxn4?usp=sharing).  

Please download the `.tropy` project file to open and experiment with a ready-to-use Tropy project. Additionally, import the **Vatican Ebrei Series Item template** and **Vatican Ebrei Series Photo template** (both provided as `.ttp` files) to ensure metadata consistency and proper structure. See [here](https://docs.tropy.org/in-the-template-editor/export-import-templates) for how to import or export templates in Tropy.
