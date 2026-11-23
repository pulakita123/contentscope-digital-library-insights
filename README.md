# Digital Content Library Analysis | Power BI & Business Analysis

I built this project to understand how a digital content library changes over time. Instead of looking only at the total number of titles, I wanted to explore what was being added, how the mix of movies and series was changing, and how content contributions differed by country and genre.

The project follows a business-analysis approach: define the business questions, translate them into measurable KPIs, organise the data for analysis, and present the results in an interactive dashboard.

> **Project status:** The README and supporting analysis documentation are available here. The connected repository review did not expose the source dataset or Power BI report file, so I have not invented exact numerical findings or claimed that the report is reproducible from this repository yet. See [Project Status & Reproducibility](docs/PROJECT_STATUS.md).

---

## Dashboard preview

<img width="578" height="326" alt="Digital content library analytics dashboard" src="https://github.com/user-attachments/assets/5fd04792-ac51-4036-9a85-17776b21bd80" />

*Dashboard preview currently embedded in the original project README.*

## The business problem

A streaming or digital media platform needs to understand how its content catalogue is developing. A simple title count does not explain whether the catalogue is becoming more diverse, whether the balance between movies and series is changing, or which genres and countries contribute most to new additions.

I approached this as a content strategy and business operations problem. The aim was to give stakeholders a way to explore catalogue composition and growth without depending on static, one-off reports.

### Business questions

1. How has the number of titles added to the library changed over time?
2. How does the catalogue split between movies and TV series?
3. Has the format mix changed across different years?
4. Which countries contribute most to the content catalogue?
5. Which genres appear most frequently?
6. How do these patterns change when the viewer filters by year, content type, country or genre?

### Intended stakeholders

- **Content strategy:** understand catalogue composition and sourcing patterns.
- **Business operations:** monitor changes in the library and prepare periodic reporting.
- **Senior management:** review high-level growth and content mix.
- **Content acquisition teams:** explore geographic and genre representation as an input to further research.

## KPIs and analytical dimensions

| KPI / dimension | What it helps answer |
|---|---|
| Total titles | How large is the catalogue in the selected filter context? |
| Titles added by year | When did catalogue additions increase or decrease? |
| Movie vs. series distribution | What is the format composition of the library? |
| Format trend over time | How has the movie/series mix changed? |
| Country contribution | Which countries are represented in the catalogue? |
| Genre contribution | Which genres appear most often? |
| Date added | When was a title added to the platform/library? |

The measures should use distinct title identifiers where available. Country and genre are multi-valued attributes in many catalogue datasets, so their contribution should be analysed through bridge tables rather than by treating comma-separated text as a single country or genre.

## What the analysis indicates

The original dashboard notes the following patterns:

- Content additions increased in later years.
- Series content grew faster than movie content over time.
- Content sourcing became more geographically diverse.
- Country and genre contributions can be explored interactively.

These are descriptive observations from the dashboard, not evidence that a particular business decision caused the changes. Exact values and the period covered should be added to the findings once the source data and PBIX are restored to the repository and the measures have been independently checked.

See [Key Findings & Interpretation](docs/KEY_FINDINGS.md) for the interpretation and the evidence still required.

## How I approached the analysis

I started by defining the questions a content strategy team might ask before deciding which visuals to build. I then identified the main content attributes needed to answer them: title, content type, rating, release year and date added. Country and genre needed special treatment because a single title can be associated with more than one country or genre.

For the data model, I planned a central Content table supported by Country and Genre dimensions and separate bridge tables. This avoids relying on comma-separated country or genre values and makes filtering more reliable. A Date table based on the date added supports year-based analysis.

After organising the model, I defined the KPIs and built visuals for growth, content format, geography and genre. I used slicers so a stakeholder can explore the same questions for different years, formats, countries and genres.

The detailed workflow, modelling considerations and validation checklist are documented in [Methodology](docs/METHODOLOGY.md).

## Data model

The intended model is:

```text
                    Date
                     |
                     | Date Added
                     |
Content -------- Content_Country -------- Country
   |
   |
   +------------- Content_Genre ---------- Genre
```

**Core table — Content:** one record per title, with title attributes such as content type, rating, release year and date added.

**Country and Content_Country:** country dimension and bridge table to represent titles associated with multiple countries.

**Genre and Content_Genre:** genre dimension and bridge table to represent titles associated with multiple genres.

**Date:** calendar table used for time-based analysis of titles added.

The exact relationship cardinalities and filter directions must be checked in the PBIX model before the diagram is treated as a verified implementation.

## Tools and skills demonstrated

- **Power BI:** dashboard design, slicers, cross-filtering and stakeholder reporting
- **Data modelling:** fact/dimension thinking and bridge tables for multi-valued attributes
- **Business analysis:** problem definition, stakeholder questions, KPI selection and requirements translation
- **Analytical thinking:** trend analysis, content mix comparisons and descriptive interpretation
- **Data storytelling:** presenting catalogue patterns in a way that supports further investigation

## Repository documentation

| Document | Purpose |
|---|---|
| [Business Problem](docs/BUSINESS_PROBLEM.md) | Business context, stakeholders, scope and questions |
| [Data Dictionary](docs/DATA_DICTIONARY.md) | Planned fields, definitions and modelling notes |
| [Methodology](docs/METHODOLOGY.md) | First-person analysis workflow and validation |
| [Key Findings](docs/KEY_FINDINGS.md) | Findings, interpretation and evidence status |
| [Requirements & KPI Mapping](docs/REQUIREMENTS_AND_KPIS.md) | Traceability from business questions to metrics and visuals |
| [Limitations & Next Steps](docs/LIMITATIONS_AND_NEXT_STEPS.md) | What the dataset can and cannot establish |
| [Project Status](docs/PROJECT_STATUS.md) | Files currently available and what is needed for reproducibility |\n| [Project Report](docs/PROJECT_REPORT.md) | A readable end-to-end business analysis report in first person |

## How to reproduce the project

The source data and Power BI file were not available through the repository files that could be retrieved during this review. I have therefore not included made-up download steps, table names or DAX formulas.

To make this project fully reproducible, the repository still needs:
1. the source dataset or a reliable source link and its usage terms;
2. the Power BI `.pbix` file;
3. a clear folder structure for data, report and documentation;
4. the actual DAX measures and relationship definitions; and
5. a checked set of numerical findings.

Once those assets are present, the setup instructions can be completed and tested by another person.

## Limitations

This analysis is based on catalogue metadata. It can describe the library's composition and the timing of content additions, but it cannot measure whether viewers watched, liked or completed a title.

The project does not include:
- views, watch time or completion rate;
- subscriptions, revenue or licensing cost;
- marketing spend or acquisition cost;
- audience demographics or satisfaction; or
- evidence explaining why content additions changed.

For that reason, I interpret the results as catalogue trends rather than content popularity, financial performance or causal impact.

## Future improvements

If I were extending this project, I would:
- add viewership and completion data to compare catalogue supply with audience demand;
- include licensing cost and revenue to understand content economics;
- create a title-level drill-through page;
- add a year-over-year growth measure and a clearly defined comparison period;
- validate country and genre counts against the bridge-table grain; and
- introduce a refreshable data pipeline for regular reporting.

---

*This is a portfolio project demonstrating my approach to translating a business question into analytical requirements, a structured data model and a stakeholder-facing dashboard.*
