# Project Status & Reproducibility

## What was available during this repository review

The GitHub integration returned the repository's README, including one embedded dashboard preview and the original project description.

Attempts to retrieve likely source-data and PBIX filenames did not return those files. This does not prove that no assets exist under any other filename or directory; it means I could not verify or inspect them through the available file retrieval.

## What has been documented

- Business problem and stakeholder needs
- Business questions and KPI definitions
- Planned data model and bridge-table approach
- Human-readable analysis methodology
- Qualitative findings already stated in the original README
- Requirements-to-KPI traceability
- Limitations and future improvements

## What is still needed for a fully reproducible portfolio project

| Asset | Why it is needed |
|---|---|
| Original source dataset or source link | Verify exact counts and calculations |
| Dataset source and licence/terms | Attribute the data correctly and confirm redistribution permissions |
| Power BI PBIX | Inspect relationships, measures, visuals and slicers |
| Exact DAX measures | Let reviewers understand the KPI logic |
| Data preparation steps or Power Query notes | Explain how raw fields become model tables |
| Verified numeric findings | Support quantified business conclusions |
| Screenshots of all dashboard pages | Show the report clearly in the repository |

## Important note

The documentation deliberately avoids inventing dataset provenance, exact numeric results, DAX code or a PBIX filename. Once the original assets are added, update this status document and complete the validation steps in [Methodology](METHODOLOGY.md).
