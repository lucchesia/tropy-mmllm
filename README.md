
# Tropy API Multimodal Large Language Models

A toolkit for enriching [Tropy](https://tropy.org) archival collections with AI-generated summaries and semantic embeddings using multimodal large language models (MMLMs).

This project adapts and extends concepts from Taylor Arnold and Lauren Tilton’s [Explainable Search and Discovery of Visual Cultural Heritage Collections with Multimodal Large Language Models](https://2024.computational-humanities-research.org/papers/paper28/), tailored for transparent metadata creation and explainable AI summaries in cultural heritage contexts. It was developed to support the DH2025 workshop *Transcribing the Past, Contextualizing the Present: AI-Assisted Document Contextualization, Limits, and Opportunities*, led by Anita Lucchesi and Sean Takats.

---

## Features

- **Multi-Model Support:** Choose between Google Gemini, OpenAI GPT-4o, or Anthropic Claude 3.5 Sonnet.
- **Direct Tropy Integration:** Uses Tropy’s local REST API to fetch project data.
- **AI-Powered Summaries:** Generates scholarly photo and item-level summaries by analyzing images and transcriptions.
- **Semantic Embeddings:** Creates vector embeddings for advanced search and clustering.
- **Automated Note Creation:** Saves machine-generated summaries directly into your Tropy project.
- **Interactive Analysis:** Search your collection with natural language, discover themes, and enhance metadata.
- **Safe & Resumable:** Features batch processing and a checkpoint system to handle large collections safely.

---

## Requirements

- [Tropy Beta 2](https://github.com/tropy/tropy/releases/tag/v1.16.3-beta.2)
- Python (version 3.8 to 3.12).
- Astra UV, a fast, modern Python package installer.
- An API Key for at least one AI provider (Google, OpenAI, or Anthropic). 

*Nota bene*: For the workshop duration, the Tropy team will provide attendees with courtesy API keys for AI providers. 

---

## Setup Instructions

### 1️⃣ Clone or Download the Repository

```bash
git clone https://github.com/lucchesia/tropy-mmllm.git
cd tropy-mmllm
```

Alternatively, download as a ZIP and extract.

---

### 2️⃣ Set Up the Python Environment with UV

**Astra UV** is a modern replacement for pip and venv.

#### Windows

1. Open PowerShell and install UV:

```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

2. **Important:** Close and re-open PowerShell for `uv` to become available.
3. Create and activate the virtual environment, then install packages:

```powershell
uv venv
.\.venv\Scripts\Activate.ps1
uv pip install -r requirements.txt
```

---

#### macOS / Linux

1. Open your terminal and install UV:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

2. Create and activate the virtual environment, then install packages:

```bash
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt
```

**Tip for Linux users:** If `uv` isn’t found after installation, run:

```bash
source $HOME/.cargo/env
```

---

### 3️⃣ Install Poppler

This utility is required for processing PDF files.

- macOS (with Homebrew):  
  ```bash
  brew install poppler
  ```
- Linux (Debian/Ubuntu):  
  ```bash
  sudo apt-get install poppler-utils
  ```
- Windows:  
  Download binaries from [Poppler for Windows](http://blog.alivate.com.au/poppler-windows/), unzip, and add the `bin/` folder to your system PATH.

---

### 4️⃣ Configure Your API Keys

Create a file named `.env` in the project’s root directory. 

- macOS and Linux:  
  ```bash
  touch .env
  ```
- Windows CMD:
  ```powershell
  echo > .env
  ```

Open `.env` and add your keys (you only need one, but can add all three):

```txt
GOOGLE_API_KEY="your-google-api-key-here"
OPENAI_API_KEY="your-openai-api-key-here"
ANTHROPIC_API_KEY="your-anthropic-api-key-here"
```

---

### 5️⃣ Enable the Tropy API

Find and open Tropy’s `state.json` file:

- macOS: `~/Library/Application Support/Tropy/state.json`
- Windows: `C:\Users\<YourUser>\AppData\Roaming\Tropy\state.json`
- Or, from Tropy 'Help' > Show User-Data Folder

Crucial: Make sure to close Tropy before editing the `state.json`.

Add `"api": true,` along other config, e.g. `"debug": false,`:

```json
{
  "debug": false,
  "api": true,
  ...
}
```

Save the file, then reopen Tropy. The API will be active at `http://localhost:2019`.

---

## Workflow Overview: The Two Notebooks

This project uses a two-stage workflow to ensure clarity and safety.

---

### Notebook 1: `tropy-mmllm-analysis-multimodel.ipynb`

**Purpose:** Data Generation

- Connects to your Tropy project.
- Lets you choose your AI model.
- Lets you select which items or lists to process.
- Generates summaries and embeddings for each photo.
- Saves results back to Tropy as notes and creates local JSON files (e.g., `tropy_embeddings_[model].json`) for the next stage.

---

### Notebook 2: `tropy-mmllm-queries-multimodel.ipynb`

**Purpose:** Interactive Analysis

- Loads the embeddings and summaries generated earlier.
- Performs semantic searches on your collection using natural language.
- Discovers thematic clusters.
- Enhances item metadata with machine-generated suggested titles.
- Programmatically tags items based on analysis.

---

## DH2025 Source Sample

For the DH2025 workshop, we selected a focused source sample from the [Serie Ebrei](https://www.vatican.va/roman_curia/secretariat_state/sezione-rapporti-stati/archivio-storico/serie-ebrei/serie-ebrei_it.html) of the Vatican Apostolic Archive, comprising files 001, 035, 067, 068, 148 and 149 with existing transcriptions and file 153 without transcriptions.

This subset was chosen to represent different thematic strands within the series while keeping a practical scale for live demonstration and hands-on analysis. The sample includes **1,389 photos**, distributed across **112 items** in Tropy, providing an ideal balance between richness and manageability for exploring multimodal summarization, metadata enrichment, and digital archival workflows.

The source sample is available for download here: [Google Drive - DH2025 Source Sample](https://drive.google.com/drive/folders/1FHK9q-j9ZpsWKCXxaBkuaxjUc3nIIxn4?usp=sharing).  

Please download the `.tropy` project file to open and experiment with a ready-to-use Tropy project. Additionally, import the **Vatican Ebrei Series Item template** and **Vatican Ebrei Series Photo template** (both provided as `.ttp` files) to ensure metadata consistency and proper structure. See [here](https://docs.tropy.org/in-the-template-editor/export-import-templates) for how to import or export templates in Tropy.

---

## Transcribe with Tropy 

As part of a this workshop experiment, an early version of the Tropy transcription plugin will be available along with 10 daily credits/images per day running through the workshop until the end of the conference. You will receive a link to download the transcription plugin and the API key by email right before the workshop.

This is a great opportunity to generate high-quality transcriptions for your own items before running them through this analysis workflow.  


---

## Ethical Considerations

Working with AI and sensitive historical archives requires critical reflection.

- **Acknowledge Bias:** AI models can perpetuate historical biases. Always critically evaluate the summaries and themes they generate.
- **Transparency:** Notes and titles created by this workflow are clearly marked as "machine-generated" to distinguish between archival fact and computational interpretation.
- **Non-Destructive:** We encourage workflows that add information (notes, tags or specific metadata fields) rather than overwrite existing metadata.

Feel free to customize prompts in the notebooks to refine your model outputs and analytical focus according to your research needs.
