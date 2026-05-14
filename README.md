# ₹ RupeeRadar - Indian Crypto Intelligence Platform

<div align="center">
  <h2>Premium Cryptocurrency Analytics for Indian Markets</h2>
  <p>Real-time market intelligence, AI-powered insights, and automated tax compliance</p>
  
  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
  [![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
  [![Streamlit](https://img.shields.io/badge/streamlit-1.28+-red.svg)](https://streamlit.io/)
</div>

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Configuration](#configuration)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

RupeeRadar is a comprehensive cryptocurrency intelligence platform specifically designed for the Indian market. It combines real-time market data, AI-powered insights, and automated tax compliance to provide Indian crypto investors with a unified analytics solution.

### Key Highlights

- India-Specific: Tailored for Indian crypto regulations and market conditions
- AI-Powered: Multi-agent system with Model Context Protocol (MCP)
- Real-Time Data: Live prices from multiple Indian exchanges
- Tax Compliance: Automated Section 115BBH tax calculations
- Premium UI: Professional fintech design with modern aesthetics

---

## Features

### Market Intelligence
- Real-time price tracking for 15+ cryptocurrencies
- Cross-exchange arbitrage opportunities
- Market sentiment analysis
- Professional charts dashboard

### AI Assistant
- Natural language query processing
- Multi-agent orchestration system
- Specialized agents (Market, Sentiment, Tax, Arbitrage)
- Real-time response generation

### Tax Compliance
- Automated Section 115BBH calculations
- TDS tracking and credit management
- Comprehensive tax rules documentation
- Year-end tax reporting

### Market News
- Aggregated news from multiple sources
- Sentiment analysis and impact scoring
- Real-time news updates
- Filtered by relevance to Indian market

---

## Architecture

### System Components

```text
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │    Backend      │    │   External      │
│                 │    │                 │    │   APIs          │
│ Streamlit UI    │◄──►│   FastAPI       │◄──►│ CoinGecko       │
│ Plotly Charts   │    │   REST API      │    │ NewsAPI         │
│ Modern Design   │    │   MCP Server    │    │ Exchange APIs   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         │              ┌─────────────────┐              │
         │              │   Database      │              │
         └──────────────►│   PostgreSQL    │◄─────────────┘
                        │   Redis Cache   │
                        └─────────────────┘
```

### Agentic AI System

- Model Context Protocol (MCP): Tool orchestration and agent communication
- Multi-Agent Architecture: Specialized agents for different domains
- Parallel Execution: Concurrent agent processing for faster responses
- Dynamic Tool Registration: Runtime tool availability management

---

## Installation

### Prerequisites

- Python 3.8 or higher
- Node.js 14+ (for development tools)
- PostgreSQL 12+ (optional, for production)
- Redis 6+ (optional, for caching)

### Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-username/RupeeRadar.git
   cd RupeeRadar
   ```

2. **Create Virtual Environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Environment Configuration**
   ```bash
   cp .env.example .env
   # Edit .env with your API keys and configuration
   ```

5. **Start Backend Server**
   ```bash
   uvicorn main:app --host 0.0.0.0 --port 8006 --reload
   ```

6. **Start Frontend Application**
   ```bash
   streamlit run app_ui.py --server.port 8508
   ```

### Dependencies

```txt
streamlit>=1.28.0
fastapi>=0.104.0
uvicorn>=0.24.0
pandas>=2.1.0
plotly>=5.17.0
requests>=2.31.0
python-multipart>=0.0.6
python-dotenv>=1.0.0
psycopg2-binary>=2.9.0
redis>=5.0.0
openai>=1.3.0
```

---

## Usage

### Accessing the Application

1. Open your browser and navigate to `http://localhost:8508`
2. The application will display the main dashboard with:
   - AI Chat Assistant
   - Market Overview
   - Charts Dashboard
   - Tax Calculator
   - Crypto News

### AI Chat Assistant

```python
# Example queries:
"What is the current price of Bitcoin in INR?"
"Show me arbitrage opportunities between WazirX and CoinDCX"
"Calculate tax for ₹50,000 investment with 30% profit"
```

### Market Data

```python
# Access market data via API
import requests

response = requests.get("http://localhost:8006/api/market/top")
data = response.json()
print(data["coins"][0]["name"])  # Bitcoin
```

### Tax Calculator

```python
# Calculate tax programmatically
tax_data = {
    "invested": 50000,
    "profit_pct": 30
}

response = requests.post("http://localhost:8006/api/tax/calculate", json=tax_data)
tax_result = response.json()
print(f"Tax payable: ₹{tax_result['tax_amount']}")
```

---

## API Documentation

### Endpoints

#### Market Data
- `GET /api/market/top` - Top 15 cryptocurrencies by market cap
- `GET /api/market/arbitrage` - Arbitrage opportunities
- `GET /api/market/sentiment` - Market sentiment analysis

#### Tax Calculator
- `POST /api/tax/calculate` - Calculate crypto tax
- `GET /api/tax/rules` - Get tax rules and regulations

#### News & Insights
- `GET /api/news/crypto` - Latest crypto news
- `GET /api/insights/sentiment` - Sentiment analysis results

#### AI Chat
- `POST /api/chat/query` - Submit query to AI assistant
- `GET /api/chat/history` - Get chat history

### Example API Usage

```python
import requests

# Get market data
market_response = requests.get("http://localhost:8006/api/market/top")
market_data = market_response.json()

# Calculate tax
tax_payload = {"invested": 100000, "profit_pct": 25}
tax_response = requests.post("http://localhost:8006/api/tax/calculate", json=tax_payload)
tax_result = tax_response.json()

# Chat with AI
chat_payload = {"query": "What is Bitcoin's current price?"}
chat_response = requests.post("http://localhost:8006/api/chat/query", json=chat_payload)
ai_response = chat_response.json()
```

---

## Configuration

### Environment Variables

```bash
# Database Configuration
DATABASE_URL=postgresql://user:password@localhost/rupeeradar
REDIS_URL=redis://localhost:6379

# API Keys
COINGECKO_API_KEY=your_coingecko_api_key
NEWSAPI_KEY=your_newsapi_key
OPENAI_API_KEY=your_openai_api_key

# Application Settings
BASE_URL=http://localhost:8006
DEBUG=false
LOG_LEVEL=INFO
```

### Customization

#### Branding
```python
# In app_ui.py
BRAND_NAME = "RupeeRadar"
BRAND_COLOR = "#FCD34D"
THEME = "dark"
```

#### Exchange Configuration
```python
# In main.py
SUPPORTED_EXCHANGES = ["wazirx", "coindcx", "zebpay"]
DEFAULT_CURRENCY = "INR"
UPDATE_INTERVAL = 30  # seconds
```

---

## Contributing

We welcome contributions! Please follow these steps:

1. **Fork the Repository**
2. **Create Feature Branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Make Changes**
4. **Test Your Changes**
   ```bash
   python -m pytest tests/
   ```
5. **Submit Pull Request**

### Development Guidelines

- Follow PEP 8 style guidelines
- Write comprehensive tests
- Update documentation
- Use semantic versioning

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- CoinGecko - Cryptocurrency data API
- NewsAPI & GNews - News aggregation services
- Streamlit - Frontend framework
- FastAPI - Backend framework
- Plotly - Data visualization library

---

## Support

- Email: lekshanapriya@gmail.com

---

<div align="center">
  <p>Made for the Indian Crypto Community</p>
  <p>© 2024 RupeeRadar. All rights reserved.</p>
</div>
