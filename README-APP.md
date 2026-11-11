# NCERT AI Teacher

A Streamlit app that teaches from uploaded NCERT PDFs section by section.

## Features

- Classes 6–12 and multiple school subjects
- Hinglish (Roman), Hindi (Devanagari), and English
- Upload one or more selectable-text PDFs
- Breaks extracted text into manageable lesson sections
- AI explanations, doubts, quiz questions, and revision notes
- Previous/next section navigation and repeat explanations
- Uses PDF page labels in the lesson context
- Handles scanned PDFs, encrypted files, and common upload errors

## Run locally

1. Install Python 3.10 or newer.
2. Open a terminal in this folder.
3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Set your OpenAI API key as an environment variable:

   **macOS / Linux**
   ```bash
   export OPENAI_API_KEY="your-api-key"
   ```

   **Windows PowerShell**
   ```powershell
   $env:OPENAI_API_KEY="your-api-key"
   ```

   Alternatively, enter the key in the app sidebar. Do not share your API key.

5. Start the app:

   ```bash
   streamlit run app.py
   ```

6. In the sidebar, choose class, subject, language, upload PDF(s), choose the page range, and click **Padhai shuru karo**.

## Configuration

- `CHAT_MODEL`: optional environment variable to select a model available to your API account. Default: `gpt-4o`.
- `OPENAI_API_KEY`: API key used to call the OpenAI API.
- `PART_WORDS` in `app.py`: approximate words per teaching section.
- `MAX_REF_WORDS` in `app.py`: maximum PDF reference text included for doubts/revision.

## Important notes

- The app sends extracted PDF text and chat messages to the OpenAI API to generate answers.
- API usage may incur charges according to your OpenAI API account.
- Scanned/image-only PDFs need OCR before upload.
- Some Hindi PDFs may extract with broken text depending on how the PDF was created.
- The app is a study aid. Check important exam facts against your NCERT book.
