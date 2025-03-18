# Report API Documentation

## Overview

These are the `reportNames` that can be called from the UI. To test, we have exposed the `/runReportSwagger` endpoint.

## Available Reports

| Report Name | Handler Function |
| ----------- | ---------------- |
| [`GET_VIEW_BY_VIEW_ID`](#getviewbyviewid) | `handle_get_view` |
| [`GET_VIEWS_BY_OWNER_ID`](#getviewsbyownerid) | `handle_get_views_by_owner` |
| [`GET_VIEW_WITH_SHARES_BY_VIEW_ID`](#getviewwithsharesbyviewid) | `handle_get_view_with_shares` |
| [`GET_VIEWS_WITH_SHARES_BY_OWNER_ID`](#getviewswithsharesbyownerid) | `handle_get_views_with_shares_by_owner` |
| [`GET_VIEWS_SHARED_BY_SHARED_TO`](#getviewssharedbysharedto) | `handle_get_shared_views` |
| [`GET_VIEWS_BY_OWNER_ID_SHARED_WITH_LIST_GROUP_OPTIONAL`](#getviewsbyowneridsharedwithlistgroupoptional) | `handle_get_all_views_for_user` |
| [`CREATE_VIEW`](#createview) | `handle_create_view` |
| [`SHARE_VIEW`](#shareview) | `handle_create_share_view` |
| [`CLONE_SHARE_VIEW_BY_VIEW_ID_TO_NEW_OWNER_ID`](#cloneshareviewbyviewidtonewownerid) | `handle_clone_shared_view` |
| [`UPDATE_VIEW`](#updateview) | `handle_update_view` |
| [`DELETE_VIEW`](#deleteview) | `handle_delete_view` |
| [`DELETE_SHARES`](#deleteshares) | `handle_delete_shares` |

## Attribute Constraints

- **ViewType** must be one of: `"template"`, `"view"`, or `"dataset"`
- **TargetType** must be one of: `"USER"` or `"GROUP"`

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
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
    "reportName": "GET_VIEW_BY_VIEW_ID",
    "reportParams": "{\"Param\":[{\"name\":\"view_id\",\"value\":\"1\"}]}"
}'
```

### GET_VIEWS_BY_OWNER_ID

#### Summary

Retrieve all views owned by a specific user.

#### Request Parameters

```json
{
    "reportName": "GET_VIEWS_BY_OWNER_ID",
    "reportParams": "{\"Param\":[{\"name\":\"owner_id\",\"value\":\"shehzada\"}]}"
}
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
    "reportName": "GET_VIEWS_BY_OWNER_ID",
    "reportParams": "{\"Param\":[{\"name\":\"owner_id\",\"value\":\"shehzada\"}]}"
}'
```

### GET_VIEW_WITH_SHARES_BY_VIEW_ID

#### Summary

Retrieve a view along with its share details.

#### Request Parameters

```json
{
    "reportName": "GET_VIEW_WITH_SHARES_BY_VIEW_ID",
    "reportParams": "{\"Param\":[{\"name\":\"view_id\",\"value\":\"1\"}]}"
}
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
    "reportName": "GET_VIEW_WITH_SHARES_BY_VIEW_ID",
    "reportParams": "{\"Param\":[{\"name\":\"view_id\",\"value\":\"1\"}]}"
}'
```

### GET_VIEWS_WITH_SHARES_BY_OWNER_ID

#### Summary

Retrieve all views with share information for a specific owner.

#### Request Parameters

```json
{
    "reportName": "GET_VIEWS_WITH_SHARES_BY_OWNER_ID",
    "reportParams": "{\"Param\":[{\"name\":\"owner_id\",\"value\":\"shehzada\"}]}"
}
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
    "reportName": "GET_VIEWS_WITH_SHARES_BY_OWNER_ID",
    "reportParams": "{\"Param\":[{\"name\":\"owner_id\",\"value\":\"shehzada\"}]}"
}'
```

### GET_VIEWS_SHARED_BY_SHARED_TO

#### Summary

Retrieve all views shared with a specific user or group.

#### Request Parameters

```json
{
    "reportName": "GET_VIEWS_SHARED_BY_SHARED_TO",
    "reportParams": "{\"Param\":[{\"name\":\"shared_to\",\"value\":\"cash_eu\"},{\"name\":\"target_type\",\"value\":\"GROUP\"}]}"
}
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
    "reportName": "GET_VIEWS_SHARED_BY_SHARED_TO",
    "reportParams": "{\"Param\":[{\"name\":\"shared_to\",\"value\":\"cash_eu\"},{\"name\":\"target_type\",\"value\":\"GROUP\"}]}"
}'
```

### GET_VIEWS_BY_OWNER_ID_SHARED_WITH_LIST_GROUP_OPTIONAL

#### Summary

Retrieve all views owned by a user and views shared with them.

#### Request Parameters

```json
{
    "reportName": "GET_VIEWS_BY_OWNER_ID_SHARED_WITH_LIST_GROUP_OPTIONAL",
    "reportParams": "{\"Param\":[{\"name\":\"owner_id\",\"value\":\"shehzada\"},{\"name\":\"include_groups\",\"value\":\"true\"}]}"
}
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
    "reportName": "GET_VIEWS_BY_OWNER_ID_SHARED_WITH_LIST_GROUP_OPTIONAL",
    "reportParams": "{\"Param\":[{\"name\":\"owner_id\",\"value\":\"shehzada\"},{\"name\":\"include_groups\",\"value\":\"true\"}]}"
}'
```

### CREATE_VIEW

#### Summary

Creates a new view entry and returns the generated `view_id`.

#### Request Parameters

```json
{
  "reportName": "CREATE_VIEW",
  "reportParams": "{\"Param\": [{\"name\": \"view_name\", \"value\": \"EU JPM Q1 Report\"}, {\"name\": \"view_template\", \"value\": \"{\\\"tnl\\\": \\\"TNL0001234\\\", \\\"strategey\\\": \\\"vwap\\\"}\"}, {\"name\": \"owner_id\", \"value\": \"haridass\"}, {\"name\": \"view_type\", \"value\": \"dataset\"}]}"
}
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "reportName": "CREATE_VIEW",
  "reportParams": "{\"Param\": [{\"name\": \"view_name\", \"value\": \"EU JPM Q1 Report\"}, {\"name\": \"view_template\", \"value\": \"{\\\"tnl\\\": \\\"TNL0001234\\\", \\\"strategey\\\": \\\"vwap\\\"}\"}, {\"name\": \"owner_id\", \"value\": \"haridass\"}, {\"name\": \"view_type\", \"value\": \"dataset\"}]}"
}'
```

### SHARE_VIEW

#### Summary

Share a view with a user or group and return the generated `shared_id`.

#### Request Parameters

```json
{
  "reportName": "SHARE_VIEW",
  "reportParams": "{\"Param\": [{\"name\": \"view_id\", \"value\": \"13\"}, {\"name\": \"shared_to\", \"value\": \"cash_eu\"}, {\"name\": \"target_type\", \"value\": \"GROUP\"}]}"
}
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "reportName": "SHARE_VIEW",
  "reportParams": "{\"Param\": [{\"name\": \"view_id\", \"value\": \"12\"}, {\"name\": \"shared_to\", \"value\": \"cash_eu\"}, {\"name\": \"target_type\", \"value\": \"GROUP\"}]}"
}'
```

### CLONE_SHARE_VIEW_BY_VIEW_ID_TO_NEW_OWNER_ID

#### Summary

Clone a shared view to a new owner.

#### Request Parameters

```json
{
  "reportName": "CLONE_SHARE_VIEW_BY_VIEW_ID_TO_NEW_OWNER_ID",
  "reportParams": "{\"Param\": [{\"name\": \"view_id\", \"value\": \"13\"}, {\"name\": \"new_owner_id\", \"value\": \"shehzada\"}]}"
}
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "reportName": "CLONE_SHARE_VIEW_BY_VIEW_ID_TO_NEW_OWNER_ID",
  "reportParams": "{\"Param\": [{\"name\": \"view_id\", \"value\": \"13\"}, {\"name\": \"new_owner_id\", \"value\": \"shehzada\"}]}"
}'
```

### UPDATE_VIEW

#### Summary

Update an existing view.

#### Request Parameters

```json
{
  "reportName": "UPDATE_VIEW",
  "reportParams": "{\"Param\": [{\"name\": \"view_id\", \"value\": \"13\"}, {\"name\": \"view_name\", \"value\": \"Updated EU JPM Q1 Report\"}, {\"name\": \"view_template\", \"value\": \"{\\\"tnl\\\": \\\"TNL0001234\\\", \\\"strategey\\\": \\\"twap\\\"}\"}, {\"name\": \"view_type\", \"value\": \"view\"}]}"
}
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "reportName": "UPDATE_VIEW",
  "reportParams": "{\"Param\": [{\"name\": \"view_id\", \"value\": \"13\"}, {\"name\": \"view_name\", \"value\": \"Updated EU JPM Q1 Report\"}, {\"name\": \"view_template\", \"value\": \"{\\\"tnl\\\": \\\"TNL0001234\\\", \\\"strategey\\\": \\\"twap\\\"}\"}, {\"name\": \"view_type\", \"value\": \"view\"}]}"
}'
```

### DELETE_VIEW

#### Summary

Delete a view by its ID.

#### Request Parameters

```json
{
  "reportName": "DELETE_VIEW",
  "reportParams": "{\"Param\": [{\"name\": \"view_id\", \"value\": \"13\"}]}"
}
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "reportName": "DELETE_VIEW",
  "reportParams": "{\"Param\": [{\"name\": \"view_id\", \"value\": \"13\"}]}"
}'
```

### DELETE_SHARES

#### Summary

Delete shares for a specific view.

#### Request Parameters

```json
{
  "reportName": "DELETE_SHARES",
  "reportParams": "{\"Param\": [{\"name\": \"view_id\", \"value\": \"13\"}, {\"name\": \"shared_to\", \"value\": \"cash_eu\"}, {\"name\": \"target_type\", \"value\": \"GROUP\"}]}"
}
```

#### CURL Command

```sh
curl -X 'POST' \
  'shehzada_local_endpoint/runReportSwagger' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "reportName": "DELETE_SHARES",
  "reportParams": "{\"Param\": [{\"name\": \"view_id\", \"value\": \"13\"}, {\"name\": \"shared_to\", \"value\": \"cash_eu\"}, {\"name\": \"target_type\", \"value\": \"GROUP\"}]}"
}'
```


import os
import re
import markdown
from fastapi import FastAPI
from fastapi.responses import HTMLResponse

app = FastAPI()

@app.get("/docs/readme", response_class=HTMLResponse)
async def get_readme():
    readme_path = os.path.join(os.path.dirname(__file__), "README.md")
    with open(readme_path, "r", encoding="utf-8") as f:
        content = f.read()
    
    # Process table links before markdown conversion
    def add_links_to_table(match):
        report_name = match.group(1).strip('`')
        handler_func = match.group(2).strip('`')
        return f"| [`{report_name}`](#{''.join(report_name.lower().split('_'))}) | `{handler_func}` |"
    
    # Find the table and add links to report names
    pattern = r"\| `([A-Z_]+)` \| `([a-z_]+)` \|"
    content = re.sub(pattern, add_links_to_table, content)
    
    # Convert Markdown to HTML with extensions
    html_content = markdown.markdown(
        content,
        extensions=["tables", "fenced_code", "codehilite"]
    )
    
    # Simple HTML template with built-in styling
    html_template = f"""
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Report API Documentation</title>
        <!-- GitHub Markdown CSS -->
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/github-markdown-css/5.2.0/github-markdown-light.min.css">
        <!-- Code highlighting CSS -->
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/styles/github.min.css">
        <style>
            body {{
                max-width: 980px;
                margin: 0 auto;
                padding: 45px;
                font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif;
            }}
            
            table {{
                border-collapse: collapse;
                width: 100%;
                margin: 16px 0;
            }}
            
            table th, table td {{
                border: 1px solid #dfe2e5;
                padding: 8px 13px;
            }}
            
            table tr:nth-child(even) {{
                background-color: #f8f8f8;
            }}
            
            pre {{
                background-color: #f6f8fa;
                border-radius: 6px;
                padding: 16px;
                overflow: auto;
            }}
            
            @media (max-width: 767px) {{
                body {{
                    padding: 15px;
                }}
            }}
        </style>
    </head>
    <body class="markdown-body">
        {html_content}
        
        <!-- Highlight.js for code highlighting -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js"></script>
        <script>hljs.highlightAll();</script>
    </body>
    </html>
    """
    
    return HTMLResponse(content=html_template)
