# YouTube Playlist Data and Comments Sentiment Analysis

This project extracts video and comment data from a specified YouTube playlist and analyzes the sentiment of comments using a pre-trained RoBERTa model. The results are saved as CSV files for further analysis or visualization.

---

## Features

- Extracts video details (title, views, likes, etc.) from a YouTube playlist.
- Scrapes comments for each video and cleans HTML content.
- Performs sentiment analysis on comments using the **`cardiffnlp/twitter-roberta-base-sentiment`** model.
- Saves the extracted data and analysis to CSV files.

---

## Installation

1. Clone this repository or download the script.
2. Install the required libraries:
   ```bash
   pip install pandas numpy tqdm google-api-python-client beautifulsoup4 transformers torch matplotlib seaborn
   ```
3. Set up your YouTube Data API key by following the instructions [here](https://developers.google.com/youtube/registering_an_application).

---

## Usage

1. **Set up API Key:**
   Replace `YOUR_API_KEY` in the script with your valid YouTube Data API key.

2. **Run the Script:**
   Execute the Python script to extract data and analyze sentiments:
   ```bash
   python youtube_analysis.py
   ```

3. **Output Files:**
   - Video details are saved as `linkin_park_youtube.csv`.
   - Comment details with sentiment analysis are saved as `linkin_park_youtube_comments.csv`.

---

## Code Details

### 1. **Extract Video Information**
   - Retrieves video details such as:
     - `Video ID`
     - `Title`
     - `Thumbnail URL`
     - `Published At`
     - `Channel ID`
     - `Channel Title`
     - `View Count`
     - `Like Count`
     - `Dislike Count` (default is 0 if unavailable).
   - Saves the data into a Pandas DataFrame.

### 2. **Scrape Comments**
   - Extracts comments, commenter names, and publication times for each video in the playlist.
   - Cleans HTML content in comments using `BeautifulSoup`.

### 3. **Sentiment Analysis**
   - Analyzes the sentiment of comments using the `cardiffnlp/twitter-roberta-base-sentiment` model.
   - Maps sentiment labels:
     - `LABEL_2`: Positive
     - `LABEL_1`: Neutral
     - `LABEL_0`: Negative
   - Displays a progress bar for sentiment analysis using `tqdm`.

### 4. **Save Results**
   - Saves both video and comment data with sentiment analysis to CSV files for further use.

---

## Sample Output

### Video Data
| Video ID       | Title                  | View Count | Like Count | Dislike Count |
|----------------|------------------------|------------|------------|---------------|
| abc123         | Video Title 1          | 5000       | 200        | 0             |

### Comment Data with Sentiments
| Video ID | Comment                | Commenter   | Sentiment   |
|----------|------------------------|-------------|-------------|
| abc123   | "Amazing content!"     | User1       | positive    |

---

## Dependencies

- Python 3.8 or later
- Pandas
- NumPy
- Tqdm
- Google API Python Client
- BeautifulSoup4
- Transformers
- Torch
- Matplotlib
- Seaborn

---

## Acknowledgements

- Pre-trained sentiment model: [CardiffNLP's Twitter RoBERTa](https://huggingface.co/cardiffnlp/twitter-roberta-base-sentiment).
- YouTube Data API for playlist and comment extraction.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
