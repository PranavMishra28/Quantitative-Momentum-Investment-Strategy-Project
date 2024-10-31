# Quantitative Momentum Strategy

A Python-based implementation of a quantitative momentum investment strategy that identifies and analyzes the top 50 highest-momentum stocks from the S&P 500.

## Overview

This project implements a sophisticated momentum investing strategy that goes beyond simple price momentum by incorporating multiple time frames to identify high-quality momentum stocks. The strategy analyzes stocks based on their:

- 1-month price returns
- 3-month price returns
- 6-month price returns
- 1-year price returns

The program calculates a High-Quality Momentum (HQM) score for each stock and generates a recommended portfolio allocation based on user-specified investment amount.

## Features

- Fetches real-time stock data using IEX Cloud API
- Calculates momentum metrics across multiple time periods
- Identifies high-quality momentum stocks using percentile scoring
- Generates equal-weight portfolio recommendations
- Exports formatted results to Excel with custom styling

## Requirements

### Python Libraries
numpy
pandas
requests
xlsxwriter
scipy
math
statistics

Install required packages using:
pip install numpy pandas requests xlsxwriter scipy

### API Requirements
- IEX Cloud API token (required for stock data)
- Save your API token in a secrets.py file:
IEX_CLOUD_API_TOKEN = "your_token_here"

### Data Requirements
- S&P 500 stocks list (sp_500_stocks.csv) in the project directory

## Implementation Details

### 1. Data Collection
- Fetches stock data using IEX Cloud API batch requests
- Retrieves price returns for multiple time periods 
- Implements efficient batch processing for API calls

### 2. Momentum Analysis
- Calculates percentile scores for each time period:
 - One-year returns
 - Six-month returns
 - Three-month returns
 - One-month returns
- Computes HQM Score as the mean of percentile scores

### 3. Portfolio Construction
- Selects top 50 stocks by HQM Score
- Calculates equal-weight positions based on portfolio size
- Determines number of shares to buy for each position

### 4. Output Generation
- Creates formatted Excel output with:
 - Stock tickers
 - Current prices
 - Return metrics for all time periods
 - Percentile scores
 - HQM Scores
 - Number of shares to buy

## Usage

1. Set up your environment:
  pip install numpy pandas requests xlsxwriter scipy

2. Configure your API token in secrets.py

3. Ensure you have the S&P 500 stocks list CSV file in your project directory

4. Run the script:
  python momentum_strategy.py

5. Input your portfolio value when prompted

6. Check the generated momentum_strategy.xlsx file for your portfolio allocation

## Output Format

The script generates an Excel file (momentum_strategy.xlsx) with the following columns:

- Ticker: Stock symbol
- Price: Current stock price
- Number of Shares to Buy: Recommended position size
- One-Year Price Return: 12-month return
- One-Year Return Percentile: Relative performance score
- Six-Month Price Return: 6-month return
- Six-Month Return Percentile: Relative performance score
- Three-Month Price Return: 3-month return
- Three-Month Return Percentile: Relative performance score
- One-Month Price Return: 1-month return
- One-Month Return Percentile: Relative performance score
- HQM Score: Combined momentum quality score

## Notes

- The strategy focuses on high-quality momentum by considering multiple time periods
- Equal-weight allocation helps maintain diversification
- Excel output includes custom formatting for better readability
- Batch API calls are used to efficiently handle data requests
- Portfolio calculations round down to whole shares only

## License

This project is open source and available under the MIT License. Feel free to modify and use it according to your needs.
