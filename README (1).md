# SAS DQ Parser

## Overview

**SAS DQ Parser** is a tool designed to process SAS programs, analyze their structure, and extract meaningful blocks of code while identifying the use of Data Quality (DQ) functions. The parser breaks code into manageable components, classifies them, and presents a summary of DQ function usage when applicable. Parsed information can be exported in both JSON and Excel formats for further analysis or reporting.

---

## Features

- **Comment Removal**: Cleans SAS code by removing comments for cleaner analysis.
- **Block Identification**: Splits code into logical sections such as macros, procedures, and data steps.
- **Dependency Analysis**: Maps macro relationships and organizes code execution order using a dependency graph.
- **Block Chunking**: Divides larger code blocks into smaller, manageable chunks based on logical endpoints.
- **Function Detection**: Scans each block for known DQ functions (e.g., `dqMatch`, `dqParse`, `dqStandardize`, `dqRule`).
- **Export Generation**: Produces structured summaries in JSON and Excel, tailored for both technical and non-technical stakeholders.

---

## Functional Workflow

1. **Input Processing**
   - Removes comments and prepares SAS code for parsing.

2. **Block Identification**
   - Detects and segments macros, procedures, and data steps.

3. **Dependency Analysis**
   - Analyzes macro relationships and builds a logical execution order.

4. **Block Chunking**
   - Splits large code blocks into smaller, logical units.

5. **Function Detection**
   - Identifies and counts DQ function usage within each block.

6. **Export Generation**
   - Generates summaries and outputs in JSON and Excel formats.

---

## Behavior Scenarios

### 🧪 Without DQ Functions

- **Structural parsing only**: Identifies all macros, data steps, and procedures.
- **No DQ functions flagged**: Related fields in output are empty or zero.
- **Exports**: JSON and Excel show block identifiers, types, and raw code content, but DQ-specific columns are blank.
- **Usefulness**: Valuable for macro tracing, procedural analysis, and migration—even if no DQ logic is present.

### 🧪 With DQ Functions

- **Structural + DQ analysis**: Detects DQ functions such as `dqMatch`, `dqParse`, `dqStandardize`, etc.
- **Function counting**: Reports how many times each DQ function is used per block.
- **Block labeling**: Marks blocks containing DQ logic.
- **Summary**: Shows total DQ function calls, block count, and function-wise breakdown (in both JSON and Excel).
- **Value**: Helps prioritize code for data cleansing, refactoring, or migration; aids in governance and lineage tasks.

---

## Key Differences: With vs Without DQ

| Attribute                | Without DQ Functions    | With DQ Functions         |
|--------------------------|------------------------|--------------------------|
| Code Chunking            | ✅ Yes                 | ✅ Yes                   |
| Macro & PROC Detection   | ✅ Detected            | ✅ Detected              |
| DQ Function Summary      | 🚫 Empty               | ✅ Populated with counts |
| Block Classification     | ✅ MACRO/PROC/DATA     | ✅ + DQSTATEMENT         |
| Total DQ Function Count  | 0                      | > 0                      |
| Excel/JSON Export        | ✅ Yes                 | ✅ Yes (with DQ metadata)|

---

## Value Proposition

- **Structural Clarity**: Even without DQ logic, the tool reveals the code’s structure and execution flow.
- **Data Quality Insights**: When DQ functions are present, surfaces hidden data-cleansing operations for faster review, audits, and modernization.
- **Flexible Exports**: JSON for integrations, Excel for business/technical review.

---

## Output Examples

### JSON Output

- Lists all blocks with identifiers, types, and code content.
- DQ-specific fields (function names, counts) are populated only if detected.

### Excel Output

- One row per code block.
- Columns for block type, code, DQ function usage, and counts.
- DQ columns empty or zero if none found.

---

## Summary

- The parser adapts based on the presence or absence of DQ functions.
- Always provides a structured breakdown of SAS code.
- DQ detection enhances its value for data governance, auditing, and migration.
- User-friendly exports support both technical and non-technical users.

---

## Getting Started

1. **Input**: Upload or paste your SAS program.
2. **Run Parser**: The tool processes and analyzes your code.
3. **Review Results**: Explore the summary and details in-app.
4. **Export**: Download results in JSON or Excel for further use.

---

## License

[MIT](LICENSE)

---

## Contact

For questions, support, or feature requests, please open an issue or contact the maintainers.
