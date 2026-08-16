# CodeAlpha Data Analytics Internship — Project Summary

This repository documents the 4 tasks completed for the CodeAlpha Data Analytics internship (Month 1). All tasks were applied to a real-world dataset for consistency and end-to-end storytelling.

## Datasets

- **Task 1 output:** custom dataset scraped from [books.toscrape.com](https://books.toscrape.com) — 100 books with title, price, rating, availability, and description (`data.csv`)
- **Tasks 2–4:** a real Amazon product reviews dataset (~34,600 reviews across 48 electronics products — Kindle, Fire tablets, Echo) (`amazon_reviews_clean.csv`)

## Task 1: Web Scraping

> **Requirements:**
> - Use Python libraries like BeautifulSoup or Scrapy to extract data from websites.
> - Identify and collect relevant datasets from public web pages.
> - If you don't code, use automated tools like Octoparse or ParseHub.
> - Learn to handle HTML structure and web navigation to gather accurate data.
> - Create custom datasets tailored to specific analysis needs.

Built a Python scraper using `requests` and `BeautifulSoup` to:
- Navigate paginated listing pages (`Next` button traversal)
- Parse HTML structure to extract product title, price, star rating, stock status, and description
- Clean and export the results into a structured CSV dataset

**Tools:** `requests`, `BeautifulSoup`, `pandas`

## Task 2: Exploratory Data Analysis (EDA)

> **Requirements:**
> - Ask meaningful questions about the dataset before analysis.
> - Explore the data structure, including variables and data types.
> - Identify trends, patterns and anomalies within the data.
> - Test hypotheses and validate assumptions using statistics and visualization.
> - Detect potential data issues or problems to address in further analysis.

Investigated the Amazon reviews dataset through 5 guiding questions, each backed by statistics and, where appropriate, formal hypothesis testing:

1. **How is the rating distributed?** → Heavily skewed positive (68.7% 5-star, ~2.3% 1–2 star) — an imbalanced dataset relevant for Task 4.
2. **Are negative reviews longer?** → Yes — confirmed with an independent t-test (t = 15.05, p < 0.0001). Negative reviews average ~250 characters vs. ~148 for 5-star reviews.
3. **Which products have the lowest/highest ratings?** → Very narrow gap (4.43–4.77), consistent with the overall positive skew. Also surfaced a data quality issue (duplicated text in some `product_name` values).
4. **Does the "recommend" field agree with the star rating?** → Mostly yes, confirmed with a chi-square test of independence (χ² = 18502.38, p < 0.0001). 83 reviews were flagged as contradictory (low rating but marked "recommend").
5. **Does the average rating change over time?** → Stable ~4.5–4.7 for most of the timeline; an apparent late drop turned out to be a sample-size artifact (only 2–3 reviews in those months), not a real trend.

**Tools:** `pandas`, `scipy.stats`

## Task 3: Data Visualization

> **Requirements:**
> - Transform raw data into visual formats like charts, graphs, and dashboards.
> - Use tools like Matplotlib, Seaborn, or Tableau for creating visuals.
> - Design visuals that enhance understanding and reveal insights clearly.
> - Craft compelling data stories that support decision-making.
> - Build a strong portfolio with impactful and well-designed visualizations.

Built 5 charts to communicate the EDA findings visually:
- Rating distribution (bar chart)
- Average review length by rating (bar chart)
- Rating trend over time (line chart)
- Recommend status by rating (stacked bar chart)
- Average rating for top 10 most-reviewed products (horizontal bar chart)

**Tools:** `matplotlib`, `seaborn`

## Task 4: Sentiment Analysis

> **Requirements:**
> - Analyze text data to classify it as positive, negative, or neutral.
> - Use NLP techniques and lexicons to detect specific emotions.
> - Apply analysis on data from sources like Amazon reviews, social media, and news sites.
> - Understand public opinion and trends through sentiment patterns.
> - Use results to inform marketing, product development, or social insights.

Applied VADER (lexicon-based sentiment analysis) to the review text, then validated the results against the actual star ratings:

- Overall agreement: 87.4% — but misleading due to class imbalance
- Per-category accuracy: **Positive 92.2%**, **Negative 40.8%**, **Neutral 9.2%**
- Manual review of misclassified negative reviews revealed VADER's key weakness: it struggles with sarcasm, conditional praise ("may be good for others"), comparisons to other products, and criticism that avoids explicitly negative vocabulary.

**Tools:** `vaderSentiment`

## Key Takeaways

- Real-world review data is heavily imbalanced toward positive sentiment — accuracy alone is a misleading metric without breaking results down by class.
- Lexicon-based sentiment tools like VADER are fast and effective for clearly-worded text, but underperform on nuanced, mixed, or sarcastic reviews compared to context-aware models.
- Formal statistical testing (t-test, chi-square) turned exploratory observations into validated conclusions.

## Author

Sakina Aliyeva
Email:aliyevaa.sakina@gmail.com
Linkedin:https://www.linkedin.com/in/sakina-aliyeva2?utm_source=share_via&utm_content=profile&utm_medium=member_android


