# AI Powered Resume Parser & Job Matcher

A production ready automations tool in Python meant for technical recruiting purposes. This solution employs the power of Large Language Models (Groq API) and rigorous schema enforcement (Pydantic) to parse unstructured free text from candidates, compare with detailed requirements and generate recruitment scorecards.
---

# What it does

Automated Document Ingestion: This tool is capable of scanning through local directories for candidate document processing. It features multi-format parsing functionality for easier processing of `.pdf` and `.docx` file formats (through `pypdf` and `python-docx` respectively).
Strict Schema Validation: Avoids the messy and unreliable output of raw LLMs by enforcing strict data schema parsing (through Pydantic) ensuring consistent extraction of names, contact details, skills and work experience
AI-Driven Recruitment Evaluation: Leverages special recruiter persona to compare parsed documents against a given target post requirements to produce a recruitment scorecard
Automated Scoring & Sorting: Calculates percentage match against target requirements, identifies skill gaps and even generates custom verdicts while automatically sorting the applicant pool to highlight best and worst matches.
---
# Technologies Used

Language: Python
AI Model: Groq API
Schema Validation: Pydantic
File Parsing: `pathlib`, `pypdf`, `python-docx`
Environment & Packaging: `uv`, `python-dotenv`
---

# Folder Structure

The project follows a standard structure as shown below:
```text
├── resumes/         # Contains resume documents from applicants

├── resume_parser.py     # Main script containing text extraction, LLM logic and ranking loop
├── pyproject.toml / uv.lock # Contains project dependencies using uv
└── .env           # Contains local environment variables (not committed to github)
```
---
# How to Setup
The project has been configured using `uv` for faster dependency resolution and virtual environment creation. Please follow the steps below to setup your local deployment while avoiding security pitfalls such as hardcoding api keys.
### Prerequisites
Ensure that you have Python and uv installed in your system
### Installation
1. Start by cloning or downloading this repository and navigating to the project folder using your terminal
2. Create a virtual environment and install dependencies using uv as follows
```bash
uv venv
source .venv/bin/activate # For windows powershell use: .venv\Scripts\Activate
uv sync
```
3. Securing your API Keys (Very important!)
Never hard-code your API keys into your code for security reasons. Instead, create a file called `.env` in your project root and store your API key there. Your secret api key will never be pushed to your repository for security reasons.
```env
GROQ_API_KEY=your_actual_api_key_here
```
4. Preparing your data
Create a folder called `resumes/` in your project root and store your target candidate documents (.pdf/.docx)
5. Finally, execute the following command in your terminal to start the parsing and ranking process
```bash
python resume_parser.py
