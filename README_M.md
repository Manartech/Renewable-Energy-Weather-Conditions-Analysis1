# Renewable Energy and Weather Conditions Analysis
> Explore the feasibility of installing solar panels in Antwerp, Belgium by assessing how local weather conditions affect their performance, and identifying the optimal operating conditions for maximum efficiency.

---

## ⚙️ Project Type Flags
> *Check what applies. This helps reviewers and collaborators understand the nature of the work at a glance. Delete this block before publishing.*

- [✅ ] Exploratory Data Analysis (EDA)
- [ ] SQL Analysis / Querying
- [ ] Dashboard / Data Visualization
- [ ] Data Pipeline / ETL
- [ ] Predictive Modelling / Machine Learning
- [ ✅] Data Cleaning / Wrangling
- [ ] End-to-End (multiple of the above)
- [ ] Other: ___________

---

## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Objectives](#2-objectives)
3. [Project Scope & Tools](#3-project-scope--tools)
4. [Repository Structure](#4-repository-structure)
5. [Data Workflow](#5-data-workflow)
6. [Data Model & Schema](#6-data-model--schema)
7. [ERD - Entity Relationship Diagram](#7-erd--entity-relationship-diagram) *(SQL projects)*
8. [Analysis & Metrics](#8-analysis--metrics)
9. [Key Insights](#9-key-insights)
10. [Recommendations](#10-recommendations)
11. [Assumptions & Limitations](#11-assumptions--limitations)
12. [Future Enhancements](#12-future-enhancements)
13. [Deliverables](#13-deliverables)
14. [Author](#14-author)

---

## 1. Project Overview

<!--
  Write 3–5 sentences in plain language.
  Cover: context → problem → approach → outcome.
  Read it out loud. If it sounds like a form - rewrite it.

  WHAT GOOD LOOKS LIKE:
  A project engineer is tasked with commissioning a solar energy project. Short‑term weather changes explain about 61% of the variation in renewable energy output, this unpredictability makes grid planning harder, increases costs, and lowers efficiency—especially during cloudy or rainy conditions. The key business issue is how to manage this volatility to ensure stable performance and financial returns.

-->
 A project engineer is tasked with commissioning a solar energy project. Short‑term weather changes explain about 61% of the variation in renewable energy output, this unpredictability makes grid planning harder, increases costs, and lowers efficiency—especially during cloudy or rainy conditions. The key business issue is how to manage this volatility to ensure stable performance and financial returns.
 
**Context:** [The project was motivated by the global push toward renewable energy and the need to understand how weather variability impacts solar power performance. Antwerp, Belgium was chosen as a case study due to its moderate climate and relevance for urban sustainability.]

**Problem Statement:** [The challenge was that short-term weather variability explained 61% of renewable energy output changes in 2020, making solar generation highly dependent on radiation and temperature. This volatility complicates grid planning, raises costs, and reduces efficiency, especially during cloudy or rainy conditions.]

**Approach:** [I analyzed solar datasets (2012–2020) including GHI, AC/DC power, inverter efficiency, temperature, and cloud cover. By correlating weather conditions with energy output, you identified peak production times, seasonal variations, and efficiency benchmarks against European standards.]

**Outcome:** [The study found that solar radiation (GHI) is the most critical driver of energy output (correlation coefficient 0.91). Peak solar potential occurred at 10:00 AM with ~1,960 Wh output, and inverter efficiency averaged 97%, meeting international standards. Recommendations included seasonal panel tilt adjustments, maintaining operating temperatures (20–25℃), and integrating storage solutions to maximize year-round efficiency.]

---

## 2. Objectives

<!--
  Write objectives that are specific enough to succeed or fail.
  Use action-oriented verbs: Identify, Determine, Quantify, Build, Evaluate.

  WHAT GOOD LOOKS LIKE:
  ✅ "Determine whether customer churn rate correlates with support ticket volume."
  ✅ "Identify the top three revenue-driving product categories across all regions."
  ✅ "Build a reproducible pipeline that ingests and cleans daily sales exports."

  WHAT TO AVOID:
  ❌ "Explore the data."
  ❌ "Gain insights."
  ❌ "Understand trends."
  (These can't fail - which means they can't succeed either.)
-->

- **Primary Objective:** Find which conditions , sunlight, cloud cover
and temperature most influence renewable
energy output.
- **Secondary Objective 1:** Study how solar radiation (GHI) affects energy
variation over different hours and months. 
- **Secondary Objective 2:** Find out when energy output is most over the
time of day or season.
- **Secondary Objective 3:** Identify efficiency performance throughout
the day 

> 💡 *Every analysis decision in this project traces back to one of these objectives.*

---

## 3. Project Scope & Tools

### Scope

<!--
  WHAT GOOD LOOKS LIKE:
  In Scope: "Transaction-level data for Regions A–E, Jan 2023–Jun 2024.
             Analysis covers revenue, return rates, and product category performance."
  Out of Scope: "Customer demographics and marketing spend data were excluded -
                 demographic data was incomplete for two regions, and marketing
                 data sits in a separate system outside this engagement."

  WHAT TO AVOID:
  ❌ Leaving Out of Scope blank. This is the section that protects your credibility.
     If you don't define the fence, reviewers assume you missed things.
-->

| Dimension | Details |
|-----------|---------|
| **In Scope** | [ Information on energy consumption and various weather parameters such as solar radiation, temperature, pressure, humidity, wind speed, and precipitation with weather conditions of Antwerp, Belgium 2012-2019 supported by solar power generation data as sample data to be utilized for the case study.
] |
| **Out of Scope** | [The analysis of other renewable energy data like wind speed, because the case study focused to be on solar and focusing on wind speed will require more data and more complex analysis.] |
| **Time Period** | [3 May 2026 - 14 May 2026] |


### Tools & Technologies

<!--
  List only what you actually used on this project.
  This is not your skills section - it's the project's technical context.
-->

| Category | Tool(s) Used |
|----------|-------------|
| Data Storage | [CSV files, BigQuery] |
| Data Processing | Python, Tableau and Excel] |
| Analysis | [pandas] |
| Visualization | [Matplotlib, Tableau] |
| Documentation | [Markdown] |


## 5. Data Workflow

<!--
  Show how data moved through your project - from source to output.
  Every transformation decision should be traceable here.

  WHAT GOOD LOOKS LIKE:
  1. Source: "Monthly CSV exports pulled from the internal POS system.
              Five files, one per region, covering Jan 2023–Jun 2024."
  2. Ingestion: "Loaded into Python using pandas. Files concatenated into
                 a single dataframe (approx. 340,000 rows)."
  3. Cleaning: "Removed 1.2% of rows with null transaction IDs.
                Standardised date formats across regional files.
                Resolved product category naming inconsistencies (3 variants → 1)."
  4. Transformation: "Created a returns_rate field at product-category level.
                      Aggregated to weekly and regional grain for trend analysis."
  5. Analysis: "Descriptive statistics, regional comparison, return rate
                segmentation by product category."
  6. Output: "Summary report (PDF), annotated notebook, processed CSV."

  WHAT TO AVOID:
  ❌ "Data was cleaned and analysed." (No chain. No decisions. No trust.)
-->

```
[Data Source(s)]
      ↓
[Ingestion / Collection Method]
      ↓
[Cleaning & Transformation]
      ↓
[Analysis / Modelling / Querying]
      ↓
[Output / Visualisation / Reporting]
```

1. **Source:** [CSV files pulled from Kaggle for the weather parameters with monthly and yearly Energy Consumption [Watt.hour] covering 2017 - 2022.]
2. **Ingestion:** [ Loaded into Python using pandas. a file that has 196,776 rows and 17 columns, another dataframe used for Antwerp, Belgium weather conditions loaded with 133669 rows and 11 columns.]
3. **Cleaning:** [The percentage of null values across all columns is 0%]
4. **Transformation:** [Created columns for fate parts: Year, Month, Day and Hour.]
5. **Analysis:** [Descriptive statistics, weather conditions correlations and comparison. ]
6. **Output:** [Summary report and processed CSV with synthesized recommendations.]

## 8. Analysis & Metrics

<!--
  Explain what you measured and how - before you share what you found.

  WHAT GOOD LOOKS LIKE:
  Metric: "Customer Return Rate"
  Definition: "Number of transactions flagged as returns divided by total
               transactions, calculated at product-category and regional grain."
  Why It Matters: "Return rate - not sales volume - was hypothesised to
                  explain regional revenue gaps. This metric tests that hypothesis."

  WHAT TO AVOID:
  ❌ Defining a metric only in code: SUM(returns) / COUNT(transaction_id)
     That's an implementation. Write the plain-language definition here.
     Both belong in your project - the definition in the README,
     the implementation in the code.
-->
Metric #1: Antwerp Weather Conditions  (%)
Definition: percentage of most frequent weather in Antwerp over the years.
Why It Matters: to support the choice of chossing this region

Metric #2: Energy by Weather Type
Definition: which weather type where the Energy Consumption [W.h] is most
Why It Matters: to support the hypothesis of optimal weather conditions for solar installment in Antwerp.

Metric #3: Clouds %, Temperarture and Sun % in 2019 over months Line Chart
Definition: line chart of month vs % of Sunny, Clouds, and Average Temperature. 
Why It Matters: to pinpoint the optimal condition that could support high energy production from solar panels.

Metric #4: Energy by Hour - Max GHI by Hour
Definition: Hourly chart of energy delta (Wh) and Global Horizontal Irradiance (Watt/m^2), peaking at 10:00 AM.
Why It Matters: Pinpoints daily production peaks, Antwerp reached approx, 1,960 W.h and 93 W/m^2 at 10 AM, guiding grid planners on when solar contribution is strongest.

Metric #5: Relationship between Solar Radiation and Energy Consumption (Scatter Plot)
Definition: Scatter plot of GHI vs. energy consumption (W.h)
Why It Matters: Shows a strong correlation (0.91) between solar irradiance and energy output, proving GHI is the most critical driver of solar performance.

Metric #6: Solar Radiation (GHI) and Temperarture by Month (2017-2022) 
Definition:  Monthly averages of GHI (W/m²), temperature (°C), and energy delta (Wh).
Why It Matters: Highlights seasonal variation, summer peaks boost efficiency, while winter drops require panel tilt optimization to capture lower-angle sunlight.

Metric #7: Energy Consumption over 24 hour (Line Chart)
Definition: Hourly energy delta (Wh) across a full day.
Why It Matters: Reveals daily demand and production cycles, low activity at night, rising with daylight, and peaking midday at 10 AM.



### Analytical Approach

I approached the analysis as an exploratory study of patterns in solar energy performance. First, I selected Antwerp, Belgium because of its moderate climate and urban sustainability relevance. I began by checking the Energy Consumption delta [Wh] under clear weather to establish a baseline. Then I examined 2019 monthly variations in temperature, sunshine, and cloud cover to see if these conditions could in principle support high solar output. Moving to the hourly scale, I identified 10:00 AM as the peak energy consumption hour, which directly reflected the Global Horizontal Irradiance (GHI) peak of 93 W/m². Extending this across the full dataset (2012–2020), I confirmed that summer months consistently produced the highest energy output, reinforcing seasonal dependency. To validate system performance, I analyzed AC/DC power generation and inverter efficiency over daily cycles, showing ~980 kW DC converted to ~957 kW AC with ~97% efficiency. Finally, I benchmarked this against the EN 50524 European standard, confirming compliance.

From this exploration, I concluded that GHI is the most critical driver (correlation 0.91), Antwerp’s climate (~46% cloud cover, ~20 °C) provides favorable conditions, and maintaining efficiency requires seasonal panel tilt, operating temperatures within 20–25 °C, storage integration, and diversified infrastructure to maximize year‑round solar output.


### Key Metrics Defined

| Metric | Plain-Language Definition | Why It Matters |
|--------|--------------------------|----------------|
| `[Metric 1]` | [Average energy output (Wh) under clear, cloudy, and rainy conditions.] | [Shows how weather variability directly impacts solar generation, highlighting clear skies as optimal.] |
| `[Metric 2]` | [Monthly averages of cloud cover, sunshine percentage, and ambient temperature.] | [Identifies the combination of conditions (e.g., June’s 20 °C, 70% sun, 46% clouds) that maximize panel efficiency.] |
| `[Metric 3]` | [Energy delta (Wh) and Global Horizontal Irradiance (W/m²) measured across 24 hours.] | [Pinpoints peak production at 10:00 AM, guiding grid planning and storage alignment.] |
| `[Metric 4]` | [Daily cycle of DC power captured, AC power delivered, and inverter efficiency.] | [Validates conversion reliability (~97%) and compliance with EN 50524 standards.] |

### Methods Used

- [Descriptive statistics: distribution of energy output by weather type.]
- [Trend analysis: seasonal variation in GHI, temperature, and energy consumption (2012–2020).]
- [Segmentation : grouping by clear, cloudy, and rainy conditions.]
- [Correlation analysis between [GHI] and [energy output (r = 0.91)]]
- [Benchmarking:  compared inverter efficiency against European EN 50524 standard.]

---

## 9. Key Insights

<!--
  Findings + implications. Not just what happened - what it means.

  WHAT GOOD LOOKS LIKE:
  ✅ "Return rates, not sales volume, explain Region A's underperformance.
      Region A's return rate on home goods was 34% - more than double the
      company average. Revenue was not lost at the point of sale; it was
      lost post-sale through refunds. This points to a fulfilment or
      product quality issue specific to that region, not a demand problem."

  WHAT TO AVOID:
  ❌ "Region A had lower revenue than other regions in Q4."
     (That's an observation. It describes what happened.
      An insight says what it means and where to look next.)

  Aim for 3–6 insights. Quality over quantity.
-->

**Insight 1: [Antwerp’s climate is favorable ]**
[With ~46% cloud cover and ~20 °C average temperatures, Antwerp provides conditions that align with the ideal photovoltaic operating range (20–25 °C). This suggests moderate climates can sustain high efficiency without overheating risks.]

**Insight 2: [Solar radiation drives output]**
[Energy production is tightly correlated with GHI (0.91), confirming irradiance as the single most critical driver of solar performance. This means grid planners should prioritize irradiance forecasting over other weather variables.]

**Insight 3: [Daily and seasonal peaks matter]**
[Energy consistently peaks at 10:00 AM and during summer months, showing predictable cycles. This implies storage and demand-side management should be aligned with these peak windows to maximize utilization.]

**Insight 4: [Efficiency is reliable and standardized  ]**
Inverter efficiency averaged ~97%, matching EN 50524 standards. This validates that nearly all captured solar energy is delivered as usable electricity, reinforcing confidence in system design and scalability.

---

## 10. Recommendations

<!--
  Action-oriented. Addressed to a real audience.
  Tied explicitly to the insight that supports each one.

  WHAT GOOD LOOKS LIKE:
  Priority: High
  Recommendation: "Conduct a fulfilment audit for home goods deliveries
                   in Region A - specifically investigating whether returns
                   correlate with a particular warehouse, carrier, or SKU batch."
  Based On: Insight 1 - return rate anomaly in Region A
  Owner: Operations / Supply Chain team

  WHAT TO AVOID:
  ❌ "Improve the return rate."
     (Not actionable. Doesn't say who, how, or where to start.)
  ❌ "Further analysis is needed."
     (This is a placeholder, not a recommendation.)
-->

| Priority | Recommendation | Based On | Suggested Owner |
|----------|---------------|----------|-----------------|
| High | [Implement real‑time monitoring of Global Horizontal Irradiance (GHI) to forecast solar output and align grid planning.] | [Insight 1 – GHI correlation coefficient of 0.91 with energy output.] | [Grid Operations / Energy Analytics Team] |
| High | [Adopt seasonal panel tilt adjustments during winter to maintain ~97% efficiency.] | [Insight 3 – Seasonal variation shows winter drop in GHI and energy output.] | [Solar Plant Engineering Team] |
| Medium | [Maintain panel operating temperatures within 20–25 °C through cooling or tilt strategies.] | [Insight 2 – Antwerp’s climate aligns with ideal photovoltaic range.] | [Plant Maintenance / Technical Operations] |
| Medium | [Integrate battery storage solutions to buffer against daily and seasonal volatility.] | [Insight 3 – Daily peaks at 10:00 AM and summer highs require storage alignment.] | [Infrastructure / Energy Storage Division] |
| Low | [Diversify solar infrastructure locations and designs to maximize year‑round output.] | [Insight 4 – Efficiency validated against EN 50524, but resilience requires diversification.] | [Strategic Planning / Sustainability Office] |

---

## 11. Assumptions & Limitations

<!--
  WHAT GOOD LOOKS LIKE:
  Assumption: "Transaction records were assumed to be complete for all five regions.
               No validation was performed against source system record counts."
  Limitation: "The analysis cannot distinguish between returns initiated by
               the customer vs. returns initiated by the business (e.g., recalls).
               If business-initiated returns are concentrated in Region A, the
               return rate finding may reflect a policy decision, not a quality issue."

  WHAT TO AVOID:
  ❌ Leaving this section blank or writing "None known."
     Every project has limitations. Documenting them is a sign of
     analytical maturity - not a confession of failure.
-->

### Assumptions
- [What did you treat as true without being able to verify?]
- [What simplifications did you make for scope or feasibility?]
- [What domain rules or definitions did you accept as given?]

### Limitations
- [What gaps exist in the data?]
- [What analysis was out of scope but could affect interpretation?]
- [What would a more rigorous version of this project include?]
- [Are there known biases in the data source or collection method?]

> *The goal here is pre-emptive Q&A. What would a thoughtful skeptic push back on? Document the answer here, before they ask.*

---

## 12. Future Enhancements

<!--
  WHAT GOOD LOOKS LIKE:
  ✅ "Automate the monthly data pull from the POS export folder using
      a scheduled Python script, replacing the current manual process."
  ✅ "Expand the return rate analysis to include carrier-level data,
      which was unavailable in this dataset but exists in the logistics system."

  WHAT TO AVOID:
  ❌ "Add a machine learning model."
     (Vague, and disconnected from the actual findings of this project.)
  ❌ Listing aspirational features that don't follow logically from the work.
-->

- [ ] [Enhancement 1 - specific and traceable to a real gap in this project]
- [ ] [Enhancement 2]
- [ ] [Enhancement 3]
- [ ] [Enhancement 4]

---

## 13. Deliverables

| Deliverable | Description | Location |
|-------------|-------------|----------|
| [Name] | [What it contains] | [`/path/to/file`] |
| [Name] | [What it contains] | [`/path/to/file`] |
| [Name] | [What it contains] | [`/path/to/file`] |

---

## 14. Author

**[Your Name]**
[Your role or title - current or target]

- 🔗 [LinkedIn URL]
- 💼 [Portfolio or GitHub profile URL]
- 📧 [Email - optional]

---

*Last updated: [Month YYYY]*
*If this template helped you, consider starring the repository.*
