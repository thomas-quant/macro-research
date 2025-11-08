🧠 Close Macro — Practical Research Roadmap
Core Goal

Build a lightweight system that helps me quantify repeatable patterns in the Nasdaq (NQ) futures market — focused on macro close, 3 pm hour, session behavior, and news-driven volatility.
The end goal: insights I can act on in live trading, not academic models.

⚙️ Phase 1 — Data Foundation (done / stable enough)

Goal: Get usable, clean historical NQ futures data in Eastern Time (ET) with proper session segmentation.

Status	Task
✅	Continuous futures data (NQ) sourced via NinjaTrader
✅	UTC → ET conversion (DST aware)
✅	Session tagging (Asia / London / NY / PM / Macro)
🔄	Validate that UTC and ET columns persist correctly
⬜	Add simple CLI to slice data by session for fast testing
⬜	Sanity-check volume/time alignment at session boundaries

Output: session_tagger.parquet with consistent timestamps.

🧩 Phase 2 — Core Features

Goal: Extract the “behavioral fingerprints” of the market around the PM & Macro sessions.

Status	Feature	Description
✅	macro_outcomes.py	Macro range, direction, expansion/consolidation label
⬜	pm_hr3.py	3 pm hour + PM session stats (range, direction, close pos, etc.)
⬜	Add consolidation logic	Detect if hr3 traded “inside a range” (mean-reverting)
⬜	Tag high/low times	When did hr3 high/low form?
⬜	Integrate with macro outcomes	Compare PM/3 pm state → next day macro

Output: One Parquet with all session & feature data per day.

📊 Phase 3 — Research Modules (Stats That Matter)

Goal: Answer practical trader questions through lightweight, visual analysis.

Status	Research Focus	Question
⬜	Markov Chain of Macro States	If today is consolidation, what’s P(tomorrow = expansion)?
⬜	Range Clustering	Do high-range macros cluster? Do low-range days cluster?
⬜	PM → Next Day Predictiveness	Does a strong PM close bias next day direction?
⬜	3 pm Consolidation Effect	If 3 pm = consolidation, does next hour expand or fade?
⬜	News Overlap Impact	How does high-impact news near 15:00 or 15:50 change outcomes?

Tools: quick Pandas/Matplotlib notebooks, describe() tables, histograms, transition matrices — no overfitting, no model building.

📰 Phase 4 — News Integration

Goal: Merge economic calendar events to flag “special conditions.”

Status	Task
✅	Scraper for ForexFactory events (USD only)
✅	Parquet file: econ_events.parquet
⬜	Merge with session data via timestamp proximity
⬜	Drop irrelevant (speeches, low impact)
⬜	Build is_news_day / is_holiday flag per session/day

Purpose: Filter or segment stats — e.g., “range expansion % on non-news days.”

🧠 Phase 5 — Interpretation Layer

Goal: Turn numbers into edge.

Status	Task
⬜	Create simple notebooks for each research module (1 page each)
⬜	Visualize key findings: histograms, conditional probabilities, transitions
⬜	Summarize “insight cards” — e.g.
“When hr3 is consolidating, next macro expands 65% of time.”	
⬜	Rank insights by stability, intuitive logic, and trade potential
🧰 Phase 6 — Maintenance / Workflow

Goal: Keep it lean & usable.

Task
Keep /data / /features / /research structure tidy
Use GitHub Project board to track features + analyses
After each chat → summarize outcome in roadmap or issue
Don’t refactor for elegance — just ensure reproducibility
Once per week → quick “insight dump” update (what we learned)
