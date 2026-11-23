# Limitations & Next Steps

## What this dataset can support

With reliable title metadata, the project can describe:
- catalogue size and additions over time;
- movie and series composition;
- country representation;
- genre distribution; and
- how these measures change under filters.

## What it cannot establish

The metadata described in this project does not provide:
- views or watch time;
- completion or abandonment rates;
- subscriber engagement or retention;
- revenue or licensing costs;
- marketing spend; or
- causal explanations for changes in catalogue additions.

Therefore, a title count should not be described as a popularity measure, and a growing genre share should not be described as proof of stronger audience demand.

## Modelling limitations

A title may have multiple countries and multiple genres. Counts grouped by those attributes are non-additive. Use distinct title counts and explain this behaviour in the report.

Date Added and Release Year represent different events and should not be used interchangeably.

## Next steps

To make the project stronger:
1. restore the source dataset and document its source and reuse terms;
2. include the actual PBIX file and verify its data model;
3. document exact DAX measures and filter behaviour;
4. add a reproducible validation script for headline counts;
5. add viewership and completion data to compare catalogue supply with audience demand;
6. add licensing costs and revenue to understand content economics; and
7. develop a title-level drill-through page for detailed exploration.
