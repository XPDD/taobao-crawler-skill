# taobao-crawler-skill

A [WorkBuddy](https://www.codebuddy.cn) Skill for launching Taobao product crawl tasks via direct curl API calls.

## Overview

This skill automates launching Taobao product crawl jobs by collecting user inputs (keyword + volume), generating a unique `request_id`, and sending a POST request to your local crawl API.

## Features

- Interactive keyword and volume collection
- Auto-generates timestamp-based `request_id`
- Direct curl calls (no wrapper scripts)
- Supports macOS, Linux, and Windows (PowerShell)

## Usage

In WorkBuddy, simply say:
- "启动淘宝爬虫"
- "爬取 XXX 商品"
- "淘宝采集"
- "taobao spider"

## API Endpoint

```
POST http://127.0.0.1:8000/api/crawl/start
```

## Request Format

```json
{
  "keyword": "手机",
  "platform": "taobao",
  "collection_volume": 100,
  "platform_parameter": {
    "shop_name": "旗舰店",
    "db_unique": true
  },
  "request_id": "20260429180234"
}
```

## Requirements

- WorkBuddy installed
- Local crawl service running on `127.0.0.1:8000`

## Install

Clone this repo to your WorkBuddy skills directory:

```bash
cp -r taobao-crawler-skill ~/.workbuddy/skills/
```
