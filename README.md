# Data Analyst Agent

This project is an AI-powered data analyst agent that can answer complex data questions, perform web scraping, analyze structured datasets, and generate visualizations—all via a FastAPI backend.

## Features

- **Web Scraping:** Scrapes data from sources like Wikipedia to answer questions about highest-grossing films.
- **Data Analysis:** Processes CSV files (e.g., sales data) to compute statistics, correlations, and more.
- **Database Querying:** Supports DuckDB queries for large datasets (e.g., Indian High Court judgments).
- **Visualization:** Generates charts (scatterplots, bar charts, line charts) and returns them as base64-encoded images.
- **Flexible Input:** Accepts questions and data files via API.

## Usage

### 1. Install Dependencies

```sh
pip install -r requirements.txt
```

### 2. Set Up Environment Variables

Create a `.env` file in the project root with your API keys:

```
API_KEY=your_openai_or_aipipe_api_key
OCR_API_KEY=your_ocr_space_api_key
gemini_api=your_google_gemini_api_key
gemini_api_2=your_second_google_gemini_api_key
```

### 3. Run the FastAPI Server

```sh
uvicorn app:app --reload
```

### 4. Send a Request

Use `curl` (or Postman) to send your questions and data:

```sh
curl.exe -X POST "http://127.0.0.1:8000/aianalyst/" ^
  -F "file=@questions.txt;type=text/plain" ^
  -F "csv=@sample-sales.csv;type=text/csv"
```

- Replace `sample-sales.csv` with your actual data file as needed.

### 5. View the Response

The API will return a JSON object with answers and base64-encoded images for charts.

## Data File Formats

- **Questions:** Plain text file (see `questions.txt` for format).
- **Sales Data:** CSV with at least `date`, `region`, and `sales` columns. Example:

    ```csv
    date,region,sales
    2024-01-01,North,120
    2024-01-01,South,130
    ...
    ```

- **Other Data:** See prompt for DuckDB and scraping requirements.

## Notes

- For Wikipedia scraping, ensure your environment supports Playwright and run `playwright install` if needed.
- All charts are returned as base64-encoded PNG images.
- For large datasets (e.g., Indian High Court judgments), ensure you have access to the required S3 buckets or data sources.

## License

MIT License

---

**Developed by:**  
Rashi Sharma
