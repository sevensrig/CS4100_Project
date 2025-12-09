# Tech Trends News Agent

An AI-powered news analysis system that retrieves technology articles, enables semantic search, generates conversational answers using a local LLM, and visualizes trending topics.

## Colab Link
https://colab.research.google.com/drive/1BVgYnpfCmaCokEHSt9dL47DjziTT8nn0?usp=sharing

## Video link
https://drive.google.com/file/d/1YYscs_qC2-t1McnWBjY0JgdyR-45pDfl/view?usp=sharing

## Quick Start

1. Click the `.ipynb` notebook file in this repository
2. Click **Open in Colab** at the top
3. Set runtime to **GPU** (Runtime → Change runtime type → T4 GPU)
4. Run all cells (Runtime → Run all)
5. Click the ngrok URL when it appears to open the app

---

## Setup and Run Instructions

### 1. Prerequisites

- Google account (for Colab)
- That's it! Everything else runs in the cloud.

---

### 2. Run in Google Colab

1. Click the notebook file (`Copy_of_12_4_New_AI_project.ipynb`) above
2. Click **Open in Colab** button at the top of the file
3. Go to **Runtime → Change runtime type → Select GPU (T4)**
4. Run all cells in order (Runtime → Run all)
5. Wait for the ngrok URL to appear (~60 seconds for model loading)
6. Click the ngrok URL to open the Streamlit app

---

### 3. API Key

You **do not need to create your own NewsAPI key**. A working API key is already included in the project configuration. The agent will automatically use it when retrieving articles.

---

### 4. Project Structure

```
tech-trends-agent/
├── app.py                 # Streamlit web interface
├── fetch_news.py          # NewsAPI article retrieval
├── preprocess.py          # NLTK tokenization and preprocessing
├── search_articles.py     # TF-IDF search and topic extraction
├── llm_interface.py       # Qwen2.5-1.5B model wrapper
├── data/
│   ├── raw/               # Raw JSON from NewsAPI
│   └── processed/         # Preprocessed article corpus
```

---

### 5. Using the App

#### Chat Tab
1. Click **"Fetch Articles"** in the sidebar to load latest technology news
2. Type a question (e.g., "What are the latest AI trends?") or click a suggestion
3. View the LLM-generated answer with expandable source citations

#### Topic Visualization Tab
1. After fetching articles, switch to the **"Topic Visualization"** tab
2. View bar chart of top 5 discovered topics
3. Expand each topic to see key terms, sample articles, and sub-trends

---

### 6. Output

- **Chat Responses**: Contextual answers displayed in the chat interface with source links
- **Topic Clusters**: Automatically extracted from article corpus using TF-IDF and co-occurrence analysis
- **Sub-Trends**: Relevance-scored sub-topics within each main topic cluster
- **Metrics**: Total articles, categorized count, and coverage percentage

---

### 7. Notes for Graders

- **Easiest path**: Run the Colab notebook with GPU runtime enabled
- The API key is pre-configured — no setup required for NewsAPI
- Model loading takes ~60 seconds on first run (downloading ~3GB)
- Once loaded, queries are answered in 2-5 seconds
- If NewsAPI rate limits are hit, previously fetched articles are cached in `data/processed/`
- The app automatically loads cached articles if available

#### To Test:
1. Run all cells in the notebook
2. Click "Fetch Articles" to retrieve latest news
3. Ask questions in the chat interface
4. Check the Topic Visualization tab for trend analysis

---

### 8. Technical Details

- **LLM**: Qwen2.5-1.5B-Instruct
- **Search**: TF-IDF with cosine similarity
- **Preprocessing**: NLTK (tokenize, stopwords, lemmatize)
- **Topic Extraction**: Co-occurrence clustering
- **Frontend**: Streamlit
- **Data Source**: NewsAPI (technology headlines)
- **GPU Support**: CUDA (float16 precision)

---

### 9. Troubleshooting

- **"No articles loaded"**: Click "Fetch Articles" in sidebar
- **Model loading slow**: Ensure GPU runtime is enabled in Colab
- **ngrok URL not working**: Re-run the last cell to generate new tunnel
- **NewsAPI error**: Rate limit reached; wait or use cached data
- **CUDA out of memory**: Restart runtime and try again
