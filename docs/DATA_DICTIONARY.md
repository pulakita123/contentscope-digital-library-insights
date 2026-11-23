# Data Dictionary & Modelling Notes

The definitions below describe the fields identified in the project's original README. Confirm the exact column names and data types against the original source file before implementing the model.

## Content table

| Business field | Meaning | Suggested type | Notes |
|---|---|---|---|
| Content ID | Unique identifier for a title | Text | Preferred primary key; use a stable source ID |
| Title | Display name of the title | Text | Not guaranteed unique |
| Type | Movie or TV series | Text/category | Standardise labels |
| Rating | Content classification | Text/category | Missing values should remain explicitly unknown |
| Release Year | Year the title was released | Whole number | Not the same as date added |
| Date Added | Date the title entered the library | Date | Main date for catalogue-growth analysis |

## Country dimension and bridge

| Table | Field | Meaning |
|---|---|---|
| Country | Country ID | Unique country key |
| Country | Country Name | Standardised country label |
| Content_Country | Content ID | Related title |
| Content_Country | Country ID | Related country |

A title can be associated with more than one country. Store one title-country pair per bridge-table row. Do not treat a comma-separated list as one country value.

## Genre dimension and bridge

| Table | Field | Meaning |
|---|---|---|
| Genre | Genre ID | Unique genre key |
| Genre | Genre Name | Standardised genre label |
| Content_Genre | Content ID | Related title |
| Content_Genre | Genre ID | Related genre |

A title can have multiple genres. Store one title-genre pair per bridge-table row.

## Date table

| Field | Meaning |
|---|---|
| Date | Continuous calendar date |
| Year | Calendar year |
| Month Number | Numeric month for correct sorting |
| Month Name | Display label |
| Quarter | Calendar quarter |

The Date table should be related to Content[Date Added] for time-based catalogue-addition analysis. Release Year should remain a separate attribute because it measures a different event.

## Data quality checks to perform

- Confirm Content ID is unique in the Content table.
- Check for blank titles and invalid or missing dates.
- Standardise Type values (for example, Movie and TV Show).
- Check rating values and preserve missing classifications.
- Parse multi-valued country and genre fields into bridge tables.
- Remove duplicate Content ID–Country ID and Content ID–Genre ID pairs.
- Check for country/genre bridge records that do not match a Content ID.
- Confirm Date Added is parsed consistently and falls within a sensible range.

## Important counting rule

When a title is associated with multiple countries or genres, a simple row count after joining a bridge table can count that title more than once. Use distinct title counts for catalogue KPIs, and explain whether contribution percentages can exceed 100% because titles may belong to multiple groups.
