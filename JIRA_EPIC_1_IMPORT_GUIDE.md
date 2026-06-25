# Jira Import Guide: Epic 1

## Import File

Use `JIRA_EPIC_1_IMPORT.csv`.

## Jira Mapping

The import uses the standard Jira hierarchy:

```text
Epic
└── Story
    └── Sub-task
```

The LMS Features are preserved in the `Component/s` column:

- User Registration and Family Access
- Teacher Account Approval
- Account Administration and Recovery

## CSV Field Mapping

During Jira CSV import, map:

| CSV Column | Jira Field |
| --- | --- |
| Issue ID | Issue ID |
| Issue Type | Issue Type |
| Summary | Summary |
| Description | Description |
| Parent ID | Parent ID |
| Epic Name | Epic Name, if available |
| Component/s | Component/s |
| Labels | Labels |

## Before Import

- Confirm that the Jira project supports Epic, Story, and Sub-task issue types.
- Create the three Components if Jira does not create them during import.
- Confirm that Sub-tasks are enabled.
- Select the target Jira project during the import.
- Map `Parent ID` so Stories are placed under the Epic and FE/BE/QA work is placed under its Story.

## Imported Work Items

- 1 Epic
- 6 Business Stories
- 18 FE, BE, and QA Sub-tasks
- 25 total Jira issues

## Alternative Custom Hierarchy

If the Jira project has a custom `Feature` issue type between Epic and Story, import the current file first using the standard hierarchy. Features can then be created and the Stories moved under them, or a custom-hierarchy CSV can be prepared after confirming the Jira issue-type configuration.
