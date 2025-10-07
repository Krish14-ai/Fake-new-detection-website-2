# Fake-new-detection-website-2

A real-time web application built with Streamlit that detects fake news using machine learning. The application fetches live news articles from GNews API and classifies them as real or fake using a trained Logistic Regression model.

## Features

- **Live News Monitoring**: Automatically fetch and analyze the latest news headlines from India
- **Keyword-Based Search**: Search for news articles by topic and get instant fake news predictions
- **URL Analysis**: Extract and analyze news articles from any URL
- **Manual Text Input**: Paste or type news content directly for analysis
- **Auto-Refresh**: Optional auto-refresh feature for continuous news monitoring
- **Real-Time Predictions**: Instant classification with visual indicators (Real/Fake)
- **Responsive UI**: Clean, modern interface with custom styling and background image

## Technologies Used

- **Frontend**: Streamlit 1.26.0
- **Machine Learning**: 
  - scikit-learn 1.3.2 (Logistic Regression model)
  - TF-IDF Vectorization for text processing
- **Web Scraping**: newspaper3k for article extraction
- **API Integration**: GNews API for live news fetching
- **Data Processing**: 
  - Pandas 1.5.3
  - NumPy 1.26.4
- **Additional Libraries**:
  - streamlit-option-menu 0.3.6 (navigation)
  - requests 2.31.0 (API calls)
  - Pillow 9.5.0 (image processing)

## Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager
- GNews API key (free tier available at [gnews.io](https://gnews.io))

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/Fake_News_Detection.git
cd Fake_News_Detection
```

2. Install required dependencies:
```bash
pip install -r requirements.txt
```

3. Add required files:
   - Place your trained model file as `lr_model.jb`
   - Place your vectorizer file as `vectorizer.jb`
   - Add a background image as `background.jpeg` (optional)

4. Configure API key:
   - Open `app.py`
   - Replace the `api_key` variable with your GNews API key:
   ```python
   api_key = "your_gnews_api_key_here"
   ```

5. Run the application:
```bash
streamlit run app.py
```

6. Open your browser and navigate to:
```
http://localhost:8501
```

## Project Structure

```
Fake_News_Detection/
│
├── app.py                  # Main application file
├── appbackup.py           # Backup version
├── requirements.txt       # Python dependencies
├── config.toml           # Streamlit theme configuration
├── lr_model.jb           # Trained Logistic Regression model
├── vectorizer.jb         # TF-IDF vectorizer
├── background.jpeg       # Background image
└── README.md            # This file
```

## Usage

### 1. Home Page - Live News Monitoring
- Click "Fetch Latest News & Predict" to get the top 6 news headlines
- Enable "Auto Refresh" for automatic updates every 60 seconds
- View predictions with color-coded indicators (Green = Real, Red = Fake)
- Paste any news article URL to analyze specific articles

### 2. Check News by Keyword
- Enter a keyword or topic (e.g., "technology", "politics", "sports")
- Click "Fetch News & Analyze"
- View up to 5 relevant articles with instant predictions
- Click article links to read full content

### 3. Check News by Entering Text
- Paste or type news article content directly
- Click "Check News" for instant analysis
- Get prediction with visual feedback
- Works best with full article text (20+ words recommended)

## How It Works

### Detection Pipeline

1. **Text Preprocessing**: Input text is cleaned and normalized
2. **Vectorization**: Text is converted to numerical features using TF-IDF vectorizer
3. **Prediction**: Logistic Regression model classifies the text
4. **Output**: Binary classification (Real = 1, Fake = 0) with visual indicators

### Model Information

- **Algorithm**: Logistic Regression
- **Text Representation**: TF-IDF (Term Frequency-Inverse Document Frequency)
- **Training**: Model trained on labeled dataset of real and fake news articles
- **Input**: Raw text from news articles
- **Output**: Binary classification (Real/Fake)

### API Integration

The application uses GNews API to fetch:
- Top headlines from India
- Keyword-based news search
- Article metadata (title, description, image, URL, publish date)

## Configuration

### Theme Customization

Edit `.streamlit/config.toml` to customize the appearance:
```toml
[theme]
primaryColor = "#e63946"      # Accent color
backgroundColor = "#f0f2f6"    # Background color
textColor = "#FFFFFF"          # Text color
```

### API Rate Limits

GNews API free tier includes:
- 100 requests per day
- 10 articles per request maximum

## Limitations

- **Accuracy**: Model provides probability-based predictions, not absolute truth
- **Text Length**: Works best with substantial text (20+ words)
- **Language**: Currently optimized for English language articles
- **API Limits**: Subject to GNews API rate limits
- **URL Extraction**: Some websites may block automated scraping
- **Domain Coverage**: Model trained on specific news domains and topics

## Troubleshooting

**Model not loading?**
- Ensure `lr_model.jb` and `vectorizer.jb` are in the project root directory

**Background image not showing?**
- Add `background.jpeg` to the project root or remove background code from `app.py`

**API errors?**
- Verify your GNews API key is valid and active
- Check if you've exceeded daily rate limits

**Article extraction fails?**
- Some websites block automated scraping
- Try a different news source URL

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/NewFeature`)
3. Commit your changes (`git commit -m 'Add NewFeature'`)
4. Push to the branch (`git push origin feature/NewFeature`)
5. Open a Pull Request

## Future Enhancements

- [ ] Multi-language support
- [ ] Advanced NLP models (BERT, transformers)
- [ ] Source credibility scoring
- [ ] Historical analysis and trending topics
- [ ] User feedback mechanism
- [ ] Export analysis reports
- [ ] Mobile app version

## Acknowledgments

- **GNews API** for live news data
- **scikit-learn** for machine learning capabilities
- **Streamlit** for the web framework
- **newspaper3k** for article extraction

## Contact

For questions, suggestions, or issues:
- Email: kkhandelwal292@gmail.com

## Disclaimer

This tool is designed to assist in identifying potentially misleading content but should not be the sole basis for determining information credibility. Always:
- Cross-reference multiple sources
- Apply critical thinking
- Verify information from authoritative sources
- Consider the model's limitations

**Note**: The predictions are based on machine learning patterns and may not always be 100% accurate. Use this tool as a supplementary aid in news verification.
