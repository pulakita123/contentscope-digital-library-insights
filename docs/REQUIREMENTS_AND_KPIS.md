# Requirements & KPI Traceability

This document connects stakeholder questions to the measures and dashboard components needed to answer them.

| ID | Business requirement | KPI / analysis | Suggested visual | Intended stakeholder |
|---|---|---|---|---|
| BR-01 | Understand catalogue size | Distinct title count | KPI card | Senior management |
| BR-02 | Track additions over time | Distinct titles by Date Added year | Column or line chart | Content strategy |
| BR-03 | Compare content formats | Movie and series title count/share | Stacked column or donut | Content strategy |
| BR-04 | Understand format change | Movie and series additions by year | Multi-series line chart | Content strategy |
| BR-05 | Explore country representation | Distinct titles by country | Bar chart or map, if geography is reliable | Acquisition team |
| BR-06 | Explore genre representation | Distinct titles by genre | Bar chart | Content strategy |
| BR-07 | Filter the analysis | Year, type, country and genre filters | Slicers | All stakeholders |
| BR-08 | Inspect underlying records | Title-level metadata | Detail table | Business operations |

## KPI definitions

**Total titles:** distinct count of Content ID in the selected filter context.

**Titles added by year:** distinct count of Content ID grouped by year of Date Added.

**Movie/series distribution:** distinct title count by content type. The percentage denominator should be the distinct title count under the same filter context.

**Country contribution:** distinct title count associated with each country. Because a title can be associated with multiple countries, country totals may exceed the overall distinct title count when added together.

**Genre contribution:** distinct title count associated with each genre. Genre totals may also exceed the overall distinct title count when added together.

## Acceptance criteria

- KPI cards respond consistently to the report's slicers.
- Date Added and Release Year are not mixed.
- Multi-country and multi-genre titles are handled without accidental double-counting in overall title KPIs.
- Visual titles and tooltips explain whether a measure is a count, share or year-over-year change.
- The dashboard does not label catalogue presence as popularity or audience engagement.
