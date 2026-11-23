# Analysis Methodology

This is the analytical workflow I used to structure the project. Exact source columns, transformation steps and DAX expressions should be reconciled with the original dataset and PBIX before treating this as a technical implementation record.

## 1. Start with the business question

I began by identifying what a content strategy or operations team would want to understand: catalogue growth, movie-versus-series composition, geographic contribution and genre distribution.

I translated those needs into specific questions and KPIs before deciding which visuals to build.

## 2. Understand the content metadata

The project description identifies title, content type, rating, release year and date added as the main title attributes. Country and genre are multi-valued attributes, because one title can be associated with more than one country or genre.

The first step in a reproducible version is to inspect the source file, confirm the actual field names, record the row count and check whether a stable title identifier exists.

## 3. Prepare the data

The preparation checklist is:
- standardise content-type labels;
- convert release year to a whole number;
- parse Date Added using an explicit locale;
- handle blank ratings and dates consistently;
- trim whitespace from text fields;
- split country and genre values into separate records;
- remove duplicate title-country and title-genre pairs; and
- retain a stable Content ID to link the tables.

Missing values should not be silently replaced with invented categories. If a label such as Unknown is introduced, document that as a modelling choice.

## 4. Build the model

I structured the model around one Content record per title. Country and Genre are separate dimensions, with bridge tables to connect a title to multiple countries and genres.

A Date table supports year and month analysis using Date Added. Release Year is kept separate because it represents the title's release date, not when it entered the library.

Before publishing, validate the relationship cardinalities, filter directions and whether any many-to-many relationships create ambiguous filtering.

## 5. Define KPIs

The planned KPIs include:
- distinct titles;
- titles added by year;
- movie and series counts and shares;
- country contribution;
- genre contribution; and
- format mix over time.

For country and genre analysis, distinct title counts are important. A title with multiple countries or genres can appear in multiple groups, so group totals may not add up to the overall title count.

## 6. Explore trends

I organised the dashboard around four themes:
1. catalogue growth over time;
2. format composition and its change;
3. geographic contribution; and
4. genre contribution.

Slicers for year, content type, country and genre allow the user to explore the same measures under different selections.

## 7. Interpret the results

The dashboard's original summary reports that additions increased in later years, series grew faster than movies over time, and sourcing became more geographically diverse.

These are descriptive patterns. They do not establish why the changes happened, whether the content was successful with viewers, or whether the library became more profitable.

## 8. Validate before publishing

A complete validation should compare:
- total distinct titles with the source file;
- movie and series counts with the raw categories;
- yearly additions with a direct grouped count by Date Added;
- country and genre results with distinct title counts;
- totals under slicers with expected filter behaviour; and
- dashboard KPI cards with independent calculations.

The original dataset and PBIX need to be present to complete these checks. See [Project Status](PROJECT_STATUS.md).
