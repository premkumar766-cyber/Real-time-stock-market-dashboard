# Real-time-stock-market-dashboard
📄 Description of the Code

🎯 Purpose:

This code creates a web-based dashboard that displays live stock data, plots interactive graphs, and shows financial indicators for any stock ticker symbol using real-time data from Yahoo Finance.

🧰 Technologies Used:

Streamlit – for building the interactive web interface.

Pandas – for handling time-series stock data.

Matplotlib – for static line plots.

Plotly – for interactive candlestick charts.

yfinance – for fetching live stock market data.

Python – for logic and computation.

🧩 Key Components of the Code:

1.Streamlit Configuration
st.set_page_config(page_title="Real-Time Stock Dashboard", layout="wide")

Sets the app’s title and layout to wide for more horizontal space.

2.Title & Sidebar User Inputs
st.title("📈 Real-Time Stock Market Dashboard")

A title is displayed at the top of the app.

Sidebar widgets:

ticker = st.sidebar.text_input(...) period = st.sidebar.selectbox(...) interval = st.sidebar.selectbox(...)

User can input a stock symbol (AAPL, TSLA, etc.), choose a time period (e.g. 1d, 1mo), and data interval (e.g. 1m, 15m).

3.Data Fetching with yfinance
@st.cache_data(ttl=300) def get_stock_data(...): data = yf.download(...)

Fetches data from Yahoo Finance for the selected stock.

Caches results for 5 minutes to avoid unnecessary re-downloads.

4.Data Validation
if data.empty: st.warning(...)

Checks if the API returned valid stock data.

Shows a warning if the ticker is incorrect or data is unavailable.

5.Display Raw Data Table
st.write(data.tail())

Displays the last few rows of the stock dataset (OHLCV - Open, High, Low, Close, Volume).

6.📉 Matplotlib Line Chart
data['Close'].plot(...)

Creates a static line plot of the closing price using Matplotlib.

7.📊 Plotly Candlestick Chart
go.Candlestick(...)

Displays an interactive candlestick chart using Plotly, where:

Green/red bars show daily price movement (Open, High, Low, Close).

8.📌 Financial Metrics
col1.metric(...), col2.metric(...), col3.metric(...)

Shows 3 key indicators:

Latest Price

Volume

Daily Change (Close - Open)

9.📏 Moving Averages
data['MA20'] = ... data['MA50'] = ...

Calculates and plots:

20-period Moving Average

50-period Moving Average
