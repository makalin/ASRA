# ASRA - App Store Review Analyzer

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Status](https://img.shields.io/badge/status-beta-yellow.svg)

ASRA is a powerful tool for analyzing app reviews from both iOS App Store and Google Play Store. It crawls reviews, analyzes them using AI (Grok API), and provides comprehensive insights including sentiment analysis, trends, common issues, feature requests, and positive aspects.

## Features

- **Platform Support**: Analyzes reviews from both iOS App Store and Google Play Store
- **Sentiment Analysis**: Provides positive/negative/neutral breakdown of reviews
- **Insights Extraction**:
  - Trends identification
  - Common issues detection
  - Feature request suggestions
  - Positive aspects summary
- **Configurable**:
  - Adjustable review limits
  - Analysis depth (light/medium/deep)
  - Cache expiration
- **Production-Ready**:
  - Robust error handling
  - Logging system
  - Rate limiting
  - Caching for efficiency

## Installation

1. Clone the repository:
```bash
git clone https://github.com/makalin/asra.git
cd asra
```

2. Install dependencies:
```bash
pip install requests beautifulsoup4 ratelimit
```

3. Set up environment variables:
```bash
export GROK_API_KEY="your-xai-api-key"
```

## Usage

Basic usage:
```python
from asra import ASRA, ASRAConfig

# Configure the analyzer
config = ASRAConfig(
    max_reviews=100,        # Maximum number of reviews to analyze
    analysis_depth="medium", # Analysis depth: "light", "medium", "deep"
    cache_ttl=86400         # Cache TTL in seconds (24 hours)
)

# Initialize and run
analyzer = ASRA(
    app_id="com.example.app",
    platform="android",     # or "ios"
    config=config
)
analyzer.generate_report()
```

Sample output:
```
=== ASRA Report ===
Analysis Depth: medium
Reviews Analyzed: 100

Sentiment Summary:
Positive: 65 reviews (65.0%)
Negative: 25 reviews (25.0%)
Neutral: 10 reviews (10.0%)

Trends:
- Increasing user engagement
- Performance improvements noted

Common Issues:
- Login failures
- Payment processing delays

Feature Requests:
- Dark mode support
- Offline functionality

Positive Aspects:
- User-friendly interface
- Fast customer support
```

## Configuration Options

| Parameter | Description | Default |
|-----------|-------------|---------|
| `max_reviews` | Maximum number of reviews to analyze | 100 |
| `analysis_depth` | Analysis detail level ("light", "medium", "deep") | "medium" |
| `cache_ttl` | Cache expiration time in seconds | 86400 (24h) |

## Requirements

- Python 3.8+
- SQLite (for caching)
- Grok API key from xAI
- Internet connection

## Dependencies

- `requests`: For HTTP requests
- `beautifulsoup4`: For Android review scraping
- `ratelimit`: For API rate limiting

## Notes

- The Android crawling uses basic web scraping and may require a more robust solution for production use
- Replace the mock Grok API endpoint with the actual xAI API endpoint
- Check `asra.log` for detailed error logs

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built with xAI's Grok API
- Inspired by the need for automated app review analysis

## Contact

For questions or suggestions, please open an issue or contact [makalin@gmail.com](mailto:makalin@gmail.com).
