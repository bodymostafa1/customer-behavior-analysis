# Customer Behavior Analysis

**Python · SQL (MySQL) · Power BI**

How can a retailer use consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?

This project analyzes 3,900 customer purchase records from a US retailer (all 50 states, amounts in USD). The data was cleaned and explored in Python, ten business questions were answered in SQL, and the findings were presented in a four-page Power BI dashboard. A full written report and a slide deck are included.

## Headline numbers

| Metric | Value |
|---|---|
| Purchases (one per customer) | 3,900 |
| Total revenue | $233,081 |
| Average purchase | $59.76 |
| Average review rating | 3.75 / 5 |

## Key findings

Revenue is steady across seasons, and Clothing leads in every one. Fall is the strongest season ($60,018) and Summer the weakest ($55,777, about 7% lower). Clothing alone brings in 44.7% of revenue, and Clothing and Accessories together bring in 76.5%.

Customers are 68% male, and that share stays between 67% and 69% in every age group. Ages are spread evenly: middle-aged customers look like the largest group only because their age band spans 20 years, against 10 to 12 for the others.

Subscribers (27% of customers) do not spend more. Their average purchase is $59.49 against $59.87 for non-subscribers.

Discounts do not lift spend or ratings. 43% of purchases carry a discount, yet the average purchase is $59.28 with one and $60.13 without. Every subscriber purchase is discounted, but even among non-subscribers alone, discounted purchases are not larger.

Shipping and payment choices are neutral. Across six shipping types and six payment methods, average spend stays between $58 and $61 and ratings between 3.7 and 3.8.

**Bottom line:** the data gives little support for blanket discounting and shows no spending premium for subscribers or for any shipping or payment option. The clearest commercial signals are in the product mix and in modest seasonal differences.

## Workflow

| Stage | Tool | Output |
|---|---|---|
| Cleaning and exploration | Python (pandas) | `customer_shopping_behavior_clean.csv` |
| Business analysis | SQL (MySQL) | Ten queries answering specific business questions |
| Dashboard | Power BI | Four-page interactive dashboard (Cover, Trends, Customers, Marketing) |

### Data preparation

Column names were converted to snake_case. The only missing values were 37 review ratings (0.9% of rows), filled with the median rating of the same category. Two fields were derived: `age_group` (young adult 18–29, adult 30–39, middle-aged 40–59, senior 60–70) and `frequency_purchase_days` (purchase-frequency labels encoded as days). The redundant `promo_code_used` column was dropped because it matched `discount_applied` in every row.

### SQL analysis

The ten queries use aggregation, subqueries, conditional aggregation, common table expressions (CTEs), and window functions. They cover revenue by gender, discounted customers who still spent above average, top-rated products, Standard vs. Express shipping, subscriber spend, most-discounted products, customer segmentation (New, Returning, Loyal), top products per category, repeat buyers and subscription, and revenue by age group.

### Dashboard

The Power BI report has a cover page and three analytical pages, each with KPI cards, supporting visuals, and a takeaway panel:

- **Trends:** how purchases change from season to season
- **Customers:** who buys, and how engaged they are (age, gender, subscription, previous purchases)
- **Marketing:** whether discounts, shipping, and payment choices change spend and ratings

## Recommendations

Because the data is a single snapshot, these are hypotheses to test rather than proven levers. Re-examine blanket discounting and test targeted promotions against a control group. Review what subscription offers, since benefits aimed at retention may fit better than discounts. Keep Clothing and Accessories at the center of the assortment year-round. Plan campaigns around the seasonal rhythm, with Summer as the natural window and Footwear well placed for Spring and Summer. Grow the female customer base, since women spend as much per purchase as men. Treat shipping and payment as operational decisions rather than sales levers.

## Limitations

The dataset has no date field, so seasonality is based on the season label and growth over time cannot be studied. Each customer appears once, so lifetime value cannot be measured directly. The analysis shows correlation, not causation, and discounts and subscription overlap, which limits how cleanly each can be evaluated. Most variables are close to evenly distributed, so no single factor explains much of the difference in spending. Conclusions should be validated on real transaction data before driving decisions.

## Next steps

- Add a predictive model (for example logistic regression or gradient boosting) for subscription or above-average spend
- Add a state-level geographic view alongside customer counts per state
- Analyze product size and color
- Collect dates and transaction history for time-series, cohort, and lifetime value analysis

## Repository structure


Adjust the file names above to match what you actually commit.

## Author

**Abdelrahman Mostafa**
B.Sc. Computers and AI, Cairo University (2022–2026)
abdelrahmanmostafa1172@outlook.com
