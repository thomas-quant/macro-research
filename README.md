🧠 Market Close Macro Investigation

A quantitative research project exploring the structure, range dynamics, and predictability of the market close macro (3:50–4:00 PM EST).
The goal is to understand what drives the macro’s size, directionality, and behavior across different sessions, days, and regimes — and how these insights might support better trade positioning into the close.

📈 Project Objectives

Quantify macro range dynamics

Measure total macro range and investigate its drivers (volume, previous day volatility, news, etc.)

Categorize macro structure

Identify whether the macro is expansionary (directional) or consolidative (choppy)

Understand timing behavior

Determine when highs/lows of the macro typically form and how they align with known liquidity injections

Model session influence

Study how prior sessions (Asia, London, NY AM, PM) shape the close macro

Integrate news and seasonality

Measure the effect of next-day economic events and possible monthly/seasonal patterns

Explore regime and sequence dynamics

Use a Markov-style model to test how macro states (expansion/consolidation) transition day to day

🔍 Research Questions
Macro Range & Structure

What factors influence the total size of the close macro?

Does macro type (expansion vs. consolidation) depend on:

Previous day’s range or volatility?

Volume distribution leading up to the close?

Market structure (liquidity availability, unbroken highs/lows)?

Session Dependencies

Does the 3 PM hour (3:00–3:50) predict macro range or directionality?

How do different sessions influence the close?

Asia (7 PM–12 AM)

London (2 AM–5 AM)

NY AM (9:30–11 AM)

Lunch (12–1 PM)

PM (1–3 PM)

Timing Behavior

When do the macro highs and lows form?

Is there a pattern in the timing of liquidity injections?

3:50 → first injection

3:55 → second injection

3:59–4:00 → acceleration

4:00+ → possible extension (esp. before next-day news)

News & External Factors

How does scheduled news (e.g., 8:30 AM releases next day) impact:

Macro range?

Directionality?

Volume persistence past 4:00?

Plan: Scrape or import economic calendar data (e.g., Forex Factory, Investing.com API)

Regime & Markov Behavior

Do high-range macros cluster (volatility regimes)?

If yesterday’s macro was expansion, what are the odds today’s is consolidation?

Include news awareness and session conditions as state-transition variables.

Liquidity & Microstructure

Quantify low resistance liquidity (trendline of unbroken highs/lows since ~3 PM).

Measure impact of unbroken overnight, London, and NY highs/lows.

Hypothesis: low resistance liquidity → greater macro expansion potential.

Seasonality

Does macro range behavior vary by month or quarter?

Are there seasonal patterns tied to earnings cycles or macroeconomic calendars?

🧩 Methodology Overview
Component	Description
Data Source	Intraday (1-min or tick) OHLCV data for major indices or futures
Session Segmentation	Tag each data point by global session (Asia, London, NY)
Macro Extraction	Extract 3:50–4:00 PM window and compute range, structure, timing metrics
Directionality Metrics	Use range ratios or momentum indicators to classify macro type
News Integration	Scrape economic calendar via Selenium/API for tagging high-impact events
Markov Modeling	Model sequence probabilities between macro states across days
Visualization	Distribution plots, regime transitions, and macro timing histograms
🧮 Metrics & Indicators
Category	Example Metrics
Range Metrics	macro_high - macro_low, normalized range, z-score of range vs. average
Directionality	(macro_close - macro_low) / (macro_high - macro_low) ratio
Timing	Timestamp of first and last 25% of total range formed
Volume	Volume profile between 3:50–4:00 and after 4:00
Session Continuity	PM session direction vs. macro direction (continuation/reversal)
Liquidity Context	Distance to last unbroken high/low; liquidity slope
Regime Variables	Rolling mean of macro range to detect shifts
🧠 Modeling Ideas

Markov Chain Model

States: Expansion / Consolidation

Transitions: P(next_state | prev_state, news, session, volume)

Goal: Estimate transition probabilities and regime persistence

Predictive Modeling

Features: previous day range, PM session type, news flag, liquidity slope

Targets: macro range classification, high/low timing, directionality score

⚙️ Technical Setup

Language: Python 3.10+

Libraries: pandas, numpy, matplotlib, scipy, sklearn, statsmodels

Optional: selenium or beautifulsoup4 for news scraping

Data Storage: CSV/Parquet for historical data; SQLite/Postgres for structured sessions

Visualization: Plotly / Matplotlib for exploratory visuals

🧭 Next Steps

 Build data ingestion + session segmentation scripts

 Implement macro extraction and metrics computation

 Scrape and integrate economic calendar data

 Build directionality and structure classifiers

 Perform Markov chain regime analysis

 Visualize distributions and conditional dependencies

 Document key findings & publish results

💡 Long-Term Vision

Build a quantitative model to estimate expected macro range and behavior given current conditions.

Detect high-probability expansion days in real time.

Extend framework to other intraday macros (e.g., open, lunch, post-news).
