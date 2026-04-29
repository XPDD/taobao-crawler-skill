---
name: taobao-crawler
description: "This skill should be used when the user wants to start a Taobao product crawling task. It prompts for a keyword and collection volume, then sends a POST request to the local crawl API at http://127.0.0.1:8000/api/crawl/start to trigger the crawl job. Triggers: 启动淘宝爬虫, 爬取淘宝商品, 淘宝采集, start taobao crawl, taobao spider."
agent_created: true
---

# Taobao Crawler Skill

## Purpose

Launch a Taobao product crawl job by collecting user inputs (keyword + volume), generating a unique `request_id`, and sending a POST request directly via curl to the local crawl API.

## When to Use

Load this skill when the user asks to:
- Start / launch a Taobao crawl task
- Collect / scrape Taobao products by keyword
- 启动淘宝爬虫 / 淘宝商品采集

## How to Execute

### Step 1: Collect Inputs

Ask the user for:
- `keyword` — the search keyword (关键字)
- `volume` — number of items to collect (采集数量)

### Step 2: Build the Request

Generate a `request_id` from the current timestamp in format `YYYYMMDDHHmmss`.

### Step 3: Execute curl

Construct and run the following curl command (no wrapper scripts needed):

**macOS / Linux:**
```bash
curl -X POST "http://127.0.0.1:8000/api/crawl/start" \
  -H "Content-Type: application/json" \
  -d '{
    "keyword": "KEYWORD",
    "platform": "taobao",
    "collection_volume": NUMBER,
    "platform_parameter": {
      "shop_name": "旗舰店",
      "db_unique": true
    },
    "request_id": "REQUEST_ID"
  }'
```

**Windows (PowerShell):**
```powershell
curl.exe -X POST "http://127.0.0.1:8000/api/crawl/start" -H "Content-Type: application/json" -d "{'keyword':'KEYWORD','platform':'taobao','collection_volume':NUMBER,'platform_parameter':{'shop_name':'旗舰店','db_unique':true},'request_id':'REQUEST_ID'}"
```

### Step 4: Report

Show the API response to the user, including the `request_id` for tracking.

## Notes

- The local crawl service must be running on `127.0.0.1:8000` before starting.
- `db_unique: true` deduplicates results in the database.
- `shop_name: "旗舰店"` filters for official flagship stores only (adjust if needed).
- No batch scripts are needed — use direct curl calls only.
