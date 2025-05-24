# EmaiLLM: Intelligent Email Classification and Filtering

**CS 329 Project: EmaiLLM - Bulk Email Cleanser**

EmaiLLM is a Python-based project developed for the CS 329 course. It leverages Large Language Models (LLMs) and Natural Language Processing (NLP) techniques to create an intelligent system for classifying and filtering emails. The primary goal is to help users manage their inboxes more effectively by identifying relevant email categories and separating bulk or unwanted emails.

## Core Functionality

- **Email Classification:** Utilizes a pre-trained LLM (via Google's Generative AI) to analyze email content and assign relevant keywords/categories.
- **Keyword-Based Filtering:** Allows users to define custom keywords for more precise email sorting.
- **Few-Shot Learning:** Employs few-shot prompting techniques (0-shot, 5-shot, 8-shot examples) to guide the LLM's classification accuracy.
- **Preprocessing:** Implements NLP techniques such as lowercasing, tokenization, lemmatization, and stopword removal (using spaCy) to prepare email text for the LLM.
- **Experimentation & Evaluation:** Includes robust scripts (`final_experiments.py`, `final_eval.py`) for running classification experiments with different configurations (e.g., with/without keyword count control) and evaluating performance using metrics like Precision, Recall, F1-score, Jaccard Index, and Accuracy.
- **Token Tracking:** Monitors and records token usage for LLM API calls to manage costs and analyze efficiency (`token_tracker.py`).

## Project Structure Highlights

- `final_experiments.py`: Contains the main logic for running email classification experiments using the LLM, including prompt construction, API calls, and data handling.
- `final_eval.py`: Provides functions to evaluate the classification performance of the experiments, calculating various metrics and generating reports.
- `preprocessing.py`: Includes functions for text preprocessing of email content.
- `token_tracker.py`: Implements a system for tracking and summarizing token usage from the LLM.
- `data/`: Directory intended for storing email datasets (e.g., `qtm_emails_final_version.json`).
- `final_experiments/`: Directory where results and token usage data from experiments are saved (e.g., `with_keyword_count_control_8shot.json`).
- `evaluation.ipynb` & `evaluation_with_tracking.ipynb`: Jupyter notebooks likely used for interactive data analysis, visualization, and exploration of evaluation results.

## Key Technologies Used

- **Python:** The primary programming language for the project.
- **Google Generative AI (Gemini API):** Used for the core email classification task.
- **spaCy:** Employed for NLP tasks like tokenization, lemmatization, and stopword removal.
- **dotenv:** Manages environment variables (e.g., API keys).
- **Tabulate:** Used in `final_eval.py` for presenting evaluation results in a structured table format.

## Potential Future Enhancements

- **User-Friendly Interface:** The original README mentioned a Flask-based UI; this could be further developed or integrated.
- **Seamless Integration:** Exploring options to integrate EmaiLLM with existing email platforms for automated processing.
- **Advanced Preprocessing:** Investigating more sophisticated preprocessing techniques.
- **Dynamic Keyword Adaptation:** Developing methods for the system to learn and adapt keywords over time.

## Setup and Usage (General Steps)

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/NateHu203/EmaiLLM.git
    cd EmaiLLM
    ```
2.  **Install dependencies:**
    Users will need to install the following key Python packages manually using pip:
    ```bash
    pip install google-generativeai spacy python-dotenv tabulate
    ```
    Then, download the spaCy English language model:
    ```bash
    python -m spacy download en_core_web_sm
    ```
3.  **Set up Environment Variables:**
    - Create a `.env` file in the root directory.
    - Add your `GOOGLE_API_KEY` to the `.env` file:
      ```
      GOOGLE_API_KEY='YOUR_API_KEY_HERE'
      ```
4.  **Prepare Data:**
    - Place your email data (e.g., in JSON format) in the `data/` directory. Ensure it's in the expected format for `final_experiments.py` and `final_eval.py`.
5.  **Run Experiments:**
    - Execute `final_experiments.py` to classify emails. This will generate output files in the `final_experiments/` directory.
    ```bash
    python final_experiments.py
    ```
6.  **Evaluate Results:**
    - Run `final_eval.py` to assess the performance of the classification.
    ```bash
    python final_eval.py
    ```
    - Alternatively, use the Jupyter Notebooks (`evaluation.ipynb`, `evaluation_with_tracking.ipynb`) for a more detailed analysis.

