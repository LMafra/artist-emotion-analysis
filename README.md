# Artist Emotion Analysis

Analyze emotional patterns in song lyrics using Spotify metadata, Genius lyrics, and GoEmotions transformer model (28 emotions).

## Features

- Fetch artist discography from Spotify (audio features: valence, energy, danceability, etc.)
- Retrieve lyrics from Genius API
- 28-emotion detection using GoEmotions RoBERTa model
- Section-level analysis (verse, chorus, bridge emotion patterns)
- Emotion flow tracking across song structure
- Correlation analysis between audio features and lyrical emotions
- Visualizations: emotion heatmaps, radar charts, co-occurrence matrices

## Setup

### 1. Get API Credentials

**Spotify:**
1. Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
2. Create an app and get Client ID and Client Secret

**Genius:**
1. Go to [Genius API Clients](https://genius.com/api-clients)
2. Create an app and get Access Token

### 2. Configure Environment

```bash
cp .env.example .env
# Edit .env with your API credentials
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run Notebooks

Run in order:

1. **Lyrics-Crawler.ipynb** - Collect data from Spotify and Genius
2. **Sentiment Analysis.ipynb** - Analyze emotions and generate visualizations

## Output Files

All outputs saved to `output/` directory:

| File | Description |
|------|-------------|
| `spotify.json` | Raw Spotify API response |
| `spotify.csv` | Track metadata + audio features |
| `lyrics.csv` | Song lyrics from Genius |
| `lyrics_missing.csv` | Tracks with missing lyrics |
| `lyrics_with_emotions.csv` | Songs + top 5 emotions + scores |
| `emotion_matrix.csv` | Full 28-emotion scores per song |
| `section_emotions.csv` | Emotion analysis per song section |
| `emotion_flows.csv` | Emotion progression through song |

## Emotion Model

Uses [SamLowe/roberta-base-go_emotions](https://huggingface.co/SamLowe/roberta-base-go_emotions):
- 28-emotion classification (admiration, amusement, anger, annoyance, approval, caring, confusion, curiosity, desire, disappointment, disapproval, disgust, embarrassment, excitement, fear, gratitude, grief, joy, love, nervousness, optimism, pride, realization, relief, remorse, sadness, surprise, neutral)
- Full-text chunking with overlap for long lyrics
- Section-level emotion tracking

## Visualizations

Generated charts include:
- Dominant emotion distribution
- Emotion flow by song section
- Section type comparison (verse vs chorus)
- Emotion heatmap (songs × emotions)
- Audio features vs emotions correlation
- Album emotion radar charts
- Emotion co-occurrence matrix

## Requirements

- Python 3.8+
- ~2GB disk space for transformer model cache
- Spotify Developer account
- Genius API token

## Project Structure

```
├── Lyrics-Crawler.ipynb      # Data collection (Spotify + Genius)
├── Sentiment Analysis.ipynb  # Emotion analysis + visualization
├── requirements.txt          # Python dependencies
├── .env.example              # Environment template
├── .gitignore
└── output/                   # Generated data (gitignored)
```
