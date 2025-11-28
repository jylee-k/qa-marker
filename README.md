# QA Annotator App

![breakdown.png](data/breakdown.png)

A Streamlit application for annotating LLM-generated answers based on specific rubrics.

## Features
- **Rubric Grading**: Grade answers on a -2 to +2 scale across 10 categories (Helpfulness, Naturalness, etc.).
- **Flexible Input**: Automatically detects generated answer columns in your CSV.
- **Progress Tracking**: Save your progress at any time by downloading the CSV and resuming later.
- **Context View**: View context, question, and ground truth side-by-side with the generated answer.
- **Rubric Selection**: Choose which rubrics to apply to reduce clutter.

## Setup

### Prerequisites
- uv
- Python >=3.11

### Installation

1.  **Create Virtual Environment and Install Dependencies**:
    ```bash
    uv venv
    source .venv/bin/activate
    uv sync
    ```

### Usage

1.  **Run the App**:
    ```bash
    streamlit run app.py
    ```

2.  **Upload Data**:
    - Open the link provided in the terminal (usually `http://localhost:8501`).
    - Use the sidebar to upload your CSV file.
    - *Note*: The CSV should have standard headers like `text_chunk`, `question`, `answer`.

3.  **Annotate**:
    - Select the Model you want to evaluate (if multiple are present).
    - Select the Rubrics you want to use.
    - Use the sliders to grade the answer. Descriptions appear below the slider and in tooltips.
    - Click **Save & Next** to move to the next row.

4.  **Save Progress**:
    - Click the **Download CSV** button in the sidebar at any time to save your work.
    - To resume, simply upload this downloaded CSV next time.

## CSV Format
The app expects columns such as:
- `text_chunk`: The context text.
- `question`: The question asked.
- `answer`: The ground truth answer.
- `[ModelName]`: Columns containing generated answers.

The app will append columns in the format: `[ModelName]_[Rubric]_score`.
