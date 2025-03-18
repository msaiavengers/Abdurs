# Report API Documentation

## Overview

This API provides endpoints to manage and retrieve reports. The `reportNames` listed below can be called from the UI. For testing, use the exposed `/runReportSwagger` endpoint.

## Available Reports

| Report Name                                             | Handler Function                        |
|---------------------------------------------------------|-----------------------------------------|
| [`GET_VIEW_BY_VIEW_ID`](#get_view_by_view_id)           | `handle_get_view`                       |
| [`GET_VIEWS_BY_OWNER_ID`](#get_views_by_owner_id)       | `handle_get_views_by_owner`             |
| [`GET_VIEW_WITH_SHARES_BY_VIEW_ID`](#get_view_with_shares_by_view_id) | `handle_get_view_with_shares`     |
| [`GET_VIEWS_WITH_SHARES_BY_OWNER_ID`](#get_views_with_shares_by_owner_id) | `handle_get_views_with_shares_by_owner` |
| [`GET_VIEWS_SHARED_BY_SHARED_TO`](#get_views_shared_by_shared_to) | `handle_get_shared_views`         |
| [`GET_VIEWS_BY_OWNER_ID_SHARED_WITH_LIST_GROUP_OPTIONAL`](#get_views_by_owner_id_shared_with_list_group_optional) | `handle_get_all_views_for_user` |
| [`CREATE_VIEW`](#create_view)                           | `handle_create_view`                    |
| [`SHARE_VIEW`](#share_view)                             | `handle_create_share_view`              |
| [`CLONE_SHARE_VIEW_BY_VIEW_ID_TO_NEW_OWNER_ID`](#clone_share_view_by_view_id_to_new_owner_id) | `handle_clone_shared_view` |
| [`UPDATE_VIEW`](#update_view)                           | `handle_update_view`                    |
| [`DELETE_VIEW`](#delete_view)                           | `handle_delete_view`                    |
| [`DELETE_SHARES`](#delete_shares)                       | `handle_delete_shares`                  |

## Attribute Constraints

- **ViewType**: Must be one of `"template"`, `"view"`, or `"dataset"`
- **TargetType**: Must be one of `"USER"` or `"GROUP"`

## API Endpoints

### GET_VIEW_BY_VIEW_ID

#### Summary
Retrieve details of a specific view by its ID.

#### Request Parameters
```json
{
    "reportName": "GET_VIEW_BY_VIEW_ID",
    "reportParams": "{\"Param\":[{\"name\":\"view_id\",\"value\":\"1\"}]}"
}

curl -X 'POST' \
  'shehzada_local_endpointrunReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
    "reportName": "GET_VIEW_BY_VIEW_ID",
    "reportParams": "{\"Param\":[{\"name\":\"view_id\",\"value\":\"1\"}]}"
}'



/* static/styles.css */
.markdown-body {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif;
}

.markdown-body h1, .markdown-body h2, .markdown-body h3 {
    border-bottom: 1px solid #eaecef;
    padding-bottom: 0.3em;
}

.markdown-body table {
    border-collapse: collapse;
    width: 100%;
}

.markdown-body table th, .markdown-body table td {
    border: 1px solid #dfe2e5;
    padding: 6px 13px;
}

.markdown-body table th {
    background-color: #f6f8fa;
}

.markdown-body pre {
    background-color: #f6f8fa;
    padding: 16px;
    border-radius: 6px;
    overflow: auto;
}


#### Key Improvements:
- Consistent header levels (`#`, `##`, `###`).
- Proper spacing around sections.
- Code blocks explicitly marked with language (e.g., ` ```json` or ` ```bash`).
- Fixed typos and improved readability.

Save this as `README.md`.

### 2. Enhancing Your FastAPI Serving Code
Your code is mostly fine, but the custom `styles.css` file isn't being served (you referenced it but didn't show how it's hosted), and the GitHub CSS might need some tweaks for better styling. Here's an updated version:

#### Updated FastAPI Code
```python
import os
import markdown
from fastapi import FastAPI
from fastapi.responses import HTMLResponse
from fastapi.staticfiles import StaticFiles

app = FastAPI()

# Mount a static directory to serve CSS files
app.mount("/static", StaticFiles(directory="static"), name="static")

@app.get("/docs/readme", response_class=HTMLResponse)
async def get_readme():
    readme_path = os.path.join(os.path.dirname(__file__), "README.md")
    with open(readme_path, "r", encoding="utf-8") as f:
        content = f.read()

    # Convert Markdown to HTML with extensions
    html_content = markdown.markdown(
        content,
        extensions=["tables", "fenced_code", "codehilite"]
    )

    # HTML template with improved styling
    html_template = f"""
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <title>Report API Documentation</title>
        <!-- GitHub Markdown CSS -->
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/github-markdown-css/5.1.0/github-markdown-light.min.css">
        <!-- Code highlighting CSS -->
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/styles/default.min.css">
        <!-- Custom Styles -->
        <link rel="stylesheet" href="/static/styles.css">
        <style>
            .markdown-body {{
                box-sizing: border-box;
                min-width: 200px;
                max-width: 980px;
                margin: 0 auto;
                padding: 45px;
            }}
            @media (max-width: 767px) {{
                .markdown-body {{
                    padding: 15px;
                }}
            }}
        </style>
    </head>
    <body>
        <article class="markdown-body">
            {html_content}
        </article>
        <!-- Highlight.js for code highlighting -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js"></script>
        <script>hljs.highlightAll();</script>
    </body>
    </html>
    """

    return HTMLResponse(content=html_template)

