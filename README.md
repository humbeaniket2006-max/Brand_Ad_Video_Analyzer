🎬 Brand Ad Video Analyzer (PineOS)
Analyze any brand's ad video for tone, messaging, and brand consistency.

The Brand Ad Video Analyzer is an automated intelligence tool built for Google Colab. It processes video advertisements, extracts key frames, and leverages Google's Gemini 2.0 Flash Lite Vision model to perform a deep analysis of brand identity, tone, and product placement.

Built by: Aniket Humbe

✨ Features
Automated Frame Extraction: Uses OpenCV to sample video frames at customizable intervals (e.g., every 2 seconds).

AI-Powered Vision Analysis: Uses the gemini-2.0-flash-lite model to evaluate each frame for products, text, colors, and tone.

Smart Synthesis: Consolidates per-frame data into a comprehensive final brand intelligence report.

Resilient API Handling: Built-in exponential backoff to handle API rate limits gracefully.

Visual & JSON Outputs: View results alongside the extracted frames directly in Colab, and download a structured JSON report for downstream use.

🛠️ Tech Stack
Language: Python 3

Video Processing: OpenCV (opencv-python-headless)

AI/LLM: Google GenAI SDK (google-genai) / Gemini 2.0 Flash Lite Vision

Visualization: Matplotlib (matplotlib)

🚀 How It Works
Upload: Provide any brand advertisement video in .mp4 format.

Extract: The script slices the video into individual image frames based on your chosen time interval.

Analyze: Gemini Vision analyzes each frame individually, scoring it for "on-brand" consistency.

Synthesize: A secondary prompt merges the frame data into a final, deduplicated summary.

Export: The output is a downloadable JSON file containing the full intelligence report.

📋 Setup & Usage
This tool is designed to be run in a Jupyter/Google Colab environment.

Prerequisites
You will need a Gemini API Key. You can get one from Google AI Studio.

Step-by-Step Instructions
Install Dependencies (Cell 1): Run the first cell to install opencv-python-headless and google-genai.

Load API Key (Cell 2): Securely load your Gemini API Key. If you have it saved in Colab Secrets as GEMINI_API_KEY, it will load automatically. Otherwise, you will be prompted to paste it.

Load Core Functions (Cell 3): Run this cell to load the extraction, API, and display logic.

Configure & Run Analysis (Cell 4):

Set the BRAND_NAME (e.g., "Mamaearth").

Set FRAME_INTERVAL_S (seconds between extracted frames).

Set MAX_FRAMES to cap the analysis (useful for free-tier rate limits).

Run the cell and upload your .mp4 file when prompted.

Review Results (Cells 5 & 6): * Cell 5 prints the raw, structured JSON report.

Cell 6 displays a visual breakdown of the analysis, pairing each extracted frame with its specific Gemini evaluation.

Download Report (Cell 7): Run the final cell to save and download a {brand_name}_video_intelligence.json file to your local machine.
