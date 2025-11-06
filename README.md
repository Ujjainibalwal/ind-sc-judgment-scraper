# ind-sc-judgment-scraper
Here is a project description for a GitHub "README" file, based on the project you outlined.

⚖️ IND-SC-Judgments-Extractor
A Scrapy pipeline to download, parse, and clean the 100 most recent Supreme Court of India judgments, saving them as structured JSON files for data analysis, R&D, or AI model training.

Overview
This project is a specialized web scraper designed to tackle the challenge of acquiring clean, machine-readable data from the Supreme Court of India's e-Courts portal. The pipeline automates the entire process:

It finds and downloads the 100 most recent judgments (which are in PDF format).

It parses each PDF to extract the raw text.

It cleans the text by removing common document clutter (like page numbers, headers, and footers).

It saves each judgment as a separate, clean .json file, ready for the next step in your data pipeline.

This repository is a foundational tool for any legal-tech, data science, or AI project that requires a high-quality, up-to-date corpus of Indian case law.

✨ Key Features
Automated Crawling: A Scrapy "spider" that navigates the e-Courts portal to find and download the latest judgments.

High-Fidelity PDF Parsing: Uses pdfplumber to accurately extract text from text-based PDFs, preserving layout information where possible.

Text Sanitization: A built-in Scrapy Item Pipeline that uses Regular Expressions (Regex) to clean the raw text. It's configured to remove:

Page numbers (e.g., "Page 1 of 50")

Common headers/footers

Unnecessary whitespace and line breaks

Structured JSON Output: Each judgment is saved as a JSON file, typically containing:

case_number: The unique identifier for the case.

judgment_date: The date the judgment was published.

source_url: The URL where the PDF was found.

clean_text: The full, cleaned text of the judgment.

Version Controlled: The project is managed with git, allowing for tracking changes to the spiders and cleaning logic over time.

💻 Tech Stack & Key Libraries
This project is built on a modern Python data-extraction stack:

Core Framework: Scrapy (for handling the crawling, asynchronous requests, and data pipeline).

PDF Parsing: pdfplumber (for opening and reading the .pdf files).

Text Cleaning: re (Regex) (Python's built-in module for pattern matching and text cleaning).

Data Serialization: json (Python's built-in module for creating the output files).

Core Language: Python 3.x

Version Control: git

⚙️ Project Workflow
The data flows through the project in a simple, four-step pipeline:

Spider (Crawl): The sc_judgment_spider starts at the target URL, identifies the links for the 100 most recent judgment PDFs, and sends them to the downloader.

PDF Parser (Parse): Once a PDF is downloaded, a custom ItemLoader or pipeline step uses pdfplumber to open the file in memory and extract all text.

Cleaning Pipeline (Clean): The raw text is passed to the TextCleaningPipeline. This pipeline applies a series of Regex substitutions to remove headers, footers, and page numbers.

JSON Exporter (Store): The final, clean item (containing the case metadata and cleaned text) is exported as a separate .json file to the /output directory.

🚀 Potential Future Enhancements
Pagination: Extend the spider to go beyond the first 100 results and crawl historical data.

OCR Integration: Add a fallback using pytesseract or PaddleOCR to handle scanned (image-based) PDFs that pdfplumber cannot read.

Database Storage: Implement a new pipeline to save the data to a database (like PostgreSQL) or a vector database (like Qdrant or Milvus) for AI applications.

Containerization: Add a Dockerfile and docker-compose.yml to make the entire project easy to run anywhere.
