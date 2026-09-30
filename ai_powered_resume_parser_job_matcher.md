# AI-Powered Resume Parser & Job Matcher

A production-ready Python automation tool designed to streamline technical recruitment. It leverages Large Language Models (**Groq API**) combined with strict schema enforcement (**Pydantic**) to extract unstructured data from candidate resumes, compare them against detailed job requirements, and output ranked recruitment scorecards.

---

## What It Does

* **Automated Document Ingestion**: Scans local directories to process candidate files, automatically handling multi-format parsing for both `.pdf` (via `pypdf`) and `.docx` (via `python-docx`) files.
* **Strict Schema Validation**: Bypasses the erratic formatting common with raw LLM outputs by enforcing rigid Pydantic data schemas, ensuring consistent extraction of names, contact info, skills, and work experience.
* **AI-Driven Recruitment Evaluation**: Compares structured candidate profiles against a target job description using a specialized recruiter persona prompt.
* **Automated Scoring & Sorting**: Evaluates candidates on a match scale, identifies missing key skills, writes custom verdicts, and automatically sorts the applicant pool to surface top and bottom matches.

---

## Tech Stack & Architecture

* **Language**: Python
* **AI Engine**: Groq API 
* **Data Validation**: Pydantic (Runtime type checking and JSON schema generation)
* **File Handling**: `pathlib`, `pypdf`, `python-docx`
* **Environment & Package Management**: `uv`, `python-dotenv`

---

## Project Structure

```text
├── resumes/                 # Directory containing applicant resume files (.pdf / .docx)
├── resume_parser.py         # Main script containing text extraction, LLM logic, and ranking loop
├── pyproject.toml / uv.lock # Dependency manifests managed via uv
└── .env                     # Local environment file for secure API key storage
```

---

## Setup & Installation Requirements

This project is built using **`uv`** for fast dependency resolution and virtual environment management. Follow these steps to configure your local machine safely without hardcoding sensitive credentials.

### Prerequisites
* Ensure Python and **`uv`** are installed on your system.

### Step-by-Step Installation

1. **Clone or download the project folder**, then open your terminal inside the root directory.

2. **Initialize the virtual environment and sync dependencies using `uv`:**
   ```bash
   uv venv
   source .venv/bin/activate  # On Windows PowerShell, use: .venv\Scripts\Activate
   uv sync
   ```

3. **Secure Your API Key (Crucial Security Step):**
   * **Never hardcode your API key** directly into `resume_parser.py`, as exposing keys risks credential theft.
   * Create a file named `.env` in the root directory.
   * Add your Groq API key inside the `.env` file like this:
     ```env
     GROQ_API_KEY=your_actual_api_key_here
     ```

4. **Prepare Your Data:**
   * Create a folder named `resumes/` in the project root.
   * Drop your target candidate resume files (`.pdf` or `.docx`) inside that folder.

5. **Run the Script:**
   ```bash
   python resume_parser.py