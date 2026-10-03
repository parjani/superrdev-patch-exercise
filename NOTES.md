# Patch Exercise Notes

## Changes Made

Fixed the task search and filtering logic in `TaskRepository.java`.

- Corrected SQL operator precedence by grouping search conditions with parentheses.
- Added assignee and priority fields to the search functionality.
- Ensured archived tasks are consistently excluded from search results.
- Ensured the selected status filter applies to all matching search results.

## Why These Changes?

The original SQL query did not group its AND and OR conditions correctly. Since SQL evaluates AND before OR, archived-task exclusion and status filtering were not consistently applied to every search condition.

Additionally, the original search supported only title and description. I extended it to include assignee and priority.

## Testing and Verification

Manually tested the API and frontend.

- Tested searching by title, description, assignee and priority.
- Tested OPEN, DONE and IN_PROGRESS status filters.
- Verified that the frontend status dropdown displays the expected results.
- Checked pagination and confirmed that the API returns the expected page size.

## Deliberately Not Changed

Kept the existing React and Spring Boot architecture, API response structure, database design and pagination implementation unchanged to avoid unnecessary refactoring.

## Biggest Remaining Risk

Pagination parameters are not yet validated for invalid or excessively large values.

## Tools Used

Used AI tools for debugging assistance and understanding SQL operator precedence. Used VS Code, PowerShell, Maven, Git and browser testing during development.
