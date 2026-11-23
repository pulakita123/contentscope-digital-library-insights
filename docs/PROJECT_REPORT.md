# ContentScope: Digital Library & Catalogue Insights — Project Report

## 1. Introduction

For this project, I wanted to understand how a digital content library changes over time. A catalogue may contain thousands of titles, but the total number alone does not tell a business team whether the mix of content is changing or where new titles are coming from.

I approached the project as a business analysis and reporting task. I focused on catalogue growth, the balance between movies and series, country representation and genre distribution. I then organised these questions into KPIs and an interactive Power BI dashboard.

## 2. Business problem

The main problem was limited visibility into the development of the content library. Stakeholders needed a way to review year-wise additions, compare content formats and explore the contribution of countries and genres without depending on separate static reports.

The objective was to make these patterns easier to understand and investigate.

## 3. Objectives

- Track the number of titles added over time.
- Compare movies and series within the catalogue.
- Understand how the format mix changes across years.
- Explore country and genre contribution.
- Provide filters that allow users to investigate the data from different perspectives.

## 4. Stakeholders

I considered the needs of content strategy, content acquisition, business operations and senior management teams. These stakeholders may use catalogue information for different purposes, so the dashboard needs both a high-level overview and the ability to explore individual dimensions.

## 5. Data understanding and preparation

The project description identifies title, content type, rating, release year and date added as the main title attributes. Country and genre are multi-valued attributes: a title may be associated with more than one country or genre.

For that reason, the intended model separates the core title information from Country and Genre dimensions. Bridge tables connect a title to its countries and genres. This structure is more reliable than treating a comma-separated list as a single value.

The source CSV and Excel workbook are present in the repository. They still need to be inspected for duplicate title IDs, missing dates, inconsistent content-type labels, blank ratings, duplicate bridge pairs and unmatched keys.

## 6. Analysis approach

I translated the business questions into a small set of measures and report views:

1. Count distinct titles to understand catalogue size.
2. Group titles by Date Added year to review catalogue growth.
3. Compare movie and series counts and shares.
4. Compare movie and series additions over time.
5. Explore title representation by country.
6. Explore title representation by genre.
7. Use year, type, country and genre slicers to let stakeholders investigate patterns.

I kept Date Added separate from Release Year because they describe different events. A title's release year does not tell us when it was added to the library.

## 7. Key observations

The original dashboard summary records three broad observations:
- content additions increased in later years;
- series content grew faster than movies over time; and
- content sourcing became more geographically diverse.

These are descriptive observations, not causal conclusions. Exact values, year-on-year percentages and the time period need to be validated against the original source data and Power BI report before they are quoted as numerical results.

## 8. Business interpretation

The patterns can help content strategy teams understand how the catalogue is developing. The movie-versus-series comparison can highlight changes in format composition, while country and genre views can help teams explore representation.

However, catalogue presence is not the same as audience demand. A country or genre appearing frequently does not prove that viewers prefer it. Viewership, watch time, completion, customer feedback and licensing cost data would be required to answer those questions.

## 9. Limitations

The described metadata supports catalogue and content-mix analysis. It does not contain the performance and financial information needed to calculate:
- views or watch time;
- completion or abandonment rates;
- subscriber retention;
- revenue or licensing cost; or
- return on content investment.

The repository contains the original CSV, Excel workbook and PBIX file. Their presence is confirmed, but the exact numeric results and internal Power BI implementation remain to be verified.

## 10. Recommendations and future work

If I were extending this project, I would:
- confirm and document the original source dataset and its licence;
- inspect the existing workbook and validate all headline KPIs independently;
- document the Power BI model, visuals and DAX measures;
- add viewership and completion data to compare content supply with audience demand;
- add licensing costs and revenue to analyse content economics; and
- create a title-level drill-through view for more detailed exploration.

## 11. Conclusion

This project helped me practise translating a broad business question into measurable requirements, organising data around a clear model and presenting trends in an interactive report. The main value is not just the visuals; it is the structure behind them—clear questions, consistent KPI definitions, careful treatment of multi-valued attributes and honest interpretation of what the available data can support.
